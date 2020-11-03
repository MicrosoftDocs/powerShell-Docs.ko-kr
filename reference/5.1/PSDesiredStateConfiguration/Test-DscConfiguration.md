---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/test-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-DscConfiguration
ms.openlocfilehash: 25c8bc61976ce3940e0b9bd949fa3ee60728450d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213577"
---
# Test-DscConfiguration

## 개요
노드의 실제 구성이 원하는 구성과 일치하는지 여부를 테스트합니다.

## SYNTAX

### ComputerNameSet (기본값)

```
Test-DscConfiguration [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-AsJob] [-Detailed] [<CommonParameters>]
```

### ComputerNameAndPathSet

```
Test-DscConfiguration [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-AsJob] [-Path] <String> [<CommonParameters>]
```

### ComputerNameAndReferenceConfigurationSet

```
Test-DscConfiguration [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-AsJob] -ReferenceConfiguration <String> [<CommonParameters>]
```

### CimSessionAndPathSet

```
Test-DscConfiguration [-ThrottleLimit <Int32>] -CimSession <CimSession[]> [-AsJob] [-Path] <String>
 [<CommonParameters>]
```

### CimSessionAndReferenceConfigurationSet

```
Test-DscConfiguration [-ThrottleLimit <Int32>] -CimSession <CimSession[]> [-AsJob]
 -ReferenceConfiguration <String> [<CommonParameters>]
```

### CimSessionSet

```
Test-DscConfiguration [-ThrottleLimit <Int32>] -CimSession <CimSession[]> [-AsJob] [-Detailed]
 [<CommonParameters>]
```

## 설명
**Test-DscConfiguration** cmdlet은 노드의 실제 구성이 원하는 구성과 일치하는지 여부를 테스트합니다.
컴퓨터 이름 또는 CIM(Common Information Model) (CIM) 세션을 사용 하 여 구성을 테스트 하려는 컴퓨터를 지정 합니다.
대상 컴퓨터를 지정하지 않으면 cmdlet이 로컬 컴퓨터의 구성을 테스트합니다.

원하는 구성과 실제 구성이 일치 하면 cmdlet이 ' t r u e '의 문자열 값을 반환 합니다.
그렇지 않으면 ' f a l s e '의 문자열 값을 반환 합니다.

## 예제

### 예제 1: 로컬 컴퓨터에 대 한 테스트 구성

```
PS C:\> Test-DscConfiguration
```

이 명령은 로컬 컴퓨터의 구성을 테스트합니다.

### 예 2: 지정 된 컴퓨터에 대 한 구성 테스트

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Test-DscConfiguration -CimSession $Session
```

이 예제에서는 CIM 세션에 지정된 컴퓨터의 구성을 테스트합니다.
또한 cmdlet에 사용하기 위해 이름이 Server01인 컴퓨터에 대한 CIM 세션을 만듭니다.
또는 지정한 여러 컴퓨터에 cmdlet을 적용하기 위해 CIM 세션 배열을 만듭니다.

첫 번째 명령은 **New-CimSession** cmdlet을 사용하여 CIM 세션을 만든 다음 **CimSession** 개체를 $Session 변수에 저장합니다.
또한 암호를 입력하라는 메시지를 표시합니다.
자세한 내용을 보려면 `Get-Help New-CimSession`를 입력하십시오.

두 번째 명령은 $Session 변수에 저장 된 **CimSession** 개체로 식별 된 컴퓨터 (이 경우 이름이 Server01 인 컴퓨터)의 구성을 테스트 합니다.

### 예제 3: 자세한 결과를 포함 하는 테스트 구성

```
PS C:\> Test-DscConfiguration -ComputerName "Server01", "Server02", "Server03" -Detailed
```

이 명령은 *ComputerName* 매개 변수로 지정 된 컴퓨터 집합에 대 한 구성을 테스트 하 고 전체 상태, 원하는 상태에 있는 리소스, 원하는 상태 및 컴퓨터 이름에 없는 리소스를 포함 하는 세부 정보를 반환 합니다.

### 예제 4: 폴더에 지정 된 테스트 구성

```
PS C:\> Test-DscConfiguration -Path "C:\Dsc\Configurations"
```

이 명령은 *Path* 매개 변수로 지정 된 폴더에 정의 된 구성을 테스트 합니다.
구성은 구성 파일의 파일 이름으로 식별 되는 컴퓨터 집합에 대해 테스트 됩니다.

### 예 5: 파일에 지정 된 테스트 구성

```
PS C:\> Test-DscConfiguration -ReferenceConfiguration "C:\Dsc\Configurations\WebServer.mof" -ComputerName "Server01", "Server02", "Server03"
```

이 명령은 *ComputerName* 매개 변수로 지정 된 컴퓨터 집합에 대해 파일에 정의 된 구성을 테스트 합니다.

## PARAMETERS

### -AsJob
이 cmdlet이 명령을 백그라운드 작업으로 실행 함을 나타냅니다.

*AsJob* 매개 변수를 지정 하는 경우이 명령은 작업을 나타내는 개체를 반환한 다음 명령 프롬프트를 표시 합니다.
작업이 완료 될 때까지 세션에서 작업을 계속할 수 있습니다.
AsJob 매개 변수를 사용하는 경우 이 명령은 백그라운드 작업을 나타내는 개체를 즉시 반환합니다.
작업을 관리하려면 Job cmdlet을 사용합니다.
작업 결과를 가져오려면 Receive-Job cmdlet을 사용하세요.

이 매개 변수를 사용 하려면 로컬 및 원격 컴퓨터를 원격으로 구성 하 고 Windows Vista 이상 버전의 Windows 운영 체제에서는 관리자 권한으로 실행 옵션을 사용 하 여 Windows PowerShell을 열어야 합니다.
자세한 내용은 [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)을 참조하세요.

Windows PowerShell 백그라운드 작업에 대 한 자세한 내용은 [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) 및 [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md)를 참조 하세요.

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
Parameter Sets: CimSessionAndPathSet, CimSessionAndReferenceConfigurationSet, CimSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ComputerName
이 cmdlet이 구성을 테스트 하는 컴퓨터 이름의 배열을 지정 합니다.
Cmdlet은 *Path* 매개 변수로 지정 된 위치에 있는 구성 문서를 이러한 컴퓨터에 테스트 합니다.

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet, ComputerNameAndPathSet, ComputerNameAndReferenceConfigurationSet
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Credential
대상 컴퓨터에 대한 사용자 이름과 암호를 **PSCredential** 개체로 지정합니다.
**PSCredential** 개체를 가져오려면 Get-Credential cmdlet을 사용합니다.
자세한 내용을 보려면 `Get-Help Get-Credential`를 입력하십시오.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameSet, ComputerNameAndPathSet, ComputerNameAndReferenceConfigurationSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Detailed
이 cmdlet이 구성 문서를 노드의 원하는 상태와 비교한 결과를 자세히 반환 함을 나타냅니다.
결과에는 전체 상태, 원하는 상태에 있는 리소스, 원하는 상태가 아닌 리소스, 컴퓨터 이름 등의 정보가 포함 됩니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerNameSet, CimSessionSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path
구성 문서 파일을 포함 하는 폴더의 경로를 지정 합니다.
Cmdlet은 *ComputerName* 또는 *CimSession* 매개 변수로 지정 된 컴퓨터의 원하는 상태에 대해 구성을 테스트 합니다.

```yaml
Type: System.String
Parameter Sets: ComputerNameAndPathSet, CimSessionAndPathSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ReferenceConfiguration
구성 문서 파일의 경로를 지정 합니다.
이 cmdlet은 *ComputerName* 또는 *CimSession* 매개 변수로 지정 된 컴퓨터의 실제 상태에 대 한 구성을 테스트 합니다.

```yaml
Type: System.String
Parameter Sets: ComputerNameAndReferenceConfigurationSet, CimSessionAndReferenceConfigurationSet
Aliases:

Required: True
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

[Get-DscConfigurationStatus](Get-DscConfigurationStatus.md)

[Restore-DscConfiguration](Restore-DscConfiguration.md)

[Start-DscConfiguration](Start-DscConfiguration.md)
