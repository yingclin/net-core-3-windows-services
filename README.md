# .NET Core 3 的 Windows Services 範例

透過 .NET Core 3.0，我們可以快速的開發出 Windows Services。

## 專案的執行環境

* SDK 3.0.100-preview8-013656
* VSCode 1.37
* Windows 10

## 安裝為 Services

### 發佈專案

或是建置(build)，兩者輸出路徑不同，到時要建立 Services 時，指的路徑也不同。
```
dotnet publish -o d:\Temp\workerpub
```
輸出
```
D:\GitHubRepo\net-core-3-windows-services>dotnet publish -o d:\Temp\workerpub
Microsoft (R) Build Engine for .NET Core 16.3.0-preview-19377-01+dd8019d9e 版
Copyright (C) Microsoft Corporation. 著作權所有，並保留一切權利。

  D:\GitHubRepo\net-core-3-windows-services\net-core-3-windows-services.csproj 的還原於 26.1 ms 完成。
  You are using a preview version of .NET Core. See: https://aka.ms/dotnet-core-preview
  net-core-3-windows-services -> D:\GitHubRepo\net-core-3-windows-services\bin\Debug\netcoreapp3.0\net-core-3-windows-services.dll
  net-core-3-windows-services -> d:\Temp\workerpub\

D:\GitHubRepo\net-core-3-windows-services>
```

### 安裝 Services

在以 `系統管理員` 權限執行的 `命令提示字元中`，利用 windows 提供的 [sc](https://docs.microsoft.com/en-us/windows/desktop/services/controlling-a-service-using-sc) 命令安裝服務，命名為 "workertest"。binPath 參數則指向輸出的執行檔。
```
sc create workertest binPath=D:\Temp\workerpub\net-core-3-windows-services.exe
```

### 啟用 Services
```
sc start workertest
```

## 參考

[以 .NET Core 快速開發 Windows Services 或 Linux systemd 服務](http://yingclin.github.io/2019/windows-services-or-linux-systemd-in-netcore.html)

