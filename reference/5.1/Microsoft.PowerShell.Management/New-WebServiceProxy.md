---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-webserviceproxy?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WebServiceProxy
ms.openlocfilehash: aea656bc8ad4416673a7abb7d32a58d45dd3cc4f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214601"
---
# New-WebServiceProxy

## 개요
PowerShell에서 웹 서비스를 사용 하 고 관리할 수 있는 웹 서비스 프록시 개체를 만듭니다.

## SYNTAX

### NoCredentials (기본값)

```
New-WebServiceProxy [-Uri] <Uri> [[-Class] <String>] [[-Namespace] <String>] [<CommonParameters>]
```

### 자격 증명

```
New-WebServiceProxy [-Uri] <Uri> [[-Class] <String>] [[-Namespace] <String>] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### UseDefaultCredential

```
New-WebServiceProxy [-Uri] <Uri> [[-Class] <String>] [[-Namespace] <String>] [-UseDefaultCredential]
 [<CommonParameters>]
```

## 설명

`New-WebServiceProxy`Cmdlet을 사용 하면 PowerShell에서 웹 서비스를 사용할 수 있습니다. Cmdlet은 웹 서비스에 연결 하 고 PowerShell에서 웹 서비스 프록시 개체를 만듭니다. 프록시 개체를 사용하여 웹 서비스를 관리할 수 있습니다.

웹 서비스는 네트워크, 특히 인터넷을 통해 데이터를 교환 하는 XML 기반 프로그램입니다. Microsoft .NET Framework는 웹 서비스를 .NET Framework 개체로 나타내는 웹 서비스 프록시 개체를 제공합니다.

## 예제

### 예제 1: 웹 서비스에 대 한 프록시 만들기

이 예제에서는 Windows PowerShell에서 계산기 웹 서비스의 .NET Framework 프록시를 만듭니다.

```powershell
$calc = New-WebServiceProxy -Uri "http://www.dneonline.com/calculator.asmx?wsdl"
```

### 예제 2: 웹 서비스에 대 한 프록시를 만들고 네임 스페이스 및 클래스 지정

이 예제에서는 cmdlet을 사용 하 여 `New-WebServiceProxy` 계산기 웹 서비스의 .NET Framework 프록시를 만듭니다.

```powershell
$URI = "http://www.dneonline.com/calculator.asmx?wsdl"
$calc = New-WebServiceProxy -Uri $URI -Namespace "WSProxy" -Class "Calculator"
```

이 명령은 **uri** 매개 변수를 사용 하 여 uri를 지정 하 고, **네임 스페이스** 및 **클래스** 매개 변수를 사용 하 여 개체의 네임 스페이스 및 클래스를 지정 합니다.

### 예제 3: 웹 서비스 프록시의 표시 메서드

```powershell
$calc | Get-Member -MemberType method
```

```Output
   TypeName: WSProxy.Calculator

Name                      MemberType Definition
----                      ---------- ----------
Abort                     Method     void Abort()
Add                       Method     int Add(int intA, int intB)
AddAsync                  Method     void AddAsync(int intA, int intB), void AddAsync(int intA,
BeginAdd                  Method     System.IAsyncResult BeginAdd(int intA, int intB, System.Asy
BeginDivide               Method     System.IAsyncResult BeginDivide(int intA, int intB, System.
BeginMultiply             Method     System.IAsyncResult BeginMultiply(int intA, int intB, Syste
BeginSubtract             Method     System.IAsyncResult BeginSubtract(int intA, int intB, Syste
CancelAsync               Method     void CancelAsync(System.Object userState)
CreateObjRef              Method     System.Runtime.Remoting.ObjRef CreateObjRef(type requestedT
Discover                  Method     void Discover()
Dispose                   Method     void Dispose(), void IDisposable.Dispose()
Divide                    Method     int Divide(int intA, int intB)
DivideAsync               Method     void DivideAsync(int intA, int intB), void DivideAsync(int
EndAdd                    Method     int EndAdd(System.IAsyncResult asyncResult)
EndDivide                 Method     int EndDivide(System.IAsyncResult asyncResult)
EndMultiply               Method     int EndMultiply(System.IAsyncResult asyncResult)
EndSubtract               Method     int EndSubtract(System.IAsyncResult asyncResult)
Equals                    Method     bool Equals(System.Object obj)
GetHashCode               Method     int GetHashCode()
GetLifetimeService        Method     System.Object GetLifetimeService()
GetType                   Method     type GetType()
InitializeLifetimeService Method     System.Object InitializeLifetimeService()
Multiply                  Method     int Multiply(int intA, int intB)
MultiplyAsync             Method     void MultiplyAsync(int intA, int intB), void MultiplyAsync(
Subtract                  Method     int Subtract(int intA, int intB)
SubtractAsync             Method     void SubtractAsync(int intA, int intB), void SubtractAsync(
ToString                  Method     string ToString()
```

이 예제에서는 cmdlet을 사용 하 여 `Get-Member` 웹 서비스 프록시 개체의 메서드를 변수에 표시 `$calc` 합니다. 다음 예제에서 이러한 메서드를 사용 합니다.

프록시 개체 WebServiceProxy의 **TypeName** 은 이전 예제에서 지정 된 네임 스페이스 및 클래스 이름을 반영 합니다.

### 예제 4: 웹 서비스 프록시 사용

```powershell
PS> $calc.Multiply(6,7)
42
```

이 예에서는 변수에 저장 된 웹 서비스 프록시를 사용 `$calc` 합니다. 이 명령은 프록시의 **곱하기** 메서드를 사용 합니다.

## PARAMETERS

### -클래스

cmdlet이 웹 서비스에 대해 만드는 프록시 클래스의 이름을 지정합니다. 이 매개 변수 값은 **네임 스페이스** 매개 변수와 함께 사용 되어 클래스의 정규화 된 이름을 제공 합니다. 기본값은 URI (Uniform Resource Identifier)에서 생성 됩니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: FileName, FN

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다. 기본값은 현재 사용자입니다. **UseDefaultCredential** 매개 변수 대신 사용할 수 있습니다.

User01 또는 Domain01\User01과 같은 사용자 이름을 입력 하거나, cmdlet에 의해 생성 된 것과 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` . 사용자 이름을 입력 하는 경우이 cmdlet은 암호를 묻는 메시지를 표시 합니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Credential
Aliases: Cred

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Namespace

새 클래스의 네임스페이스를 지정합니다.

이 매개 변수 값은 클래스 매개 변수의 값과 함께 사용 되어 **클래스의** 정규화 된 이름을 생성 합니다. 기본값은 **Microsoft. PowerShell. NewWebserviceProxy입니다. AutogeneratedTypes** 와 URI에서 생성 되는 형식을 더한 값입니다.

동일한 이름을 가진 여러 웹 서비스에 액세스할 수 있도록 **Namespace** 매개 변수의 값을 설정할 수 있습니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: NS

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Uri

웹 서비스의 URI를 지정합니다. 서비스 설명이 포함 된 파일의 경로 및 파일 이름 또는 URI를 입력 합니다.

URI는 `.asmx` 서비스 설명을 반환 하는 페이지 또는 페이지를 반환 해야 합니다. ASP.NET를 사용 하 여 만든 웹 서비스에 대 한 서비스 설명을 반환 하려면 "?를 추가 합니다. WSDL "에서 웹 서비스의 URL (예:)을 사용할 수 `http://www.contoso.com/MyWebService.asmx?WSDL` 있습니다.

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: WL, WSDL, Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseDefaultCredential

이 cmdlet이 기본 자격 증명을 사용 함을 나타냅니다. 이 cmdlet은 결과 프록시 개체의 **UseDefaultCredential** 속성을 True로 설정 합니다. **Credential** 매개 변수를 사용 하는 대신 사용할 수 있습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseDefaultCredential
Aliases: UDC

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

이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### 웹 서비스 프록시 개체입니다.

이 cmdlet은 웹 서비스 프록시 개체를 반환 합니다. 개체의 네임스페이스 및 클래스는 명령의 매개 변수에 따라 결정됩니다. 기본값은 입력 URI에서 생성 됩니다.

## 참고

`New-WebServiceProxy`**시스템 .net. WebClient** 클래스를 사용 하 여 지정 된 웹 서비스를 로드 합니다.

## 관련 링크

[New-Service](New-Service.md)
