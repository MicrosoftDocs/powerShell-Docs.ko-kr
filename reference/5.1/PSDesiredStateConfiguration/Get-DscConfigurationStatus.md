---
external help file: Get-DscConfigurationStatus.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscConfigurationStatus
ms.openlocfilehash: 0d59ce58a70eab68441ea1fe6097bbdf7792a54f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215362"
---
# Get-DscConfigurationStatus

## 개요
완료 된 구성 실행에 대 한 데이터를 검색 합니다.

## SYNTAX

```
Get-DscConfigurationStatus [-All] [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob]
 [<CommonParameters>]
```

## 설명
**Get DscConfigurationStatus** cmdlet은 시스템에서 완료 된 구성 실행에 대 한 자세한 정보를 검색 합니다.
기본적으로 마지막 구성 실행에 대 한 정보를 반환 합니다.
이 cmdlet은 구성이 실행 된 시간, 실행 상태, 구성의 리소스 수, 성공 또는 실패 한 리소스와 같은 구성 실행에 대 한 기록 정보를 찾는 데 유용 합니다.

## 예제

### 예제 1: 마지막 구성 실행에 대 한 정보 가져오기

```
PS C:\> Get-DscConfigurationStatus
```

이 명령은 마지막 구성 실행에 대 한 정보를 가져옵니다.

### 예제 2: 모든 구성에 대 한 정보 가져오기

```
PS C:\> Get-DscConfigurationStatus -All
```

이 명령은 Windows PowerShell DSC (필요한 상태 구성) 일관성 확인을 포함 하 여 시스템에서 실행 된 모든 구성에 대 한 정보를 가져옵니다.

### 예 3: 원격 컴퓨터에서 구성 실행에 대 한 정보 가져오기

```
PS C:\> Get-DscConfigurationStatus -CimSession "Server01"
```

이 명령은 Server01 라는 원격 컴퓨터의 구성 실행 정보를 가져옵니다.
이 경우 WSMan 전송을 사용 하 여 원격 컴퓨터에 연결 하 고 연결 하는 사용자가 원격 컴퓨터의 관리자 여야 합니다.

## PARAMETERS

### -All
이 cmdlet은 구성 응용 프로그램 및 일관성 확인을 포함 하 여 컴퓨터에서 실행 되는 모든 구성에 대 한 정보를 검색 함을 나타냅니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsJob
이 cmdlet이 명령을 백그라운드 작업으로 실행 함을 나타냅니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CimSession
원격 세션에서 또는 원격 컴퓨터에서 cmdlet을 실행합니다.
[CimSession](/powershell/module/cimcmdlets/new-cimsession) 또는 [CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet의 출력과 같은 컴퓨터 이름 또는 세션 개체를 입력 합니다.
기본값은 로컬 컴퓨터의 현재 세션입니다.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: (All)
Aliases: Session

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit
cmdlet을 실행하도록 설정할 수 있는 최대 동시 작업 수를 지정합니다.
이 매개 변수를 생략 하거나 값을 `0` 입력 하면 Windows PowerShell은 컴퓨터에서 실행 되는 CIM cmdlet의 수에 따라 cmdlet에 대 한 최적의 스로틀 제한을 계산 합니다.
스로틀 제한은 현재 cmdlet에만 적용되며 세션이나 컴퓨터에는 적용되지 않습니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

## 출력

## 참고

## 관련 링크

[Windows PowerShell Desired State Configuration 개요](/powershell/scripting/dsc/overview/dscforengineers)

[Get-DscConfiguration](Get-DscConfiguration.md)

[Get DscLocalConfigurationManager](Get-DscLocalConfigurationManager.md)

[Restore-DscConfiguration](Restore-DscConfiguration.md)

[Start-DscConfiguration](Start-DscConfiguration.md)

[Test-DscConfiguration](Test-DscConfiguration.md)
