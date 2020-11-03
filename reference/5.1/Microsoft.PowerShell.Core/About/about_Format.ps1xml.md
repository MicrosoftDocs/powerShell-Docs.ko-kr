---
description: Powershell `Format.ps1xml` 의 파일은 powershell 콘솔에서 개체의 기본 표시를 정의 합니다. 사용자 고유의 `Format.ps1xml` 파일을 만들어 개체 표시를 변경 하거나 PowerShell에서 만든 새 개체 유형에 대 한 기본 표시를 정의할 수 있습니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_format.ps1xml?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Format.ps1xml
ms.openlocfilehash: be88007d23ab98b9c2f707b77f9c43578ba9887b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222761"
---
# <a name="about-formatps1xml"></a><span data-ttu-id="4188e-105">Format.ps1xml 정보</span><span class="sxs-lookup"><span data-stu-id="4188e-105">About Format.ps1xml</span></span>

## <a name="short-description"></a><span data-ttu-id="4188e-106">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="4188e-106">Short description</span></span>

<span data-ttu-id="4188e-107">Powershell `Format.ps1xml` 의 파일은 powershell 콘솔에서 개체의 기본 표시를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-107">The `Format.ps1xml` files in PowerShell define the default display of objects in the PowerShell console.</span></span> <span data-ttu-id="4188e-108">사용자 고유의 `Format.ps1xml` 파일을 만들어 개체 표시를 변경 하거나 PowerShell에서 만든 새 개체 유형에 대 한 기본 표시를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-108">You can create your own `Format.ps1xml` files to change the display of objects or to define default displays for new object types that you create in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="4188e-109">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-109">Long description</span></span>

<span data-ttu-id="4188e-110">`Format.ps1xml`Powershell의 파일은 powershell에서 개체의 기본 표시를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-110">The `Format.ps1xml` files in PowerShell define the default display of objects in PowerShell.</span></span> <span data-ttu-id="4188e-111">사용자 고유의 `Format.ps1xml` 파일을 만들어 개체 표시를 변경 하거나 PowerShell에서 만든 새 개체 유형에 대 한 기본 표시를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-111">You can create your own `Format.ps1xml` files to change the display of objects or to define default displays for new object types that you create in PowerShell.</span></span>

<span data-ttu-id="4188e-112">PowerShell에서 개체를 표시 하면 구조화 된 서식 파일의 데이터를 사용 하 여 개체의 기본 표시를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-112">When PowerShell displays an object, it uses the data in structured formatting files to determine the default display of the object.</span></span> <span data-ttu-id="4188e-113">서식 파일의 데이터는 개체가 테이블이 나 목록에서 렌더링 되는지 여부를 결정 하 고 기본적으로 표시 되는 속성을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-113">The data in the formatting files determines whether the object is rendered in a table or in a list, and it determines which properties are displayed by default.</span></span>

<span data-ttu-id="4188e-114">서식 지정은 표시에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-114">The formatting affects the display only.</span></span> <span data-ttu-id="4188e-115">파이프라인으로 전달 되는 개체 속성이 나 전달 되는 방법에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-115">It doesn't affect which object properties are passed down the pipeline or how they're passed.</span></span> <span data-ttu-id="4188e-116">`Format.ps1xml` 파일은 해시 테이블에 대 한 출력 형식을 사용자 지정 하는 데 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-116">`Format.ps1xml` files can't be used to customize the output format for hash tables.</span></span>

<span data-ttu-id="4188e-117">PowerShell에는 7 개의 서식 파일이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-117">PowerShell includes seven formatting files.</span></span> <span data-ttu-id="4188e-118">이러한 파일은 설치 디렉터리 ()에 있습니다 `$PSHOME` .</span><span class="sxs-lookup"><span data-stu-id="4188e-118">These files are located in the installation directory (`$PSHOME`).</span></span> <span data-ttu-id="4188e-119">각 파일은 Microsoft .NET Framework 개체의 그룹 표시를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-119">Each file defines the display of a group of Microsoft .NET Framework objects:</span></span>

1. `Certificate.Format.ps1xml`

   <span data-ttu-id="4188e-120">X.509 인증서 및 인증서 저장소와 같은 인증서 저장소의 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-120">Objects in the Certificate store, such as X.509 certificates and certificate stores.</span></span>

1. `DotNetTypes.Format.ps1xml`

   <span data-ttu-id="4188e-121">CultureInfo, FileVersionInfo 및 EventLogEntry 개체와 같은 기타 .NET Framework 형식</span><span class="sxs-lookup"><span data-stu-id="4188e-121">Other .NET Framework types, such as CultureInfo, FileVersionInfo, and EventLogEntry objects.</span></span>

1. `FileSystem.Format.ps1xml`

   <span data-ttu-id="4188e-122">파일 및 디렉터리와 같은 파일 시스템 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-122">File system objects, such as files and directories.</span></span>

1. `Help.Format.ps1xml`

   <span data-ttu-id="4188e-123">세부 정보 및 전체 보기, 매개 변수 및 예제와 같은 도움말 보기</span><span class="sxs-lookup"><span data-stu-id="4188e-123">Help views, such as detailed and full views, parameters, and examples.</span></span>

1. `PowerShellCore.Format.ps1xml`

   <span data-ttu-id="4188e-124">PowerShell 핵심 cmdlet (예: 및)에 의해 생성 된 개체 `Get-Member` `Get-History` 입니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-124">Objects generated by PowerShell core cmdlets, such as `Get-Member` and `Get-History`.</span></span>

1. `PowerShellTrace.Format.ps1xml`

   <span data-ttu-id="4188e-125">Cmdlet에서 생성 된 개체와 같은 추적 개체 `Trace-Command` 입니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-125">Trace objects, such as those generated by the `Trace-Command` cmdlet.</span></span>

1. `Registry.Format.ps1xml`

   <span data-ttu-id="4188e-126">레지스트리 개체 (예: 키 및 항목)</span><span class="sxs-lookup"><span data-stu-id="4188e-126">Registry objects, such as keys and entries.</span></span>

<span data-ttu-id="4188e-127">서식 파일은 각 개체의 네 가지 뷰를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-127">A formatting file can define four different views of each object:</span></span>

- <span data-ttu-id="4188e-128">테이블</span><span class="sxs-lookup"><span data-stu-id="4188e-128">Table</span></span>
- <span data-ttu-id="4188e-129">목록</span><span class="sxs-lookup"><span data-stu-id="4188e-129">List</span></span>
- <span data-ttu-id="4188e-130">넓게</span><span class="sxs-lookup"><span data-stu-id="4188e-130">Wide</span></span>
- <span data-ttu-id="4188e-131">사용자 지정</span><span class="sxs-lookup"><span data-stu-id="4188e-131">Custom</span></span>

<span data-ttu-id="4188e-132">예를 들어 명령 출력을 `Get-ChildItem` 명령으로 파이프 하면는 `Format-List` `Format-List` 파일의 뷰를 사용 하 여 `FileSystem.Format.ps1xml` 파일 및 폴더 개체를 목록으로 표시 하는 방법을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-132">For example, when the output of a `Get-ChildItem` command is piped to a `Format-List` command, `Format-List` uses the view in the `FileSystem.Format.ps1xml` file to determine how to display the file and folder objects as a list.</span></span>

<span data-ttu-id="4188e-133">서식 파일에 개체의 뷰가 두 개 이상 포함 된 경우 PowerShell은 찾은 첫 번째 뷰를 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-133">When a formatting file includes more than one view of an object, PowerShell applies the first view that it finds.</span></span>

<span data-ttu-id="4188e-134">파일에서 뷰는 뷰의 `Format.ps1xml` 이름을 설명 하는 XML 태그 집합, 개체를 적용할 수 있는 개체의 형식, 열 머리글 및 뷰의 본문에 표시 되는 속성에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-134">In a `Format.ps1xml` file, a view is defined by a set of XML tags that describe the name of the view, the type of object to which it can be applied, the column headers, and the properties that are displayed in the body of the view.</span></span> <span data-ttu-id="4188e-135">파일의 형식은 `Format.ps1xml` 데이터가 사용자에 게 표시 되기 직전에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-135">The format in `Format.ps1xml` files is applied just before the data is presented to the user.</span></span>

## <a name="creating-new-formatps1xml-files"></a><span data-ttu-id="4188e-136">새 Format.ps1xml 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="4188e-136">Creating new Format.ps1xml files</span></span>

<span data-ttu-id="4188e-137">`.ps1xml`PowerShell과 함께 설치 되는 파일은 서식에 스크립트 블록을 포함할 수 있으므로 변조를 방지 하기 위해 디지털로 서명 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-137">The `.ps1xml` files that are installed with PowerShell are digitally signed to prevent tampering because the formatting can include script blocks.</span></span> <span data-ttu-id="4188e-138">기존 개체 뷰의 표시 형식을 변경 하거나 새 개체에 대 한 보기를 추가 하려면 고유한 `Format.ps1xml` 파일을 만든 다음 PowerShell 세션에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-138">To change the display format of an existing object view, or to add views for new objects, create your own `Format.ps1xml` files, and then add them to your PowerShell session.</span></span>

<span data-ttu-id="4188e-139">새 파일을 만들려면 기존 파일을 복사 `Format.ps1xml` 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-139">To create a new file, copy an existing `Format.ps1xml` file.</span></span> <span data-ttu-id="4188e-140">새 파일에는 아무 이름이 나 지정할 수 있지만 `.ps1xml` 파일 이름 확장명이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-140">The new file can have any name, but it must have a `.ps1xml` file name extension.</span></span> <span data-ttu-id="4188e-141">PowerShell에 액세스할 수 있는 모든 디렉터리에 새 파일을 저장할 수 있지만 PowerShell 설치 디렉터리 ( `$PSHOME` ) 또는 설치 디렉터리의 하위 디렉터리에 파일을 저장 하는 것이 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-141">You can place the new file in any directory that is accessible to PowerShell, but it's useful to place the files in the PowerShell installation directory (`$PSHOME`) or in a subdirectory of the installation directory.</span></span>

<span data-ttu-id="4188e-142">현재 뷰의 서식을 변경 하려면 서식 파일에서 뷰를 찾은 다음 태그를 사용 하 여 보기를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-142">To change the formatting of a current view, locate the view in the formatting file, and then use the tags to change the view.</span></span> <span data-ttu-id="4188e-143">새 개체 유형에 대 한 뷰를 만들려면 새 뷰를 만들거나 기존 뷰를 모델로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-143">To create a view for a new object type, create a new view, or use an existing view as a model.</span></span> <span data-ttu-id="4188e-144">태그는 다음 섹션에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-144">The tags are described in the next section.</span></span> <span data-ttu-id="4188e-145">그런 다음 파일의 다른 모든 뷰를 삭제 하 여 파일을 검사 하는 모든 사용자가 해당 변경 내용을 명확 하 게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-145">You can then delete all the other views in the file so that the changes are obvious to anyone examining the file.</span></span>

<span data-ttu-id="4188e-146">변경 내용을 저장 한 후 cmdlet을 사용 `Update-FormatData` 하 여 PowerShell 세션에 새 파일을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-146">After you save the changes, use the `Update-FormatData` cmdlet to add the new file to your PowerShell session.</span></span> <span data-ttu-id="4188e-147">기본 제공 파일에 정의 된 보기 보다 보기가 우선적으로 적용 되도록 하려면 **PrependPath** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-147">If you want your view to take precedence over a view defined in the built-in files, use the **PrependPath** parameter.</span></span>
<span data-ttu-id="4188e-148">`Update-FormatData` 현재 세션에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-148">`Update-FormatData` affects only the current session.</span></span> <span data-ttu-id="4188e-149">모든 이후 세션을 변경 하려면 `Update-FormatData` PowerShell 프로필에 명령을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-149">To make the change to all future sessions, add the `Update-FormatData` command to your PowerShell profile.</span></span>

### <a name="example-adding-calendar-data-to-culture-objects"></a><span data-ttu-id="4188e-150">예: culture 개체에 일정 데이터 추가</span><span class="sxs-lookup"><span data-stu-id="4188e-150">Example: Adding calendar data to culture objects</span></span>

<span data-ttu-id="4188e-151">이 예제에서는 현재 PowerShell 세션에서 cmdlet에 의해 생성 된 문화권 개체의 형식을 변경 하는 방법을 보여 **줍니다.** `Get-Culture`</span><span class="sxs-lookup"><span data-stu-id="4188e-151">This example shows how to change the formatting of the culture objects **System.Globalization.CultureInfo** generated by the `Get-Culture` cmdlet in the current PowerShell session.</span></span> <span data-ttu-id="4188e-152">이 예제의 명령은 culture 개체의 기본 테이블 뷰 표시에 **Calendar** 속성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-152">The commands in the example add the **Calendar** property to the default table view display of culture objects.</span></span>

<span data-ttu-id="4188e-153">첫 번째 단계는 `Format.ps1xml` culture 개체의 현재 보기를 포함 하는 파일을 찾는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-153">The first step is to find the `Format.ps1xml` file that contains the current view of the culture objects.</span></span> <span data-ttu-id="4188e-154">다음 `Select-String` 명령은 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-154">The following `Select-String` command finds the file:</span></span>

```powershell
$Parms = @{
  Path = "$PSHOME\*Format.ps1xml"
  Pattern = "System.Globalization.CultureInfo"
}

Select-String @Parms
```

```Output
C:\Windows\System32\WindowsPowerShell\v1.0\DotNetTypes.format.ps1xml:113:
     <Name>System.Globalization.CultureInfo</Name>
C:\Windows\System32\WindowsPowerShell\v1.0\DotNetTypes.format.ps1xml:115:
<TypeName>System.Globalization.CultureInfo</TypeName>
```

<span data-ttu-id="4188e-155">이 명령은 정의가 파일에 있음을 나타냅니다 `DotNetTypes.Format.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="4188e-155">This command reveals that the definition is in the `DotNetTypes.Format.ps1xml` file.</span></span>

<span data-ttu-id="4188e-156">다음 명령은 파일 내용을 새 파일인에 복사 `MyDotNetTypes.Format.ps1xml` 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-156">The next command copies the file contents to a new file, `MyDotNetTypes.Format.ps1xml`.</span></span>

```powershell
Copy-Item $PSHome\DotNetTypes.format.ps1xml MyDotNetTypes.Format.ps1xml
```

<span data-ttu-id="4188e-157">`MyDotNetTypes.Format.ps1xml`XML 또는 텍스트 편집기 (예: Visual Studio Code)에서 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-157">Open the `MyDotNetTypes.Format.ps1xml` file in any XML or text editor, such as Visual Studio Code.</span></span> <span data-ttu-id="4188e-158">**System.web** 개체 섹션을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-158">Find the **System.Globalization.CultureInfo** object section.</span></span> <span data-ttu-id="4188e-159">다음 XML은 **CultureInfo** 개체의 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-159">The following XML defines the views of the **CultureInfo** object.</span></span> <span data-ttu-id="4188e-160">개체에는 **TableControl** 보기만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-160">The object has only a **TableControl** view.</span></span>

```xml
<View>
  <Name>System.Globalization.CultureInfo</Name>
  <ViewSelectedBy>
    <TypeName>Deserialized.System.Globalization.CultureInfo</TypeName>
    <TypeName>System.Globalization.CultureInfo</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>
      <TableColumnHeader>
        <Width>16</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>16</Width>
      </TableColumnHeader>
    </TableHeaders>
    <TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
            <PropertyName>LCID</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>
  </TableControl>
</View>
```

<span data-ttu-id="4188e-161">열기 `<?xml>` , `<Configuration>` 및 `<ViewDefinitions>` 태그와 닫는 `<ViewDefinitions>` 및 `<Configuration>` 태그를 제외 하 고 파일의 나머지 부분을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-161">Delete the remainder of the file, except for the opening `<?xml>`, `<Configuration>`, and `<ViewDefinitions>` tags and the closing `<ViewDefinitions>` and `<Configuration>` tags.</span></span> <span data-ttu-id="4188e-162">디지털 서명이 있는 경우 사용자 지정 파일에서 삭제 `Format.ps1xml` 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-162">If there is a digital signature, delete it from your custom `Format.ps1xml`file.</span></span>

<span data-ttu-id="4188e-163">`MyDotNetTypes.Format.ps1xml`이제 파일이 다음 샘플과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-163">The `MyDotNetTypes.Format.ps1xml` file should now look like the following sample:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Configuration>
<ViewDefinitions>
<View>
  <Name>System.Globalization.CultureInfo</Name>
  <ViewSelectedBy>
    <TypeName>Deserialized.System.Globalization.CultureInfo</TypeName>
    <TypeName>System.Globalization.CultureInfo</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>
      <TableColumnHeader>
        <Width>16</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>16</Width>
      </TableColumnHeader>
      <TableColumnHeader/>
    </TableHeaders>
    <TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
            <PropertyName>LCID</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>
  </TableControl>
</View>
</ViewDefinitions>
</Configuration>
```

<span data-ttu-id="4188e-164">새 태그 집합을 추가 하 여 **Calendar** 속성의 새 열을 만듭니다 `<TableColumnHeader>` .</span><span class="sxs-lookup"><span data-stu-id="4188e-164">Create a new column for the **Calendar** property by adding a new set of `<TableColumnHeader>` tags.</span></span> <span data-ttu-id="4188e-165">**Calendar** 속성의 값은 long 일 수 있으므로 값으로 45 문자를 지정 `<Width>` 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-165">The value of the **Calendar** property can be long, so specify a value of 45 characters as the `<Width>`.</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>
    <Width>16</Width>
  </TableColumnHeader>
  <TableColumnHeader>
    <Width>16</Width>
  </TableColumnHeader>
  <TableColumnHeader>
    <Width>45</Width>
  </TableColumnHeader>
  <TableColumnHeader/>
</TableHeaders>
```

<span data-ttu-id="4188e-166">및 태그를 사용 하 여 테이블 행에 **일정** 에 대 한 새 열 항목을 추가 합니다 `<TableColumnItem>` `<PropertyName` .</span><span class="sxs-lookup"><span data-stu-id="4188e-166">Add a new column item for **Calendar** in the table rows using the `<TableColumnItem>` and `<PropertyName` tags:</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>
    <TableColumnItems>
      <TableColumnItem>
        <PropertyName>LCID</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName>Name</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName>Calendar</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName>DisplayName</PropertyName>
      </TableColumnItem>
    </TableColumnItems>
  </TableRowEntry>
</TableRowEntries>
```

<span data-ttu-id="4188e-167">파일을 저장하고 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-167">Save and close the file.</span></span> <span data-ttu-id="4188e-168">`Update-FormatData`를 사용 하 여 현재 PowerShell 세션에 새 서식 파일을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-168">Use `Update-FormatData` to add the new format file to the current PowerShell session.</span></span>

<span data-ttu-id="4188e-169">이 예에서는 **PrependPath** 매개 변수를 사용 하 여 새 파일을 원래 파일 보다 우선 순위가 더 높은 순서로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-169">This example uses the **PrependPath** parameter to place the new file in a higher precedence order than the original file.</span></span> <span data-ttu-id="4188e-170">자세한 내용은 [업데이트 FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4188e-170">For more information, see [Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData).</span></span>

```powershell
Update-FormatData -PrependPath $PSHOME\MyDotNetTypes.Format.ps1xml
```

<span data-ttu-id="4188e-171">변경을 테스트 하려면 `Get-Culture` **Calendar** 속성을 포함 하는 출력을 입력 하 고 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-171">To test the change, type `Get-Culture` and review the output that includes the **Calendar** property.</span></span>

```powershell
Get-Culture
```

```Output
LCID Name  Calendar                               DisplayName
---- ----  --------                               -----------
1033 en-US System.Globalization.GregorianCalendar English (United States)
```

## <a name="the-xml-in-formatps1xml-files"></a><span data-ttu-id="4188e-172">Format.ps1xml 파일의 XML</span><span class="sxs-lookup"><span data-stu-id="4188e-172">The XML in Format.ps1xml files</span></span>

<span data-ttu-id="4188e-173">GitHub의 PowerShell 소스 코드 리포지토리에서 전체 스키마 정의를 [.Xsd 형식](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Format.xsd) 으로 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-173">The full schema definition can be found in [Format.xsd](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Format.xsd) in the PowerShell source code repository on GitHub.</span></span>

<span data-ttu-id="4188e-174">각 파일의 **viewdefinitions** 섹션에는 `Format.ps1xml` `<View>` 각 뷰를 정의 하는 태그가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-174">The **ViewDefinitions** section of each `Format.ps1xml` file contains the `<View>` tags that define each view.</span></span> <span data-ttu-id="4188e-175">일반적인 `<View>` 태그는 다음 태그를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-175">A typical `<View>` tag includes the following tags:</span></span>

- <span data-ttu-id="4188e-176">`<Name>` 뷰의 이름을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-176">`<Name>` identifies the name of the view.</span></span>
- <span data-ttu-id="4188e-177">`<ViewSelectedBy>` 뷰가 적용 되는 개체 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-177">`<ViewSelectedBy>` specifies the object type or types to which the view applies.</span></span>
- <span data-ttu-id="4188e-178">`<GroupBy>` 뷰의 항목을 그룹으로 결합 하는 방법을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-178">`<GroupBy>` specifies how items in the view will be combined in groups.</span></span>
- <span data-ttu-id="4188e-179">`<TableControl>`,, 및에는 `<ListControl>` `<WideControl>` `<CustomControl>` 각 항목이 표시 되는 방법을 지정 하는 태그가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-179">`<TableControl>`, `<ListControl>`, `<WideControl>`, and `<CustomControl>` contain the tags that specify how each item will be displayed.</span></span>

### <a name="viewselectedby-tag"></a><span data-ttu-id="4188e-180">ViewSelectedBy 태그</span><span class="sxs-lookup"><span data-stu-id="4188e-180">ViewSelectedBy tag</span></span>

<span data-ttu-id="4188e-181">`<ViewSelectedBy>`태그는 `<TypeName>` 뷰가 적용 되는 각 개체 유형에 대 한 태그를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-181">The `<ViewSelectedBy>` tag can contain a `<TypeName>` tag for each object type to which the view applies.</span></span> <span data-ttu-id="4188e-182">또는 `<SelectionSetName>` 태그를 사용 하 여 다른 곳에 정의 된 선택 집합을 참조 하는 태그를 포함할 수 있습니다 `<SelectionSet>` .</span><span class="sxs-lookup"><span data-stu-id="4188e-182">Or, it can contain a `<SelectionSetName>` tag that references a selection set that is defined elsewhere by using a `<SelectionSet>` tag.</span></span>

### <a name="groupby-tag"></a><span data-ttu-id="4188e-183">GroupBy 태그</span><span class="sxs-lookup"><span data-stu-id="4188e-183">GroupBy tag</span></span>

<span data-ttu-id="4188e-184">태그에는 항목을 그룹화 하는 데 기준이 되는 `<GroupBy>` `<PropertyName>` 개체 속성을 지정 하는 태그가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-184">The `<GroupBy>` tag contains a `<PropertyName>` tag that specifies the object property by which items are to be grouped.</span></span> <span data-ttu-id="4188e-185">또한 `<Label>` 각 그룹의 레이블로 사용할 문자열을 지정 하는 태그 또는 `<CustomControlName>` 태그를 사용 하 여 다른 곳에서 정의 된 사용자 지정 컨트롤을 참조 하는 태그를 포함 `<Control>` 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-185">It also contains either a `<Label>` tag that specifies a string to be used as a label for each group or a `<CustomControlName>` tag that references a custom control defined elsewhere using a `<Control>` tag.</span></span> <span data-ttu-id="4188e-186">태그에는 태그 `<Control>` `<Name>` 와 태그가 포함 `<CustomControl>` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-186">The `<Control>` tag contains a `<Name>` tag and a `<CustomControl>` tag.</span></span>

### <a name="tablecontroltag"></a><span data-ttu-id="4188e-187">TableControlTag</span><span class="sxs-lookup"><span data-stu-id="4188e-187">TableControlTag</span></span>

<span data-ttu-id="4188e-188">태그에는 `<TableControl>` 일반적 `<TableHeaders>` 으로 `<TableRowEntries>` 테이블의 헤드 및 행에 대 한 서식을 정의 하는 및 태그가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-188">The `<TableControl>` tag typically contains `<TableHeaders>` and `<TableRowEntries>` tags that define the formatting for the table's heads and rows.</span></span> <span data-ttu-id="4188e-189">태그에는 `<TableHeaders>` 일반적으로, `<TableColumnHeader>` 및 태그가 포함 된 태그가 포함 되어 있습니다 `<Label>` `<Width>` `<Alignment>` .</span><span class="sxs-lookup"><span data-stu-id="4188e-189">The `<TableHeaders>` tag typically contains `<TableColumnHeader>` tags that contain `<Label>`, `<Width>`, and `<Alignment>` tags.</span></span> <span data-ttu-id="4188e-190">`<TableRowEntries>`태그에는 `<TableRowEntry>` 테이블의 각 행에 대 한 태그가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-190">The `<TableRowEntries>` tag contains `<TableRowEntry>` tags for each row in the table.</span></span> <span data-ttu-id="4188e-191">태그에는 `<TableRowEntry>` `<TableColumnItems>` `<TableColumnItem>` 행의 각 열에 대 한 태그가 포함 된 태그가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-191">The `<TableRowEntry>` tag contains a `<TableColumnItems>` tag that contains a `<TableColumnItem>` tag for each column in the row.</span></span> <span data-ttu-id="4188e-192">일반적으로 `<TableColumnItem>` 태그는 `<PropertyName>` 정의 된 위치에 표시 되는 개체 속성을 식별 하는 태그 또는 `<ScriptBlock>` 위치에 표시 될 결과를 계산 하는 스크립트 코드를 포함 하는 태그를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-192">Typically, the `<TableColumnItem>` tag contains either a `<PropertyName>` tag that identifies the object property to be displayed in the defined location, or a `<ScriptBlock>` tag that contains script code that calculates a result that is to be displayed in the location.</span></span>

> [!NOTE]
> <span data-ttu-id="4188e-193">계산 된 결과가 유용할 수 있는 위치에 스크립트 블록을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-193">Script blocks can also be used elsewhere in locations where calculated results can be useful.</span></span>

<span data-ttu-id="4188e-194">태그에는 `<TableColumnItem>` `<FormatString>` 속성 또는 계산 된 결과가 표시 되는 방법을 지정 하는 태그가 포함 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-194">The `<TableColumnItem>` tag can also contain a `<FormatString>` tag that specifies how the property or the calculated results will be displayed.</span></span>

### <a name="listcontrol-tag"></a><span data-ttu-id="4188e-195">이 listcontrol 태그</span><span class="sxs-lookup"><span data-stu-id="4188e-195">ListControl tag</span></span>

<span data-ttu-id="4188e-196">태그에는 `<ListControl>` 일반적으로 `<ListEntries>` 태그가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-196">The `<ListControl>` tag typically contains a `<ListEntries>` tag.</span></span> <span data-ttu-id="4188e-197">태그에 `<ListEntries>` 는 `<ListEntry>` 태그가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-197">The `<ListEntries>` tag contains a `<ListEntry>` tag.</span></span> <span data-ttu-id="4188e-198">태그에 `<ListEntry>` 는 `<ListItems>` 태그가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-198">The `<ListEntry>` tag contains a `<ListItems>` tag.</span></span> <span data-ttu-id="4188e-199">태그는 태그를 포함 하 `<ListItems>` 는 태그를 포함 합니다 `<ListItem>` `<PropertyName>` .</span><span class="sxs-lookup"><span data-stu-id="4188e-199">The `<ListItems>` tag contains `<ListItem>` tags, which contain `<PropertyName>` tags.</span></span> <span data-ttu-id="4188e-200">`<PropertyName>`태그는 목록의 지정 된 위치에 표시 되는 개체 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-200">The `<PropertyName>` tags specify the object property to be displayed at the specified location in the list.</span></span> <span data-ttu-id="4188e-201">선택 집합을 사용 하 여 뷰 선택을 정의 하는 경우 `<ListControl>` 및 `<ListEntry>` 태그는 하나 이상의 `<EntrySelectedBy>` 태그를 포함 하는 태그를 포함할 수도 있습니다 `<TypeName>` .</span><span class="sxs-lookup"><span data-stu-id="4188e-201">If the view selection is defined using a selection set, the `<ListControl>` and `<ListEntry>` tags can also contain an `<EntrySelectedBy>` tag that contains one or more `<TypeName>` tags.</span></span> <span data-ttu-id="4188e-202">이러한 `<TypeName>` 태그는 태그가 표시할 개체 유형을 지정 합니다 `<ListControl>` .</span><span class="sxs-lookup"><span data-stu-id="4188e-202">These `<TypeName>` tags specify the object type that the `<ListControl>` tag is intended to display.</span></span>

### <a name="widecontrol-tag"></a><span data-ttu-id="4188e-203">WideControl 태그</span><span class="sxs-lookup"><span data-stu-id="4188e-203">WideControl tag</span></span>

<span data-ttu-id="4188e-204">태그에는 `<WideControl>` 일반적으로 `<WideEntries>` 태그가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-204">The `<WideControl>` tag typically contains a `<WideEntries>` tag.</span></span> <span data-ttu-id="4188e-205">`<WideEntries>`태그는 하나 이상의 태그를 포함 합니다 `<WideEntry>` .</span><span class="sxs-lookup"><span data-stu-id="4188e-205">The `<WideEntries>` tag contains one or more `<WideEntry>` tags.</span></span> <span data-ttu-id="4188e-206">태그에는 `<WideEntry>` 일반적으로 `<PropertyName>` 뷰의 지정 된 위치에 표시할 속성을 지정 하는 태그가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-206">A `<WideEntry>` tag typically contains a `<PropertyName>` tag that specifies the property to be displayed at the specified location in the view.</span></span> <span data-ttu-id="4188e-207">태그에는 `<PropertyName>` `<FormatString>` 속성이 표시 되는 방법을 지정 하는 태그가 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-207">The `<PropertyName>` tag can contain a `<FormatString>` tag that specifies how the property is to be displayed.</span></span>

### <a name="customcontrol-tag"></a><span data-ttu-id="4188e-208">CustomControl 태그</span><span class="sxs-lookup"><span data-stu-id="4188e-208">CustomControl tag</span></span>

<span data-ttu-id="4188e-209">태그를 사용 하 여 `<CustomControl>` 형식을 정의 하는 스크립트 블록을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-209">The `<CustomControl>` tag lets you use a script block to define a format.</span></span> <span data-ttu-id="4188e-210">태그에는 `<CustomControl>` 일반적으로 `<CustomEntries>` 여러 태그를 포함 하는 태그가 포함 되어 있습니다 `<CustomEntry>` .</span><span class="sxs-lookup"><span data-stu-id="4188e-210">A `<CustomControl>` tag typically contains a `<CustomEntries>` tag that contains multiple `<CustomEntry>` tags.</span></span> <span data-ttu-id="4188e-211">각 `<CustomEntry>` 태그에는 `<CustomItem>` `<Text>` ,, `<Indentation>` `<ExpressionBinding>` 및 태그를 포함 하 여 보기에서 지정 된 위치의 내용과 서식을 지정 하는 다양 한 태그를 포함할 수 있는 태그가 포함 되어 있습니다 `<NewLine>` .</span><span class="sxs-lookup"><span data-stu-id="4188e-211">Each `<CustomEntry>` tag contains a `<CustomItem>` tag that can contain a variety of tags that specify contents and formatting of the specified location in the view, including `<Text>`, `<Indentation>`, `<ExpressionBinding>`, and `<NewLine>` tags.</span></span>

## <a name="default-displays-in-typesps1xml"></a><span data-ttu-id="4188e-212">Types.ps1xml에 기본 표시</span><span class="sxs-lookup"><span data-stu-id="4188e-212">Default displays in Types.ps1xml</span></span>

<span data-ttu-id="4188e-213">일부 기본 개체 형식의 기본 표시는 디렉터리의 파일에 정의 되어 있습니다 `Types.ps1xml` `$PSHOME` .</span><span class="sxs-lookup"><span data-stu-id="4188e-213">The default displays of some basic object types are defined in the `Types.ps1xml` file in the `$PSHOME` directory.</span></span> <span data-ttu-id="4188e-214">노드 이름은 **Psstandardmembers** 이며 하위 노드는 다음 태그 중 하나를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-214">The nodes are named **PsStandardMembers** , and the subnodes use one of the following tags:</span></span>

- `<DefaultDisplayProperty>`
- `<DefaultDisplayPropertySet>`
- `<DefaultKeyPropertySet>`

<span data-ttu-id="4188e-215">자세한 내용은 [about_Types.ps1xml](about_Types.ps1xml.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4188e-215">For more information, see [about_Types.ps1xml](about_Types.ps1xml.md).</span></span>

## <a name="tracing-formatps1xml-file-use"></a><span data-ttu-id="4188e-216">Xml 파일 사용 추적 Format.ps1</span><span class="sxs-lookup"><span data-stu-id="4188e-216">Tracing Format.ps1xml file use</span></span>

<span data-ttu-id="4188e-217">파일 로드 또는 응용 프로그램에서 오류를 검색 하려면 `Format.ps1xml` `Trace-Command` 다음 형식 구성 요소 중 하나를 **Name** 매개 변수 값으로 사용 하 여 cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-217">To detect errors in the loading or application of `Format.ps1xml` files, use the `Trace-Command` cmdlet with any of the following format components as the value of the **Name** parameter:</span></span>

- <span data-ttu-id="4188e-218">FormatFileLoading</span><span class="sxs-lookup"><span data-stu-id="4188e-218">FormatFileLoading</span></span>
- <span data-ttu-id="4188e-219">FormatViewBinding</span><span class="sxs-lookup"><span data-stu-id="4188e-219">FormatViewBinding</span></span>

<span data-ttu-id="4188e-220">자세한 내용은 [Trace-Command](xref:Microsoft.PowerShell.Utility.Trace-Command) 및 [TraceSource](xref:Microsoft.PowerShell.Utility.Get-TraceSource)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4188e-220">For more information, see [Trace-Command](xref:Microsoft.PowerShell.Utility.Trace-Command) and [Get-TraceSource](xref:Microsoft.PowerShell.Utility.Get-TraceSource).</span></span>

## <a name="signing-a-formatps1xml-file"></a><span data-ttu-id="4188e-221">Format.ps1xml 파일에 서명</span><span class="sxs-lookup"><span data-stu-id="4188e-221">Signing a Format.ps1xml file</span></span>

<span data-ttu-id="4188e-222">파일의 사용자를 보호 하려면 `Format.ps1xml` 디지털 서명을 사용 하 여 파일에 서명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-222">To protect the users of your `Format.ps1xml` file, sign the file using a digital signature.</span></span> <span data-ttu-id="4188e-223">자세한 내용은 [about_Signing](about_Signing.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4188e-223">For more information, see [about_Signing](about_Signing.md).</span></span>

## <a name="sample-xml-for-a-format-table-custom-view"></a><span data-ttu-id="4188e-224">Format-Table 사용자 지정 보기에 대 한 샘플 XML</span><span class="sxs-lookup"><span data-stu-id="4188e-224">Sample XML for a Format-Table custom view</span></span>

<span data-ttu-id="4188e-225">다음 샘플에서는 `Format-Table` 에서 만든 **System.io.directoryinfo** 및 **system.object** 개체에 대 한 사용자 지정 뷰를 만듭니다 `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="4188e-225">The following sample creates a `Format-Table` custom view for the **System.IO.DirectoryInfo** and **System.IO.FileInfo** objects created by `Get-ChildItem`.</span></span> <span data-ttu-id="4188e-226">사용자 지정 보기의 이름을 **mygciview** 로 지정 하 고 테이블에 **CreationTime** 열을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-226">The custom view is named **mygciview** and adds the **CreationTime** column to the table.</span></span>

<span data-ttu-id="4188e-227">사용자 지정 보기는 `FileSystem.Format.ps1xml` PowerShell 5.1에 저장 된 파일의 편집 된 버전에서 만들어집니다 `$PSHOME` .</span><span class="sxs-lookup"><span data-stu-id="4188e-227">The custom view is created from an edited version of the `FileSystem.Format.ps1xml` file that's stored in `$PSHOME` on PowerShell 5.1.</span></span>

<span data-ttu-id="4188e-228">사용자 지정 파일을 저장 한 후에는를 `.ps1xml` 사용 `Update-FormatData` 하 여 PowerShell 세션에 뷰를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-228">After your custom `.ps1xml` file is saved, use `Update-FormatData` to include the view in a PowerShell session.</span></span> <span data-ttu-id="4188e-229">이 예에서는 사용자 지정 뷰에서 테이블 형식을 사용 해야 합니다. 그렇지 않으면이 `Format-Table` 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-229">For this example, the custom view must use the table format, otherwise, `Format-Table` fails.</span></span>

<span data-ttu-id="4188e-230">`Format-Table` **View** 매개 변수와 함께 사용 하 여 사용자 지정 보기의 이름을 지정 하 고 테이블의 출력 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-230">Use `Format-Table` with the **View** parameter to specify the custom view's name and format the table's output.</span></span> <span data-ttu-id="4188e-231">명령이 실행 되는 방법에 대 한 예는 [서식 테이블](xref:Microsoft.PowerShell.Utility.Format-Table)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="4188e-231">For an example of how the command is run, see [Format-Table](xref:Microsoft.PowerShell.Utility.Format-Table).</span></span>

```powershell
$Parms = @{
  Path = "$PSHOME\*Format.ps1xml"
  Pattern = "System.IO.DirectoryInfo"
}
Select-String @Parms
Copy-Item $PSHome\FileSystem.format.ps1xml .\MyFileSystem.Format.ps1xml
Update-FormatData -PrependPath $PSHOME\Format\MyFileSystem.Format.ps1xml
```

> [!NOTE]
> <span data-ttu-id="4188e-232">줄 너비 제한 내에서 XML 샘플을 맞추려면 일부 들여쓰기를 압축 하 고 코드에서 줄 바꿈을 사용 해야 했습니다.</span><span class="sxs-lookup"><span data-stu-id="4188e-232">To fit the XML sample within line width limitations, it was necessary to compress some indentation and use line breaks within the code.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Configuration>
    <SelectionSets>
        <SelectionSet>
            <Name>FileSystemTypes</Name>
            <Types>
                <TypeName>System.IO.DirectoryInfo</TypeName>
                <TypeName>System.IO.FileInfo</TypeName>
            </Types>
        </SelectionSet>
    </SelectionSets>
<Controls>
<Control>
<Name>FileSystemTypes-GroupingFormat</Name>
<CustomControl>
 <CustomEntries>
  <CustomEntry>
    <CustomItem>
    <Frame>
    <LeftIndent>4</LeftIndent>
    <CustomItem>
    <Text AssemblyName="System.Management.Automation"
    BaseName="FileSystemProviderStrings"
    ResourceId="DirectoryDisplayGrouping"/>
    <ExpressionBinding>
     <ScriptBlock>
      $_.PSParentPath.Replace("Microsoft.PowerShell.Core\FileSystem::", "")
     </ScriptBlock>
    </ExpressionBinding>
    <NewLine/>
    </CustomItem>
    </Frame>
    </CustomItem>
    </CustomEntry>
 </CustomEntries>
</CustomControl>
</Control>
</Controls>
<ViewDefinitions>
    <View>
    <Name>mygciview</Name>
    <ViewSelectedBy>
        <SelectionSetName>FileSystemTypes</SelectionSetName>
    </ViewSelectedBy>
    <GroupBy>
      <PropertyName>PSParentPath</PropertyName>
      <CustomControlName>FileSystemTypes-GroupingFormat</CustomControlName>
    </GroupBy>
        <TableControl>
            <TableHeaders>
                <TableColumnHeader>
                    <Label>Mode</Label>
                    <Width>7</Width>
                    <Alignment>left</Alignment>
                </TableColumnHeader>
                <TableColumnHeader>
                    <Label>LastWriteTime</Label>
                    <Width>25</Width>
                    <Alignment>right</Alignment>
                </TableColumnHeader>
                <TableColumnHeader>
                    <Label>CreationTime</Label>
                    <Width>25</Width>
                    <Alignment>right</Alignment>
                </TableColumnHeader>
                <TableColumnHeader>
                    <Label>Length</Label>
                    <Width>14</Width>
                    <Alignment>right</Alignment>
                </TableColumnHeader>
                <TableColumnHeader/>
            </TableHeaders>
            <TableRowEntries>
                <TableRowEntry>
                    <Wrap/>
                    <TableColumnItems>
                        <TableColumnItem>
                            <PropertyName>Mode</PropertyName>
                        </TableColumnItem>
                        <TableColumnItem>
                            <ScriptBlock>
                                [String]::Format("{0,10}  {1,8}",
                                    $_.LastWriteTime.ToString("d"),
                                    $_.LastWriteTime.ToString("t"))
                            </ScriptBlock>
                        </TableColumnItem>
                        <TableColumnItem>
                            <ScriptBlock>
                                [String]::Format("{0,10}  {1,8}",
                                    $_.CreationTime.ToString("d"),
                                    $_.LastWriteTime.ToString("t"))
                            </ScriptBlock>
                        </TableColumnItem>
                        <TableColumnItem>
                        <PropertyName>Length</PropertyName>
                        </TableColumnItem>
                        <TableColumnItem>
                            <PropertyName>Name</PropertyName>
                        </TableColumnItem>
                    </TableColumnItems>
                </TableRowEntry>
            </TableRowEntries>
        </TableControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

## <a name="see-also"></a><span data-ttu-id="4188e-233">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4188e-233">See also</span></span>

[<span data-ttu-id="4188e-234">Export-FormatData</span><span class="sxs-lookup"><span data-stu-id="4188e-234">Export-FormatData</span></span>](xref:Microsoft.PowerShell.Utility.Export-FormatData)

[<span data-ttu-id="4188e-235">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="4188e-235">Get-FormatData</span></span>](xref:Microsoft.PowerShell.Utility.Get-FormatData)

[<span data-ttu-id="4188e-236">Get-TraceSource</span><span class="sxs-lookup"><span data-stu-id="4188e-236">Get-TraceSource</span></span>](xref:Microsoft.PowerShell.Utility.Get-TraceSource)

[<span data-ttu-id="4188e-237">형식 스키마 XML 참조</span><span class="sxs-lookup"><span data-stu-id="4188e-237">Format Schema XML Reference</span></span>](/powershell/scripting/developer/format/format-schema-xml-reference)

[<span data-ttu-id="4188e-238">Trace-Command</span><span class="sxs-lookup"><span data-stu-id="4188e-238">Trace-Command</span></span>](xref:Microsoft.PowerShell.Utility.Trace-Command)

[<span data-ttu-id="4188e-239">Update-FormatData</span><span class="sxs-lookup"><span data-stu-id="4188e-239">Update-FormatData</span></span>](xref:Microsoft.PowerShell.Utility.Update-FormatData)

[<span data-ttu-id="4188e-240">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="4188e-240">Writing a PowerShell Formatting File</span></span>](/powershell/scripting/developer/format/writing-a-powershell-formatting-file)
