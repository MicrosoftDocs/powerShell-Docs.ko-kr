---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/new-ciminstance?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-CimInstance
ms.openlocfilehash: 7cd9d27eb291358fb4d2ee93d0a1e5ade3467249
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93218337"
---
# New-CimInstance

## 개요
CIM 인스턴스를 만듭니다.

## SYNTAX

### ClassNameComputerSet (기본값)

```
New-CimInstance [-ClassName] <String> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-ComputerName <String[]>] [-ClientOnly]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ClassNameSessionSet

```
New-CimInstance [-ClassName] <String> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] -CimSession <CimSession[]> [-ClientOnly]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ResourceUriSessionSet

```
New-CimInstance -ResourceUri <Uri> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] -CimSession <CimSession[]> [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### ResourceUriComputerSet

```
New-CimInstance -ResourceUri <Uri> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-ComputerName <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### CimClassSessionSet

```
New-CimInstance [-CimClass] <CimClass> [[-Property] <IDictionary>] [-OperationTimeoutSec <UInt32>]
 -CimSession <CimSession[]> [-ClientOnly] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CimClassComputerSet

```
New-CimInstance [-CimClass] <CimClass> [[-Property] <IDictionary>] [-OperationTimeoutSec <UInt32>]
 [-ComputerName <String[]>] [-ClientOnly] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`New-CimInstance`Cmdlet은 로컬 컴퓨터 또는 원격 컴퓨터의 클래스 정의를 기반으로 하는 CIM 클래스의 인스턴스를 만듭니다. 기본적으로 cmdlet은 `New-CimInstance` 로컬 컴퓨터에 인스턴스를 만듭니다.

## 예제

### 예제 1: CIM 클래스의 인스턴스 만들기

이 예제에서는 컴퓨터의 root/cimv2 네임 스페이스에 win32_environment 라는 CIM 클래스의 인스턴스를 만듭니다.

```powershell
New-CimInstance -ClassName Win32_Environment -Property @{Name="testvar";VariableValue="testvalue";UserName="domain\user"}
```

클래스가 없거나 속성이 올바르지 않거나 서버에서 호출을 거부 하는 경우 클라이언트 쪽 유효성 검사가 수행 되지 않습니다. 인스턴스가 성공적으로 만들어지면 cmdlet은 새로 만든 인스턴스를 출력 합니다.

### 예제 2: 클래스 스키마를 사용 하 여 CIM 클래스의 인스턴스 만들기

이 예제에서는 CIM 클래스 개체를 검색 하 여 라는 변수에 저장 `$class` 합니다. 그런 다음 변수의 내용이 cmdlet에 전달 됩니다 `New-CimInstance` .

```powershell
$class = Get-CimClass -ClassName Win32_Environment
New-CimInstance -CimClass $class -Property @{Name="testvar";VariableValue="testvalue";UserName="Contoso\User1"}
```

### 예 3: 클라이언트에서 동적 인스턴스 만들기

이 예제에서는 서버에서 인스턴스를 가져오지 않고 클라이언트 컴퓨터에 **Win32_Process** 라는 CIM 클래스의 동적 인스턴스를 만듭니다. 새 인스턴스는 변수에 저장 됩니다 `$a` . 이 키가 있는 인스턴스가 서버에 있는 경우이 동적 인스턴스를 사용 하 여 작업을 수행할 수 있습니다.

```powershell
$a = New-CimInstance -ClassName Win32_Process -Property @{Handle=0} -Key Handle -ClientOnly
Get-CimInstance -CimInstance $a
Invoke-CimMethod -CimInstance $a -MethodName GetOwner
```

```Output
ProcessId Name                HandleCount WorkingSetSize VirtualSize
--------- ----                ----------- -------------- -----------
0         System Idle Process 0           8192           8192

Domain         :
ReturnValue    : 2
User           :
PSComputerName :
```

`Get-CimInstance`그런 다음 cmdlet은 특정 단일 인스턴스를 검색 합니다. `Invoke-CimMethod`Cmdlet은 검색 된 인스턴스의 **getowner** 메서드를 호출 합니다.

### 예제 4: 특정 네임 스페이스의 CIM 클래스에 대 한 인스턴스 만들기

이 예제에서는 네임 스페이스 **루트/어딘가에** 있는 **MSFT_Something** 라는 CIM 클래스의 인스턴스를 가져와 라는 변수에 저장 `$class` 합니다. 변수는 `New-CimInstance` 새 CIM 인스턴스를 만들고 새 인스턴스에서 클라이언트 쪽 유효성 검사를 수행 하기 위해 cmdlet에 전달 됩니다.

```powershell
$class = Get-CimClass -ClassName MSFT_Something -Namespace root/somewhere
New-CimInstance -CimClass $class -Property @{"Prop1"=1;"Prop2"="value"} -ClientOnly
```

이 예에서는 **ClassName** 매개 변수 대신 **CimClass** 매개 변수를 사용 하 여 **Prop1** 및 **Prop2** 이 실제로 존재 하 고 키가 올바르게 표시 되어 있는지 확인 합니다.

**ComputerName** 또는 **CimSession** 매개 변수는 **clientonly** 매개 변수와 함께 사용할 수 없습니다.

## PARAMETERS

### -CimClass

인스턴스의 유형을 나타내는 CIM 클래스 개체를 지정 합니다. Cmdlet을 사용 `Get-CimClass` 하 여 컴퓨터에서 클래스 선언을 검색 합니다. 이 매개 변수를 사용 하면 클라이언트 쪽 스키마 유효성 검사가 향상 됩니다.

```yaml
Type: Microsoft.Management.Infrastructure.CimClass
Parameter Sets: CimClassSessionSet, CimClassComputerSet
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
Parameter Sets: ClassNameSessionSet, ResourceUriSessionSet, CimClassSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ClassName

작업에서 인스턴스를 만드는 CIM 클래스의 이름을 지정 합니다. 참고: PowerShell은 클래스 이름 목록을 제공 하기 위해 로컬 WMI 서버에서 클래스 목록을 가져오기 때문에 탭 완성 기능을 사용 하 여 클래스 목록을 찾아볼 수 있습니다.

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ClientOnly

인스턴스가 CIM 서버로 이동 하지 않고 PowerShell 에서만 생성 됨을 나타냅니다. 이 매개 변수를 사용 하 여 후속 PowerShell 작업에서 사용할 메모리 내 CIM 인스턴스를 만들 수 있습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, CimClassSessionSet, CimClassComputerSet
Aliases: Local

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

CIM 작업을 실행 하려는 컴퓨터의 이름을 지정 합니다. FQDN (정규화 된 도메인 이름), NetBIOS 이름 또는 IP 주소를 지정할 수 있습니다.

이 매개 변수를 지정 하면 cmdlet이 WSMan 프로토콜을 사용 하 여 지정 된 컴퓨터에 대 한 임시 세션을 만듭니다.

이 매개 변수를 지정 하지 않으면 cmdlet은 COM (구성 요소 개체 모델)을 사용 하 여 로컬 컴퓨터에서 작업을 수행 합니다.

동일한 컴퓨터에서 여러 작업을 수행 하는 경우 CIM 세션을 사용 하 여 연결 하면 성능이 향상 됩니다.

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ResourceUriComputerSet, CimClassComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -키

키로 사용 되는 속성을 지정 합니다. **키** 가 지정 된 경우에는 **CimSession** 및 **ComputerName** 을 사용할 수 없습니다.

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, ResourceUriSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Namespace

새 인스턴스에 대 한 클래스의 네임 스페이스를 지정 합니다. 기본 네임 스페이스는 **root/cimv2** 입니다.
PowerShell에서 네임 스페이스 목록을 제공 하기 위해 로컬 WMI 서버에서 네임 스페이스 목록을 가져오기 때문에 탭 완성 기능을 사용 하 여 네임 스페이스 목록을 찾아볼 수 있습니다.

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, ResourceUriSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -OperationTimeoutSec

Cmdlet이 CIM 서버의 응답을 기다리는 시간을 지정 합니다. 기본적으로이 매개 변수의 값은 0 이며이는 cmdlet이 서버에 대 한 기본 시간 제한 값을 사용 함을 의미 합니다. **Operationtimeoutsec** 매개 변수가 강력한 연결 다시 시도 시간 제한 3 분 보다 작은 값으로 설정 된 경우, 서버에서 작업을 다시 연결할 수 있기 때문에 **operationtimeoutsec** 매개 변수의 값 보다 마지막으로 네트워크 오류가 복구 되지 않습니다.

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

### -속성

해시 테이블 (이름-값 쌍)을 사용 하 여 CIM 인스턴스의 속성을 지정 합니다.

**CimClass** 매개 변수를 지정 하면 `New-CimInstance` cmdlet이 클라이언트에서 속성 유효성 검사를 수행 하 여 지정 된 속성이 서버의 클래스 선언과 일치 하는지 확인 합니다. **CimClass** 매개 변수를 지정 하지 않으면 서버에서 속성 유효성 검사가 수행 됩니다.

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases: Arguments

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ResourceUri

리소스 클래스 또는 인스턴스의 리소스 URI (uniform resource identifier)를 지정 합니다. URI는 컴퓨터에서 특정 유형의 리소스(예: 디스크 또는 프로세스)를 식별하는 데 사용됩니다.

URI는 접두사와 리소스 경로로 구성됩니다. 다음은 그 예입니다. 

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

기본적으로이 매개 변수를 지정 하지 않으면 DMTF 표준 리소스 URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` 가 사용 되 고 클래스 이름이 추가 됩니다.

**ResourceURI** 는 wsman 프로토콜을 사용 하 여 만든 cim 세션에만 사용할 수 있으며, **ComputerName** 매개 변수를 지정 하는 경우에만 wsman을 사용 하 여 cim 세션을 만들 수 있습니다. **ComputerName** 매개 변수를 지정 하지 않고이 매개 변수를 지정 하거나 dcom 프로토콜을 사용 하 여 만든 CIM 세션을 지정 하는 경우 Dcom 프로토콜이 **ResourceURI** 매개 변수를 지원 하지 않으므로 오류가 발생 합니다.

**ResourceUri** 매개 변수와 **필터** 매개 변수를 모두 지정 하면 **필터** 매개 변수가 무시 됩니다.

```yaml
Type: System.Uri
Parameter Sets: ResourceUriSessionSet, ResourceUriComputerSet
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

### 없음

이 cmdlet은 입력 개체를 허용 하지 않습니다.

## 출력

### System.Object

이 cmdlet은 CIM 인스턴스 정보를 포함 하는 개체를 반환 합니다.

## 참고

## 관련 링크

[Get-CimClass](get-cimclass.md)

[Get-CimInstance](get-ciminstance.md)

[Remove-CimInstance](remove-ciminstance.md)

[Set-CimInstance](Set-CimInstance.md)

