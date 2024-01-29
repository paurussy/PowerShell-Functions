# Upload-Discord

```powershell
function Upload-Discord {

[CmdletBinding()]
param (
    [parameter(Position=0,Mandatory=$False)]
    [string]$file,
    [parameter(Position=1,Mandatory=$False)]
    [string]$text 
)

$hookurl = '<WEB HOOK>'

$Body = @{
  'username' = $env:username
  'content' = $text
}

if (-not ([string]::IsNullOrEmpty($text))){
Invoke-RestMethod -ContentType 'Application/Json' -Uri $hookurl  -Method Post -Body ($Body | ConvertTo-Json)};

if (-not ([string]::IsNullOrEmpty($file))){curl.exe -F "file1=@$file" $hookurl}
}
```
<br>

> [!NOTE]
> Usage:
> ```powershell
> Upload-Discord -text 'TEST'
> 
> Upload-Discord -file test.txt
> 
> Upload-Discord -file test.txt -text 'TEST'
>```

> [!IMPORTANT]
> It's necessary to change.
> ```powershell
>$hookurl = 'CHANGE!!'
>```
