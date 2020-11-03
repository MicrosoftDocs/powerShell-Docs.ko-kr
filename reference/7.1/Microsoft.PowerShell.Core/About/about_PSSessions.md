---
description: PowerShell 세션 (PSSessions)을 설명 하 고 원격 컴퓨터에 대 한 영구 연결을 설정 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssessions?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSSessions
ms.openlocfilehash: 2be48b458ec156852be59d9079e8bbf50af9b499
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222041"
---
# <a name="about-pssessions"></a>PSSessions 정보

## <a name="short-description"></a>간단한 설명
PowerShell 세션 (PSSessions)을 설명 하 고 원격 컴퓨터에 대 한 영구 연결을 설정 하는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명

원격 컴퓨터에서 PowerShell 명령을 실행 하려면 cmdlet의 **ComputerName** 매개 변수를 사용 하거나, powershell 세션 (pssession)을 만들고 pssession에서 명령을 실행할 수 있습니다.

PSSession을 만들 때 PowerShell은 원격 컴퓨터에 대 한 영구 연결을 설정 합니다. PSSession을 사용 하 여 원격 컴퓨터에서 일련의 관련 명령을 실행 합니다. 동일한 PSSession에서 실행 되는 명령은 변수, 별칭 및 함수 값과 같은 데이터를 공유할 수 있습니다.

로컬 컴퓨터에서 PSSession을 만들고 명령을 실행할 수도 있습니다.
로컬 PSSession은 PowerShell 원격 인프라를 사용 하 여 PSSession을 만들고 유지 관리 합니다.

Windows PowerShell 3.0부터 pssession은 생성 된 세션과는 독립적입니다. 활성 pssession은 원격 컴퓨터 (또는 원격 끝에 있는 컴퓨터 또는 연결의 "서버 쪽")에서 유지 관리 됩니다. 결과적으로 PSSession에서 연결을 끊고 나중에 동일한 컴퓨터 또는 다른 컴퓨터에서 다시 연결할 수 있습니다.

이 항목에서는 pssession을 만들고 사용 하 고 가져오고 삭제 하는 방법을 설명 합니다. 자세한 내용은 [about_PSSession_Details](about_PSSession_Details.md)를 참조 하세요.

참고: PSSessions는 PowerShell 원격 인프라를 사용 합니다. Pssession을 사용 하려면 원격 컴퓨터에 대 한 로컬 및 원격 컴퓨터를 구성 해야 합니다.
자세한 내용은 [about_Remote_Requirements](about_Remote_Requirements.md)을 참조하세요.

Windows Vista 이상 버전에서 로컬 컴퓨터에 PSSession을 만들려면 "관리자 권한으로 실행" 옵션을 사용 하 여 PowerShell을 시작 해야 합니다.

## <a name="what-is-a-session"></a>세션 이란?

세션은 PowerShell을 실행 하는 환경입니다.

PowerShell을 시작할 때마다 세션이 만들어지고 세션에서 명령을 실행할 수 있습니다. 모듈 및 스냅인과 같은 항목을 세션에 추가 하 고 변수, 함수 및 별칭과 같은 항목을 만들 수도 있습니다. 이러한 항목은 세션에만 존재 하며 세션이 종료 될 때 삭제 됩니다.

로컬 컴퓨터 또는 원격 컴퓨터에서 사용자 관리 세션 ("PowerShell 세션" 또는 "PSSessions")을 만들 수도 있습니다. 기본 세션과 마찬가지로 PSSession에서 명령을 실행 하 고 항목을 추가 하 고 만들 수 있습니다. 그러나 자동으로 시작 되는 세션과 달리 사용자가 만든 pssession을 제어할 수 있습니다. 이러한 항목을 가져오고, 만들고, 구성 하 고, 제거 하 고, 연결을 끊고 다시 연결 하 고, 동일한 PSSession에서 여러 명령을 실행할 수 있습니다. PSSession을 삭제 하거나 시간 초과가 발생할 때까지 PSSession을 계속 사용할 수 있습니다.

일반적으로 원격 컴퓨터에서 일련의 관련 명령을 실행 하려면 PSSession을 만듭니다. 원격 컴퓨터에서 PSSession을 만들 때 PowerShell은 세션을 지원 하기 위해 원격 컴퓨터에 대 한 영구 연결을 설정 합니다.

또는 cmdlet의 **ComputerName** 매개 변수를 사용 하 여 `Invoke-Command` `Enter-PSSession` 원격 명령을 실행 하거나 대화형 세션을 시작 하는 경우 PowerShell은 원격 컴퓨터에 임시 세션을 만들고 명령이 완료 되는 즉시 또는 대화형 세션이 종료 되는 즉시 세션을 닫습니다. 이러한 임시 세션은 제어할 수 없으며 단일 명령 또는 단일 대화형 세션에 사용할 수 없습니다.

PowerShell에서 "현재 세션"은 작업 중인 세션입니다. "현재 세션"은 임시 세션이 나 PSSession을 비롯 한 모든 세션을 참조할 수 있습니다.

## <a name="why-use-a-pssession"></a>PSSession을 사용 하는 이유

원격 컴퓨터에 대 한 영구 연결이 필요한 경우 PSSession을 사용 합니다.
PSSession을 사용 하 여 변수 값, 함수의 내용 또는 별칭 정의와 같은 데이터를 공유 하는 일련의 명령을 실행할 수 있습니다.

PSSession을 만들지 않고 원격 명령을 실행할 수 있습니다. 원격 지원 cmdlet의 **ComputerName** 매개 변수를 사용 하 여 하나 이상의 컴퓨터에서 단일 명령이 나 일련의 관련 되지 않은 명령을 실행 합니다.

또는의 **ComputerName** 매개 변수를 사용 하는 경우 `Invoke-Command` PowerShell은 `Enter-PSSession` 원격 컴퓨터에 대 한 임시 연결을 설정한 다음 명령이 완료 되는 즉시 연결을 닫습니다. 연결을 닫을 때 사용자가 만드는 모든 데이터 요소가 손실 됩니다.

**ComputerName** 매개 변수가 있는 다른 cmdlet (예: 및)은 `Get-Eventlog` 다양 한 `Get-WmiObject` 원격 기술을 사용 하 여 데이터를 수집 합니다. 없음 PSSession과 같은 영구 연결을 만듭니다.

## <a name="how-to-create-a-pssession"></a>PSSession을 만드는 방법

PSSession을 만들려면 cmdlet을 사용 `New-PSSession` 합니다. 원격 컴퓨터에서 PSSession을 만들려면 cmdlet의 **ComputerName** 매개 변수를 사용 합니다 `New-PSSession` .

예를 들어 다음 명령은 Server01 컴퓨터에 새 PSSession을 만듭니다.

```powershell
New-PSSession -ComputerName Server01
```

명령을 제출할 때는 PSSession을 `New-PSSession` 만들고 pssession을 나타내는 개체를 반환 합니다. PSSession을 만들 때 개체를 변수에 저장 하거나, 명령을 사용 하 여 나중에 PSSession을 가져올 수 있습니다 `Get-PSSession` .

예를 들어 다음 명령은 Server01 컴퓨터에 새 PSSession을 만든 다음 결과 개체를 $ps 변수에 저장 합니다.

```powershell
$ps = New-PSSession -ComputerName Server01
```

## <a name="how-to-create-pssessions-on-multiple-computers"></a>여러 컴퓨터에서 PSSessions를 만드는 방법

여러 컴퓨터에서 PSSessions를 만들려면 cmdlet의 **ComputerName** 매개 변수를 사용 `New-PSSession` 합니다. 원격 컴퓨터의 이름을 쉼표로 구분 된 목록으로 입력 합니다.

예를 들어 Server01, Server02 및 Server03 컴퓨터에서 PSSessions를 만들려면 다음을 입력 합니다.

```powershell
New-PSSession -ComputerName Server01, Server02, Server03
```

`New-PSSession` 각 원격 컴퓨터에 하나의 PSSession을 만듭니다.

## <a name="how-to-get-pssessions"></a>PSSessions를 가져오는 방법

현재 세션에서 만들어진 pssession을 가져오려면 `Get-PSSession` **ComputerName** 매개 변수 없이 cmdlet을 사용 합니다. `Get-PSSession` 가 반환 하는 개체의 동일한 형식을 반환 합니다 `New-PSSession` .

다음 명령은 현재 세션에서 만들어진 모든 pssession을 가져옵니다.

```powershell
Get-PSSession
```

Pssession의 기본 표시에는 ID 및 기본 표시 이름이 표시 됩니다. 세션을 만들 때 대체 표시 이름을 할당할 수 있습니다.

```output
Id   Name       ComputerName    State    ConfigurationName
---  ----       ------------    -----    ---------------------
1    Session1   Server01        Opened   Microsoft.PowerShell
2    Session2   Server02        Opened   Microsoft.PowerShell
3    Session3   Server03        Opened   Microsoft.PowerShell
```

PSSessions를 변수에 저장할 수도 있습니다. 다음 명령은 PSSessions를 가져와 \$ ps123 변수에 저장 합니다.

```powershell
$ps123 = Get-PSSession
```

PSSession cmdlet을 사용 하는 경우 해당 ID, 이름 또는 인스턴스 ID (GUID)로 PSSession을 참조할 수 있습니다. 다음 명령은 해당 ID로 PSSession을 가져와 \$ ps01 변수에 저장 합니다.

```powershell
$ps01 = Get-PSSession -Id 1
```

Windows PowerShell 3.0부터 pssession은 원격 컴퓨터에 유지 됩니다. 특정 원격 컴퓨터에서 만든 pssession을 가져오려면 cmdlet의 **ComputerName** 매개 변수를 사용 `Get-PSSession` 합니다. 다음 명령은 Server01 원격 컴퓨터에서 만든 PSSessions를 가져옵니다. 여기에는 현재 세션에서 생성 된 pssession과 로컬 컴퓨터 또는 다른 컴퓨터의 다른 세션이 포함 됩니다.

```powershell
Get-PSSession -ComputerName Server01
```

Windows PowerShell 2.0에서는 `Get-PSSession` 현재 세션에서 만들어진 pssession만 가져옵니다. 세션이에 연결 되어 있고 로컬 컴퓨터에서 명령을 실행 하는 경우에도 다른 세션이 나 다른 컴퓨터에서 만들어진 pssession은 가져오지 않습니다.

## <a name="how-to-run-commands-in-a-pssession"></a>PSSession에서 명령을 실행 하는 방법

하나 이상의 pssession에서 명령을 실행 하려면 cmdlet을 사용 `Invoke-Command` 합니다.
Session 매개 변수를 사용 하 여 PSSessions을 지정 하 고 **ScriptBlock** 매개 변수를 사용 하 여 명령을 지정 합니다.

예를 들어 `Get-ChildItem` $ps 123 변수에 저장 된 각각의 3 개의 pssession에서 ("dir") 명령을 실행 하려면 다음을 입력 합니다.

```powershell
Invoke-Command -Session $ps123 -ScriptBlock { Get-ChildItem }
```

## <a name="how-to-delete-pssessions"></a>Pssession을 삭제 하는 방법

PSSession을 마친 후에는 cmdlet을 사용 하 여 `Remove-PSSession` pssession을 삭제 하 고 사용 중인 리소스를 해제 합니다.

```powershell
Remove-PSSession -Session $ps
```

또는

```powershell
Remove-PSSession -Id 1
```

원격 컴퓨터에서 PSSession을 제거 하려면 cmdlet의 **ComputerName** 매개 변수를 사용 `Remove-PSSession` 합니다.

```powershell
Remove-PSSession -ComputerName Server01 -Id 1
```

PSSession을 삭제 하지 않은 경우에는 제한 시간이 초과 될 때까지 PSSession을 계속 사용할 수 있습니다.

또한 cmdlet의 **IdleTimeout** 매개 변수를 사용 `New-PSSessionOption` 하 여 유휴 PSSession에 대 한 만료 시간을 설정할 수 있습니다. 자세한 내용은 [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)을 참조 하세요.

## <a name="the-pssession-cmdlets"></a>PSSession Cmdlet

PSSession cmdlet 목록을 보려면 다음을 입력 합니다.

```powershell
Get-Help *-PSSession
```

- 연결-PSSession: PSSession을 현재 세션에 연결 합니다.
- 연결 끊기-PSSession: 현재 세션에서 PSSession의 연결을 끊습니다.
- Enter-PSSession: 대화형 세션을 시작 합니다.
- 종료-PSSession: 대화형 세션 종료
- Get PSSession: 현재 세션의 PSSession을 가져옵니다.
- 새-PSSession: 로컬 또는 원격 컴퓨터에 새 PSSession을 만듭니다.
- 수신 PSSession: 연결 되지 않은 세션에서 실행 된 명령의 결과를 가져옵니다.
- 제거-PSSession: 현재 세션의 PSSession을 삭제 합니다.

## <a name="for-more-information"></a>참조 항목

Pssession에 대 한 자세한 내용은 [about_PSSession_Details](about_PSSession_Details.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[about_Remote](about_Remote.md)

[about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md)

[about_Remote_Requirements](about_Remote_Requirements.md)

[Connect-PSSession](xref:Microsoft.PowerShell.Core.Connect-PSSession)

[Disconnect-PSSession](xref:Microsoft.PowerShell.Core.Disconnect-PSSession)

[Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[Exit-PSSession](xref:Microsoft.PowerShell.Core.Exit-PSSession)

[Get-PSSession](xref:Microsoft.PowerShell.Core.Get-PSSession)

[Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[Remove-PSSession](xref:Microsoft.PowerShell.Core.Remove-PSSession)

