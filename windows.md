## PowerShellで環境変数確認
```
> [System.Environment]::GetEnvironmentVariable("HTTP_PROXY", "machine")
```

## PowerShellで環境変数設定
```
> [System.Environment]::SetEnvironmentVariable("HTTP_PROXY","http://z2h9343:nama-0510@ctcpro.ctc-g.co.jp:8080", "machine")
```