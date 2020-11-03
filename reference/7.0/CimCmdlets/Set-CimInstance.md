---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/set-ciminstance?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-CimInstance
ms.openlocfilehash: 9d68e59cf00e94a2318190800c47a4248a384e6f
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93218521"
---
# Set-CimInstance

## 개요
Cim 클래스의 ModifyInstance 메서드를 호출 하 여 CIM 서버에서 CIM 인스턴스를 수정 합니다.

## SYNTAX

### CimInstanceComputerSet (기본값)

```
Set-CimInstance [-ComputerName <String[]>] [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-Property <IDictionary>] [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### CimInstanceSessionSet

```
Set-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-Property <IDictionary>] [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### QuerySessionSet

```
Set-CimInstance -CimSession <CimSession[]> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-Query] <String> [-QueryDialect <String>] -Property <IDictionary> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### QueryComputerSet

```
Set-CimInstance [-ComputerName <String[]>] [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-Query] <String> [-QueryDialect <String>] -Property <IDictionary> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## 설명

이 cmdlet은 CIM 서버에서 CIM 인스턴스를 수정 합니다.

**InputObject** 매개 변수를 지정 하지 않으면 cmdlet은 다음 방법 중 하나로 작동 합니다.

- **ComputerName** 매개 변수와 **CimSession** 매개 변수를 모두 지정 하지 않으면이 Cmdlet은 COM (구성 요소 개체 모델) 세션을 사용 하 여 WMI (로컬 WMI(Windows Management Instrumentation))에서 작동 합니다.
- **Computername** 매개 변수 또는 **CimSession** 매개 변수를 지정 하는 경우이 cmdlet은 **computername** 매개 변수 또는 **CimSession** 매개 변수로 지정 된 CIM 서버에 대해 작동 합니다.

**InputObject** 매개 변수를 지정 하는 경우 cmdlet은 다음 방법 중 하나로 작동 합니다.

- **ComputerName** 매개 변수와 **CimSession** 매개 변수를 모두 지정 하지 않으면이 cmdlet은 입력 개체의 컴퓨터 이름과 CIM 세션을 사용 합니다.
- **ComputerName** 매개 변수 또는 **CimSession** 매개 변수 중 하나가 지정 된 경우이 cmdlet은 **CimSession** 매개 변수 값 또는 **ComputerName** 매개 변수 값을 사용 합니다. 이는 그다지 일반적이 지 않습니다.

## 예제

### 예제 1: CIM 인스턴스 설정

이 예에서는 **쿼리** 매개 변수를 사용 하 여 **VariableValue** 속성의 값을 **abcd** 로 설정 합니다. WQL (WMI(Windows Management Instrumentation) Query Language) 쿼리와 일치 하는 인스턴스를 수정할 수 있습니다.

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"}
```

### 예 2: 파이프라인을 사용 하 여 CIM 인스턴스 속성 설정

이 예에서는 cmdlet을 사용 하 여 **쿼리** 매개 변수를 통해 필터링 된 CIM 인스턴스 개체를 검색 합니다 `Get-CimInstance` . `Set-CimInstance`Cmdlet은 **VariableValue** 속성의 값을 **abcd** 로 수정 합니다.

```powershell
Get-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' |
  Set-CimInstance -Property @{VariableValue="abcd"}
```

### 예제 3: input 개체를 사용 하 여 CIM 인스턴스 속성 설정

```powershell
$x = Get-CimInstance -Query 'Select * from Win32_Environment where Name="testvar"'
Set-CimInstance -InputObject $x -Property @{VariableValue="somevalue"} -PassThru
```

이 예에서는를 사용 하 여 변수에서 쿼리 매개 변수로 필터링 된 CIM 인스턴스 개체를 검색 한 `$x` `Get-CimInstance` 다음 변수의 내용을 cmdlet에 전달 합니다 `Set-CimInstance` . `Set-CimInstance` 그런 다음 **VariableValue** 속성을 **somevalue** 로 수정 합니다. **Passthru** 매개 변수를 사용 하기 때문에이 예에서는 수정 된 CIM 인스턴스 개체를 반환 합니다.

### 예제 4: CIM 인스턴스 속성 설정

이 예에서는 cmdlet을 사용 하 여 **쿼리** 매개 변수에 지정 된 CIM 인스턴스 개체를 변수로 검색 하 `$x` `Get-CimInstance` 고 변경할 개체의 **VariableValue** 속성 값을 변경 합니다. 그런 다음 cmdlet을 사용 하 여 CIM 인스턴스 개체를 저장 합니다 `Set-CimInstance` .
**Passthru** 매개 변수를 사용 하기 때문에이 예에서는 수정 된 CIM 인스턴스 개체를 반환 합니다.

```powershell
$x = Get-CimInstance -Query 'Select * from Win32_Environment where name="testvar"'
$x.VariableValue = "Change"
Set-CimInstance -CimInstance $x -PassThru
```

### 예 5: WhatIf를 사용 하 여 수정할 CIM 인스턴스 목록 표시

이 예제에서는 일반 매개 변수 **WhatIf** 를 사용 하 여 수정 작업을 수행 하지 않도록 지정 하지만 완료 된 경우에만 발생 하는 결과를 출력 합니다.

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"} -WhatIf
```

### 예 6: 사용자의 확인 후 CIM 인스턴스 설정

이 예에서는 일반 매개 변수 **확인** 을 사용 하 여 사용자가 확인 한 후에만 수정 작업을 수행 하도록 지정 합니다.

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"} -Confirm
```

### 예 7: 만든 CIM 인스턴스 설정

이 예에서는 cmdlet을 사용 하 여 지정 된 속성을 사용 하 여 CIM 인스턴스를 만들고 `New-CimInstance` 해당 내용을 변수에 검색 `$x` 합니다. 그런 다음 변수는 cmdlet으로 전달 되어 `Set-CimInstance` **VariableValue** 속성의 값을 **somevalue** 로 수정 합니다.
**Passthru** 매개 변수를 사용 하기 때문에이 예에서는 수정 된 CIM 인스턴스 개체를 반환 합니다.

```powershell
$x = New-CimInstance -ClassName Win32_Environment -Property @{Name="testvar";UserName="domain\user"} -Keys Name,UserName -ClientOnly
Set-CimInstance -CimInstance $x -Property @{VariableValue="somevalue"} -PassThru
```

## PARAMETERS

### -CimSession

원격 컴퓨터에서 cmdlet을 실행 합니다. 컴퓨터 이름 또는 세션 개체 (예: 또는 cmdlet의 출력)를 입력 `New-CimSession` 합니다 `Get-CimSession` .

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimInstanceSessionSet, QuerySessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ComputerName

CIM 작업을 실행 하려는 컴퓨터의 이름을 지정 합니다. FQDN (정규화 된 도메인 이름) 또는 NetBIOS 이름을 지정할 수 있습니다.

이 매개 변수를 지정 하지 않으면 cmdlet은 COM (구성 요소 개체 모델)을 사용 하 여 로컬 컴퓨터에서 작업을 수행 합니다.

이 매개 변수를 지정 하면 cmdlet이 WsMan 프로토콜을 사용 하 여 지정 된 컴퓨터에 대 한 임시 세션을 만듭니다.

동일한 컴퓨터에서 여러 작업을 수행 하는 경우 CIM 세션을 사용 하 여 연결 하면 성능이 향상 됩니다.

```yaml
Type: System.String[]
Parameter Sets: CimInstanceComputerSet, QueryComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

입력으로 사용할 CIM 인스턴스 개체를 지정 합니다.

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases: CimInstance

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Namespace

CIM 작업에 대 한 네임 스페이스를 지정 합니다. 기본 네임 스페이스는 root/cimv2입니다. PowerShell에서 네임 스페이스 목록을 제공 하기 위해 로컬 WMI 서버에서 네임 스페이스 목록을 가져오기 때문에 탭 완성 기능을 사용 하 여 네임 스페이스 목록을 찾아볼 수 있습니다.

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -OperationTimeoutSec

Cmdlet이 컴퓨터의 응답을 기다리는 시간을 지정 합니다. 기본적으로이 매개 변수의 값은 0 이며이는 cmdlet이 서버에 대 한 기본 시간 제한 값을 사용 함을 의미 합니다.

**Operationtimeoutsec** 매개 변수가 강력한 연결 다시 시도 시간 제한 3 분 보다 작은 값으로 설정 된 경우, 서버에서 작업을 다시 연결할 수 있기 때문에 **operationtimeoutsec** 매개 변수의 값 보다 마지막으로 네트워크 오류가 복구 되지 않습니다.

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

작업 중인 항목을 나타내는 개체를 반환합니다. 기본적으로 이 cmdlet은 출력을 생성하지 않습니다.

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

### -속성

이름-값 쌍을 사용 하 여 CIM 인스턴스의 속성을 해시 테이블로 지정 합니다. 이 매개 변수를 사용 하 여 지정한 속성만 변경 됩니다. CIM 인스턴스의 다른 속성은 변경 되지 않습니다.

```yaml
Type: System.Collections.IDictionary
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet, QuerySessionSet, QueryComputerSet
Aliases: Arguments

Required: True (QuerySessionSet, QueryComputerSet), False (CimInstanceComputerSet, CimInstanceSessionSet)
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Query

Cmdlet을 실행할 CIM 인스턴스를 검색 하기 위해 CIM 서버에서 실행할 쿼리를 지정 합니다. QueryDialect 매개 변수를 사용 하 여 쿼리 언어를 지정할 수 있습니다.

지정 된 값에 큰따옴표 ( `"` ), 작은따옴표 () `'` 또는 백슬래시 ()가 포함 된 경우 `\` 백슬래시 () 문자를 접두사로 사용 하 여 해당 문자를 이스케이프 해야 합니다 `\` . 지정 된 값이 WQL **LIKE** 연산자를 사용 하는 경우 대괄호 ( `[]` ): 백분율 ( `%` ), 밑줄 ( `_` ) 또는 여는 대괄호 ()로 묶어 다음 문자를 이스케이프 해야 합니다 `[` .

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -QueryDialect

쿼리 매개 변수에 사용 되는 쿼리 언어를 지정 합니다. 이 매개 변수에 허용 되는 값은 **WQL** 또는 **CQL** 입니다. 기본값은 **WQL** 입니다.

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ResourceUri

리소스 클래스 또는 인스턴스의 리소스 URI (uniform resource identifier)를 지정 합니다. URI는 컴퓨터에서 특정 유형의 리소스(예: 디스크 또는 프로세스)를 식별하는 데 사용됩니다.

URI는 접두사와 리소스 경로로 구성됩니다. 다음은 그 예입니다. 

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

기본적으로이 매개 변수를 지정 하지 않으면 DMTF 표준 리소스 URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` 가 사용 되 고 클래스 이름이 추가 됩니다.

ResourceURI는 WSMan 프로토콜을 사용 하 여 만든 CIM 세션에만 사용할 수 있으며, ComputerName 매개 변수를 지정 하는 경우에만 WSMan을 사용 하 여 CIM 세션을 만들 수 있습니다. ComputerName 매개 변수를 지정 하지 않고이 매개 변수를 지정 하거나 DCOM 프로토콜을 사용 하 여 만든 CIM 세션을 지정 하는 경우 DCOM 프로토콜이 ResourceURI 매개 변수를 지원 하지 않으므로 오류가 발생 합니다.

**ResourceUri** 매개 변수와 **필터** 매개 변수를 모두 지정 하면 **필터** 매개 변수가 무시 됩니다.

```yaml
Type: System.Uri
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases:

Required: False
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

cmdlet을 실행할 경우 발생하는 일을 표시합니다. cmdlet은 실행되지 않습니다.

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

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### Ciminstance 개체로.

## 출력

### Ciminstance 개체로.

**Passthru** 매개 변수를 지정 하면이 cmdlet이 수정 된 CIM 인스턴스 개체를 반환 합니다.

## 참고

## 관련 링크

[Get-CimInstance](get-ciminstance.md)

[New-CimInstance](New-CimInstance.md)

[Remove-CimInstance](remove-ciminstance.md)
