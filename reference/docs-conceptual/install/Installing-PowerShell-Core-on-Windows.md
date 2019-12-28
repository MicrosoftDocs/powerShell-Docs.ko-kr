---
title: Windows에서 PowerShell Core 설치
description: Windows에서 PowerShell Core를 설치하는 방법에 대한 정보
ms.date: 08/06/2018
ms.openlocfilehash: 00a1d8064a3c1ec6608a46415bbabb8d98d880f0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416771"
---
# <a name="installing-powershell-core-on-windows"></a>Windows에서 PowerShell Core 설치

Windows에서 여러 가지 방법으로 PowerShell Core를 설치할 수 있습니다.

> [!TIP]
> [.NET Core SDK](/dotnet/core/sdk)가 이미 설치되어 있는 경우 PowerShell을 [.NET 전역 도구](/dotnet/core/tools/global-tools)로 쉽게 설치할 수 있습니다.
>
> ```
> dotnet tool install --global PowerShell
> ```

## <a name="prerequisites"></a>필수 구성 요소

WSMan을 통한 PowerShell 원격 기능을 사용하려면 다음 전제 조건을 충족해야 합니다.

- Windows 10 이전의 Windows 버전에서는 [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410)을 설치하여야만 합니다. 직접 다운로드 또는 Windows 업데이트를 통해 설치할 수 있습니다. 옵션 패키지를 포함하여 완전히 패치된 지원 시스템에는 이미 설치되어 있습니다.
- Windows 7 및 Windows Server 2008 R2에서는 WMF(Windows Management Framework) 4.0 이상을 설치해야만 합니다. WMF에 대한 자세한 내용은 [WMF 개요](/powershell/scripting/wmf/overview)를 참조하세요.

## <a name="a-idmsi-installing-the-msi-package"></a><a id="msi" />MSI 패키지 설치

Windows 클라이언트 또는 Windows Server(Windows 7 SP1, Server 2008 R2 이상에서 작동)에 PowerShell을 설치하려면 GitHub [릴리스][releases] 페이지에서 MSI 패키지를 다운로드합니다. 설치하려는 릴리스의 **Assets** 섹션까지 아래로 스크롤합니다. Assets 섹션이 축소되어 있으면 클릭해서 확장합니다.

MSI 파일은 다음과 같습니다. - `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well -->

다운로드가 완료되면 설치 프로그램을 두 번 클릭하고 지시를 따릅니다.

설치 관리자는 Windows 시작 메뉴에 바로 가기를 만듭니다.

- 기본적으로 패키지는 `$env:ProgramFiles\PowerShell\<version>`에 설치됩니다.
- 시작 메뉴 또는 `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`를 통해 PowerShell을 시작할 수 있습니다.

### <a name="administrative-install-from-the-command-line"></a>명령줄에서 관리 설치

MSI 패키지를 명령줄에서 설치할 수 있습니다. 이렇게 하면 관리자가 사용자 개입 없이 패키지를 배포할 수 있습니다. PowerShell용 MSI 패키지에는 설치 옵션을 제어하는 다음 속성이 포함되어 있습니다.

- **ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - 이 속성은 Windows 탐색기의 컨택스트 메뉴에 **Open PowerShell** 항목을 추가하는 옵션을 제어합니다.
- **ENABLE_PSREMOTING** - 이 속성은 설치 중 PowerShell 원격 조정을 사용하는 옵션을 제어합니다.
- **REGISTER_MANIFEST** - 이 속성은 Windows 이벤트 로깅 매니페스트를 등록하는 옵션을 제어합니다.

다음 예제에서는 모든 설치 옵션을 사용하도록 설정하여 PowerShell Core를 자동으로 설치하는 방법을 보여 줍니다.

```powershell
msiexec.exe /package PowerShell-<version>-win-<os-arch>.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

Msiexec.exe에 대한 명령줄 옵션의 전체 목록은 [명령줄 옵션](/windows/desktop/Msi/command-line-options)을 참조하세요.

## <a name="a-idmsix-installing-the-msix-package"></a><a id="msix" />MSIX 패키지 설치

Windows 10 클라이언트에 MSIX 패키지를 수동으로 설치하려면 GitHub [릴리스][releases] 페이지에서 MSIX 패키지를 다운로드합니다. 설치하려는 릴리스의 **Assets** 섹션까지 아래로 스크롤합니다. Assets 섹션이 축소되어 있으면 클릭해서 확장합니다.

MSI 파일은 다음과 같습니다. - `PowerShell-<version>-win-<os-arch>.msix`

다운로드한 후에는 이 패키지에서 가상화되지 않은 리소스를 사용해야 하므로 설치 관리자를 두 번 클릭해서는 설치할 수는 없습니다.  설치하려면 `Add-AppxPackage` cmdlet을 사용해야 합니다.

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

## <a name="a-idzip-installing-the-zip-package"></a><a id="zip" />ZIP 패키지 설치

고급 배포 시나리오를 지원하기 위해 PowerShell 이진 ZIP 아카이브가 제공됩니다. ZIP 아카이브를 사용하면 MSI 패키지에서와 같이 전제 조건 확인을 받지 못하게 됩니다. WSMan에서 원격 기능이 제대로 작동하려면 [필수 조건](#prerequisites)이 충족되는지 확인하세요.

## <a name="deploying-on-windows-iot"></a>Windows IoT에 배포

Windows IoT는 이미 Windows PowerShell과 함께 제공되며, Windows PowerShell을 사용하여 PowerShell Core 6을 배포합니다.

1. 대상 디바이스에 대한 `PSSession` 만들기

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. 디바이스에 ZIP 패키지 복사

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. 디바이스에 연결하고 보관 확장

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. PowerShell Core 6에 대한 원격 설정

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. 디바이스에서 PowerShell Core 6 엔드포인트에 연결

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a>Nano 서버에 배포

이 지침은 PowerShell 버전이 이미 Nano 서버 이미지에서 실행 중이며 [Nano 서버 이미지 작성기](/windows-server/get-started/deploy-nano-server)에 의해 생성된 것으로 가정합니다.
Nano 서버는 “헤드리스” OS입니다. 두 가지 방법으로 Core 이진 파일을 배포할 수 있습니다.

1. 오프라인 - Nano 서버 VHD를 탑재하고 zip 파일의 내용을 탑재된 이미지 내의 선택한 위치에 압축을 풉니다.
2. 온라인 - PowerShell 세션을 통해 zip 파일을 전송하고 선택한 위치에서 압축을 풉니다.

두 경우 모두 Windows 10 x64 ZIP 릴리스 패키지가 필요하며 “관리자” PowerShell 인스턴스 내에서 명령을 실행해야 합니다.

### <a name="offline-deployment-of-powershell-core"></a>PowerShell Core의 오프라인 배포

1. 자주 사용하는 zip 유틸리티로 패키지를 탑재된 Nano 서버 이미지 내의 디렉터리에 압축을 풉니다.
2. 이미지를 탑재 해제하고 부팅합니다.
3. Windows PowerShell의 받은 편지함 인스턴스에 연결합니다.
4. 지침에 따라 [“다른 인스턴스 기법”](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)을 사용하여 원격 엔드포인트를 만듭니다.

### <a name="online-deployment-of-powershell-core"></a>PowerShell Core의 온라인 배포

다음 단계는 PowerShell Core를 실행 중인 Nano 서버 인스턴스에 배포하고 원격 엔드포인트를 구성하는 과정을 안내합니다.

- Windows PowerShell의 받은 편지함 인스턴스에 연결

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- Nano 서버 인스턴스에 파일 복사

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- 세션 입력

  ```powershell
  Enter-PSSession $session
  ```

- ZIP 파일 추출

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- WSMan 기반 원격 작업이 필요한 경우 지침에 따라 [“다른 인스턴스 기법”](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)을 사용하여 원격 엔드포인트를 만듭니다.

## <a name="how-to-create-a-remoting-endpoint"></a>원격 엔드포인트를 만드는 방법

PowerShell Core는 WSMan 및 SSH와 함께 PowerShell Remoting Protocol(PSRP)을 지원합니다. 자세한 내용은 다음을 참조하세요.

- [PowerShell Core에서의 SSH 원격 작업][ssh-remoting]
- [PowerShell Core에서의 WSMan 원격 작업][wsman-remoting]

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
