---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 정적 클래스 및 메서드 사용
ms.assetid: 418ad766-afa6-4b8c-9a44-471889af7fd9
ms.openlocfilehash: 0f2b02c3a40365ad0335118b057a4e548c9f6535
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403212"
---
# <a name="using-static-classes-and-methods"></a>정적 클래스 및 메서드 사용
일부 .NET Framework 클래스는 **New-Object**를 사용하여 만들 수 없습니다. 예를 들어 **New-Object**를 사용하여 **System.Environment** 또는 **System.Math** 개체를 만들려고 하면 다음과 같은 오류 메시지가 나타납니다.

```
PS> New-Object System.Environment
New-Object : Constructor not found. Cannot find an appropriate constructor for
type System.Environment.
At line:1 char:11
+ New-Object  <<<< System.Environment

PS> New-Object System.Math
New-Object : Constructor not found. Cannot find an appropriate constructor for
type System.Math.
At line:1 char:11
+ New-Object  <<<< System.Math
```

이러한 오류는 .NET Framework 클래스에서 새 개체를 만들 수 없기 때문에 발생합니다. .NET Framework 클래스는 상태가 바뀌지 않는 메서드와 속성의 참조 라이브러리로, 직접 만들지 않아도 사용할 수 있습니다. 만들거나, 제거하거나, 변경할 수 없으므로 이러한 클래스와 메서드를 *정적 클래스*라고 합니다. 이해를 돕기 위해 이 설명서에서는 정적 클래스를 사용하는 예제를 제공합니다.

### <a name="getting-environment-data-with-systemenvironment"></a>System.Environment를 사용하여 환경 데이터 보기
일반적으로 Windows PowerShell에서 개체를 사용할 때 수행하는 첫 단계는 Get-Member를 사용하여 해당 개체 안에 들어 있는 멤버를 확인하는 것입니다. 정적 클래스를 사용할 경우 실제 클래스가 개체가 아니므로 약간 다른 방식으로 이 작업을 수행합니다.

#### <a name="referring-to-the-static-systemenvironment-class"></a>정적 System.Environment 클래스 참조
클래스 이름을 대괄호로 묶으면 정적 클래스를 참조할 수 있습니다. 예를 들어 대괄호 안에 이름을 입력하여 **System.Environment**를 참조할 수 있습니다. 이렇게 하면 다음과 같은 일반적인 유형 정보가 표시됩니다.

```
PS> [System.Environment]

IsPublic IsSerial Name                                     BaseType
-------- -------- ----                                     --------
True     False    Environment                              System.Object
```

> [!NOTE]
> 앞에서 언급한 것처럼 Windows PowerShell에서 **New Object** 를 사용하면 자동으로 유형 이름 앞에 '**System.**'이 추가됩니다. 대괄호로 묶은 유형 이름을 사용하는 경우에도 마찬가지이므로 **\[System.Environment]** 를 **\[Environment]** 로 지정할 수 있습니다.

**System.Environment** 클래스에는 현재 프로세스(Windows PowerShell에서 작업하는 경우 powershell.exe임)의 작업 환경에 대한 일반적인 정보가 포함되어 있습니다.

**\[System.Environment] | Get-Member**를 입력하여 이 클래스에 대한 세부 정보를 표시하면 다음과 같이 개체 유형이 **System.Environment**가 아니라 **System.RuntimeType**으로 표시됩니다.

```
PS> [System.Environment] | Get-Member

   TypeName: System.RuntimeType
```

Get-Member를 사용하여 정적 멤버를 보려면 다음과 같이 **Static** 매개 변수를 지정합니다.

```
PS> [System.Environment] | Get-Member -Static

   TypeName: System.Environment

Name                       MemberType Definition
----                       ---------- ----------
Equals                     Method     static System.Boolean Equals(Object ob...
Exit                       Method     static System.Void Exit(Int32 exitCode)
...
CommandLine                Property   static System.String CommandLine {get;}
CurrentDirectory           Property   static System.String CurrentDirectory ...
ExitCode                   Property   static System.Int32 ExitCode {get;set;}
HasShutdownStarted         Property   static System.Boolean HasShutdownStart...
MachineName                Property   static System.String MachineName {get;}
NewLine                    Property   static System.String NewLine {get;}
OSVersion                  Property   static System.OperatingSystem OSVersio...
ProcessorCount             Property   static System.Int32 ProcessorCount {get;}
StackTrace                 Property   static System.String StackTrace {get;}
SystemDirectory            Property   static System.String SystemDirectory {...
TickCount                  Property   static System.Int32 TickCount {get;}
UserDomainName             Property   static System.String UserDomainName {g...
UserInteractive            Property   static System.Boolean UserInteractive ...
UserName                   Property   static System.String UserName {get;}
Version                    Property   static System.Version Version {get;}
WorkingSet                 Property   static System.Int64 WorkingSet {get;}
TickCount                               ExitCode
```

이제 System.Environment를 사용하여 표시할 속성을 선택할 수 있습니다.

#### <a name="displaying-static-properties-of-systemenvironment"></a>System.Environment의 정적 속성 표시

System.Environment의 속성도 정적이므로 일반적인 속성과 다른 방식으로 지정해야 합니다. Windows PowerShell에서는 **::** 을 사용하여 작업할 정적 메서드나 속성을 나타냅니다. Windows PowerShell을 시작하는 데 사용된 명령을 보려면 다음과 같이 입력하여 **CommandLine** 속성을 표시합니다.

```
PS> [System.Environment]::Commandline
"C:\Program Files\Windows PowerShell\v1.0\powershell.exe"
```

운영 체제 버전을 확인하려면 다음과 같이 입력하여 OSVersion 속성을 표시합니다.

```
PS> [System.Environment]::OSVersion

           Platform ServicePack         Version             VersionString
           -------- -----------         -------             -------------
            Win32NT Service Pack 2      5.1.2600.131072     Microsoft Windows...
```

다음과 같이 **HasShutdownStarted** 속성을 표시하면 컴퓨터가 종료 중인지 여부를 확인할 수 있습니다.

```
PS> [System.Environment]::HasShutdownStarted
False
```

### <a name="doing-math-with-systemmath"></a>System.Math를 사용하여 산술 연산 수행

System.Math 정적 클래스는 일부 산술 연산을 수행하는 데 유용합니다. **System.Math**의 중요한 멤버는 대부분 **Get-Member**를 사용하여 표시할 수 있는 메서드입니다.

> [!NOTE]
> System.Math에는 동일한 이름을 가진 메서드가 여러 개 있지만 유형이 서로 다릅니다.

다음 명령을 입력하면 **System.Math** 클래스의 메서드를 표시할 수 있습니다.

```
PS> [System.Math] | Get-Member -Static -MemberType Methods

   TypeName: System.Math

Name            MemberType Definition
----            ---------- ----------
Abs             Method     static System.Single Abs(Single value), static Sy...
Acos            Method     static System.Double Acos(Double d)
Asin            Method     static System.Double Asin(Double d)
Atan            Method     static System.Double Atan(Double d)
Atan2           Method     static System.Double Atan2(Double y, Double x)
BigMul          Method     static System.Int64 BigMul(Int32 a, Int32 b)
Ceiling         Method     static System.Double Ceiling(Double a), static Sy...
Cos             Method     static System.Double Cos(Double d)
Cosh            Method     static System.Double Cosh(Double value)
DivRem          Method     static System.Int32 DivRem(Int32 a, Int32 b, Int3...
Equals          Method     static System.Boolean Equals(Object objA, Object ...
Exp             Method     static System.Double Exp(Double d)
Floor           Method     static System.Double Floor(Double d), static Syst...
IEEERemainder   Method     static System.Double IEEERemainder(Double x, Doub...
Log             Method     static System.Double Log(Double d), static System...
Log10           Method     static System.Double Log10(Double d)
Max             Method     static System.SByte Max(SByte val1, SByte val2), ...
Min             Method     static System.SByte Min(SByte val1, SByte val2), ...
Pow             Method     static System.Double Pow(Double x, Double y)
ReferenceEquals Method     static System.Boolean ReferenceEquals(Object objA...
Round           Method     static System.Double Round(Double a), static Syst...
Sign            Method     static System.Int32 Sign(SByte value), static Sys...
Sin             Method     static System.Double Sin(Double a)
Sinh            Method     static System.Double Sinh(Double value)
Sqrt            Method     static System.Double Sqrt(Double d)
Tan             Method     static System.Double Tan(Double a)
Tanh            Method     static System.Double Tanh(Double value)
Truncate        Method     static System.Decimal Truncate(Decimal d), static...
```

여기에는 여러 가지 산술 메서드가 포함되어 있습니다. 다음은 일반적인 메서드의 작동 방법을 보여 주는 명령 목록입니다.

```
PS> [System.Math]::Sqrt(9)
3
PS> [System.Math]::Pow(2,3)
8
PS> [System.Math]::Floor(3.3)
3
PS> [System.Math]::Floor(-3.3)
-4
PS> [System.Math]::Ceiling(3.3)
4
PS> [System.Math]::Ceiling(-3.3)
-3
PS> [System.Math]::Max(2,7)
7
PS> [System.Math]::Min(2,7)
2
PS> [System.Math]::Truncate(9.3)
9
PS> [System.Math]::Truncate(-9.3)
-9
```