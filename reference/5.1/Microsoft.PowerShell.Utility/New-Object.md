---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-object?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Object
ms.openlocfilehash: a21fadd58ba566edfc6e484d753b53548f2b519b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213809"
---
# <span data-ttu-id="e4889-103">New-Object</span><span class="sxs-lookup"><span data-stu-id="e4889-103">New-Object</span></span>

## <span data-ttu-id="e4889-104">개요</span><span class="sxs-lookup"><span data-stu-id="e4889-104">SYNOPSIS</span></span>
<span data-ttu-id="e4889-105">Microsoft .NET Framework 또는 COM 개체의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-105">Creates an instance of a Microsoft .NET Framework or COM object.</span></span>

## <span data-ttu-id="e4889-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e4889-106">SYNTAX</span></span>

### <span data-ttu-id="e4889-107">Net (기본값)</span><span class="sxs-lookup"><span data-stu-id="e4889-107">Net (Default)</span></span>

```
New-Object [-TypeName] <String> [[-ArgumentList] <Object[]>] [-Property <IDictionary>] [<CommonParameters>]
```

### <span data-ttu-id="e4889-108">C</span><span class="sxs-lookup"><span data-stu-id="e4889-108">Com</span></span>

```
New-Object [-ComObject] <String> [-Strict] [-Property <IDictionary>] [<CommonParameters>]
```

## <span data-ttu-id="e4889-109">설명</span><span class="sxs-lookup"><span data-stu-id="e4889-109">DESCRIPTION</span></span>

<span data-ttu-id="e4889-110">`New-Object`Cmdlet은 .NET Framework 또는 COM 개체의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-110">The `New-Object` cmdlet creates an instance of a .NET Framework or COM object.</span></span>

<span data-ttu-id="e4889-111">COM 개체의 ProgID(프로그래밍 ID)나 .NET Framework 클래스의 유형을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-111">You can specify either the type of a .NET Framework class or a ProgID of a COM object.</span></span> <span data-ttu-id="e4889-112">기본적으로 .NET Framework 클래스의 정규화된 이름을 입력하면 cmdlet은 해당 클래스의 인스턴스에 대한 참조를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-112">By default, you type the fully qualified name of a .NET Framework class and the cmdlet returns a reference to an instance of that class.</span></span> <span data-ttu-id="e4889-113">COM 개체의 인스턴스를 만들려면 **ComObject** 매개 변수를 사용 하 고 개체의 ProgID를 해당 값으로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-113">To create an instance of a COM object, use the **ComObject** parameter and specify the ProgID of the object as its value.</span></span>

## <span data-ttu-id="e4889-114">예제</span><span class="sxs-lookup"><span data-stu-id="e4889-114">EXAMPLES</span></span>

### <span data-ttu-id="e4889-115">예제 1: System.object 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="e4889-115">Example 1: Create a System.Version object</span></span>

<span data-ttu-id="e4889-116">이 예제에서는 "1.2.3.4" 문자열을 생성자로 사용 하 여 **system.object** 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-116">This example creates a **System.Version** object using the "1.2.3.4" string as the constructor.</span></span>

```powershell
New-Object -TypeName System.Version -ArgumentList "1.2.3.4"
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
1      2      3      4
```

### <span data-ttu-id="e4889-117">예제 2: Internet Explorer COM 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="e4889-117">Example 2: Create an Internet Explorer COM object</span></span>

<span data-ttu-id="e4889-118">이 예제에서는 Internet Explorer 응용 프로그램을 나타내는 COM 개체의 인스턴스 두 개를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-118">This example creates two instances of the COM object that represents the Internet Explorer application.</span></span> <span data-ttu-id="e4889-119">첫 번째 인스턴스는 **Property** 매개 변수 해시 테이블을 사용 하 여 **Navigate2** 메서드를 호출 하 고 개체의 **visible** 속성을로 설정 하 여 `$True` 응용 프로그램이 표시 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-119">The first instance uses the **Property** parameter hash table to call the **Navigate2** method and set the **Visible** property of the object to `$True` to make the application visible.</span></span>
<span data-ttu-id="e4889-120">두 번째 인스턴스는 개별 명령과 동일한 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-120">The second instance gets the same results with individual commands.</span></span>

```powershell
$IE1 = New-Object -COMObject InternetExplorer.Application -Property @{Navigate2="www.microsoft.com"; Visible = $True}

# The following command gets the same results as the example above.
$IE2 = New-Object -COMObject InternetExplorer.Application`
$IE2.Navigate2("www.microsoft.com")`
$IE2.Visible = $True`
```

### <span data-ttu-id="e4889-121">예 3: Strict 매개 변수를 사용 하 여 종료 되지 않는 오류 생성</span><span class="sxs-lookup"><span data-stu-id="e4889-121">Example 3: Use the Strict parameter to generate a non-terminating error</span></span>

<span data-ttu-id="e4889-122">이 예제에서는 **Strict** 매개 변수를 추가 하면 `New-Object` COM 개체에서 interop 어셈블리를 사용 하는 경우 cmdlet이 종료 되지 않는 오류를 생성 하는 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-122">This example demonstrates that adding the **Strict** parameter causes the `New-Object` cmdlet to generate a non-terminating error when the COM object uses an interop assembly.</span></span>

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

### <span data-ttu-id="e4889-123">예제 4: Windows 데스크톱을 관리 하는 COM 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="e4889-123">Example 4: Create a COM object to manage Windows desktop</span></span>

<span data-ttu-id="e4889-124">이 예제에서는 COM 개체를 만들고 사용하여 Windows 바탕 화면을 관리하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-124">This example shows how to create and use a COM object to manage your Windows desktop.</span></span>

<span data-ttu-id="e4889-125">첫 번째 명령은 cmdlet의 **ComObject** 매개 변수를 사용 하 여 `New-Object` **Shell. 응용 프로그램** PROGID를 사용 하 여 COM 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-125">The first command uses the **ComObject** parameter of the `New-Object` cmdlet to create a COM object with the **Shell.Application** ProgID.</span></span> <span data-ttu-id="e4889-126">결과 개체를 `$ObjShell` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-126">It stores the resulting object in the `$ObjShell` variable.</span></span> <span data-ttu-id="e4889-127">두 번째 명령은 변수를 `$ObjShell` cmdlet으로 파이프 합니다 `Get-Member` . 그러면이 CMDLET이 COM 개체의 속성 및 메서드를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-127">The second command pipes the `$ObjShell` variable to the `Get-Member` cmdlet, which displays the properties and methods of the COM object.</span></span> <span data-ttu-id="e4889-128">메서드 중에는 **ToggleDesktop** 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-128">Among the methods is the **ToggleDesktop** method.</span></span> <span data-ttu-id="e4889-129">세 번째 명령은 개체의 **ToggleDesktop** 메서드를 호출하여 바탕 화면에 열려 있는 창을 최소화합니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-129">The third command calls the **ToggleDesktop** method of the object to minimize the open windows on your desktop.</span></span>

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

### <span data-ttu-id="e4889-130">예제 5: 생성자에 여러 인수 전달</span><span class="sxs-lookup"><span data-stu-id="e4889-130">Example 5: Pass multiple arguments to a constructor</span></span>

<span data-ttu-id="e4889-131">이 예제에서는 여러 매개 변수를 사용 하는 생성자를 사용 하 여 개체를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-131">This example shows how to create an object with a constructor that takes multiple parameters.</span></span> <span data-ttu-id="e4889-132">**Argumentlist** 매개 변수를 사용 하는 경우 매개 변수를 배열에 넣어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-132">The parameters must be put in an array when using **ArgumentList** parameter.</span></span>

```powershell
$array = @('One', 'Two', 'Three')
$parameters = @{
    TypeName = 'System.Collections.Generic.HashSet[string]'
    ArgumentList = ([string[]]$array, [System.StringComparer]::OrdinalIgnoreCase)
}
$set = New-Object @parameters
```

<span data-ttu-id="e4889-133">PowerShell은 배열의 각 멤버를 생성자의 매개 변수에 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-133">PowerShell binds each member of the array to a parameter of the constructor.</span></span>

> [!NOTE]
> <span data-ttu-id="e4889-134">이 예제에서는 가독성을 위해 스 플랫 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-134">This example uses parameter splatting for readability.</span></span> <span data-ttu-id="e4889-135">자세한 내용은 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e4889-135">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

### <span data-ttu-id="e4889-136">예제 6: 배열을 단일 매개 변수로 사용 하는 생성자 호출</span><span class="sxs-lookup"><span data-stu-id="e4889-136">Example 6: Calling a constructor that takes an array as a single parameter</span></span>

<span data-ttu-id="e4889-137">이 예제에서는 배열 또는 컬렉션인 매개 변수를 사용 하는 생성자를 사용 하 여 개체를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-137">This example shows how to create an object with a constructor that takes a parameter that is an array or collection.</span></span> <span data-ttu-id="e4889-138">배열 매개 변수는 다른 배열 내에 래핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-138">The array parameter must be put in wrapped inside another array.</span></span>

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

<span data-ttu-id="e4889-139">이 예제에서 개체를 만드는 첫 번째 시도가 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-139">The first attempt to create the object in this example fails.</span></span> <span data-ttu-id="e4889-140">PowerShell에서 세 개의 멤버를 `$array` 생성자의 매개 변수에 바인딩하려고 했지만 생성자는 세 개의 매개 변수를 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-140">PowerShell attempted to bind the three members of `$array` to parameters of the constructor but the constructor does not take three parameter.</span></span> <span data-ttu-id="e4889-141">`$array`다른 배열로 래핑하여 PowerShell에서의 세 멤버를 `$array` 생성자의 매개 변수에 바인딩하지 못하게 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-141">Wrapping `$array` in another array prevents PowerShell from attempting to bind the three members of `$array` to parameters of the constructor.</span></span>

## <span data-ttu-id="e4889-142">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e4889-142">PARAMETERS</span></span>

### <span data-ttu-id="e4889-143">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="e4889-143">-ArgumentList</span></span>

<span data-ttu-id="e4889-144">.NET Framework 클래스의 생성자에 전달할 인수의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-144">Specifies an array of arguments to pass to the constructor of the .NET Framework class.</span></span> <span data-ttu-id="e4889-145">생성자가 배열인 단일 매개 변수를 사용 하는 경우 해당 매개 변수를 다른 배열 내에 래핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-145">If the constructor takes a single parameter that is an array, you must wrap that parameter inside another array.</span></span> <span data-ttu-id="e4889-146">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="e4889-146">For example:</span></span>

`$cert = New-Object System.Security.Cryptography.X509Certificates.X509Certificate -ArgumentList (,$bytes)`

<span data-ttu-id="e4889-147">**Argumentlist** 의 동작에 대 한 자세한 내용은 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e4889-147">For more information about the behavior of **ArgumentList** , see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays).</span></span>

<span data-ttu-id="e4889-148">**ArgumentList** 의 별칭은 **Args** 입니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-148">The alias for **ArgumentList** is **Args** .</span></span>

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

### <span data-ttu-id="e4889-149">-ComObject</span><span class="sxs-lookup"><span data-stu-id="e4889-149">-ComObject</span></span>

<span data-ttu-id="e4889-150">COM 개체의 ProgID(프로그래밍 ID)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-150">Specifies the programmatic identifier (ProgID) of the COM object.</span></span>

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

### <span data-ttu-id="e4889-151">-속성</span><span class="sxs-lookup"><span data-stu-id="e4889-151">-Property</span></span>

<span data-ttu-id="e4889-152">속성 값을 설정하고 새 개체의 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-152">Sets property values and invokes methods of the new object.</span></span>

<span data-ttu-id="e4889-153">키가 속성 또는 메서드의 이름이고 값이 속성 값이나 메서드 인수인 해시 테이블을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-153">Enter a hash table in which the keys are the names of properties or methods and the values are property values or method arguments.</span></span> <span data-ttu-id="e4889-154">`New-Object` 개체를 만들고 각 속성 값을 설정 하 고 해시 테이블에 나타나는 순서 대로 각 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-154">`New-Object` creates the object and sets each property value and invokes each method in the order that they appear in the hash table.</span></span>

<span data-ttu-id="e4889-155">새 개체가 **PSObject** 클래스에서 파생 되 고 개체에 존재 하지 않는 속성을 지정 하는 경우는 지정 된 속성을 `New-Object` 개체에 메모 속성으로 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-155">If the new object is derived from the **PSObject** class, and you specify a property that does not exist on the object, `New-Object` adds the specified property to the object as a NoteProperty.</span></span> <span data-ttu-id="e4889-156">개체가 **PSObject** 가 아닌 경우 명령은 종료 되지 않는 오류를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-156">If the object is not a **PSObject** , the command generates a non-terminating error.</span></span>

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

### <span data-ttu-id="e4889-157">-Strict</span><span class="sxs-lookup"><span data-stu-id="e4889-157">-Strict</span></span>

<span data-ttu-id="e4889-158">만들려는 COM 개체에서 interop 어셈블리를 사용 하는 경우 cmdlet에서 종료 되지 않는 오류를 생성 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-158">Indicates that the cmdlet generates a non-terminating error when a COM object that you attempt to create uses an interop assembly.</span></span> <span data-ttu-id="e4889-159">이 기능은 실제 COM 개체를 COM 호출 가능 래퍼를 사용하는 .NET Framework 개체와 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-159">This feature distinguishes actual COM objects from .NET Framework objects with COM-callable wrappers.</span></span>

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

### <span data-ttu-id="e4889-160">-TypeName</span><span class="sxs-lookup"><span data-stu-id="e4889-160">-TypeName</span></span>

<span data-ttu-id="e4889-161">.NET Framework 클래스의 정규화된 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-161">Specifies the fully qualified name of the .NET Framework class.</span></span> <span data-ttu-id="e4889-162">**TypeName** 매개 변수와 **ComObject** 매개 변수를 모두 지정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-162">You cannot specify both the **TypeName** parameter and the **ComObject** parameter.</span></span>

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

### <span data-ttu-id="e4889-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e4889-163">CommonParameters</span></span>

<span data-ttu-id="e4889-164">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e4889-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e4889-165">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e4889-165">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e4889-166">입력</span><span class="sxs-lookup"><span data-stu-id="e4889-166">INPUTS</span></span>

### <span data-ttu-id="e4889-167">없음</span><span class="sxs-lookup"><span data-stu-id="e4889-167">None</span></span>

<span data-ttu-id="e4889-168">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-168">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="e4889-169">출력</span><span class="sxs-lookup"><span data-stu-id="e4889-169">OUTPUTS</span></span>

### <span data-ttu-id="e4889-170">Object</span><span class="sxs-lookup"><span data-stu-id="e4889-170">Object</span></span>

<span data-ttu-id="e4889-171">`New-Object` 만들어진 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-171">`New-Object` returns the object that is created.</span></span>

## <span data-ttu-id="e4889-172">참고</span><span class="sxs-lookup"><span data-stu-id="e4889-172">NOTES</span></span>

- <span data-ttu-id="e4889-173">`New-Object` VBScript CreateObject 함수에서 가장 일반적으로 사용 되는 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-173">`New-Object` provides the most commonly-used functionality of the VBScript CreateObject function.</span></span> <span data-ttu-id="e4889-174">VBScript에서와 같은 문은 `Set objShell = CreateObject("Shell.Application")` PowerShell에서로 변환할 수 있습니다 `$objShell = New-Object -COMObject "Shell.Application"` .</span><span class="sxs-lookup"><span data-stu-id="e4889-174">A statement like `Set objShell = CreateObject("Shell.Application")` in VBScript can be translated to `$objShell = New-Object -COMObject "Shell.Application"` in PowerShell.</span></span>
- <span data-ttu-id="e4889-175">`New-Object` 는 명령줄 및 스크립트 내에서 .NET Framework 개체를 쉽게 사용할 수 있도록 하 여 Windows 스크립트 호스트 환경에서 사용할 수 있는 기능을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4889-175">`New-Object` expands upon the functionality available in the Windows Script Host environment by making it easy to work with .NET Framework objects from the command line and within scripts.</span></span>

## <span data-ttu-id="e4889-176">관련 링크</span><span class="sxs-lookup"><span data-stu-id="e4889-176">RELATED LINKS</span></span>

[<span data-ttu-id="e4889-177">about_Object_Creation</span><span class="sxs-lookup"><span data-stu-id="e4889-177">about_Object_Creation</span></span>](../Microsoft.PowerShell.Core/About/about_Object_Creation.md)

[<span data-ttu-id="e4889-178">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="e4889-178">Compare-Object</span></span>](Compare-Object.md)

[<span data-ttu-id="e4889-179">Group-Object</span><span class="sxs-lookup"><span data-stu-id="e4889-179">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="e4889-180">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="e4889-180">Measure-Object</span></span>](Measure-Object.md)

[<span data-ttu-id="e4889-181">Select-Object</span><span class="sxs-lookup"><span data-stu-id="e4889-181">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="e4889-182">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="e4889-182">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="e4889-183">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="e4889-183">Tee-Object</span></span>](Tee-Object.md)
