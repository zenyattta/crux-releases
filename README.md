# Prism Releases

Official Windows binary distribution repository for **Prism** (auto-update endpoint).
Application source code is maintained privately in `zenyattta/prism-personal`.

## 別PCへのインストール手順（Windows 10 / 11）

Git や .NET SDK のインストールは不要です。PowerShell を開いて以下を実行すると、最新版がインストールされて起動します（2回目以降は Prism 起動時に自動で最新版へアップデートされます）：

```powershell
$dir = "$env:LOCALAPPDATA\Programs\Prism"
New-Item -ItemType Directory -Force -Path $dir | Out-Null
Invoke-WebRequest "https://github.com/zenyattta/prism-releases/releases/latest/download/Prism-standalone.exe" -OutFile "$dir\Prism.exe"
Start-Process "$dir\Prism.exe"
```

（すでに .NET 10 Runtime が入っているPCでは軽量版の `Prism.exe` でも動作し、どちらを入れても次回以降は同じ形式のバイナリで自動更新されます。）
