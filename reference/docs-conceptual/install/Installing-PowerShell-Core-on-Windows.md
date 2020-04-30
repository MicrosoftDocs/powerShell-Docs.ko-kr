---
title: Windows에 PowerShell 설치
description: Windows에서 PowerShell을 설치하는 방법에 대한 정보
ms.date: 08/06/2018
ms.openlocfilehash: a8543a91ad503364c5346a11c9c9d9f910547278
ms.sourcegitcommit: b80ce0396550d0896189d0205d6c4b4372ac2015
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141392"
---
# <a name="installing-powershell-on-windows"></a>Windows에 PowerShell 설치

Windows에서 여러 가지 방법으로 PowerShell을 설치할 수 있습니다.

## <a name="prerequisites"></a>사전 요구 사항

PowerShell의 최신 릴리스는 Windows 7 SP1, Server 2008 R2 이상 버전에서 지원됩니다.

WSMan을 통한 PowerShell 원격 기능을 사용하려면 다음 전제 조건을 충족해야 합니다.

- Windows 10 이전의 Windows 버전에서는 [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410)을 설치해야 합니다. 직접 다운로드 또는 Windows 업데이트를 통해 설치할 수 있습니다. 완전히 패치된 시스템에는 이 패키지가 이미 설치되어 있습니다.
- Windows 7 및 Windows Server 2008 R2에서는 WMF(Windows Management Framework) 4.0 이상을 설치해야만 합니다. WMF에 대한 자세한 내용은 [WMF 개요](/powershell/scripting/wmf/overview)를 참조하세요.

## <a name="download-the-installer-package"></a>설치 프로그램 패키지 다운로드

Windows에서 PowerShell을 설치하려면 GitHub [릴리스][releases] 페이지에서 설치 패키지를 다운로드합니다. 릴리스 페이지의 **Assets** 섹션이 나올 때까지 아래로 스크롤합니다. **Assets** 섹션이 축소되어 있으면 클릭하여 확장합니다.

## <a name="installing-the-msi-package"></a><a id="msi" />MSI 패키지 설치

MSI 파일은 `PowerShell-<version>-win-<os-arch>.msi`과 비슷합니다. 다음은 그 예입니다. 

- `PowerShell-7.0.0-win-x64.msi`
- `PowerShell-7.0.0-win-x86.msi`

다운로드가 완료되면 설치 프로그램을 두 번 클릭하고 지시를 따릅니다.

설치 관리자는 Windows 시작 메뉴에 바로 가기를 만듭니다.

- 기본적으로 패키지는 `$env:ProgramFiles\PowerShell\<version>`에 설치됩니다.
- 시작 메뉴 또는 `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`를 통해 PowerShell을 시작할 수 있습니다.

> [!NOTE]
> PowerShell 7은 새 디렉터리에 설치되고 Windows PowerShell 5.1과 함께 실행됩니다. PowerShell Core 6.x의 경우 PowerShell 7은 PowerShell Core 6.x를 제거하는 현재 위치 업그레이드입니다.
>
> - PowerShell 7은 `$env:ProgramFiles\PowerShell\7`에 설치됩니다.
> - `$env:ProgramFiles\PowerShell\7` 폴더가 `$env:PATH`에 추가됩니다.
> - `$env:ProgramFiles\PowerShell\6` 폴더가 삭제됩니다.
>
> PowerShell 6과 PowerShell 7을 함께 실행해야 하는 경우 [ZIP 설치](#zip) 방법을 사용하여 PowerShell 6을 다시 설치합니다.

### <a name="administrative-install-from-the-command-line"></a>명령줄에서 관리 설치

명령줄에서 MSI 패키지를 설치할 수 있으므로 관리자는 사용자 상호 작용 없이 패키지를 배포할 수 있습니다. MSI 패키지에는 다음과 같은 설치 옵션 제어 속성이 포함되어 있습니다.

- **ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - 이 속성은 Windows 탐색기의 컨택스트 메뉴에 **Open PowerShell** 항목을 추가하는 옵션을 제어합니다.
- **ENABLE_PSREMOTING** - 이 속성은 설치 중 PowerShell 원격 조정을 사용하는 옵션을 제어합니다.
- **REGISTER_MANIFEST** - 이 속성은 Windows 이벤트 로깅 매니페스트를 등록하는 옵션을 제어합니다.

다음 예제에서는 PowerShell을 자동으로 설치할 때 모든 설치 옵션을 사용하도록 설정하는 방법을 보여 줍니다.

```powershell
msiexec.exe /package PowerShell-7.0.0-win-x64.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

`Msiexec.exe`에 대한 명령줄 옵션의 전체 목록은 [명령줄 옵션](/windows/desktop/Msi/command-line-options)을 참조하세요.

## <a name="installing-the-msix-package"></a><a id="msix" />MSIX 패키지 설치

Windows 10 클라이언트에 MSIX 패키지를 수동으로 설치하려면 GitHub [릴리스][releases] 페이지에서 MSIX 패키지를 다운로드합니다. 설치하려는 릴리스의 **Assets** 섹션까지 아래로 스크롤합니다. Assets 섹션이 축소되어 있으면 클릭해서 확장합니다.

MSIX 파일은 다음과 같습니다. `PowerShell-<version>-win-<os-arch>.msix`

패키지를 설치하려면 `Add-AppxPackage` cmdlet을 사용해야 합니다.

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

> [!NOTE]
> MSIX 패키지는 아직 릴리스되지 않았습니다. 릴리스되면 Microsoft Store 및 GitHub [릴리스][releases] 페이지에서 확인할 수 있습니다.

## <a name="installing-the-zip-package"></a><a id="zip" />ZIP 패키지 설치

고급 배포 시나리오를 지원하기 위해 PowerShell 이진 ZIP 아카이브가 제공됩니다. ZIP 보관 파일 설치는 MSI 패키지처럼 필수 조건을 확인하지는 않습니다. [releases][releases] 페이지에서 ZIP 보관 파일을 다운로드합니다. 파일을 다운로드하는 방법에 따라 `Unblock-File` cmdlet을 사용하여 파일의 차단을 해제해야 할 수도 있습니다. 원하는 위치에 콘텐츠의 압축을 풀고, 여기서 `pwsh.exe`를 실행합니다. WSMan에서 원격 기능이 제대로 작동하도록 하려면 [필수 조건](#prerequisites)을 충족했는지 확인하세요.

## <a name="deploying-on-windows-10-iot-enterprise"></a>Windows 10 IoT Enterprise에 배포

Windows 10 IoT Enterprise는 PowerShell 7을 배포하는 데 사용할 수 있는 Windows PowerShell과 함께 제공됩니다.

1. 대상 디바이스에 대한 `PSSession` 만들기

   ```powershell
   Set-Item -Path WSMan:\localhost\Client\TrustedHosts <deviceip>
   $S = New-PSSession -ComputerName <deviceIp> -Credential Administrator
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

4. PowerShell 7에 대한 원격 설정

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. 디바이스에서 PowerShell 7 엔드포인트에 연결

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```
## <a name="deploying-on-windows-10-iot-core"></a>Windows 10 IoT Core에 배포

Windows 10 IoT Core는 *IOT_POWERSHELL* 기능을 포함할 때 Windows PowerShell을 추가하여 PowerShell 7을 배포하는 데 사용할 수 있습니다.
IoT Core에 대해서도 위에서 정의한 Windows 10 IoT Enterprise 단계를 따를 수 있습니다.

배송 이미지에 최신 powershell을 추가하려면 [Import-PSCoreRelease](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-PSCoreRelease.md#Import-PSCoreRelease) 명령을 사용하여 패키지를 워크 영역에 포함하고 *OPENSRC_POWERSHELL* 기능을 이미지에 추가합니다.

> [!NOTE]
> ARM64 아키텍처의 경우 *IOT_POWERSHELL*을 포함할 때 Windows Powershell이 추가되지 않습니다. 따라서 zip 기반 설치가 작동하지 않습니다.
> Import-PSCoreRelease 명령을 사용하여 이미지에 추가해야 합니다.

## <a name="deploying-on-nano-server"></a>Nano 서버에 배포

이 지침에서는 Nano 서버가 한 가지 버전의 PowerShell이 이미 실행 중인 "헤드리스" OS라고 가정합니다. 자세한 내용은 [Nano 서버 이미지 작성기](/windows-server/get-started/deploy-nano-server) 설명서를 참조하세요.

두 가지 방법으로 PowerShell 이진 파일을 배포할 수 있습니다.

1. 오프라인 - Nano 서버 VHD를 탑재하고 zip 파일의 내용을 탑재된 이미지 내의 선택한 위치에 압축을 풉니다.
2. 온라인 - PowerShell 세션을 통해 zip 파일을 전송하고 선택한 위치에서 압축을 풉니다.

두 경우 모두 Windows 10 x64 ZIP 릴리스 패키지가 필요합니다. PowerShell의 "관리자" 인스턴스 내에서 명령을 실행합니다.

### <a name="offline-deployment-of-powershell"></a>PowerShell의 오프라인 배포

1. 자주 사용하는 zip 유틸리티로 패키지를 탑재된 Nano 서버 이미지 내의 디렉터리에 압축을 풉니다.
2. 이미지를 탑재 해제하고 부팅합니다.
3. Windows PowerShell의 받은 편지함 인스턴스에 연결합니다.
4. 지침에 따라 [“다른 인스턴스 기법”](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)을 사용하여 원격 엔드포인트를 만듭니다.

### <a name="online-deployment-of-powershell"></a>PowerShell의 온라인 배포

다음 단계에 따라 PowerShell을 Nano 서버로 배포하세요.

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
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShell_<version>"
  ```

- WSMan 기반 원격 작업이 필요한 경우 지침에 따라 [“다른 인스턴스 기법”](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)을 사용하여 원격 엔드포인트를 만듭니다.

## <a name="install-as-a-net-global-tool"></a>.NET 전역 도구로 설치

[.NET Core SDK](/dotnet/core/sdk)가 이미 설치되어 있는 경우 PowerShell을 [.NET 전역 도구](/dotnet/core/tools/global-tools)로 쉽게 설치할 수 있습니다.

```
dotnet tool install --global PowerShell
```

dotnet 도구 설치 프로그램은 `$env:PATH` 환경 변수에 `$env:USERPROFILE\dotnet\tools`를 추가합니다. 그러나 현재 실행 중인 셸에는 업데이트된 `$env:PATH`가 없습니다. 새 셸에서 `pwsh`를 입력하여 PowerShell을 시작할 수 있습니다.

## <a name="how-to-create-a-remoting-endpoint"></a>원격 엔드포인트를 만드는 방법

PowerShell은 WSMan 및 SSH와 함께 PowerShell Remoting Protocol(PSRP)을 지원합니다. 자세한 내용은 다음을 참조하세요.

- [PowerShell Core에서의 SSH 원격 작업][ssh-remoting]
- [PowerShell Core에서의 WSMan 원격 작업][wsman-remoting]

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
