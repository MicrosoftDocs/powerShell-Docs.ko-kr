---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 01/21/2020
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/invoke-cimmethod?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-CimMethod
ms.openlocfilehash: 328abb5776366f6e2d9b5106c93337f5d45533ed
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93218113"
---
# Invoke-CimMethod

## 개요
CIM 클래스의 메서드를 호출 합니다.

## SYNTAX

### ClassNameComputerSet (기본값)

```
Invoke-CimMethod [-ClassName] <String> [-ComputerName <String[]>] [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### ClassNameSessionSet

```
Invoke-CimMethod [-ClassName] <String> -CimSession <CimSession[]> [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### ResourceUriComputerSet

```
Invoke-CimMethod -ResourceUri <Uri> [-ComputerName <String[]>] [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### CimInstanceSessionSet

```
Invoke-CimMethod [-ResourceUri <Uri>] [-InputObject] <CimInstance> -CimSession <CimSession[]>
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### CimInstanceComputerSet

```
Invoke-CimMethod [-ResourceUri <Uri>] [-InputObject] <CimInstance> [-ComputerName <String[]>]
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### ResourceUriSessionSet

```
Invoke-CimMethod -ResourceUri <Uri> -CimSession <CimSession[]> [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### CimClassComputerSet

```
Invoke-CimMethod [-CimClass] <CimClass> [-ComputerName <String[]>] [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CimClassSessionSet

```
Invoke-CimMethod [-CimClass] <CimClass> -CimSession <CimSession[]> [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### QueryComputerSet

```
Invoke-CimMethod -Query <String> [-QueryDialect <String>] [-ComputerName <String[]>]
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### QuerySessionSet

```
Invoke-CimMethod -Query <String> [-QueryDialect <String>] -CimSession <CimSession[]>
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Invoke-CimMethod`Cmdlet은 **Arguments** 매개 변수로 지정 된 이름-값 쌍을 사용 하 여 CIM 클래스 또는 cim 인스턴스의 메서드를 호출 합니다.

**InputObject** 매개 변수를 지정 하지 않으면 cmdlet은 다음 방법 중 하나로 작동 합니다.

- **ComputerName** 매개 변수와 **CimSession** 매개 변수를 모두 지정 하지 않으면이 Cmdlet은 COM (구성 요소 개체 모델) 세션을 사용 하 여 WMI (로컬 WMI(Windows Management Instrumentation))에서 작동 합니다.
- **Computername** 매개 변수 또는 **CimSession** 매개 변수를 지정 하는 경우이 cmdlet은 **computername** 매개 변수 또는 **CimSession** 매개 변수로 지정 된 CIM 서버에 대해 작동 합니다.

**InputObject** 매개 변수를 지정 하는 경우 cmdlet은 다음 방법 중 하나로 작동 합니다.

- **ComputerName** 매개 변수와 **CimSession** 매개 변수를 모두 지정 하지 않으면이 cmdlet은 입력 개체의 컴퓨터 이름과 CIM 세션을 사용 합니다.
- **ComputerName** 매개 변수 또는 **CimSession** 매개 변수 중 하나가 지정 된 경우이 cmdlet은 **CimSession** 매개 변수 값 또는 **ComputerName** 매개 변수 값을 사용 합니다. 이는 일반적인 시나리오가 아닙니다.

## 예제

### 예제 1: 메서드 호출

이 예제에서는 **Win32_Process** 클래스의 **Terminate** 메서드를 호출 합니다.

```powershell
Invoke-CimMethod -Query 'select * from Win32_Process where name like "notepad%"' -MethodName "Terminate"
```

### 예제 2: CIM 인스턴스 개체를 사용 하 여 메서드 호출

이 예에서는 CIM 인스턴스 개체를 검색 하 여 `$x` cmdlet을 사용 하 여 라는 변수에 저장 합니다 `Get-CimInstance` . 그러면 변수의 내용이 cmdlet에 대 한 **InputObject** 로 사용 됩니다 `Invoke-CimMethod` . **Getowner** 메서드가 **ciminstance 개체로** 에 대해 호출 됩니다.

```powershell
$x = Get-CimInstance -Query 'Select * from Win32_Process where name like "notepad%"'
Invoke-CimMethod -InputObject $x -MethodName GetOwner
```

### 예제 3: 인수를 사용 하 여 정적 메서드 호출

이 예제에서는 **Arguments** 매개 변수를 사용 하 여 라는 **Create** 메서드를 호출 합니다.

```powershell
Invoke-CimMethod -ClassName Win32_Process -MethodName "Create" -Arguments @{
  CommandLine = 'notepad.exe'; CurrentDirectory = "C:\windows\system32"
}
```

### 예제 4: 클라이언트 쪽 유효성 검사

이 예제에서는 **CimClass** 개체를에 전달 하 여 **xyz** 메서드에 대 한 클라이언트 쪽 유효성 검사를 수행 `Invoke-CimMethod` 합니다.

```powershell
$c = Get-CimClass -ClassName Win32_Process
Invoke-CimMethod -CimClass $c -MethodName "xyz" -Arguments @{ CommandLine = 'notepad.exe' }
```

## PARAMETERS

### -Arguments

호출된 메서드에 전달할 매개 변수를 지정합니다. 이 매개 변수에 대 한 값을 해시 테이블에 저장 된 이름-값 쌍으로 지정 합니다. 입력 한 값의 순서는 중요 하지 않습니다.

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -CimClass

서버의 CIM 클래스 정의를 나타내는 CIM 클래스 개체를 지정 합니다. 클래스의 정적 메서드를 호출할 때이 매개 변수를 사용 합니다.

Cmdlet을 사용 하 여 `Get-CimClass` 서버에서 클래스 정의를 검색할 수 있습니다.

이 매개 변수를 사용 하면 클라이언트 쪽 스키마 유효성 검사가 향상 됩니다.

```yaml
Type: Microsoft.Management.Infrastructure.CimClass
Parameter Sets: CimClassComputerSet, CimClassSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -CimSession

지정 된 CIM 세션을 사용 하 여 명령을 실행 합니다. CIM 세션을 포함 하는 변수 또는 CIM 세션을 만들거나 가져오는 명령 (예: 또는 cmdlet)을 입력 합니다 `New-CimSession` `Get-CimSession` . 자세한 내용은 [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)를 참조 하세요.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: ClassNameSessionSet, CimInstanceSessionSet, CimClassSessionSet, QuerySessionSet, ResourceUriSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ClassName

작업을 수행할 CIM 클래스의 이름을 지정 합니다. 이 매개 변수는 정적 메서드에만 사용 됩니다. PowerShell은 클래스 이름 목록을 제공 하기 위해 로컬 WMI 서버에서 클래스 목록을 가져오기 때문에 탭 완성 기능을 사용 하 여 클래스 목록을 찾아볼 수 있습니다.

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet
Aliases: Class

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ComputerName

CIM 작업을 실행 하려는 컴퓨터의 이름을 지정 합니다. FQDN (정규화 된 도메인 이름), NetBIOS 이름 또는 IP 주소를 지정할 수 있습니다.

이 매개 변수를 사용 하는 경우 cmdlet은 WsMan 프로토콜을 사용 하 여 지정 된 컴퓨터에 대 한 임시 세션을 만듭니다. 그렇지 않으면 cmdlet은 COM (구성 요소 개체 모델)을 사용 하 여 로컬 컴퓨터에서 작업을 수행 합니다.

동일한 컴퓨터에서 여러 작업을 수행 하는 경우 더 나은 성능을 위해 CIM 세션을 사용 하 여 연결 합니다.

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ResourceUriComputerSet, CimClassComputerSet, CimInstanceComputerSet, QueryComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InputObject

메서드를 호출 하기 위한 입력으로 사용할 CIM 인스턴스 개체를 지정 합니다. 이 매개 변수는 인스턴스 메서드를 호출 하는 데만 사용할 수 있습니다. 클래스의 정적 메서드를 호출 하려면 **클래스** 매개 변수 또는 **CimClass** 매개 변수를 사용 합니다.

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: CimInstanceSessionSet, CimInstanceComputerSet
Aliases: CimInstance

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -MethodName

호출할 CIM 메서드의 이름을 지정 합니다. 이 매개 변수는 필수이며 null이거나 비어 있을 수 없습니다. CIM 클래스의 정적 메서드를 호출 하려면 **ClassName** 또는 **CimClass** 매개 변수를 사용 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Name

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Namespace

CIM 작업에 대 한 네임 스페이스를 지정 합니다. 기본 네임 스페이스는 **root/cimv2** 입니다. PowerShell에서 네임 스페이스 목록을 제공 하기 위해 로컬 WMI 서버에서 네임 스페이스 목록을 가져오기 때문에 탭 완성 기능을 사용 하 여 네임 스페이스 목록을 찾아볼 수 있습니다.

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, ResourceUriComputerSet, ResourceUriSessionSet, QueryComputerSet, QuerySessionSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -OperationTimeoutSec

Cmdlet이 컴퓨터의 응답을 기다리는 시간을 지정 합니다. 기본적으로이 값은 0입니다. 즉, cmdlet이 서버에 대 한 기본 시간 제한 값을 사용 합니다.

**Operationtimeoutsec** 매개 변수가 기본 연결 다시 시도 시간 제한 3 분 보다 작은 값으로 설정 된 경우 **operationtimeoutsec** 매개 변수 값 보다 마지막으로 지난 네트워크 오류는 복구할 수 없습니다.

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

### -Query

CIM 서버에서 실행할 쿼리를 지정 합니다. 쿼리 결과로 받은 인스턴스에서 메서드가 호출 됩니다. **Querydialect** 매개 변수를 사용 하 여 쿼리 언어를 지정할 수 있습니다.

지정 된 값에 큰따옴표 ( `"` ), 작은따옴표 () `'` 또는 백슬래시 ()가 포함 된 경우 `\` 백슬래시 () 문자를 접두사로 사용 하 여 해당 문자를 이스케이프 해야 합니다 `\` . 지정 된 값이 WQL LIKE 연산자를 사용 하는 경우 대괄호 ( `[]` ): 백분율 ( `%` ), 밑줄 ( `_` ) 또는 여는 대괄호 ()로 묶어 다음 문자를 이스케이프 해야 합니다 `[` .

```yaml
Type: System.String
Parameter Sets: QueryComputerSet, QuerySessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -QueryDialect

쿼리 매개 변수에 사용 되는 쿼리 언어를 지정 합니다. 이 매개 변수에 허용 되는 값은 **WQL** 또는 **CQL** 입니다.

기본값은 **WQL** 입니다.

```yaml
Type: System.String
Parameter Sets: QueryComputerSet, QuerySessionSet
Aliases:

Required: False
Position: Named
Default value: WQL
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ResourceUri

리소스 클래스 또는 인스턴스의 리소스 URI (uniform resource identifier)를 지정 합니다.
URI는 컴퓨터에서 특정 유형의 리소스(예: 디스크 또는 프로세스)를 식별하는 데 사용됩니다.

URI는 접두사와 리소스 경로로 구성됩니다. 다음은 그 예입니다. 

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

기본적으로이 매개 변수를 지정 하지 않으면 DMTF 표준 리소스 URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` 가 사용 되 고 클래스 이름이 추가 됩니다.

**ResourceURI** 는 wsman 프로토콜을 사용 하 여 만든 cim 세션에만 사용할 수 있으며, **ComputerName** 매개 변수를 지정 하는 경우에만 wsman을 사용 하 여 cim 세션을 만들 수 있습니다.

**ComputerName** 매개 변수를 지정 하지 않고이 매개 변수를 지정 하거나 DCOM 프로토콜을 사용 하 여 만든 CIM 세션을 지정 하면 오류가 발생 합니다. DCOM 프로토콜은 **ResourceURI** 매개 변수를 지원 하지 않습니다.

**ResourceUri** 매개 변수와 **필터** 매개 변수를 모두 지정 하면 **필터** 매개 변수가 무시 됩니다.

```yaml
Type: System.Uri
Parameter Sets: ResourceUriSessionSet, ResourceUriComputerSet
Aliases:

Required: True (ResourceUriSessionSet, ResourceUriComputerSet), False (CimInstanceSessionSet, CimInstanceComputerSet)
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

### CimClass.

이 cmdlet은 CIM 클래스를 입력 개체로 받아들입니다.

### Ciminstance 개체로.

이 cmdlet은 CIM 인스턴스를 입력 개체로 받아들입니다.

## 출력

### PSCustomObject.

이 cmdlet은 개체를 반환 합니다.

## 참고

## 관련 링크

[Get-CimClass](get-cimclass.md)

[Get-CimInstance](get-ciminstance.md)

[Get-CimSession](Get-CimSession.md)

[New-CimSession](New-CimSession.md)
