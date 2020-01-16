---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Windows PowerShell 2.0 엔진 시작
ms.openlocfilehash: 824077008d2dcfd707e977d2112f0882d07a8aca
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030435"
---
# <a name="starting-the-windows-powershell-20-engine"></a>Windows PowerShell 2.0 엔진 시작

이 섹션에서는 Windows PowerShell 2.0 엔진이 포함된 Windows 8.1, Windows Server 2012 R2, Windows 8 및 Windows Server 2012와 Windows PowerShell 2.0, Windows PowerShell 3.0 및 Windows PowerShell 4.0이 설치된 다른 시스템에서 Windows PowerShell 2.0 엔진을 시작하는 방법을 설명합니다.

Windows PowerShell 4.0 및 Windows PowerShell 3.0은 이전 버전인 Windows PowerShell 2.0과 호환되도록 설계되었습니다. Windows PowerShell 2.0용으로 작성된 cmdlet, 공급자, 스냅인, 모듈 및 스크립트는 Windows PowerShell 4.0 및 Windows PowerShell 3.0에서 문제 없이 실행됩니다. 그러나 Microsoft .NET Framework 4의 런타임 정품 인증 정책 변경으로 인해 Windows PowerShell 2.0용으로 작성되고 CLR(공용 언어 런타임) 2.0으로 컴파일된 Windows PowerShell 호스트 프로그램은 CLR 4.0으로 컴파일된 Windows PowerShell 3.0 또는 Windows PowerShell 4.0에서 수정 없이 실행할 수 없습니다. Windows PowerShell 2.0 엔진은 기존 스크립트 또는 호스트 프로그램이 Windows PowerShell 4.0, Windows PowerShell 3.0 또는 Microsoft .NET Framework 4와 호환되지 않아 실행할 수 없는 경우에만 사용됩니다. 이러한 경우는 많지 않을 것으로 예상됩니다.

Windows PowerShell 2.0 엔진을 필요로 하는 대부분의 프로그램은 자동으로 엔진을 시작합니다. 이러한 지침은 엔진을 수동으로 시작해야 하는 드문 경우를 위해 포함되었습니다.

## <a name="installing-and-enabling-required-programs"></a>필요한 프로그램 설치 및 사용

Windows PowerShell 2.0 엔진을 시작하기 전에 Windows PowerShell 2.0 엔진과 Microsoft .NET Framework 3.5 서비스 팩 1을 사용하도록 설정합니다. 자세한 내용은 [Windows PowerShell 설치](../install/Installing-Windows-PowerShell.md)를 참조하세요.

Windows Management Framework 4.0 또는 Windows Management Framework 3.0이 설치된 시스템에는 필요한 구성 요소가 모두 있습니다. 추가 구성은 필요하지 않습니다. [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/?LinkID=293881) 또는 Windows Management Framework 3.0 설치에 대한 자세한 내용은 [Windows PowerShell 설치](../install/Installing-Windows-PowerShell.md)를 참조하세요.

## <a name="how-to-start-the-windows-powershell-20-engine"></a>Windows PowerShell 2.0 엔진을 시작하는 방법

Windows PowerShell을 시작하는 경우 기본적으로 최신 버전이 시작됩니다. Windows PowerShell 및 Windows PowerShell 2.0 엔진을 시작하려면 PowerShell.exe의 Version 매개 변수를 사용합니다. Windows PowerShell 및 Cmd.exe를 비롯한 모든 명령 프롬프트에서 명령을 실행할 수 있습니다.

```
PowerShell.exe -Version 2
```

## <a name="how-to-start-a-remote-session-with-the-windows-powershell-20-engine"></a>Windows PowerShell 2.0 엔진과 원격 세션을 시작하는 방법

원격 세션으로 Windows PowerShell 2.0 엔진을 실행하려면 Windows PowerShell 2.0 엔진을 로드하는 원격 컴퓨터에서 세션 구성("엔드포인트"이라고도 함)을 만듭니다. 세션 구성은 원격 컴퓨터에 저장되며, Windows PowerShell 2.0 엔진을 사용하는 모든 권한 있는 사용자가 이용할 수 있습니다.

이는 일반적으로 시스템 관리자가 수행하는 고급 작업입니다.

다음 절차에서는 [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) cmdlet의 **PSVersion** 매개 변수를 통해 Windows PowerShell 2.0 엔진을 사용하는 세션 구성을 만듭니다. [New-PSSessionConfigurationFile](https://technet.microsoft.com/library/5f3e3633-6e90-479c-aea9-ba45a1954866) cmdlet의 **PowerShellVersion** 매개 변수를 사용하여 Windows PowerShell 2.0 엔진을 로드하는 세션에 대한 세션 구성 파일을 만들 수도 있으며, [Set-PSSessionConfiguration](https://technet.microsoft.com/library/b21fbad3-1759-4260-b206-dcb8431cd6ea) 매개 변수의 **PSVersion** 매개 변수를 통해 Windows PowerShell 2.0 엔진을 사용하도록 세션 구성을 변경할 수 있습니다.

세션 구성 파일에 대한 자세한 내용은 [about_Session_Configuration_Files](https://technet.microsoft.com/library/c7217447-1ebf-477b-a8ef-4dbe9a1473b8)를 참조하세요. 설정 및 보안을 비롯한 세션 구성에 대한 자세한 내용은 [about_Session_Configurations[v4]](https://technet.microsoft.com/library/a2fbe12a-350c-4d04-be50-24102824e3ab)를 참조하세요.

#### <a name="to-start-a-remote-windows-powershell-20-session"></a>원격 Windows PowerShell 2.0 세션을 시작하려면

1. Windows PowerShell 2.0 엔진을 필요로 하는 세션 구성을 만들려면 [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) cmdlet의 **PSVersion** 매개 변수에 값 "2.0"을 사용합니다. 연결의 "서버 쪽" 또는 수신 끝에 있는 컴퓨터에서 이 명령을 실행합니다.

   다음 샘플 명령은 Server01 컴퓨터에서 PS2 세션 구성을 만듭니다. 이 명령을 실행하려면 **관리자 권한으로 실행** 옵션을 사용하여 Windows PowerShell 4.0 또는 Windows PowerShell 3.0을 시작합니다.

   ```powershell
   Register-PSSessionConfiguration -Name PS2 -PSVersion 2.0
   ```

2. PS2 세션 구성을 사용하는 Server01 컴퓨터에서 세션을 만들려면 [New-PSSession](https://technet.microsoft.com/library/76f6628c-054c-4eda-ba7a-a6f28daaa26f) cmdlet과 같이 원격 세션을 만드는 cmdlet의 **ConfigurationName** 매개 변수를 사용합니다.

   세션 구성을 사용하는 세션이 시작되면 Windows PowerShell 2.0 엔진이 자동으로 세션에 로드됩니다.

   다음 명령은 PS2 세션 구성을 사용하는 Server01 컴퓨터에서 세션을 시작합니다. 이 명령은 세션을 $s 변수에 저장합니다.

   ```powershell
   $s = New-PSSession -ComputerName Server01 -ConfigurationName PS2
   ```

## <a name="how-to-start-a-background-job-with-the-windows-powershell-20-engine"></a>Windows PowerShell 2.0 엔진을 사용하여 백그라운드 작업을 시작하는 방법

Windows PowerShell 2.0 엔진을 사용하여 백그라운드 작업을 시작하려면 [Start-Job](https://technet.microsoft.com/library/2bc04935-0deb-4ec0-b856-d7290cca6442) cmdlet의 **PSVersion** 매개 변수를 사용합니다.

다음 명령은 Windows PowerShell 2.0 엔진을 사용하여 백그라운드 작업을 시작합니다.

```powershell
Start-Job {Get-Process} -PSVersion 2.0
```

백그라운드 작업에 대한 자세한 내용은 [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)를 참조하세요.
