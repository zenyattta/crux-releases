# Prism Releases

Official Windows binary distribution repository for **Prism** (auto-update endpoint).
Application source code is maintained privately in `zenyattta/prism-personal`.

## 別PCへのインストール・入れ替え手順（Windows 10 / 11）

Git や .NET SDK のインストールは不要です。PowerShell で以下を実行すると、起動中の古い Prism があれば終了させたうえで最新版に入れ替えて起動します（2回目以降は Prism 起動時に自動で最新版へアップデートされます）：

```powershell
$dir = "$env:LOCALAPPDATA\Programs\Prism"; Get-Process Prism -ErrorAction SilentlyContinue | Stop-Process -Force; Start-Sleep -Milliseconds 500; New-Item -ItemType Directory -Force -Path $dir | Out-Null; if (Test-Path "$dir\wwwroot") { Remove-Item "$dir\wwwroot" -Recurse -Force }; Invoke-WebRequest "https://github.com/zenyattta/prism-releases/releases/latest/download/Prism-standalone.exe" -OutFile "$dir\Prism.exe"; Start-Process "$dir\Prism.exe"
```