---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 08/11/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-DscResource
ms.openlocfilehash: 4703586008d9044ae68fd7375db65f0d0a9b9980
ms.sourcegitcommit: f05f18154913d346012527c23020d48d87ccac74
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/13/2020
ms.locfileid: "93219529"
---
# Invoke-DscResource

## 개요
지정 된 PowerShell DSC (필요한 상태 구성) 리소스의 메서드를 실행 합니다.

## SYNTAX

```
Invoke-DscResource [[-Method] <Object>] [[-Name] <Object>] [[-Property] <Object>]
 [[-ModuleName] <Object>] [-AsJob] [<CommonParameters>]
```

## 설명

`Invoke-DscResource` cmdlet은 지정된 PowerShell DSC(Desired State Configuration) 리소스의 메서드를 실행합니다.

이 cmdlet은 구성 문서를 만들지 않고 DSC 리소스를 직접 호출합니다. 이 cmdlet을 사용 하 여 구성 관리 제품은 DSC 리소스를 사용 하 여 windows 또는 Linux를 관리할 수 있습니다. 이 cmdlet을 사용하면 디버깅을 사용하도록 설정한 상태에서 DSC 엔진이 실행 중일 때에도 리소스를 디버그할 수 있습니다.

> [!NOTE]
> `Invoke-DscResource` 는 PowerShell 7의 실험적 기능입니다. Cmdlet을 사용 하려면 다음 명령을 사용 하 여 cmdlet을 사용 하도록 설정 해야 합니다.
>
> `Enable-ExperimentalFeature PSDesiredStateConfiguration.InvokeDscResource`

## 예제

### 예제 1: 필수 속성을 지정 하 여 리소스의 Set 메서드를 호출 합니다.

이 예제에서는 **windowsprocess** 라는 리소스의 **Set** 메서드를 호출 하 고, 지정 된 Windows 프로세스를 시작 하기 위한 필수 **경로** 및 **인수** 속성을 제공 합니다.

```powershell
Invoke-DscResource -Name WindowsProcess -Method Set -ModuleName PSDesiredStateConfiguration -Property @{
  Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'
  Arguments = ''
}
```

### 예제 2: 지정 된 모듈에 대 한 리소스의 테스트 메서드 호출

이 예제에서는 **PSDesiredStateConfiguration** 라는 모듈에 있는 **windowsprocess** 라는 리소스의 **테스트** 메서드를 호출 합니다.

```powershell
$SplatParam = @{
  Name = 'WindowsProcess'
  ModuleName = 'PSDesiredStateConfiguration'
  Property = @{Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'; Arguments = ''}
  Method = Test
}

Invoke-DscResource @SplatParam
```

## PARAMETERS

### -메서드

이 cmdlet이 호출 하는 리소스의 메서드를 지정 합니다. 이 매개 변수에 허용 되는 값은 **Get** , **Set** 및 **Test** 입니다.

```yaml
Type: String
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
Type: ModuleSpecification
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
Type: String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -속성

해시 테이블의 리소스 속성 이름 및 해당 값을 키와 값으로 각각 지정합니다.

```yaml
Type: Hashtable
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

- 이전에는 Windows PowerShell 5.1 리소스가 **PsDscRunAsCredential** 키를 사용 하 여 사용자 컨텍스트에 지정 되지 않는 한 시스템 컨텍스트에서 실행 되었습니다. PowerShell 7.0에서 리소스는 사용자의 컨텍스트에서 실행 되 고 **PsDscRunAsCredential** 는 더 이상 지원 되지 않습니다. 이 키를 사용 하는 이전 구성에서는 예외가 throw 됩니다.

- PowerShell 7에서는 `Invoke-DscResource` 더 이상 WMI DSC 리소스의 호출을 지원 하지 않습니다. 여기에는 **PSDesiredStateConfiguration** 의 **File** 및 **Log** 리소스가 포함됩니다.

## 관련 링크

[Windows PowerShell Desired State Configuration 개요](/powershell/scripting/dsc/overview/dscforengineers)

[Get-DscResource](Get-DscResource.md)
