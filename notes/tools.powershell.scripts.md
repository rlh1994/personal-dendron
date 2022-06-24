---
id: XHTgVsuKj8Or8OQrpSGv8
title: Scripts
desc: ''
updated: 1642006820772
created: 1642006272521
---


### Get count of files by type
```powershell
Get-ChildItem -Recurse -File | group Extension -NoElement  | sort Count -Descending
```

### Write all filenames of type to file

```powershell
$list = Get-ChildItem -Path 'D:\Movies\' -Recurse | Where-Object { $_.PSIsContainer -eq $false -and $_.Extension -ne '.srt' }

write-host "`nTotal : "$list.Count "movies `n"
ForEach($n in $list){
 $n.Name | Out-File -Append 'D:\Movielist.txt'
}
```
