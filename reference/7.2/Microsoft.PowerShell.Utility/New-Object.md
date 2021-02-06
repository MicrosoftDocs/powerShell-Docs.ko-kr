---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Object
ms.openlocfilehash: 3b2db400c5a8a1c61ec30ecee07f91d29b5eb3c1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601466"
---
# <span data-ttu-id="393cf-102">New-Object</span><span class="sxs-lookup"><span data-stu-id="393cf-102">New-Object</span></span>

## <span data-ttu-id="393cf-103">개요</span><span class="sxs-lookup"><span data-stu-id="393cf-103">SYNOPSIS</span></span>
<span data-ttu-id="393cf-104">Microsoft .NET Framework 또는 COM 개체의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-104">Creates an instance of a Microsoft .NET Framework or COM object.</span></span>

## <span data-ttu-id="393cf-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="393cf-105">SYNTAX</span></span>

### <span data-ttu-id="393cf-106">Net (기본값)</span><span class="sxs-lookup"><span data-stu-id="393cf-106">Net (Default)</span></span>

```
New-Object [-TypeName] <String> [[-ArgumentList] <Object[]>] [-Property <IDictionary>] [<CommonParameters>]
```

### <span data-ttu-id="393cf-107">C</span><span class="sxs-lookup"><span data-stu-id="393cf-107">Com</span></span>

```
New-Object [-ComObject] <String> [-Strict] [-Property <IDictionary>] [<CommonParameters>]
```

## <span data-ttu-id="393cf-108">설명</span><span class="sxs-lookup"><span data-stu-id="393cf-108">DESCRIPTION</span></span>

<span data-ttu-id="393cf-109">`New-Object`Cmdlet은 .NET Framework 또는 COM 개체의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-109">The `New-Object` cmdlet creates an instance of a .NET Framework or COM object.</span></span>

<span data-ttu-id="393cf-110">COM 개체의 ProgID(프로그래밍 ID)나 .NET Framework 클래스의 유형을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-110">You can specify either the type of a .NET Framework class or a ProgID of a COM object.</span></span> <span data-ttu-id="393cf-111">기본적으로 .NET Framework 클래스의 정규화된 이름을 입력하면 cmdlet은 해당 클래스의 인스턴스에 대한 참조를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-111">By default, you type the fully qualified name of a .NET Framework class and the cmdlet returns a reference to an instance of that class.</span></span> <span data-ttu-id="393cf-112">COM 개체의 인스턴스를 만들려면 **ComObject** 매개 변수를 사용 하 고 개체의 ProgID를 해당 값으로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-112">To create an instance of a COM object, use the **ComObject** parameter and specify the ProgID of the object as its value.</span></span>

## <span data-ttu-id="393cf-113">예제</span><span class="sxs-lookup"><span data-stu-id="393cf-113">EXAMPLES</span></span>

### <span data-ttu-id="393cf-114">예제 1: System.object 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="393cf-114">Example 1: Create a System.Version object</span></span>

<span data-ttu-id="393cf-115">이 예제에서는 "1.2.3.4" 문자열을 생성자로 사용 하 여 **system.object** 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-115">This example creates a **System.Version** object using the "1.2.3.4" string as the constructor.</span></span>

```powershell
New-Object -TypeName System.Version -ArgumentList "1.2.3.4"
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
1      2      3      4
```

### <span data-ttu-id="393cf-116">예제 2: Internet Explorer COM 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="393cf-116">Example 2: Create an Internet Explorer COM object</span></span>

<span data-ttu-id="393cf-117">이 예제에서는 Internet Explorer 응용 프로그램을 나타내는 COM 개체의 인스턴스 두 개를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-117">This example creates two instances of the COM object that represents the Internet Explorer application.</span></span> <span data-ttu-id="393cf-118">첫 번째 인스턴스는 **Property** 매개 변수 해시 테이블을 사용 하 여 **Navigate2** 메서드를 호출 하 고 개체의 **visible** 속성을로 설정 하 여 `$True` 응용 프로그램이 표시 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-118">The first instance uses the **Property** parameter hash table to call the **Navigate2** method and set the **Visible** property of the object to `$True` to make the application visible.</span></span>
<span data-ttu-id="393cf-119">두 번째 인스턴스는 개별 명령과 동일한 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-119">The second instance gets the same results with individual commands.</span></span>

```powershell
$IE1 = New-Object -COMObject InternetExplorer.Application -Property @{Navigate2="www.microsoft.com"; Visible = $True}

# The following command gets the same results as the example above.
$IE2 = New-Object -COMObject InternetExplorer.Application`
$IE2.Navigate2("www.microsoft.com")`
$IE2.Visible = $True`
```

### <span data-ttu-id="393cf-120">예 3: Strict 매개 변수를 사용 하 여 종료 되지 않는 오류 생성</span><span class="sxs-lookup"><span data-stu-id="393cf-120">Example 3: Use the Strict parameter to generate a non-terminating error</span></span>

<span data-ttu-id="393cf-121">이 예제에서는 **Strict** 매개 변수를 추가 하면 `New-Object` COM 개체에서 interop 어셈블리를 사용 하는 경우 cmdlet이 종료 되지 않는 오류를 생성 하는 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-121">This example demonstrates that adding the **Strict** parameter causes the `New-Object` cmdlet to generate a non-terminating error when the COM object uses an interop assembly.</span></span>

```powershell
$A = New-Object -COMObject Word.Application -Strict -Property @{Visible = $True}
```

```Output
New-Object : The object written to the pipeline is an instance of the type
"Microsoft.Office.Interop.Word.ApplicationClass" from the component's primary interop assembly. If
this type exposes different members than the IDispatch members, scripts written to work with this
object might not work if the primary interop assembly is not installed.

At line:1 char:14
+ $A = New-Object  <<<< -COM Word.Application -Strict; $a.visible=$true
```

### <span data-ttu-id="393cf-122">예제 4: Windows 데스크톱을 관리 하는 COM 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="393cf-122">Example 4: Create a COM object to manage Windows desktop</span></span>

<span data-ttu-id="393cf-123">이 예제에서는 COM 개체를 만들고 사용하여 Windows 바탕 화면을 관리하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-123">This example shows how to create and use a COM object to manage your Windows desktop.</span></span>

<span data-ttu-id="393cf-124">첫 번째 명령은 cmdlet의 **ComObject** 매개 변수를 사용 하 여 `New-Object` **Shell. 응용 프로그램** PROGID를 사용 하 여 COM 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-124">The first command uses the **ComObject** parameter of the `New-Object` cmdlet to create a COM object with the **Shell.Application** ProgID.</span></span> <span data-ttu-id="393cf-125">결과 개체를 `$ObjShell` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-125">It stores the resulting object in the `$ObjShell` variable.</span></span> <span data-ttu-id="393cf-126">두 번째 명령은 변수를 `$ObjShell` cmdlet으로 파이프 합니다 `Get-Member` . 그러면이 CMDLET이 COM 개체의 속성 및 메서드를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-126">The second command pipes the `$ObjShell` variable to the `Get-Member` cmdlet, which displays the properties and methods of the COM object.</span></span> <span data-ttu-id="393cf-127">메서드 중에는 **ToggleDesktop** 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-127">Among the methods is the **ToggleDesktop** method.</span></span> <span data-ttu-id="393cf-128">세 번째 명령은 개체의 **ToggleDesktop** 메서드를 호출하여 바탕 화면에 열려 있는 창을 최소화합니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-128">The third command calls the **ToggleDesktop** method of the object to minimize the open windows on your desktop.</span></span>

```powershell
$Objshell = New-Object -COMObject "Shell.Application"
$objshell | Get-Member
$objshell.ToggleDesktop()
```

```Output
   TypeName: System.__ComObject#{866738b9-6cf2-4de8-8767-f794ebe74f4e}

Name                 MemberType Definition
----                 ---------- ----------
AddToRecent          Method     void AddToRecent (Variant, string)
BrowseForFolder      Method     Folder BrowseForFolder (int, string, int, Variant)
CanStartStopService  Method     Variant CanStartStopService (string)
CascadeWindows       Method     void CascadeWindows ()
ControlPanelItem     Method     void ControlPanelItem (string)
EjectPC              Method     void EjectPC ()
Explore              Method     void Explore (Variant)
ExplorerPolicy       Method     Variant ExplorerPolicy (string)
FileRun              Method     void FileRun ()
FindComputer         Method     void FindComputer ()
FindFiles            Method     void FindFiles ()
FindPrinter          Method     void FindPrinter (string, string, string)
GetSetting           Method     bool GetSetting (int)
GetSystemInformation Method     Variant GetSystemInformation (string)
Help                 Method     void Help ()
IsRestricted         Method     int IsRestricted (string, string)
IsServiceRunning     Method     Variant IsServiceRunning (string)
MinimizeAll          Method     void MinimizeAll ()
NameSpace            Method     Folder NameSpace (Variant)
Open                 Method     void Open (Variant)
RefreshMenu          Method     void RefreshMenu ()
ServiceStart         Method     Variant ServiceStart (string, Variant)
ServiceStop          Method     Variant ServiceStop (string, Variant)
SetTime              Method     void SetTime ()
ShellExecute         Method     void ShellExecute (string, Variant, Variant, Variant, Variant)
ShowBrowserBar       Method     Variant ShowBrowserBar (string, Variant)
ShutdownWindows      Method     void ShutdownWindows ()
Suspend              Method     void Suspend ()
TileHorizontally     Method     void TileHorizontally ()
TileVertically       Method     void TileVertically ()
ToggleDesktop        Method     void ToggleDesktop ()
TrayProperties       Method     void TrayProperties ()
UndoMinimizeALL      Method     void UndoMinimizeALL ()
Windows              Method     IDispatch Windows ()
WindowsSecurity      Method     void WindowsSecurity ()
WindowSwitcher       Method     void WindowSwitcher ()
Application          Property   IDispatch Application () {get}
Parent               Property   IDispatch Parent () {get}
```

### <span data-ttu-id="393cf-129">예제 5: 생성자에 여러 인수 전달</span><span class="sxs-lookup"><span data-stu-id="393cf-129">Example 5: Pass multiple arguments to a constructor</span></span>

<span data-ttu-id="393cf-130">이 예제에서는 여러 매개 변수를 사용 하는 생성자를 사용 하 여 개체를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-130">This example shows how to create an object with a constructor that takes multiple parameters.</span></span> <span data-ttu-id="393cf-131">**Argumentlist** 매개 변수를 사용 하는 경우 매개 변수를 배열에 넣어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-131">The parameters must be put in an array when using **ArgumentList** parameter.</span></span>

```powershell
$array = @('One', 'Two', 'Three')
$parameters = @{
    TypeName = 'System.Collections.Generic.HashSet[string]'
    ArgumentList = ([string[]]$array, [System.StringComparer]::OrdinalIgnoreCase)
}
$set = New-Object @parameters
```

<span data-ttu-id="393cf-132">PowerShell은 배열의 각 멤버를 생성자의 매개 변수에 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-132">PowerShell binds each member of the array to a parameter of the constructor.</span></span>

> [!NOTE]
> <span data-ttu-id="393cf-133">이 예제에서는 가독성을 위해 스 플랫 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-133">This example uses parameter splatting for readability.</span></span> <span data-ttu-id="393cf-134">자세한 내용은 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="393cf-134">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

### <span data-ttu-id="393cf-135">예제 6: 배열을 단일 매개 변수로 사용 하는 생성자 호출</span><span class="sxs-lookup"><span data-stu-id="393cf-135">Example 6: Calling a constructor that takes an array as a single parameter</span></span>

<span data-ttu-id="393cf-136">이 예제에서는 배열 또는 컬렉션인 매개 변수를 사용 하는 생성자를 사용 하 여 개체를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-136">This example shows how to create an object with a constructor that takes a parameter that is an array or collection.</span></span> <span data-ttu-id="393cf-137">배열 매개 변수는 다른 배열 내에 래핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-137">The array parameter must be put in wrapped inside another array.</span></span>

```powershell
$array = @('One', 'Two', 'Three')
# This command throws an exception.
$set = New-Object -TypeName 'System.Collections.Generic.HashSet[string]' -ArgumentList $array
# This command succeeds.
$set = New-Object -TypeName 'System.Collections.Generic.HashSet[string]' -ArgumentList (,[string[]]$array)
$set
```

```Output
New-Object : Cannot find an overload for "HashSet`1" and the argument count: "3".
At line:1 char:8
+ $set = New-Object -TypeName 'System.Collections.Generic.HashSet[strin ...
+        ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : InvalidOperation: (:) [New-Object], MethodException
+ FullyQualifiedErrorId : ConstructorInvokedThrowException,Microsoft.PowerShell.Commands.NewObjectCommand

One
Two
Three
```

<span data-ttu-id="393cf-138">이 예제에서 개체를 만드는 첫 번째 시도가 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-138">The first attempt to create the object in this example fails.</span></span> <span data-ttu-id="393cf-139">PowerShell에서 세 개의 멤버를 `$array` 생성자의 매개 변수에 바인딩하려고 했지만 생성자는 세 개의 매개 변수를 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-139">PowerShell attempted to bind the three members of `$array` to parameters of the constructor but the constructor does not take three parameter.</span></span> <span data-ttu-id="393cf-140">`$array`다른 배열로 래핑하여 PowerShell에서의 세 멤버를 `$array` 생성자의 매개 변수에 바인딩하지 못하게 합니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-140">Wrapping `$array` in another array prevents PowerShell from attempting to bind the three members of `$array` to parameters of the constructor.</span></span>

## <span data-ttu-id="393cf-141">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="393cf-141">PARAMETERS</span></span>

### <span data-ttu-id="393cf-142">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="393cf-142">-ArgumentList</span></span>

<span data-ttu-id="393cf-143">.NET Framework 클래스의 생성자에 전달할 인수의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-143">Specifies an array of arguments to pass to the constructor of the .NET Framework class.</span></span> <span data-ttu-id="393cf-144">생성자가 배열인 단일 매개 변수를 사용 하는 경우 해당 매개 변수를 다른 배열 내에 래핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-144">If the constructor takes a single parameter that is an array, you must wrap that parameter inside another array.</span></span> <span data-ttu-id="393cf-145">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="393cf-145">For example:</span></span>

`$cert = New-Object System.Security.Cryptography.X509Certificates.X509Certificate -ArgumentList (,$bytes)`

<span data-ttu-id="393cf-146">**Argumentlist** 의 동작에 대 한 자세한 내용은 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="393cf-146">For more information about the behavior of **ArgumentList**, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays).</span></span>

<span data-ttu-id="393cf-147">**ArgumentList** 의 별칭은 **Args** 입니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-147">The alias for **ArgumentList** is **Args**.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: Net
Aliases: Args

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="393cf-148">-ComObject</span><span class="sxs-lookup"><span data-stu-id="393cf-148">-ComObject</span></span>

<span data-ttu-id="393cf-149">COM 개체의 ProgID(프로그래밍 ID)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-149">Specifies the programmatic identifier (ProgID) of the COM object.</span></span>

```yaml
Type: System.String
Parameter Sets: Com
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="393cf-150">-속성</span><span class="sxs-lookup"><span data-stu-id="393cf-150">-Property</span></span>

<span data-ttu-id="393cf-151">속성 값을 설정하고 새 개체의 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-151">Sets property values and invokes methods of the new object.</span></span>

<span data-ttu-id="393cf-152">키가 속성 또는 메서드의 이름이고 값이 속성 값이나 메서드 인수인 해시 테이블을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-152">Enter a hash table in which the keys are the names of properties or methods and the values are property values or method arguments.</span></span> <span data-ttu-id="393cf-153">`New-Object` 개체를 만들고 각 속성 값을 설정 하 고 해시 테이블에 나타나는 순서 대로 각 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-153">`New-Object` creates the object and sets each property value and invokes each method in the order that they appear in the hash table.</span></span>

<span data-ttu-id="393cf-154">새 개체가 **PSObject** 클래스에서 파생 되 고 개체에 존재 하지 않는 속성을 지정 하는 경우는 지정 된 속성을 `New-Object` 개체에 메모 속성으로 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-154">If the new object is derived from the **PSObject** class, and you specify a property that does not exist on the object, `New-Object` adds the specified property to the object as a NoteProperty.</span></span> <span data-ttu-id="393cf-155">개체가 **PSObject** 가 아닌 경우 명령은 종료 되지 않는 오류를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-155">If the object is not a **PSObject**, the command generates a non-terminating error.</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="393cf-156">-Strict</span><span class="sxs-lookup"><span data-stu-id="393cf-156">-Strict</span></span>

<span data-ttu-id="393cf-157">만들려는 COM 개체에서 interop 어셈블리를 사용 하는 경우 cmdlet에서 종료 되지 않는 오류를 생성 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-157">Indicates that the cmdlet generates a non-terminating error when a COM object that you attempt to create uses an interop assembly.</span></span> <span data-ttu-id="393cf-158">이 기능은 실제 COM 개체를 COM 호출 가능 래퍼를 사용하는 .NET Framework 개체와 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-158">This feature distinguishes actual COM objects from .NET Framework objects with COM-callable wrappers.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Com
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="393cf-159">-TypeName</span><span class="sxs-lookup"><span data-stu-id="393cf-159">-TypeName</span></span>

<span data-ttu-id="393cf-160">.NET Framework 클래스의 정규화된 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-160">Specifies the fully qualified name of the .NET Framework class.</span></span> <span data-ttu-id="393cf-161">**TypeName** 매개 변수와 **ComObject** 매개 변수를 모두 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-161">You cannot specify both the **TypeName** parameter and the **ComObject** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: Net
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="393cf-162">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="393cf-162">CommonParameters</span></span>

<span data-ttu-id="393cf-163">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="393cf-163">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="393cf-164">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="393cf-164">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="393cf-165">입력</span><span class="sxs-lookup"><span data-stu-id="393cf-165">INPUTS</span></span>

### <span data-ttu-id="393cf-166">없음</span><span class="sxs-lookup"><span data-stu-id="393cf-166">None</span></span>

<span data-ttu-id="393cf-167">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-167">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="393cf-168">출력</span><span class="sxs-lookup"><span data-stu-id="393cf-168">OUTPUTS</span></span>

### <span data-ttu-id="393cf-169">Object</span><span class="sxs-lookup"><span data-stu-id="393cf-169">Object</span></span>

<span data-ttu-id="393cf-170">`New-Object` 만들어진 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-170">`New-Object` returns the object that is created.</span></span>

## <span data-ttu-id="393cf-171">참고</span><span class="sxs-lookup"><span data-stu-id="393cf-171">NOTES</span></span>

- <span data-ttu-id="393cf-172">`New-Object` VBScript CreateObject 함수에서 가장 일반적으로 사용 되는 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-172">`New-Object` provides the most commonly-used functionality of the VBScript CreateObject function.</span></span> <span data-ttu-id="393cf-173">VBScript에서와 같은 문은 `Set objShell = CreateObject("Shell.Application")` PowerShell에서로 변환할 수 있습니다 `$objShell = New-Object -COMObject "Shell.Application"` .</span><span class="sxs-lookup"><span data-stu-id="393cf-173">A statement like `Set objShell = CreateObject("Shell.Application")` in VBScript can be translated to `$objShell = New-Object -COMObject "Shell.Application"` in PowerShell.</span></span>
- <span data-ttu-id="393cf-174">`New-Object` 는 명령줄 및 스크립트 내에서 .NET Framework 개체를 쉽게 사용할 수 있도록 하 여 Windows 스크립트 호스트 환경에서 사용할 수 있는 기능을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="393cf-174">`New-Object` expands upon the functionality available in the Windows Script Host environment by making it easy to work with .NET Framework objects from the command line and within scripts.</span></span>

## <span data-ttu-id="393cf-175">관련 링크</span><span class="sxs-lookup"><span data-stu-id="393cf-175">RELATED LINKS</span></span>

[<span data-ttu-id="393cf-176">about_Object_Creation</span><span class="sxs-lookup"><span data-stu-id="393cf-176">about_Object_Creation</span></span>](../Microsoft.PowerShell.Core/About/about_Object_Creation.md)

[<span data-ttu-id="393cf-177">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="393cf-177">Compare-Object</span></span>](Compare-Object.md)

[<span data-ttu-id="393cf-178">Group-Object</span><span class="sxs-lookup"><span data-stu-id="393cf-178">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="393cf-179">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="393cf-179">Measure-Object</span></span>](Measure-Object.md)

[<span data-ttu-id="393cf-180">Select-Object</span><span class="sxs-lookup"><span data-stu-id="393cf-180">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="393cf-181">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="393cf-181">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="393cf-182">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="393cf-182">Tee-Object</span></span>](Tee-Object.md)

