---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/21/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-ciminstance?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimInstance
ms.openlocfilehash: 468b0e62925774fb838263b9bd9aea6a74151b5f
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93218106"
---
# Get-CimInstance

## 개요
CIM 서버에서 클래스의 CIM 인스턴스를 가져옵니다.

## SYNTAX

### ClassNameComputerSet (기본값)

```
Get-CimInstance [-ClassName] <String> [-ComputerName <String[]>] [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-QueryDialect <String>] [-Shallow] [-Filter <String>]
 [-Property <String[]>] [<CommonParameters>]
```

### ResourceUriSessionSet

```
Get-CimInstance -CimSession <CimSession[]> -ResourceUri <Uri> [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-Shallow] [-Filter <String>] [-Property <String[]>]
 [<CommonParameters>]
```

### QuerySessionSet

```
Get-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] -Query <String> [-QueryDialect <String>] [-Shallow]
 [<CommonParameters>]
```

### ClassNameSessionSet

```
Get-CimInstance -CimSession <CimSession[]> [-ClassName] <String> [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-QueryDialect <String>] [-Shallow] [-Filter <String>]
 [-Property <String[]>] [<CommonParameters>]
```

### CimInstanceSessionSet

```
Get-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [<CommonParameters>]
```

### CimInstanceComputerSet

```
Get-CimInstance [-ResourceUri <Uri>] [-ComputerName <String[]>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [<CommonParameters>]
```

### ResourceUriComputerSet

```
Get-CimInstance -ResourceUri <Uri> [-ComputerName <String[]>] [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-Shallow] [-Filter <String>] [-Property <String[]>]
 [<CommonParameters>]
```

### QueryComputerSet

```
Get-CimInstance [-ResourceUri <Uri>] [-ComputerName <String[]>] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] -Query <String> [-QueryDialect <String>] [-Shallow]
 [<CommonParameters>]
```

## 설명

`Get-CimInstance`Cmdlet은 cim 서버에서 클래스의 cim 인스턴스를 가져옵니다. 이 cmdlet에 대 한 쿼리 또는 클래스 이름을 지정할 수 있습니다. 이 cmdlet은 cim 서버에 있는 CIM 인스턴스의 스냅숏을 나타내는 CIM 인스턴스 개체를 하나 이상 반환 합니다.

**InputObject** 매개 변수를 지정 하지 않으면 cmdlet은 다음 방법 중 하나로 작동 합니다.

- **ComputerName** 매개 변수와 **CimSession** 매개 변수를 모두 지정 하지 않으면이 Cmdlet은 COM (구성 요소 개체 모델) 세션을 사용 하 여 WMI (로컬 WMI(Windows Management Instrumentation))에서 작동 합니다.
- **Computername** 매개 변수 또는 **CimSession** 매개 변수를 지정 하는 경우이 cmdlet은 **computername** 매개 변수 또는 **CimSession** 매개 변수로 지정 된 CIM 서버에 대해 작동 합니다.

**InputObject** 매개 변수를 지정 하는 경우 cmdlet은 다음 방법 중 하나로 작동 합니다.

- **ComputerName** 매개 변수와 **CimSession** 매개 변수를 모두 지정 하지 않으면이 cmdlet은 입력 개체의 컴퓨터 이름과 CIM 세션을 사용 합니다.
- **ComputerName** 매개 변수 또는 **CimSession** 매개 변수 중 하나가 지정 된 경우이 cmdlet은 CimSession 매개 변수 값 또는 **ComputerName** 매개 변수 값을 사용 합니다.

## 예제

### 예제 1: 지정 된 클래스의 CIM 인스턴스 가져오기

이 예제에서는 **Win32_Process** 이라는 클래스의 CIM 인스턴스를 검색 합니다.

```powershell
Get-CimInstance -ClassName Win32_Process
```

### 예제 2: WMI 서버에서 네임 스페이스 목록 가져오기

이 예제에서는 WMI 서버의 **루트** 네임 스페이스에서 네임 스페이스 목록을 검색 합니다.

```powershell
Get-CimInstance -Namespace root -ClassName __Namespace
```

### 예제 3: 쿼리를 사용 하 여 필터링 된 클래스의 인스턴스 가져오기

이 예제에서는 **쿼리** 매개 변수로 지정 된 쿼리를 사용 하 여 **Win32_Process** 이라는 클래스의 **P** 문자로 시작 하는 모든 CIM 인스턴스를 검색 합니다.

```powershell
Get-CimInstance -Query "SELECT * from Win32_Process WHERE name LIKE 'P%'"
```

### 예제 4: 클래스 이름 및 필터 식을 사용 하 여 필터링 된 클래스의 인스턴스 가져오기

이 예제에서는 Filter 매개 변수를 사용 하 여 **Win32_Process** 이라는 클래스의 **P** 문자로 시작 하는 모든 CIM 인스턴스를 검색 합니다.

```powershell
Get-CimInstance -ClassName Win32_Process -Filter "Name like 'P%'"
```

### 예 5: 키 속성만 채워진 CIM 인스턴스 가져오기

이 예제에서는 key 속성을 사용 하 여 **Win32_Process** 라는 클래스에 대해 메모리에 새 CIM 인스턴스를 만들고 `@{ "Handle"=0 }` 라는 변수에 저장 `$x` 합니다. 변수는 `Get-CimInstance` 특정 인스턴스를 가져오기 위해 cmdlet에 CIM 인스턴스로 전달 됩니다.

```powershell
$x = New-CimInstance -ClassName Win32_Process -Namespace root\cimv2 -Property @{ "Handle"=0 } -Key Handle -ClientOnly
Get-CimInstance -CimInstance $x
```

### 예제 6: CIM 인스턴스 검색 및 다시 사용

이 예제에서는 **Win32_Process** 된 클래스의 CIM 인스턴스를 가져와 및 변수에 저장 `$x` `$y` 합니다. `$x`그런 다음 변수는 **Name** 및 **KernelModeTime** 속성만 포함 된 테이블에서 **AutoSize** 로 설정 된 테이블로 형식이 지정 됩니다.

```powershell
$x,$y = Get-CimInstance -ClassName Win32_Process
$x | Format-Table -Property Name,KernelModeTime -AutoSize
```

```Output
Name                 KernelModeTime
----                 --------------
System Idle Process 157238797968750
```

### 예 7: 원격 컴퓨터에서 CIM 인스턴스 가져오기

이 예제에서는 **Server01** 및 **Server02** 라는 원격 컴퓨터에서 **Win32_ComputerSystem** 이라는 클래스의 CIM 인스턴스를 검색 합니다.

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName Server01,Server02
```

### 예 8: 모든 속성 대신 키 속성만 가져오기

이 예제에서는 개체 및 네트워크 트래픽의 크기를 줄이는 키 속성만 검색 합니다.

```powershell
$x = Get-CimInstance -Class Win32_Process -KeyOnly
$x | Invoke-CimMethod -MethodName GetOwner
```

### 예 9: 모든 속성 대신 속성의 하위 집합만 가져오기

이 예제에서는 개체 및 네트워크 트래픽의 크기를 줄이는 속성의 하위 집합만 검색 합니다.

```powershell
Get-CimInstance -Class Win32_Process -Property Name,KernelModeTime
$x = Get-CimInstance -Class Win32_Process -Property Name,KernelModeTime
$x | Invoke-CimMethod -MethodName GetOwner
```

**Property** 매개 변수를 사용 하 여 검색 된 인스턴스는 다른 CIM 작업 (예: 또는)을 수행 하는 데 사용할 수 있습니다 `Set-CimInstance` `Invoke-CimMethod` .

### 예 10: CIM 세션을 사용 하 여 CIM 인스턴스 가져오기

이 예에서는 cmdlet을 사용 하 여 **Server01** 및 **Server02** 라는 컴퓨터에서 CIM 세션을 만들고 `New-CimSession` 이라는 변수에 세션 정보를 저장 `$s` 합니다. 그런 다음 CimSession 매개 변수를 사용 하 여 변수의 내용을에 전달 하 여 `Get-CimInstance` **Win32_ComputerSystem** 라는 클래스의 CIM 인스턴스를 가져옵니다. **CimSession**

```powershell
$s = New-CimSession -ComputerName Server01,Server02
Get-CimInstance -ClassName Win32_ComputerSystem -CimSession $s
```

## PARAMETERS

### -CimSession

이 cmdlet에 사용할 CIM 세션을 지정 합니다. Cim 세션을 포함 하는 변수 또는 CIM 세션을 만들거나 가져오는 명령 (예: 또는 cmdlet)을 입력 `New-CimSession` 합니다 `Get-CimSession` . 자세한 내용은 [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)를 참조 하세요.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: ResourceUriSessionSet, QuerySessionSet, ClassNameSessionSet, CimInstanceSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ClassName

CIM 인스턴스를 검색할 CIM 클래스의 이름을 지정 합니다. PowerShell은 클래스 이름 목록을 제공 하기 위해 로컬 WMI 서버에서 클래스 목록을 가져오기 때문에 탭 완성 기능을 사용 하 여 클래스 목록을 찾아볼 수 있습니다.

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

### -ComputerName

CIM 작업을 실행 하려는 컴퓨터를 지정 합니다. FQDN (정규화 된 도메인 이름), NetBIOS 이름 또는 IP 주소를 지정할 수 있습니다. 이 매개 변수를 지정 하지 않으면 cmdlet은 COM (구성 요소 개체 모델)을 사용 하 여 로컬 컴퓨터에서 작업을 수행 합니다.

이 매개 변수를 지정 하면 cmdlet이 WsMan 프로토콜을 사용 하 여 지정 된 컴퓨터에 대 한 임시 세션을 만듭니다.

동일한 컴퓨터에서 여러 작업을 수행 하는 경우 더 나은 성능을 위해 CIM 세션을 사용 하 여 연결 합니다.

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, CimInstanceComputerSet, ResourceUriComputerSet, QueryComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Filter

필터로 사용할 where 절을 지정 합니다. **WQL** 또는 **CQL** 쿼리 언어에서 절을 지정 합니다. `WHERE`매개 변수 값에 키워드를 포함 하지 마십시오.

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, ClassNameSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InputObject

입력으로 사용할 CIM 인스턴스 개체를 지정 합니다.

이미 CIM 인스턴스 개체로 작업 하는 경우이 매개 변수를 사용 하 여 cim 서버에서 최신 스냅숏을 가져오기 위해 CIM 인스턴스 개체를 전달할 수 있습니다. CIM 인스턴스 개체를 입력으로 전달 하는 경우 `Get-CimInstance` 열거 또는 쿼리 작업 대신 cim 가져오기 작업을 사용 하 여 서버에서 개체를 반환 합니다. CIM 가져오기 작업을 사용 하면 모든 인스턴스를 검색 한 다음 필터링 하는 것 보다 효율적입니다.

CIM 클래스가 get 작업을 구현 하지 않는 경우 **InputObject** 매개 변수를 지정 하면 오류가 반환 됩니다.

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

### -KeyOnly

키 속성이 채워진 개체만 반환 됨을 나타냅니다. **Keyonly** 매개 변수를 지정 하면 네트워크를 통해 전송 되는 데이터의 양이 줄어듭니다.

**Keyonly** 매개 변수를 사용 하 여 또는 cmdlet과 같은 다른 작업에 사용할 수 있는 개체의 작은 부분만 반환 합니다 `Set-CimInstance` `Get-CimAssociatedInstance` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, ClassNameSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Namespace

CIM 클래스의 네임 스페이스를 지정 합니다.

기본 네임 스페이스는 **root/cimv2** 입니다. PowerShell에서 네임 스페이스 목록을 제공 하기 위해 로컬 WMI 서버에서 네임 스페이스 목록을 가져오기 때문에 탭 완성 기능을 사용 하 여 네임 스페이스 목록을 찾아볼 수 있습니다.

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, QuerySessionSet, ClassNameSessionSet, ResourceUriComputerSet, QueryComputerSet
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

### -속성

검색할 인스턴스 속성의 집합을 지정 합니다. 반환 되는 개체의 크기를 메모리 또는 네트워크를 통해 줄여야 할 때이 매개 변수를 사용 합니다. 반환 된 개체에는 **속성** 매개 변수를 사용 하 여 목록에 나열 되지 않은 경우에도 키 속성도 포함 되어 있습니다. 클래스의 다른 속성이 있지만 채워지지 않습니다.

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, ClassNameSessionSet, ResourceUriComputerSet
Aliases: SelectProperties

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Query

CIM 서버에서 실행할 쿼리를 지정 합니다. 지정 된 값에 큰따옴표 `"` , 작은따옴표 또는 백슬래시가 포함 된 경우 `'` `\` 백슬래시 문자를 접두사로 사용 하 여 해당 문자를 이스케이프 해야 합니다. 지정 된 값이 WQL **LIKE** 연산자를 사용 하는 경우 대괄호 ( `[]` 백분율 `%` , 밑줄 `_` 또는 여는 대괄호)로 묶어 다음 문자를 이스케이프 해야 `[` 합니다.

메타 데이터 쿼리를 사용 하 여 클래스 또는 이벤트 쿼리 목록을 검색할 수 없습니다. 클래스 목록을 검색 하려면 cmdlet을 사용 `Get-CimClass` 합니다. 이벤트 쿼리를 검색 하려면 cmdlet을 사용 `Register-CimIndicationEvent` 합니다.

**Querydialect** 매개 변수를 사용 하 여 쿼리 언어를 지정할 수 있습니다.

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -QueryDialect

쿼리 매개 변수에 사용 되는 쿼리 언어를 지정 합니다. 이 매개 변수에 허용 되는 값은 **WQL** 또는 **CQL** 입니다. 기본값은 **WQL** 입니다.

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, QuerySessionSet, ClassNameSessionSet, QueryComputerSet
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

**ResourceURI** 는 wsman 프로토콜을 사용 하 여 만든 cim 세션에만 사용할 수 있으며, **ComputerName** 매개 변수를 지정 하는 경우에만 wsman을 사용 하 여 cim 세션을 만들 수 있습니다. **ComputerName** 매개 변수를 지정 하지 않고이 매개 변수를 지정 하거나 dcom 프로토콜을 사용 하 여 만든 CIM 세션을 지정 하는 경우 Dcom 프로토콜이 **ResourceURI** 매개 변수를 지원 하지 않으므로 오류가 발생 합니다.

**ResourceUri** 매개 변수와 **필터** 매개 변수를 모두 지정 하면 **필터** 매개 변수가 무시 됩니다.

```yaml
Type: System.Uri
Parameter Sets: ResourceUriSessionSet, ResourceUriComputerSet, QuerySessionSet, QueryComputerSet, CimInstanceSessionSet, CimInstanceComputerSet
Aliases:

Required: True (ResourceUriSessionSet, ResourceUriComputerSet), False (QuerySessionSet, QueryComputerSet, CimInstanceSessionSet, CimInstanceComputerSet)
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -단순

자식 클래스의 인스턴스를 포함 하지 않고 클래스 인스턴스가 반환 됨을 나타냅니다. 기본적으로 cmdlet은 클래스 및 해당 자식 클래스의 인스턴스를 반환 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, QuerySessionSet, ClassNameSessionSet, ResourceUriComputerSet, QueryComputerSet
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

### Ciminstance 개체로.

이 cmdlet은 InputObject 매개 변수를 사용 하 여 지정 된 입력 개체를 허용 합니다.

## 출력

### Ciminstance 개체로.

이 cmdlet은 cim 서버에서 CIM 인스턴스의 스냅숏을 나타내는 CIM 인스턴스 개체를 하나 이상 반환 합니다.

## 참고

## 관련 링크

[Format-Table](../microsoft.powershell.utility/format-table.md)

[Get-CimAssociatedInstance](Get-CimAssociatedInstance.md)

[Get-CimClass](Get-CimClass.md)

[Invoke-CimMethod](invoke-cimmethod.md)

[New-CimInstance](New-CimInstance.md)

[Register-CimIndicationEvent](Register-CimIndicationEvent.md)

[Remove-CimInstance](remove-ciminstance.md)

[Set-CimInstance](Set-CimInstance.md)
