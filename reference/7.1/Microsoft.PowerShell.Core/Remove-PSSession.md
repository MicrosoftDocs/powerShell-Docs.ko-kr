---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-pssession?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSSession
ms.openlocfilehash: 1b0fbfca365e9cf369decbf4eafc0a8b4e2741bc
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93217017"
---
# Remove-PSSession

## 개요
하나 이상의 PowerShell 세션 (PSSessions)을 닫습니다.

## SYNTAX

### Id (기본값)

```
Remove-PSSession [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 세션

```
Remove-PSSession [-Session] <PSSession[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ContainerId

```
Remove-PSSession -ContainerId <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### VMId

```
Remove-PSSession -VMId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### VMName

```
Remove-PSSession -VMName <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceId

```
Remove-PSSession -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 속성

```
Remove-PSSession -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### 컴퓨터 이름

```
Remove-PSSession [-ComputerName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

**Remove PSSession** cmdlet은 현재 세션에서 PowerShell 세션 ( **pssessions** )을 닫습니다.
**Pssession은 pssession** 에서 실행 되는 모든 명령을 **중지 하 고** pssession을 종료 한 다음 **pssession** 이 사용 하 던 리소스를 해제 합니다.
**PSSession** 이 원격 컴퓨터에 연결 되어 있는 경우이 cmdlet은 로컬 컴퓨터와 원격 컴퓨터 간의 연결도 닫습니다.

**PSSession** 을 제거 하려면 세션의 *Name* , *ComputerName* , *ID* 또는 *InstanceID* 를 입력 합니다.

*Pssession* 을 변수에 저장 한 경우 세션 개체는 변수에 남아 있지만 *pssession* 의 상태는 닫힙니다.

## 예제

### 예제 1: Id를 사용 하 여 세션 제거

```powershell
Remove-PSSession -Id 1, 2
```

이 명령은 Id가 1과 **2 인 pssession을 제거 합니다.**

### 예 2: 현재 세션의 모든 세션 제거

```powershell
Get-PSSession | Remove-PSSession
Remove-PSSession -Session (Get-PSSession)
$s = Get-PSSession
Remove-PSSession -Session $s
```

이러한 명령은 현재 **세션의 모든** pssession을 제거 합니다.
이 세 명령 형식이 다르게 보이지만 효과는 동일합니다.

### 예제 3: 이름을 사용 하 여 세션 닫기

```powershell
$r = Get-PSSession -ComputerName Serv*
$r | Remove-PSSession
```

이러한 명령은 이름이 Serv로 시작 하는 컴퓨터에 연결 된 **Pssessions** 를 닫습니다.

### 예제 4: 포트에 연결 된 세션 닫기

```powershell
Get-PSSession | where {$_.port -eq 90} | Remove-PSSession
```

이 명령은 포트 90에 연결 된 **Pssessions** 를 닫습니다.
이 명령 형식을 사용 하 여 *ComputerName* , *Name* , *InstanceID* 및 *ID* 이외의 속성으로 **pssessions** 를 식별할 수 있습니다.

### 예 5: 인스턴스 ID에 따라 세션 닫기

```powershell
Get-PSSession | Format-Table ComputerName, InstanceID  -AutoSize
```

```Output
ComputerName InstanceId
------------ ----------------
Server01     875d231b-2788-4f36-9f67-2e50d63bb82a
localhost    c065ffa0-02c4-406e-84a3-dacb0d677868
Server02     4699cdbc-61d5-4e0d-b916-84f82ebede1f
Server03     4e5a3245-4c63-43e4-88d0-a7798bfc2414
TX-TEST-01   fc4e9dfa-f246-452d-9fa3-1adbdd64ae85 PS C:\> Remove-PSSession -InstanceID fc4e9dfa-f246-452d-9fa3-1adbdd64ae85
```

이러한 명령은 인스턴스 ID 또는 **RemoteRunspaceID** 을 기반으로 **PSSession** 을 닫는 방법을 보여 줍니다.

첫 번째 명령은 **Get PSSession** cmdlet을 사용 하 여 현재 세션 **의 PSSession을 가져옵니다** .
파이프라인 연산자 (|)를 사용 하 여 **pssession을 Format-Table cmdlet으로 보냅니다** . 그러면이 Cmdlet에서 **ComputerName** 및 **InstanceID** 속성을 테이블 형식으로 지정 합니다.
*AutoSize* 매개 변수는 표시할 열을 압축 합니다.

결과 디스플레이에서 닫을 **PSSession** 을 식별 하 고 해당 **pssession** 의 *InstanceID* 를 복사 하 여 두 번째 명령에 붙여 넣을 수 있습니다.

두 번째 명령은 **Remove pssession** cmdlet을 사용 하 여 지정 된 인스턴스 ID의 *pssession* 을 제거 합니다.

### 예제 6: 현재 세션의 모든 세션을 삭제 하는 함수 만들기

```powershell
Function EndPSS { Get-PSSession | Remove-PSSession }
```

이 함수는 현재 **세션의 모든** pssession을 삭제 합니다.
이 함수를 PowerShell 프로필에 추가한 후 모든 세션을 삭제 하려면를 입력 `EndPSS` 합니다.

## PARAMETERS

### -ComputerName

컴퓨터 이름 배열을 지정 합니다.
이 cmdlet은 지정 된 컴퓨터에 연결 된 **Pssessions** 를 닫습니다.
와일드카드 문자를 사용할 수 있습니다.

하나 이상의 원격 컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 입력하세요.
로컬 컴퓨터를 지정 하려면 컴퓨터 이름, localhost 또는 점 (.)을 입력 합니다.

```yaml
Type: System.String[]
Parameter Sets: ComputerName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -ContainerId

컨테이너의 Id 배열을 지정 합니다. 이 cmdlet은 지정 된 각 컨테이너에 대 한 세션을 제거 합니다. 명령을 사용 `docker ps` 하 여 컨테이너 id 목록을 가져옵니다. 자세한 내용은 [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) 명령에 대 한 도움말을 참조 하세요.

```yaml
Type: System.String[]
Parameter Sets: ContainerId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Id

세션의 Id 배열을 지정 합니다.
이 cmdlet은 지정 된 Id *를 가진 pssession을 닫습니다* .
하나 이상의 Id를 쉼표로 구분 하 여 입력 하거나 범위 연산자 (...)를 사용 하 여 Id 범위를 지정 합니다.

ID는 현재 세션의 **PSSession** 을 고유 하 게 식별 하는 정수입니다.
이는 *InstanceId* 보다 쉽게 기억할 수 있으며, 입력은 현재 세션 에서만 고유 합니다.
**PSSession** 의 ID를 찾으려면 매개 변수 없이 Get-PSSession cmdlet을 실행 합니다.

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

인스턴스 Id의 배열을 지정 합니다.
이 cmdlet은 지정 된 인스턴스 Id를 가진 **pssession을 닫습니다** .

인스턴스 ID는 현재 세션의 **PSSession** 을 고유 하 게 식별 하는 GUID입니다.
인스턴스 ID는 단일 컴퓨터에서 여러 세션이 실행 되는 경우에도 고유 합니다.

인스턴스 ID는 **PSSession** 을 나타내는 개체의 **InstanceID** 속성에 저장 됩니다.
현재 **세션에서 pssession의** **InstanceID** 를 찾으려면를 입력 `Get-PSSession | Format-Table Name, ComputerName, InstanceId` 합니다.

```yaml
Type: System.Guid[]
Parameter Sets: InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

세션의 이름 배열을 지정 합니다.
이 cmdlet은 지정 된 이름을 가진 **pssession을 닫습니다** .
와일드카드 문자를 사용할 수 있습니다.

**PSSession** 이름이 고유 하지 않을 수 있으므로 *name* 매개 변수를 사용 하는 경우에는 **Remove Pssession** 명령에 *WhatIf* 또는 *Confirm* 매개 변수도 사용 하는 것이 좋습니다.

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Session

닫을 **pssession의 세션** 개체를 지정 합니다.
PSSession이 포함 된 변수 또는 PSSession을 만들거나 가져오는 **명령 (예** : New-PSSession 또는 **Get PSSession** 명령)을 **입력 합니다.**
하나 이상의 세션 개체를 **제거** 로 파이프 할 수도 있습니다.

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -VMId

가상 컴퓨터의 ID 배열을 지정 합니다.
이 cmdlet은 지정 된 각 가상 컴퓨터와 대화형 세션을 시작 합니다.
사용할 수 있는 가상 컴퓨터를 보려면 다음 명령을 사용 합니다.

`Get-VM | Select-Object -Property Name, ID`

```yaml
Type: System.Guid[]
Parameter Sets: VMId
Aliases: VMGuid

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -VMName

가상 컴퓨터의 이름 배열을 지정합니다.
이 cmdlet은 지정 된 각 가상 컴퓨터와 대화형 세션을 시작 합니다.
사용할 수 있는 가상 컴퓨터를 확인 하려면 **GET VM** cmdlet을 사용 합니다.

```yaml
Type: System.String[]
Parameter Sets: VMName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Confirm

cmdlet을 실행하기 전에 확인을 요청합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

cmdlet을 실행할 경우 발생하는 일을 표시합니다.
cmdlet은 실행되지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### Runspace입니다.

세션 개체를이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### 없음

이 cmdlet은 개체를 반환하지 않습니다.

## 참고

* *Id* 매개 변수는 필수입니다. 현재 **세션의 모든** pssession을 삭제 하려면를 입력 `Get-PSSession | Remove-PSSession` 합니다.
* **PSSession** 은 원격 컴퓨터에 대 한 영구 연결을 사용 합니다. 데이터를 공유 하는 일련의 명령을 실행 하는 **PSSession** 을 만듭니다. 자세한 내용을 보려면 `Get-Help about_PSSessions`를 입력하십시오.
* Pssession **은 현재 세션에만 적용** 됩니다. 세션을 종료 하면 해당 세션에서 만든 **pssession이 강제로** 닫힙니다.

## 관련 링크

[Connect-PSSession](Connect-PSSession.md)

[Disconnect-PSSession](Disconnect-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Exit-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-Command](Invoke-Command.md)

[New-PSSession](New-PSSession.md)

[Receive-PSSession](Receive-PSSession.md)

[about_PSSessions](About/about_PSSessions.md)

[about_Remote](About/about_Remote.md)

