---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/add-type?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Type
ms.openlocfilehash: cbf211f4ae5262255a74fa7fb97d2493202d71fa
ms.sourcegitcommit: e0f9fe6335be1e0f94bedaa0e8baec2acaeaa076
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/10/2020
ms.locfileid: "93219897"
---
# Add-Type

## 개요
PowerShell 세션에 Microsoft .NET Core 클래스를 추가 합니다.

## SYNTAX

### FromSource (기본값)

```
Add-Type [-TypeDefinition] <String> [-Language <Language>] [-ReferencedAssemblies <String[]>]
 [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings]
 [-CompilerOptions <String[]>] [<CommonParameters>]
```

### FromMember

```
Add-Type [-Name] <String> [-MemberDefinition] <String[]> [-Namespace <String>]
 [-UsingNamespace <String[]>] [-Language <Language>] [-ReferencedAssemblies <String[]>]
 [-OutputAssembly <String>] [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings]
 [-CompilerOptions <String[]>] [<CommonParameters>]
```

### FromPath

```
Add-Type [-Path] <String[]> [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>]
 [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings] [-CompilerOptions <String[]>]
 [<CommonParameters>]
```

### FromLiteralPath

```
Add-Type -LiteralPath <String[]> [-ReferencedAssemblies <String[]>] [-OutputAssembly <String>]
 [-OutputType <OutputAssemblyType>] [-PassThru] [-IgnoreWarnings] [-CompilerOptions <String[]>]
 [<CommonParameters>]
```

### FromAssemblyName

```
Add-Type -AssemblyName <String[]> [-PassThru] [<CommonParameters>]
```

## 설명

`Add-Type`Cmdlet을 사용 하 여 PowerShell 세션에서 Microsoft .NET Core 클래스를 정의할 수 있습니다. 그런 다음 cmdlet을 사용 하 여 개체를 인스턴스화하고 `New-Object` .Net Core 개체를 사용 하는 것 처럼 개체를 사용할 수 있습니다. `Add-Type`Powershell 프로필에 명령을 추가 하는 경우 클래스는 모든 powershell 세션에서 사용할 수 있습니다.

기존 어셈블리 또는 소스 코드 파일을 지정하여 유형을 지정할 수도 있고 인라인 또는 변수에 저장된 소스 코드를 지정할 수도 있습니다. 메서드만 지정 하 고 `Add-Type` 클래스를 정의 하 고 생성할 수도 있습니다. Windows에서는이 기능을 사용 하 여 PowerShell의 관리 되지 않는 함수에 대 한 플랫폼 호출 (P/Invoke)을 수행할 수 있습니다. 소스 코드를 지정 하는 경우는 `Add-Type` 지정 된 소스 코드를 컴파일하고 새 .Net Core 형식이 포함 된 메모리 내 어셈블리를 생성 합니다.

의 매개 변수를 사용 `Add-Type` 하 여 대체 언어 및 컴파일러를 지정할 수 있습니다. c #은 기본값, 컴파일러 옵션, 어셈블리 종속성, 클래스 네임 스페이스, 형식 이름 및 결과 어셈블리를 지정 합니다.

PowerShell 7부터 `Add-Type` 같은 이름의 형식이 이미 있는 경우는 형식을 컴파일하지 않습니다. 또한는가 `Add-Type` `ref` 포함 된 폴더의 폴더에서 어셈블리를 찾습니다 `pwsh.dll` .

## 예제

### 예제 1: 세션에 .NET 형식 추가

이 예제에서는 변수에 저장 된 소스 코드를 지정 하 여 **Basictest** 클래스를 세션에 추가 합니다. **Basictest** 클래스는 정수를 추가 하 고, 개체를 만들고, 정수를 곱하는 데 사용 됩니다.

```powershell
$Source = @"
public class BasicTest
{
  public static int Add(int a, int b)
    {
        return (a + b);
    }
  public int Multiply(int a, int b)
    {
    return (a * b);
    }
}
"@

Add-Type -TypeDefinition $Source
[BasicTest]::Add(4, 3)
$BasicTestObject = New-Object BasicTest
$BasicTestObject.Multiply(5, 2)
```

`$Source`변수는 클래스에 대 한 소스 코드를 저장 합니다. 형식에 라는 정적 메서드와 `Add` 비정적 메서드가 `Multiply` 있습니다.

`Add-Type`Cmdlet은 세션에 클래스를 추가 합니다. 이 명령은 인라인 소스 코드를 사용 하기 때문에 **Typedefinition** 매개 변수를 사용 하 여 변수의 코드를 지정 합니다 `$Source` .

`Add` **Basictest** 클래스의 정적 메서드는 이중 콜론 문자 ()를 사용 `::` 하 여 클래스의 정적 멤버를 지정 합니다. 정수가 추가 되 고 합계가 표시 됩니다.

`New-Object`Cmdlet은 **basictest** 클래스의 인스턴스를 인스턴스화합니다. 새 개체를 `$BasicTestObject` 변수에 저장 합니다.

`$BasicTestObject` 메서드를 사용 `Multiply` 합니다. 정수가 곱하고 제품이 표시 됩니다.

### 예제 2: 추가 된 형식 검사

이 예에서는 cmdlet을 사용 하 여 `Get-Member` `Add-Type` 및 `New-Object` cmdlet이 **예제 1** 에서 만든 개체를 검사 합니다.

```powershell
[BasicTest] | Get-Member
```

```Output
   TypeName: System.RuntimeType

Name                 MemberType Definition
----                 ---------- ----------
AsType               Method     type AsType()
Clone                Method     System.Object Clone(), System.Object ICloneable.Clone()
Equals               Method     bool Equals(System.Object obj), bool Equals(type o)
FindInterfaces       Method     type[] FindInterfaces(System.Reflection.TypeFilter filter...
...
```

```powershell
[BasicTest] | Get-Member -Static
```

```Output
  TypeName: BasicTest

Name            MemberType Definition
----            ---------- ----------
Add             Method     static int Add(int a, int b)
Equals          Method     static bool Equals(System.Object objA, System.Object objB)
new             Method     BasicTest new()
ReferenceEquals Method     static bool ReferenceEquals(System.Object objA, System.Object objB)
```

```powershell
$BasicTestObject | Get-Member
```

```Output
   TypeName: BasicTest

Name        MemberType Definition
----        ---------- ----------
Equals      Method     bool Equals(System.Object obj)
GetHashCode Method     int GetHashCode()
GetType     Method     type GetType()
Multiply    Method     int Multiply(int a, int b)
ToString    Method     string ToString()
```

`Get-Member`Cmdlet은 세션에 추가 된 **basictest** 클래스의 형식 및 멤버를 가져옵니다 `Add-Type` . `Get-Member`이 명령은 **system.object** 클래스에서 파생 된 **system.environment 아니라 system.runtimetype** 개체 임을 보여 줍니다.

`Get-Member` **정적** 매개 변수는 **basictest** 클래스의 정적 속성 및 메서드를 가져옵니다. 출력은 `Add` 메서드가 포함 되어 있음을 보여 줍니다.

`Get-Member`Cmdlet은 변수에 저장 된 개체의 멤버를 가져옵니다 `$BasicTestObject` .
`$BasicTestObject` 는 `New-Object` **basictest** 클래스와 함께 cmdlet을 사용 하 여 만들었습니다. 출력에는 `$BasicTestObject` 변수의 값이 **basictest** 클래스의 인스턴스이고 라는 멤버가 포함 되어 있음을 알 수 `Multiply` 있습니다.

### 예제 3: 어셈블리에서 형식 추가

이 예제에서는 어셈블리의 클래스를 `NJsonSchema.dll` 현재 세션에 추가 합니다.

```powershell
Set-Location -Path $PSHOME
$AccType = Add-Type -AssemblyName *jsonschema* -PassThru
```

`Set-Location`**Path** 매개 변수를 사용 하 여 `$PSHOME` 변수를 지정 합니다. 변수는 DLL 파일이 있는 PowerShell 설치 디렉터리를 참조 합니다.

`$AccType`변수는 cmdlet을 사용 하 여 만든 개체를 저장 `Add-Type` 합니다. `Add-Type`**AssemblyName** 매개 변수를 사용 하 여 어셈블리의 이름을 지정 합니다. 별표 ( `*` ) 와일드 카드 문자를 사용 하면 이름이 나 철자를 잘 모르는 경우에도 올바른 어셈블리를 가져올 수 있습니다. **PassThru** 매개 변수는 세션에 추가 된 클래스를 나타내는 개체를 생성 합니다.

### 예제 4: 네이티브 Windows Api 호출

이 예제에서는 PowerShell에서 네이티브 Windows Api를 호출 하는 방법을 보여 줍니다. `Add-Type` 플랫폼 호출 (P/Invoke) 메커니즘을 사용 하 여 PowerShell에서의 함수를 호출 `User32.dll` 합니다. 이 예제는 Windows 운영 체제를 실행 하는 컴퓨터 에서만 작동 합니다.

```powershell
$Signature = @"
[DllImport("user32.dll")]public static extern bool ShowWindowAsync(IntPtr hWnd, int nCmdShow);
"@

$ShowWindowAsync = Add-Type -MemberDefinition $Signature -Name "Win32ShowWindowAsync" -Namespace Win32Functions -PassThru

# Minimize the PowerShell console

$ShowWindowAsync::ShowWindowAsync((Get-Process -Id $pid).MainWindowHandle, 2)

# Restore the PowerShell console

$ShowWindowAsync::ShowWindowAsync((Get-Process -Id $Pid).MainWindowHandle, 4)
```

`$Signature`변수는 함수의 c # 시그니처를 저장 합니다 `ShowWindowAsync` . 결과 메서드가 PowerShell 세션에서 표시 되도록 하려면 `public` 키워드가 표준 서명에 추가 되었습니다. 자세한 내용은 [Showwindowasync 함수](/windows/win32/api/winuser/nf-winuser-showwindowasync)를 참조 하세요.

`$ShowWindowAsync`변수는 `Add-Type` **PassThru** 매개 변수에 의해 생성 된 개체를 저장 합니다.
`Add-Type`Cmdlet은 함수를 `ShowWindowAsync` PowerShell 세션에 정적 메서드로 추가 합니다. 이 명령은 **memberdefinition** 매개 변수를 사용 하 여 변수에 저장 된 메서드 정의를 지정 합니다 `$Signature` . 이 명령은 **Name** 및 **Namespace** 매개 변수를 사용하여 클래스의 이름 및 네임스페이스를 지정하고, **PassThru** 매개 변수는 형식을 나타내는 개체를 생성 합니다.

새 `ShowWindowAsync` 정적 메서드는 PowerShell 콘솔을 최소화 하 고 복원 하는 명령에 사용 됩니다. 이 메서드는 창 핸들과 창 표시 방법을 지정 하는 정수의 두 매개 변수를 사용 합니다.

PowerShell 콘솔을 최소화 하기 위해에서는 `ShowWindowAsync` `Get-Process` 자동 변수와 함께 cmdlet을 사용 하 여 `$PID` 현재 PowerShell 세션을 호스트 하는 프로세스를 가져옵니다. 그런 다음 현재 프로세스의 **MainWindowHandle** 속성을 사용 하 고 값을 나타내는 값을 사용 `2` `SW_MINIMIZE` 합니다.

창을 복원 하기 위해는 `ShowWindowAsync` `4` 값을 나타내는 창 위치에 값을 사용 `SW_RESTORE` 합니다.

창을 최대화 하려면를 나타내는 값을 사용 `3` `SW_MAXIMIZE` 합니다.

## PARAMETERS

### -AssemblyName

해당 유형을 포함하는 어셈블리 이름을 지정합니다. `Add-Type` 지정 된 어셈블리의 형식을 사용 합니다. 이 매개 변수는 어셈블리 이름을 기반으로 형식을 만들 때 필요 합니다.

어셈블리의 전체 이름 또는 단순한 이름 (부분 이름이 라고도 함)을 입력 합니다. 어셈블리 이름에는 와일드카드 문자를 사용할 수 있습니다. 단순 이름 또는 부분 이름을 입력 하면에서 `Add-Type` 전체 이름으로 확인 한 다음 전체 이름을 사용 하 여 어셈블리를 로드 합니다.

이 매개 변수는 경로 또는 파일 이름을 허용 하지 않습니다. 어셈블리 DLL (동적 연결 라이브러리) 파일에 대 한 경로를 입력 하려면 **path** 매개 변수를 사용 합니다.

```yaml
Type: System.String[]
Parameter Sets: FromAssemblyName
Aliases: AN

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -CompilerOptions

소스 코드 컴파일러에 대한 옵션을 지정합니다. 이 옵션은 수정 없이 컴파일러로 보내집니다.

이 매개 변수를 사용 하면 실행 파일을 생성 하거나, 리소스를 포함 하거나, 옵션과 같은 명령줄 옵션을 설정 하도록 컴파일러에 지시할 수 있습니다 `/unsafe` .

동일한 명령에서 **CompilerOptions** 및 **referencedassemblies** 매개 변수를 사용할 수 없습니다.

```yaml
Type: System.String[]
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IgnoreWarnings

컴파일러 경고를 무시합니다. 이 매개 변수를 사용 하 여 `Add-Type` 컴파일러 경고를 오류로 처리 하지 않도록 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -언어

소스 코드에서 사용된 언어를 지정합니다. 이 매개 변수에 허용 되는 값은 **CSharp** 입니다.

```yaml
Type: Microsoft.PowerShell.Commands.Language
Parameter Sets: FromSource, FromMember
Aliases:
Accepted values: CSharp

Required: False
Position: Named
Default value: CSharp
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

해당 유형이 포함된 소스 코드 파일 또는 어셈블리 DLL 파일의 경로를 지정합니다. **Path** 와 달리 **LiteralPath** 매개 변수 값은 입력 한 대로 사용 됩니다. 어떠한 문자도 와일드카드로 해석되지 않습니다. 이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요. 작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

```yaml
Type: System.String[]
Parameter Sets: FromLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MemberDefinition

클래스의 새 속성 또는 메서드를 지정합니다. `Add-Type` 속성이 나 메서드를 지 원하는 데 필요한 템플릿 코드를 생성 합니다.

Windows에서는이 기능을 사용 하 여 PowerShell의 관리 되지 않는 함수에 대 한 플랫폼 호출 (P/Invoke)을 수행할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: FromMember
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

만들 클래스의 이름을 지정합니다. 멤버 정의에서 유형을 생성하는 경우 이 매개 변수는 필수입니다.

유형 이름 및 네임스페이스는 세션 내부에서 고유해야 합니다. 유형을 언로드하거나 변경할 수 없습니다.
형식에 대 한 코드를 변경 하려면 이름을 변경 하거나 새 PowerShell 세션을 시작 해야 합니다.
그러지 않으면 명령이 실패합니다.

```yaml
Type: System.String
Parameter Sets: FromMember
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Namespace

유형의 네임스페이스를 지정합니다.

이 매개 변수가 명령에 포함 되지 않은 경우 형식은 **Microsoft. PowerShell. AddType. AutoGeneratedTypes** 네임 스페이스에 만들어집니다. 매개 변수가 명령에 빈 문자열 값 또는 값으로 포함 되어 있으면 `$Null` 해당 형식이 전역 네임 스페이스에서 생성 됩니다.

```yaml
Type: System.String
Parameter Sets: FromMember
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputAssembly

어셈블리에 대한 DLL 파일을 해당 위치에 지정된 이름으로 생성합니다. 선택적 경로와 파일 이름을 입력 합니다. 와일드카드 문자를 사용할 수 있습니다. 기본적으로는 `Add-Type` 메모리에만 어셈블리를 생성 합니다.

```yaml
Type: System.String
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases: OA

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -OutputType

출력 어셈블리의 출력 유형을 지정합니다. 기본적으로 출력 유형은 지정되지 않습니다. 이 매개 변수는 명령에서 출력 어셈블리를 지정한 경우에만 사용할 수 있습니다. 값에 대 한 자세한 내용은 [Outputassemblytype 열거](/dotnet/api/microsoft.powershell.commands.outputassemblytype)를 참조 하세요.

이 매개 변수에 허용 되는 값은 다음과 같습니다.

- ConsoleApplication
- 라이브러리
- Windowsapplication.zip

> [!IMPORTANT]
> `ConsoleApplication`및 `WindowsApplication` 값은 작업 출력을 생성 하지 않으므로 사용 하면 안 됩니다.

```yaml
Type: Microsoft.PowerShell.Commands.OutputAssemblyType
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases: OT
Accepted values: ConsoleApplication, Library, WindowsApplication

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

추가된 유형을 나타내는 **System.Runtime** 개체를 반환합니다. 기본적으로이 cmdlet은 출력을 생성 하지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

해당 유형이 포함된 소스 코드 파일 또는 어셈블리 DLL 파일의 경로를 지정합니다.

소스 코드 파일을 제출 하는 경우는 `Add-Type` 파일의 코드를 컴파일하고 형식의 메모리 내 어셈블리를 만듭니다. **Path** 값에 지정 된 파일 확장명은를 사용 하는 컴파일러를 결정 합니다 `Add-Type` .

어셈블리 파일을 제출 하는 경우는 `Add-Type` 어셈블리의 형식을 사용 합니다. 메모리 내 어셈블리 또는 전역 어셈블리 캐시를 지정하려면 **AssemblyName** 매개 변수를 사용합니다.

```yaml
Type: System.String[]
Parameter Sets: FromPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ReferencedAssemblies

유형이 종속된 어셈블리를 지정합니다. 기본적으로는 `Add-Type` 및를 참조 `System.dll` `System.Management.Automation.dll` 합니다. 이 매개 변수를 사용하여 지정하는 어셈블리는 기본 어셈블리에 추가하여 참조됩니다.

PowerShell 6부터 **Referencedassemblies** 는 기본 .net 어셈블리를 포함 하지 않습니다. 이 매개 변수에 전달 된 값에이에 대 한 특정 참조를 포함 해야 합니다.

동일한 명령에서 **CompilerOptions** 및 **referencedassemblies** 매개 변수를 사용할 수 없습니다.

```yaml
Type: System.String[]
Parameter Sets: FromSource, FromMember, FromPath, FromLiteralPath
Aliases: RA

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeDefinition

유형 정의가 포함된 소스 코드를 지정합니다. 소스 코드를 문자열 또는 here-string으로 입력하거나 소스 코드가 포함된 변수를 입력하세요. 이러한 문자열에 대 한 자세한 내용은 [about_Quoting_Rules](../Microsoft.PowerShell.Core/about/about_Quoting_Rules.md)를 참조 하세요.

유형 정의에 네임스페이스 선언을 포함하세요. 네임스페이스 선언을 누락하면 유형 이름이 다른 유형 또는 다른 유형의 바로 가기 이름과 같아져서 해당 유형을 덮어쓰는 일이 발생할 수 있습니다. 예를 들어 **exception** 이라는 형식을 정의 하는 경우 exception을 위한 바로 가기로 **예외** 를 사용 하는 **스크립트는 실패** 합니다.

```yaml
Type: System.String
Parameter Sets: FromSource
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UsingNamespace

클래스에 필요한 다른 네임스페이스를 지정합니다. 이는 c # 키워드인와 매우 비슷합니다 `Using` .

기본적으로 `Add-Type` 은 **System** 네임 스페이스를 참조 합니다. **Memberdefinition** 매개 변수를 사용 하는 경우은 `Add-Type` 기본적으로 **t e m** 네임 스페이스를 참조 합니다. **UsingNamespace** 매개 변수를 사용하여 추가한 네임스페이스는 기본 네임스페이스에 추가로 참조됩니다.

```yaml
Type: System.String[]
Parameter Sets: FromMember
Aliases: Using

Required: False
Position: Named
Default value: System namespace
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

파이프라인에서로 개체를 보낼 수 없습니다 `Add-Type` .

## 출력

### 없음 또는 System.object

**PassThru** 매개 변수를 사용 하는 경우는 `Add-Type` 새 형식을 나타내는 **system.object** 개체를 반환 합니다. 그렇지 않으면이 cmdlet은 출력을 생성 하지 않습니다.

## 참고

추가한 유형은 현재 세션에만 있습니다. 모든 세션에서 형식을 사용 하려면 PowerShell 프로필에 추가 합니다. 프로필에 대 한 자세한 내용은 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)를 참조 하세요.

형식 이름 및 네임 스페이스는 세션 내에서 고유 해야 합니다. 유형을 언로드하거나 변경할 수 없습니다. 형식에 대 한 코드를 변경 해야 하는 경우 이름을 변경 하거나 새 PowerShell 세션을 시작 해야 합니다.
그러지 않으면 명령이 실패합니다.

Windows PowerShell (버전 5.1이 하)에서 `Add-Type` 아직 로드 되지 않은 모든 항목에 대해을 사용 해야 합니다. 가장 일반적으로이는 GAC (전역 어셈블리 캐시)에 있는 어셈블리에 적용 됩니다.
PowerShell 6 이상에서는 GAC가 없으므로 PowerShell에서 자체 어셈블리를 설치 `$PSHome` 합니다.
이러한 어셈블리는 요청 시 자동으로 로드 되므로를 사용 하 여 로드할 필요가 없습니다 `Add-Type` . 그러나를 사용 하면 `Add-Type` 스크립트를 모든 버전의 PowerShell과 암시적으로 호환 되도록 허용할 수 있습니다.

GAC의 어셈블리는 경로 대신 형식 이름으로 로드할 수 있습니다. 임의 경로에서 어셈블리를 로드 하려면 `Add-Type` 이러한 어셈블리를 자동으로 로드할 수 없기 때문에 필요 합니다.

## 관련 링크

[about_Profiles](../Microsoft.PowerShell.Core/About/about_profiles.md)

[about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)

[Add-Member](Add-Member.md)

[New-Object](New-Object.md)

[OutputAssemblyType](/dotnet/api/microsoft.powershell.commands.outputassemblytype)

[P/Invoke(플랫폼 호출)](/dotnet/standard/native-interop/pinvoke)

[Where-Object](../Microsoft.PowerShell.Core/Where-Object.md)
