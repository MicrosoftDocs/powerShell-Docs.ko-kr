---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimassociatedinstance?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimAssociatedInstance
ms.openlocfilehash: 10790507b24bc4212db062589cf76d5260554b30
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93218098"
---
# Get-CimAssociatedInstance

## 개요
연결에 의해 특정 CIM 인스턴스에 연결 된 CIM 인스턴스를 검색 합니다.

## SYNTAX

### ComputerSet (기본값)

```
Get-CimAssociatedInstance [[-Association] <String>] [-ResultClassName <String>]
 [-InputObject] <CimInstance> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-ResourceUri <Uri>] [-ComputerName <String[]>] [-KeyOnly] [<CommonParameters>]
```

### SessionSet

```
Get-CimAssociatedInstance [[-Association] <String>] [-ResultClassName <String>]
 [-InputObject] <CimInstance> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-ResourceUri <Uri>] -CimSession <CimSession[]> [-KeyOnly] [<CommonParameters>]
```

## 설명

`Get-CimAssociatedInstance`Cmdlet은 연결을 통해 원본 인스턴스 라고 하는 특정 cim 인스턴스에 연결 된 cim 인스턴스를 검색 합니다.

연결에서 각 CIM 인스턴스는 명명 된 역할을 가지 며 동일한 CIM 인스턴스는 다른 역할의 연결에 참여할 수 있습니다.

InputObject 매개 변수를 지정 하지 않으면 cmdlet은 다음 방법 중 하나로 작동 합니다.

- **ComputerName** 매개 변수와 **CimSession** 매개 변수를 모두 지정 하지 않으면이 Cmdlet은 COM (구성 요소 개체 모델) 세션을 사용 하 여 WMI (로컬 WMI(Windows Management Instrumentation))에서 작동 합니다.
- **Computername** 매개 변수 또는 **CimSession** 매개 변수를 지정 하는 경우이 cmdlet은 **computername** 매개 변수 또는 **CimSession** 매개 변수로 지정 된 CIM 서버에 대해 작동 합니다.

## 예제

### 예 1: 특정 인스턴스의 연결 된 모든 인스턴스 가져오기

```powershell
$disk = Get-CimInstance -ClassName Win32_LogicalDisk -KeyOnly
Get-CimAssociatedInstance -InputObject $disk[1]
```

이 명령 집합은 Win32_LogicalDisk 된 클래스의 인스턴스를 검색 하 고 `$disk` cmdlet을 사용 하 여 라는 변수에 정보를 저장 합니다 `Get-CimInstance` . 그러면 변수의 첫 번째 논리 디스크 인스턴스가 cmdlet에 대 한 입력 개체로 사용 되어 지정 된 `Get-CimAssociatedInstance` cim 인스턴스의 모든 연결 된 cim 인스턴스를 가져옵니다.

### 예제 2: 특정 형식의 모든 연결 된 인스턴스 가져오기

```powershell
$disk = Get-CimInstance -ClassName Win32_LogicalDisk -KeyOnly
Get-CimAssociatedInstance -InputObject $disk[1] -ResultClass Win32_DiskPartition
```

이 명령 집합은 **Win32_LogicalDisk** 클래스의 모든 인스턴스를 검색 하 여 라는 변수에 저장 `$disk` 합니다. 그런 다음 변수의 첫 번째 논리 디스크 인스턴스는 `Get-CimAssociatedInstance` **Win32_DiskPartition** 지정 된 연결 클래스를 통해 연결 된 모든 연결 된 인스턴스를 가져오기 위해 cmdlet에 대 한 입력 개체로 사용 됩니다.

### 예 3: 특정 클래스의 한정자를 통해 연결 된 모든 인스턴스 가져오기

```powershell
$s = Get-CimInstance -Query "Select * from Win32_Service where name like 'Winmgmt'"
Get-CimClass -ClassName *Service* -Qualifier "Association"
$c.CimClasName
```

```Output
Win32_LoadOrderGroupServiceDependencies
Win32_DependentService
Win32_SystemServices
Win32_LoadOrderGroupServiceMembers
Win32_ServiceSpecificationService
```

```powershell
Get-CimAssociatedInstance -InputObject $s -Association Win32_DependentService
```

이 명령 집합은 WMI 서비스에 종속 된 서비스를 검색 하 여 라는 변수에 저장 `$s` 합니다. **Win32_DependentService** 의 연결 클래스 이름은 Cmdlet으로 연결을 지정 하 여 cmdlet을 사용 하 여 검색 된 `Get-CimClass` 다음 cmdlet에 $s를 전달 하 여 **Association** `Get-CimAssociatedInstance` 검색 된 연결 클래스의 연결 된 모든 인스턴스를 가져옵니다.

## PARAMETERS

### -연결

연결 클래스의 이름을 지정 합니다. 이 매개 변수를 지정 하지 않으면 cmdlet은 모든 형식의 기존 연결 개체를 모두 반환 합니다.

예를 들어, 클래스 A가 AB1 및 AB2의 두 연결을 통해 B 클래스와 연결 된 경우이 매개 변수를 사용 하 여 연결 형식 (AB1 또는 AB2)을 지정할 수 있습니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -CimSession

지정 된 CIM 세션을 사용 하 여 명령을 실행 합니다. CIM 세션을 포함 하는 변수 또는 CIM 세션을 만들거나 가져오는 명령 (예: 또는)을 입력 `New-CimSession` `Get-CimSession` 합니다. 자세한 내용은 [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)를 참조 하세요.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: SessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ComputerName

CIM 작업을 실행 하려는 컴퓨터의 이름을 지정 합니다. FQDN (정규화 된 도메인 이름) 또는 NetBIOS 이름을 지정할 수 있습니다.

이 매개 변수를 지정 하면 cmdlet이 WsMan 프로토콜을 사용 하 여 지정 된 컴퓨터에 대 한 임시 세션을 만듭니다.

이 매개 변수를 지정 하지 않으면 cmdlet은 COM (구성 요소 개체 모델)을 사용 하 여 로컬 컴퓨터에서 작업을 수행 합니다.

동일한 컴퓨터에서 여러 작업을 수행 하는 경우 CIM 세션을 사용 하 여 연결 하면 성능이 향상 됩니다.

```yaml
Type: System.String[]
Parameter Sets: ComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

이 cmdlet에 대한 입력을 지정합니다. 이 매개 변수를 사용하거나 이 cmdlet에 입력을 파이프할 수 있습니다.

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: (All)
Aliases: CimInstance

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -KeyOnly

키 속성만 채워진 개체를 반환 합니다. 이렇게 하면 네트워크를 통해 전송 되는 데이터의 양이 줄어듭니다.

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

### -Namespace

CIM 작업에 대 한 네임 스페이스를 지정 합니다. 기본 네임 스페이스는 root/cimv2입니다.

> [!NOTE]
> PowerShell에서 네임 스페이스 목록을 제공 하기 위해 로컬 WMI 서버에서 네임 스페이스 목록을 가져오기 때문에 탭 완성 기능을 사용 하 여 네임 스페이스 목록을 찾아볼 수 있습니다.

```yaml
Type: System.String
Parameter Sets: (All)
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
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ResourceUri

리소스 클래스 또는 인스턴스의 리소스 URI (uniform resource identifier)를 지정 합니다. URI는 컴퓨터에서 특정 유형의 리소스(예: 디스크 또는 프로세스)를 식별하는 데 사용됩니다.

URI는 접두사와 리소스 경로로 구성됩니다. 다음은 그 예입니다. 

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

기본적으로이 매개 변수를 지정 하지 않으면 DMTF 표준 리소스 URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` 가 사용 되 고 클래스 이름이 추가 됩니다.

**ResourceURI** 는 wsman 프로토콜을 사용 하 여 만든 cim 세션에만 사용할 수 있으며, **ComputerName** 매개 변수를 지정 하는 경우에만 wsman을 사용 하 여 cim 세션을 만들 수 있습니다. **ComputerName** 매개 변수를 지정 하지 않고이 매개 변수를 지정 하거나 dcom 프로토콜을 사용 하 여 만든 CIM 세션을 지정 하는 경우 Dcom 프로토콜이 **ResourceURI** 매개 변수를 지원 하지 않기 때문에 오류가 발생 합니다.

**ResourceUri** 매개 변수와 **필터** 매개 변수를 모두 지정 하면 **필터** 매개 변수가 무시 됩니다.

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ResultClassName

연결 된 인스턴스의 클래스 이름을 지정 합니다. CIM 인스턴스는 하나 이상의 CIM 인스턴스와 연결 될 수 있습니다. 결과 클래스 이름을 지정 하지 않으면 연결 된 모든 CIM 인스턴스가 반환 됩니다.

기본적으로이 매개 변수의 값은 null 이며 연결 된 모든 CIM 인스턴스가 반환 됩니다.

특정 클래스 이름과 일치 하도록 연결 결과를 필터링 할 수 있습니다. 서버에서 필터링이 수행 됩니다. 이 매개 변수를 지정 하지 않으면 `Get-CIMAssociatedInstance` 기존 연결을 모두 반환 합니다. 예를 들어 클래스 A가 B, C 및 D 클래스와 연결 된 경우이 매개 변수를 사용 하 여 출력을 특정 형식 (B, C 또는 D)으로 제한할 수 있습니다.

```yaml
Type: System.String
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

### 없음

이 cmdlet은 입력 개체를 허용 하지 않습니다.

## 출력

### System.Object

이 cmdlet은 개체를 반환 합니다.

## 참고

## 관련 링크

[Get-CimClass](get-cimclass.md)

[Get-CimInstance](get-ciminstance.md)
