---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 04/29/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/set-dsclocalconfigurationmanager?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-DscLocalConfigurationManager
ms.openlocfilehash: 0d35aa56a52f0e6c17abd0e7b2707869e780324c
ms.sourcegitcommit: 0d4d3e47f6979876550591f62061096e7a568f7e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2020
ms.locfileid: "93218017"
---
# Set-DscLocalConfigurationManager

## 개요

LCM (로컬 Configuration Manager) 설정을 노드에 적용 합니다.

## SYNTAX

### ComputerNameSet (기본값)

```
Set-DscLocalConfigurationManager [-Path] <String> [-Force] [[-ComputerName] <String[]>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CimSessionSet

```
Set-DscLocalConfigurationManager [-Path] <String> [-Force] [-ThrottleLimit <Int32>] -CimSession <CimSession[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Set-DscLocalConfigurationManager`Cmdlet은 LCM 설정 또는 메타 구성을 노드에 적용 합니다. 컴퓨터 이름을 지정하거나 CIM(Common Information Model) 세션을 사용하여 컴퓨터를 지정합니다. 대상 컴퓨터를 지정하지 않으면 cmdlet이 로컬 컴퓨터에 설정을 적용합니다.

## 예제

### 예제 1: LCM 설정 적용

```
Set-DscLocalConfigurationManager -Path "C:\DSC\Configurations\"
```

이 명령은에서 대상 노드에 LCM 설정을 적용 `C:\DSC\Configurations\` 합니다. 설정을 받은 후 LCM에서 해당 설정을 처리 합니다.

> [!WARNING]
> 지정 된 폴더에 저장 된 동일한 컴퓨터에 대 한 메타 mof 여러 개 있는 경우 첫 번째 메타 mof만 적용 됩니다.

### 예제 2: CIM 세션을 사용 하 여 LCM 설정 적용

```
$Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
Set-DscLocalConfigurationManager -Path "C:\DSC\Configurations\" -CimSession $Session
```

이 예제에서는 컴퓨터에 LCM 설정을 적용 하 고 설정을 적용 합니다. 또한 cmdlet에 사용하기 위해 이름이 Server01인 컴퓨터에 대한 CIM 세션을 만듭니다. 또는 지정한 여러 컴퓨터에 cmdlet을 적용하기 위해 CIM 세션 배열을 만듭니다.

첫 번째 명령은 cmdlet을 사용 하 여 CIM 세션을 만든 `New-CimSession` 다음 변수에 **CimSession** 개체를 저장 합니다 `$Session` . 또한 암호를 입력하라는 메시지를 표시합니다. 자세한 내용을 보려면 `Get-Help New-CimSession`를 입력하십시오.

두 번째 명령은에서 대상 노드에 대 한 LCM 설정을 `C:\DSC\Configurations\` 변수에 저장 된 **CimSession** 개체로 식별 된 컴퓨터에 적용 `$Session` 합니다. 이 예에서 `$Session` 변수는 이름이 Server01 인 컴퓨터에 대 한 CIM 세션을 포함 합니다. 명령이 설정을 적용합니다. 설정을 받은 후 LCM에서 해당 설정을 처리 합니다.

## PARAMETERS

### -CimSession

원격 세션에서 또는 원격 컴퓨터에서 cmdlet을 실행합니다. [CimSession](/powershell/module/CimCmdlets/New-CimSession) 또는 [CimSession](/powershell/module/CimCmdlets/Get-CimSession) cmdlet의 출력과 같은 컴퓨터 이름 또는 세션 개체를 입력 합니다.
기본값은 로컬 컴퓨터의 현재 세션입니다.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ComputerName

컴퓨터 이름 배열을 지정합니다. 이 매개 변수는 **Path** 매개 변수에서 메타 구성 문서가 있는 컴퓨터를 배열에 지정 된 것으로 제한 합니다.

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Credential

대상 컴퓨터에 대한 사용자 이름과 암호를 **PSCredential** 개체로 지정합니다. **PSCredential** 개체를 가져오려면 Get-Credential cmdlet을 사용합니다. 자세한 내용을 보려면 `Get-Help Get-Credential`를 입력하십시오.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

사용자 확인을 요청하지 않고 명령을 강제 실행합니다.

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

### -Path

구성 설정 파일이 포함된 폴더의 파일 경로를 지정합니다. Cmdlet은 지정 된 경로에 설정 파일이 있는 컴퓨터에 이러한 LCM 설정을 게시 하 고 적용 합니다. 각 대상 노드에는 다음 형식의 설정 파일이 있어야 합니다 `NetBIOS Name.meta.mof` ..

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

cmdlet을 실행하도록 설정할 수 있는 최대 동시 작업 수를 지정합니다. 이 매개 변수를 생략 하거나 값을 `0` 입력 하면 Windows PowerShell은 컴퓨터에서 실행 되는 CIM cmdlet의 수에 따라 cmdlet에 대 한 최적의 스로틀 제한을 계산 합니다. 스로틀 제한은 현재 cmdlet에만 적용되며 세션이나 컴퓨터에는 적용되지 않습니다.

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

## 출력

## 참고

## 관련 링크

[Windows PowerShell Desired State Configuration 개요](/powershell/scripting/dsc/overview/overview)

[Get DscLocalConfigurationManager](Get-DscLocalConfigurationManager.md)
