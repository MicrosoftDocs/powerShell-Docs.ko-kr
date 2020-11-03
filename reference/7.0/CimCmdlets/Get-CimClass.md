---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimclass?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimClass
ms.openlocfilehash: 2fd87935e2594a643327d2ae07fad112b1b9386f
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210033"
---
# Get-CimClass

## 개요
특정 네임 스페이스에 있는 CIM 클래스의 목록을 가져옵니다.

## SYNTAX

### ComputerSet (기본값)

```
Get-CimClass [[-ClassName] <String>] [[-Namespace] <String>] [-OperationTimeoutSec <UInt32>]
 [-ComputerName <String[]>] [-MethodName <String>] [-PropertyName <String>]
 [-QualifierName <String>] [<CommonParameters>]
```

### SessionSet

```
Get-CimClass [[-ClassName] <String>] [[-Namespace] <String>] [-OperationTimeoutSec <UInt32>]
 -CimSession <CimSession[]> [-MethodName <String>] [-PropertyName <String>]
 [-QualifierName <String>] [<CommonParameters>]
```

## 설명

`Get-CimClass`Cmdlet은 특정 네임 스페이스에서 CIM 클래스 목록을 검색 합니다. 제공 된 클래스 이름이 없으면 cmdlet은 네임 스페이스의 모든 클래스를 반환 합니다. Cim 인스턴스와 달리 cim 클래스는 검색 된 CIM 세션 또는 컴퓨터 이름을 포함 하지 않습니다.

## 예제

### 예제 1: 모든 클래스 정의 가져오기

이 예제에서는 네임 스페이스 **root/cimv2** 의 모든 클래스 정의를 가져옵니다.

```powershell
Get-CimClass
```

### 예제 2: 특정 이름을 가진 클래스 가져오기

이 예제에서는 이름에 word **디스크** 를 포함 하는 클래스를 가져옵니다.

```powershell
Get-CimClass -ClassName *disk*
```

### 예 3: 특정 메서드 이름으로 클래스 가져오기

이 예제에서는 이름 **Win32** 로 시작 하 고 **Term** 로 시작 하는 메서드 이름이 있는 클래스를 가져옵니다.

```powershell
Get-CimClass -ClassName Win32* -MethodName Term*
```

### 예제 4: 특정 속성 이름을 사용 하 여 클래스 가져오기

이 예제에서는 **Win32** 이름으로 시작 하 고 **Handle** 이라는 속성을 포함 하는 클래스를 가져옵니다.

```powershell
Get-CimClass -ClassName Win32* -PropertyName Handle
```

### 예 5: 특정 한정자 이름으로 클래스 가져오기

이 예제에서는 **Win32** 이름으로 시작 하는 클래스를 가져오고, 이름에 word **디스크** 를 포함 하 고, 지정 된 한정자를 **연결** 합니다.

```powershell
Get-CimClass -ClassName Win32*Disk* -QualifierName Association
```

### 예제 6: 특정 네임 스페이스에서 클래스 정의 가져오기

이 예제에서는 지정 된 네임 스페이스 **root/standardCimv2** 에서 이름에 **Net** 이라는 단어가 포함 된 클래스 정의를 가져옵니다.

```powershell
Get-CimClass -Namespace root/standardCimv2 -ClassName *Net*
```

### 예 7: 원격 서버에서 클래스 정의 가져오기

이 예제에서는 지정 된 원격 서버 **Server01** 및 **Server02** 에서 이름에 word **디스크** 를 포함 하는 클래스 정의를 가져옵니다.

```powershell
Get-CimClass -ClassName *disk* -ComputerName Server01, Server02
```

### 예 8: CIM 세션을 사용 하 여 클래스 가져오기

```powershell
$s = New-CimSession -ComputerName Server01, Server02
Get-CimClass -ClassName *disk* -CimSession $s
```

이 명령 집합은 여러 컴퓨터를 포함 하는 세션을 만들고 `$s` cmdlet을 사용 하 여 변수에 저장 한 `New-CimSession` 다음 cmdlet을 사용 하 여 클래스를 가져옵니다 `Get-CimClass` .

## PARAMETERS

### -CimSession

원격 세션에서 또는 원격 컴퓨터에서 cmdlet을 실행합니다. 컴퓨터 이름 또는 세션 개체 (예: 또는 cmdlet의 출력)를 입력 `New-CimSession` 합니다 `Get-CimSession` . 기본값은 로컬 컴퓨터의 현재 세션입니다.

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

### -ClassName

작업을 수행할 CIM 클래스의 이름을 지정 합니다. PowerShell은 클래스 이름 목록을 제공 하기 위해 로컬 WMI 서버에서 클래스 목록을 가져오기 때문에 탭 완성 기능을 사용 하 여 클래스 목록을 찾아볼 수 있습니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -ComputerName

CIM 작업을 실행 하려는 컴퓨터를 지정 합니다. FQDN (정규화 된 도메인 이름)에 NetBIOS 이름 또는 IP 주소를 지정할 수 있습니다.

이 매개 변수를 지정 하면 cmdlet이 WsMan 프로토콜을 사용 하 여 지정 된 컴퓨터에 대 한 임시 세션을 만듭니다.

이 매개 변수를 지정 하지 않으면 cmdlet은 COM (구성 요소 개체 모델)을 사용 하 여 로컬 컴퓨터에서 작업을 수행 합니다.

동일한 컴퓨터에서 여러 작업을 수행 하는 경우에는 CIM 세션을 사용 하면 성능이 향상 됩니다.

```yaml
Type: System.String[]
Parameter Sets: ComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MethodName

이 이름과 일치 하는 메서드가 있는 클래스를 찾습니다. 이 매개 변수와 함께 와일드 카드 문자를 사용할 수 있습니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Namespace

CIM 작업에 대 한 네임 스페이스를 지정 합니다. 기본 네임 스페이스는 **root/cimv2** 입니다. PowerShell에서 네임 스페이스 목록을 제공 하기 위해 로컬 WMI 서버에서 네임 스페이스 목록을 가져오기 때문에 탭 완성 기능을 사용 하 여 네임 스페이스 목록을 찾아볼 수 있습니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
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

### -PropertyName

이 이름과 일치 하는 속성이 있는 클래스를 찾습니다. 이 매개 변수와 함께 와일드 카드 문자를 사용할 수 있습니다.

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

### -QualifierName

클래스 수준 한정자 이름별로 클래스를 필터링 합니다. 이 매개 변수와 함께 와일드 카드 문자를 사용할 수 있습니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

이 cmdlet은 입력 개체를 허용 하지 않습니다.

## 출력

### CimClass.

이 cmdlet은 CIM 클래스 개체를 반환 합니다.

## 참고

## 관련 링크

[New-CimSession](New-CimSession.md)
