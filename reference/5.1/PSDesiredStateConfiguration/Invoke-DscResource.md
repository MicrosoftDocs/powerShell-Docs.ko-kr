---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-DscResource
ms.openlocfilehash: d73d8d6a30e6b7c08b5a0b7988ea2327be34002a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215313"
---
# Invoke-DscResource

## 개요
지정 된 DSC 리소스의 메서드를 실행 합니다.

## SYNTAX

```
Invoke-DscResource [-Name] <String> [-Method] <String> -ModuleName <ModuleSpecification> -Property <Hashtable>
 [<CommonParameters>]
```

## 설명
**Get-dscresource** cmdlet은 지정 된 WINDOWS PowerShell DSC (필요한 상태 구성) 리소스의 메서드를 실행 합니다.
이 cmdlet을 실행 하기 전에 로컬 Configuration Manager (LCM)의 새로 고침 모드를 사용 안 함으로 설정 합니다.

이 cmdlet은 구성 문서를 만들지 않고 DSC 리소스를 직접 호출합니다.
이 cmdlet을 사용 하 여 구성 관리 제품은 DSC 리소스를 사용 하 여 windows를 관리할 수 있습니다.
이 cmdlet을 사용 하면 디버깅을 사용 하도록 설정한 상태에서 DSC 엔진 또는 LCM이 실행 중일 때에도 리소스를 디버깅할 수 있습니다.

## 예제

### 예제 1: 필수 속성을 지정 하 여 리소스의 Set 메서드를 호출 합니다.

```
PS C:\> Invoke-DscResource -Name Log -Method Set -Property @{Message = 'Hello World'} -ModuleName PSDesiredStateConfiguration
```

이 명령은 Log 라는 리소스의 **Set** 메서드를 호출 하 고이에 대 한 **메시지** 속성을 지정 합니다.

### 예제 2: 지정 된 모듈에 대 한 리소스의 테스트 메서드 호출

```
PS C:\> Invoke-DscResource -Name WindowsProcess -Method Test -Property @{Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'; Arguments = ''} -ModuleName PSDesiredStateConfiguration
```

이 명령은 PSDesiredStateConfiguration 라는 모듈에 있는 WindowsProcess 라는 리소스의 **테스트** 메서드를 호출 합니다.

## PARAMETERS

### -메서드
이 cmdlet이 호출 하는 리소스의 메서드를 지정 합니다. 이 매개 변수에 허용 되는 값은 Get, Set 및 Test입니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Get, Set, Test

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ModuleName
이 cmdlet이 지정 된 리소스를 호출 하는 모듈의 이름을 지정 합니다.

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name
시작할 DSC 리소스의 이름을 지정 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -속성
해시 테이블의 리소스 속성 이름 및 해당 값을 키와 값으로 각각 지정합니다. **Get-DscResource** cmdlet을 사용하여 리소스 속성 및 해당 종류를 검색합니다.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters
이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

## 출력

### Ciminstance 개체로, System.web. 부울

## 참고

## 관련 링크

[Windows PowerShell Desired State Configuration 개요](/powershell/scripting/dsc/overview/dscforengineers)

[Get-DscConfiguration](Get-DscConfiguration.md)

[Get-DscConfigurationStatus](Get-DscConfigurationStatus.md)

[Get-DscResource](Get-DscResource.md)

[Restore-DscConfiguration](Restore-DscConfiguration.md)

[Set-DscLocalConfigurationManager](Set-DscLocalConfigurationManager.md)

[Start-DscConfiguration](Start-DscConfiguration.md)

[Test-DscConfiguration](Test-DscConfiguration.md)
