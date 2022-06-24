---
id: nqzrrukexapiynkc23gtn4m
title: CI/CD
desc: ''
updated: 1656075359129
created: 1648040156022
---


# Writing back to the repo
If you generate a file in the CI/CD process that you want to commit back to the repository then you will need to set up the appropriate git configurations and keys within the project and CI/CD pipeline.

## Personal Access Token
1. Create a PAT token within your repository (`Settings` -> `Access Tokens` with `write_repository` level and whatever role is required to push to the branch the pipeline will be running on (in the case of main it may be protected so you may need to make this `Maintainer` level). Ensure you remember the name and copy the key!
2. Copy this key and create a  CI/CD Variable named `PAT_KEY` (`Settings -> CI/CD -> Variables`) for this key, make sure it is marked as `Protected`.

## yml file
Your `.gitlab-ci/yml` file should contain the following within the `before-script` section of the file

```bash
- git config user.email "ci@example.com"
- git config user.name "CI"
- git remote add main_origin "https://<PAT_token_name>:$PAT_KEY@$CI_SERVER_HOST/$CI_PROJECT_PATH.git"

```
Where `<PAT_token_name>` is the name you gave your token. You also need to make sure that your stage is using an image with git installed, an example lightweight image is be `image: alpine/git`.

The file should also contain some checks to make sure that it doesn't run once it makes a commit itself! This example triggers on any push to main, but won't if the `xyz` file is edited. Find out more details [here](https://docs.gitlab.com/ee/ci/yaml/#only--except).

```bash
only:
    refs:
        - main
    except:
        - xyz
```

An full example script is below

```bash
stages:          # List of stages for jobs, and their order of execution
  - my_push_stage

"This CI job pushes to its own repo":
    stage: my_push_stage
    resource_group: this_option_comes_handy_when_pushing
    only:
        refs:
          - main
    except:
      - xyz
    image: alpine/git
    before_script:
        - git config user.email "ci@example.com"
        - git config user.name "CI"
        - git remote add main_origin "https://cicdpipeline:$PAT_KEY@$CI_SERVER_HOST/$CI_PROJECT_PATH.git"

    script:
        - touch "xyz"  # Make an edit
        - git add "xyz"
        - git commit -m "My CI commit"
        - git push main_origin HEAD:$CI_BUILD_REF_NAME 

```

# Get list of files that have changed in a merge request
To get a list of files that have changed compared to the base branch you can use the command (on an instance with git running e.g. `alpine/git`)
`FILES=$(git diff-tree --name-only --diff-filter=ACM $CI_MERGE_REQUEST_DIFF_BASE_SHA $CI_COMMIT_SHA -r)`.

You can then filter this further using a `grep` however this outputs with a weird separator that I struggle to replace without first writing to a file then loading and replacing new lines. A full example is below that replaces the new lines with some prefix to be used as part of a dynamic pytest call, but this could be simplified or replaced with any other character. It then saves this file as an artefact which can then be loaded in the next stage using the `dependencies:` keyword. 

```yaml
script:
        # change grep in the below to filter to specific files
        - FILES=$(git diff-tree --name-only --diff-filter=ACM $CI_MERGE_REQUEST_DIFF_BASE_SHA $CI_COMMIT_SHA -r | grep 'test') 

        # There has to be a better way to do this but I cannot work it out...
        - prefix=' --fileinput='
        - echo -n "FILES= $FILES" > files_temp.env # send to a file (with no newline at end, -n) now because replacing a new line in a variable is basically impossible I found
        - tr '\n' ' ' < files_temp.env | sed "s/ /$prefix/g" > files.env # Read the file, replacing new lines with spaces, then replace those spaces with the prefix, output that to new file.
    artifacts:
        reports:
            dotenv: files.env # save that file for the next stage to call



```
