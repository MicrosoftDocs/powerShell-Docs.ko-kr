---
title: PowerShell Core에서 WSMan(WS-Management) 원격
description: WSMan을 사용하여 PowerShell Core에서 원격 작업
ms.date: 08/06/2018
ms.openlocfilehash: ce58ed88f59f32b0f83951e55de36e829f7fa3f4
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403452"
---
# <a name="ws-management-wsman-remoting-in-powershell-core"></a>PowerShell Core에서 WSMan(WS-Management) 원격

## <a name="instructions-to-create-a-remoting-endpoint"></a>원격 엔드포인트 만들기 지침

Windows용 PowerShell Core 패키지의 `$PSHome`에는 WinRM 플러그인(`pwrshplugin.dll`) 및 설치 스크립트(`Install-PowerShellRemoting.ps1`)가 들어 있습니다.
이러한 파일은 엔드포인트가 지정된 경우에 PowerShell이 들어오는 PowerShell 원격 연결을 수락하도록 허용합니다.

### <a name="motivation"></a>동기

PowerShell을 설치하면 `New-PSSession` 및 `Enter-PSSession`을 사용하여 원격 컴퓨터에 대한 PowerShell 세션을 설정할 수 있습니다.
들어오는 PowerShell 원격 연결을 수락하도록 허용하려면 사용자가 WinRM 원격 기능 엔드포인트를 만들어야 합니다.
이는 사용자가 Install-PowerShellRemoting.ps1을 실행하여 WinRM 엔드포인트를 만드는 명시적인 옵트인 시나리오입니다.
설치 스크립트는 `Enable-PSRemoting`에 추가 기능을 추가하여 동일한 동작을 수행할 때까지 단기적인 솔루션입니다.
자세한 내용은 [#1193](https://github.com/PowerShell/PowerShell/issues/1193) 문제를 참조하세요.

### <a name="script-actions"></a>스크립트 동작

스크립트

1. %windir%\System32\PowerShell 내에 플러그인에 대한 디렉터리를 만듭니다.
1. pwrshplugin.dll을 해당 위치에 복사합니다.
1. 구성 파일을 생성합니다.
1. 해당 플러그 인을 WinRM에 등록합니다.

### <a name="registration"></a>등록

스크립트는 관리자 수준의 PowerShell 세션 내에서 실행되어야 하며, 두 가지 모드로 실행됩니다.

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a>등록할 PowerShell의 인스턴스에서 실행

```powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a>등록할 인스턴스 대신 PowerShell의 다른 인스턴스에서 실행

```powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

예를 들면 다음과 같습니다.

```powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

**참고:** 원격 기능 등록 스크립트는 WinRM을 다시 시작하므로 스크립트가 실행된 후 기존의 모든 PSRP 세션이 즉시 종료됩니다. 원격 세션 중에 실행될 경우 연결이 종료됩니다.

## <a name="how-to-connect-to-the-new-endpoint"></a>새 엔드포인트에 연결하는 방법

`-ConfigurationName "some endpoint name"`을 지정하여 새로운 PowerShell 엔드포인트에 대한 PowerShell 세션을 만듭니다. 위의 예제에서 PowerShell 인스턴스에 연결하려면 다음 중 하나를 사용합니다.

```powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

`-ConfigurationName`을 지정하지 않는 `New-PSSession` 및 `Enter-PSSession` 호출은 기본 PowerShell 엔드포인트인 `microsoft.powershell`을 대상으로 합니다.