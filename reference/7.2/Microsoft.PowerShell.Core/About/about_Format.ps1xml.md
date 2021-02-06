---
description: PowerShell 6부터 개체의 기본 뷰는 PowerShell 소스 코드에서 정의 됩니다.  사용자 고유의 `Format.ps1xml` 파일을 만들어 개체 표시를 변경 하거나 PowerShell에서 만든 새 개체 유형에 대 한 기본 표시를 정의할 수 있습니다.
Locale: en-US
ms.date: 11/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_format.ps1xml?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Format.ps1xml
ms.openlocfilehash: 56bac204e33c39aa6192da9e6a899f00b0a4a743
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600834"
---
# <a name="about-formatps1xml"></a><span data-ttu-id="4ad62-104">Format.ps1xml 정보</span><span class="sxs-lookup"><span data-stu-id="4ad62-104">About Format.ps1xml</span></span>

## <a name="short-description"></a><span data-ttu-id="4ad62-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="4ad62-105">Short description</span></span>

<span data-ttu-id="4ad62-106">PowerShell 6부터 개체의 기본 뷰는 PowerShell 소스 코드에서 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-106">Beginning in PowerShell 6, the default views for objects are defined in PowerShell source code.</span></span>

<span data-ttu-id="4ad62-107">사용자 고유의 `Format.ps1xml` 파일을 만들어 개체 표시를 변경 하거나 PowerShell에서 만든 새 개체 유형에 대 한 기본 표시를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-107">You can create your own `Format.ps1xml` files to change the display of objects or to define default displays for new object types that you create in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="4ad62-108">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-108">Long description</span></span>

<span data-ttu-id="4ad62-109">PowerShell 6 부터는 기본 보기가 PowerShell 소스 코드에 정의 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-109">Beginning in PowerShell 6, the default views are defined in PowerShell source code.</span></span> <span data-ttu-id="4ad62-110">Powershell `Format.ps1xml` 5.1 이전 버전의 파일은 powershell 6 이상 버전에 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-110">The `Format.ps1xml` files from PowerShell 5.1 and earlier versions don't exist in PowerShell 6 and later versions.</span></span>

<span data-ttu-id="4ad62-111">Powershell 소스 코드는 PowerShell 콘솔에서 개체의 기본 표시를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-111">The PowerShell source code defines the default display of objects in the PowerShell console.</span></span> <span data-ttu-id="4ad62-112">사용자 고유의 `Format.ps1xml` 파일을 만들어 개체 표시를 변경 하거나 PowerShell에서 만든 새 개체 유형에 대 한 기본 표시를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-112">You can create your own `Format.ps1xml` files to change the display of objects or to define default displays for new object types that you create in PowerShell.</span></span>

<span data-ttu-id="4ad62-113">PowerShell에서 개체를 표시 하면 구조화 된 서식 파일의 데이터를 사용 하 여 개체의 기본 표시를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-113">When PowerShell displays an object, it uses the data in structured formatting files to determine the default display of the object.</span></span> <span data-ttu-id="4ad62-114">서식 파일의 데이터는 개체가 테이블이 나 목록에서 렌더링 되는지 여부를 결정 하 고 기본적으로 표시 되는 속성을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-114">The data in the formatting files determines whether the object is rendered in a table or in a list, and it determines which properties are displayed by default.</span></span>

<span data-ttu-id="4ad62-115">서식 지정은 표시에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-115">The formatting affects the display only.</span></span> <span data-ttu-id="4ad62-116">파이프라인으로 전달 되는 개체 속성이 나 전달 되는 방법에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-116">It doesn't affect which object properties are passed down the pipeline or how they're passed.</span></span> <span data-ttu-id="4ad62-117">`Format.ps1xml` 파일은 해시 테이블에 대 한 출력 형식을 사용자 지정 하는 데 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-117">`Format.ps1xml` files can't be used to customize the output format for hash tables.</span></span>

<span data-ttu-id="4ad62-118">`.ps1xml`서식 파일은 각 개체의 네 가지 뷰를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-118">A `.ps1xml` formatting file can define four different views of each object:</span></span>

- <span data-ttu-id="4ad62-119">테이블</span><span class="sxs-lookup"><span data-stu-id="4ad62-119">Table</span></span>
- <span data-ttu-id="4ad62-120">목록</span><span class="sxs-lookup"><span data-stu-id="4ad62-120">List</span></span>
- <span data-ttu-id="4ad62-121">넓게</span><span class="sxs-lookup"><span data-stu-id="4ad62-121">Wide</span></span>
- <span data-ttu-id="4ad62-122">사용자 지정</span><span class="sxs-lookup"><span data-stu-id="4ad62-122">Custom</span></span>

<span data-ttu-id="4ad62-123">예를 들어 `Get-ChildItem` 명령의 출력이 명령으로 파이프 되 면는 `Format-List` `Format-List` 소스 코드에 정의 된 목록 뷰를 사용 하 여 파일 및 폴더 개체를 목록으로 표시 하는 방법을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-123">For example, when the output of a `Get-ChildItem` command is piped to a `Format-List` command, `Format-List` uses the list view defined in the source code to determine how to display the file and folder objects as a list.</span></span>

<span data-ttu-id="4ad62-124">서식 파일에 개체의 뷰가 두 개 이상 포함 된 경우 PowerShell은 찾은 첫 번째 뷰를 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-124">When a formatting file includes more than one view of an object, PowerShell applies the first view that it finds.</span></span>

<span data-ttu-id="4ad62-125">사용자 지정 파일에서 뷰는 뷰의 `Format.ps1xml` 이름을 설명 하는 XML 태그 집합, 개체를 적용할 수 있는 개체의 형식, 열 머리글 및 뷰의 본문에 표시 되는 속성에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-125">In a custom `Format.ps1xml` file, a view is defined by a set of XML tags that describe the name of the view, the type of object to which it can be applied, the column headers, and the properties that are displayed in the body of the view.</span></span> <span data-ttu-id="4ad62-126">파일의 형식은 `Format.ps1xml` 데이터가 사용자에 게 표시 되기 직전에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-126">The format in `Format.ps1xml` files is applied just before the data is presented to the user.</span></span>

## <a name="creating-new-formatps1xml-files"></a><span data-ttu-id="4ad62-127">새 Format.ps1xml 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="4ad62-127">Creating new Format.ps1xml files</span></span>

<span data-ttu-id="4ad62-128">기존 개체 뷰의 표시 형식을 변경 하거나 새 개체에 대 한 보기를 추가 하려면 고유한 `Format.ps1xml` 파일을 만든 다음 PowerShell 세션에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-128">To change the display format of an existing object view, or to add views for new objects, create your own `Format.ps1xml` files, and then add them to your PowerShell session.</span></span>

<span data-ttu-id="4ad62-129">`Format.ps1xml`사용자 지정 보기를 정의 하는 파일을 만들려면 [Get formatdata](xref:Microsoft.PowerShell.Utility.Get-FormatData) 및 [Export-formatdata](xref:Microsoft.PowerShell.Utility.Export-FormatData) cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-129">To create a `Format.ps1xml` file to define a custom view, use the [Get-FormatData](xref:Microsoft.PowerShell.Utility.Get-FormatData) and [Export-FormatData](xref:Microsoft.PowerShell.Utility.Export-FormatData) cmdlets.</span></span> <span data-ttu-id="4ad62-130">텍스트 편집기를 사용 하 여 파일을 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-130">Use a text editor to edit the file.</span></span> <span data-ttu-id="4ad62-131">이 파일은의 하위 디렉터리와 같이 PowerShell에서 액세스할 수 있는 모든 디렉터리에 저장할 수 있습니다 `$HOME` .</span><span class="sxs-lookup"><span data-stu-id="4ad62-131">The file can be saved to any directory that PowerShell can access, such as a subdirectory of `$HOME`.</span></span>

<span data-ttu-id="4ad62-132">현재 뷰의 서식을 변경 하려면 서식 파일에서 뷰를 찾은 다음 태그를 사용 하 여 보기를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-132">To change the formatting of a current view, locate the view in the formatting file, and then use the tags to change the view.</span></span> <span data-ttu-id="4ad62-133">새 개체 유형에 대 한 뷰를 만들려면 새 뷰를 만들거나 기존 뷰를 모델로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-133">To create a view for a new object type, create a new view, or use an existing view as a model.</span></span> <span data-ttu-id="4ad62-134">태그는 다음 섹션에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-134">The tags are described in the next section.</span></span> <span data-ttu-id="4ad62-135">그런 다음 파일의 다른 모든 뷰를 삭제 하 여 파일을 검사 하는 모든 사용자가 해당 변경 내용을 명확 하 게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-135">You can then delete all the other views in the file so that the changes are obvious to anyone examining the file.</span></span>

<span data-ttu-id="4ad62-136">변경 내용을 저장 한 후에는 [업데이트 FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData) 를 사용 하 여 PowerShell 세션에 새 파일을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-136">After you save the changes, use the [Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData) to add the new file to your PowerShell session.</span></span> <span data-ttu-id="4ad62-137">기본 제공 파일에 정의 된 보기 보다 보기가 우선적으로 적용 되도록 하려면 **PrependPath** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-137">If you want your view to take precedence over a view defined in the built-in files, use the **PrependPath** parameter.</span></span> <span data-ttu-id="4ad62-138">`Update-FormatData` 현재 세션에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-138">`Update-FormatData` affects only the current session.</span></span> <span data-ttu-id="4ad62-139">모든 이후 세션을 변경 하려면 `Update-FormatData` PowerShell 프로필에 명령을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-139">To make the change to all future sessions, add the `Update-FormatData` command to your PowerShell profile.</span></span>

### <a name="example-add-calendar-data-to-culture-objects"></a><span data-ttu-id="4ad62-140">예: culture 개체에 일정 데이터 추가</span><span class="sxs-lookup"><span data-stu-id="4ad62-140">Example: Add calendar data to culture objects</span></span>

<span data-ttu-id="4ad62-141">이 예제에서는 현재 PowerShell 세션에서 cmdlet에 의해 생성 된 문화권 개체의 형식을 변경 하는 방법을 보여 **줍니다.** `Get-Culture`</span><span class="sxs-lookup"><span data-stu-id="4ad62-141">This example shows how to change the formatting of the culture objects **System.Globalization.CultureInfo** generated by the `Get-Culture` cmdlet in the current PowerShell session.</span></span> <span data-ttu-id="4ad62-142">이 예제의 명령은 culture 개체의 기본 테이블 뷰 표시에 **Calendar** 속성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-142">The commands in the example add the **Calendar** property to the default table view display of culture objects.</span></span>

<span data-ttu-id="4ad62-143">시작 하려면 소스 코드 파일에서 형식 데이터를 가져오고 `Format.ps1xml` 문화권 개체의 현재 뷰를 포함 하는 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-143">To begin, get the format data from the source code file and create a `Format.ps1xml` file that contains the current view of the culture objects.</span></span>

```powershell
Get-FormatData -TypeName System.Globalization.CultureInfo |
  Export-FormatData -Path $HOME\Format\CultureInfo.Format.ps1xml
```

<span data-ttu-id="4ad62-144">`CultureInfo.Format.ps1xml`XML 또는 텍스트 편집기 (예: Visual Studio Code)에서 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-144">Open the `CultureInfo.Format.ps1xml` file in any XML or text editor, such as Visual Studio Code.</span></span> <span data-ttu-id="4ad62-145">다음 XML은 **CultureInfo** 개체의 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-145">The following XML defines the views of the **CultureInfo** object.</span></span>

<span data-ttu-id="4ad62-146">`CultureInfo.Format.ps1xml`파일은 다음 샘플과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-146">The `CultureInfo.Format.ps1xml` file should look like the following sample:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<Configuration>
  <ViewDefinitions>
    <View>
      <Name>System.Globalization.CultureInfo</Name>
      <ViewSelectedBy>
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
          <TableColumnHeader />
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

<span data-ttu-id="4ad62-147">새 태그 집합을 추가 하 여 **Calendar** 속성의 새 열을 만듭니다 `<TableColumnHeader>` .</span><span class="sxs-lookup"><span data-stu-id="4ad62-147">Create a new column for the **Calendar** property by adding a new set of `<TableColumnHeader>` tags.</span></span> <span data-ttu-id="4ad62-148">**Calendar** 속성의 값은 long 일 수 있으므로 값으로 45 문자를 지정 `<Width>` 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-148">The value of the **Calendar** property can be long, so specify a value of 45 characters as the `<Width>`.</span></span>

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

<span data-ttu-id="4ad62-149">및 태그를 사용 하 여 테이블 행에 **일정** 에 대 한 새 열 항목을 추가 합니다 `<TableColumnItem>` `<PropertyName` .</span><span class="sxs-lookup"><span data-stu-id="4ad62-149">Add a new column item for **Calendar** in the table rows using the `<TableColumnItem>` and `<PropertyName` tags:</span></span>

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

<span data-ttu-id="4ad62-150">파일을 저장하고 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-150">Save and close the file.</span></span> <span data-ttu-id="4ad62-151">`Update-FormatData`를 사용 하 여 현재 PowerShell 세션에 새 서식 파일을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-151">Use `Update-FormatData` to add the new format file to the current PowerShell session.</span></span>

<span data-ttu-id="4ad62-152">이 예에서는 **PrependPath** 매개 변수를 사용 하 여 새 파일을 원래 파일 보다 우선 순위가 더 높은 순서로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-152">This example uses the **PrependPath** parameter to place the new file in a higher precedence order than the original file.</span></span> <span data-ttu-id="4ad62-153">자세한 내용은 [업데이트 FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4ad62-153">For more information, see [Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData).</span></span>

```powershell
Update-FormatData -PrependPath $HOME\Format\CultureInfo.Format.ps1xml
```

<span data-ttu-id="4ad62-154">변경을 테스트 하려면 `Get-Culture` **Calendar** 속성을 포함 하는 출력을 입력 하 고 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-154">To test the change, type `Get-Culture` and review the output that includes the **Calendar** property.</span></span>

```powershell
Get-Culture
```

```Output
LCID  Name   Calendar                                DisplayName
----  ----   --------                                -----------
1033  en-US  System.Globalization.GregorianCalendar  English (United States)
```

## <a name="the-xml-in-formatps1xml-files"></a><span data-ttu-id="4ad62-155">Format.ps1xml 파일의 XML</span><span class="sxs-lookup"><span data-stu-id="4ad62-155">The XML in Format.ps1xml files</span></span>

<span data-ttu-id="4ad62-156">GitHub의 PowerShell 소스 코드 리포지토리에서 전체 스키마 정의를 [.Xsd 형식](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Format.xsd) 으로 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-156">The full schema definition can be found in [Format.xsd](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Format.xsd) in the PowerShell source code repository on GitHub.</span></span>

<span data-ttu-id="4ad62-157">각 파일의 **viewdefinitions** 섹션에는 `Format.ps1xml` `<View>` 각 뷰를 정의 하는 태그가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-157">The **ViewDefinitions** section of each `Format.ps1xml` file contains the `<View>` tags that define each view.</span></span> <span data-ttu-id="4ad62-158">일반적인 `<View>` 태그는 다음 태그를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-158">A typical `<View>` tag includes the following tags:</span></span>

- <span data-ttu-id="4ad62-159">`<Name>` 뷰의 이름을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-159">`<Name>` identifies the name of the view.</span></span>
- <span data-ttu-id="4ad62-160">`<ViewSelectedBy>` 뷰가 적용 되는 개체 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-160">`<ViewSelectedBy>` specifies the object type or types to which the view applies.</span></span>
- <span data-ttu-id="4ad62-161">`<GroupBy>` 뷰의 항목을 그룹으로 결합 하는 방법을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-161">`<GroupBy>` specifies how items in the view will be combined in groups.</span></span>
- <span data-ttu-id="4ad62-162">`<TableControl>`,, 및에는 `<ListControl>` `<WideControl>` `<CustomControl>` 각 항목이 표시 되는 방법을 지정 하는 태그가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-162">`<TableControl>`, `<ListControl>`, `<WideControl>`, and `<CustomControl>` contain the tags that specify how each item will be displayed.</span></span>

### <a name="viewselectedby-tag"></a><span data-ttu-id="4ad62-163">ViewSelectedBy 태그</span><span class="sxs-lookup"><span data-stu-id="4ad62-163">ViewSelectedBy tag</span></span>

<span data-ttu-id="4ad62-164">`<ViewSelectedBy>`태그는 `<TypeName>` 뷰가 적용 되는 각 개체 유형에 대 한 태그를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-164">The `<ViewSelectedBy>` tag can contain a `<TypeName>` tag for each object type to which the view applies.</span></span> <span data-ttu-id="4ad62-165">또는 `<SelectionSetName>` 태그를 사용 하 여 다른 곳에 정의 된 선택 집합을 참조 하는 태그를 포함할 수 있습니다 `<SelectionSet>` .</span><span class="sxs-lookup"><span data-stu-id="4ad62-165">Or, it can contain a `<SelectionSetName>` tag that references a selection set that is defined elsewhere by using a `<SelectionSet>` tag.</span></span>

### <a name="groupby-tag"></a><span data-ttu-id="4ad62-166">GroupBy 태그</span><span class="sxs-lookup"><span data-stu-id="4ad62-166">GroupBy tag</span></span>

<span data-ttu-id="4ad62-167">태그에는 항목을 그룹화 하는 데 기준이 되는 `<GroupBy>` `<PropertyName>` 개체 속성을 지정 하는 태그가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-167">The `<GroupBy>` tag contains a `<PropertyName>` tag that specifies the object property by which items are to be grouped.</span></span> <span data-ttu-id="4ad62-168">또한 `<Label>` 각 그룹의 레이블로 사용할 문자열을 지정 하는 태그 또는 `<CustomControlName>` 태그를 사용 하 여 다른 곳에서 정의 된 사용자 지정 컨트롤을 참조 하는 태그를 포함 `<Control>` 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-168">It also contains either a `<Label>` tag that specifies a string to be used as a label for each group or a `<CustomControlName>` tag that references a custom control defined elsewhere using a `<Control>` tag.</span></span> <span data-ttu-id="4ad62-169">태그에는 태그 `<Control>` `<Name>` 와 태그가 포함 `<CustomControl>` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-169">The `<Control>` tag contains a `<Name>` tag and a `<CustomControl>` tag.</span></span>

### <a name="tablecontroltag"></a><span data-ttu-id="4ad62-170">TableControlTag</span><span class="sxs-lookup"><span data-stu-id="4ad62-170">TableControlTag</span></span>

<span data-ttu-id="4ad62-171">태그에는 `<TableControl>` 일반적 `<TableHeaders>` 으로 `<TableRowEntries>` 테이블의 헤드 및 행에 대 한 서식을 정의 하는 및 태그가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-171">The `<TableControl>` tag typically contains `<TableHeaders>` and `<TableRowEntries>` tags that define the formatting for the table's heads and rows.</span></span> <span data-ttu-id="4ad62-172">태그에는 `<TableHeaders>` 일반적으로, `<TableColumnHeader>` 및 태그가 포함 된 태그가 포함 되어 있습니다 `<Label>` `<Width>` `<Alignment>` .</span><span class="sxs-lookup"><span data-stu-id="4ad62-172">The `<TableHeaders>` tag typically contains `<TableColumnHeader>` tags that contain `<Label>`, `<Width>`, and `<Alignment>` tags.</span></span> <span data-ttu-id="4ad62-173">`<TableRowEntries>`태그에는 `<TableRowEntry>` 테이블의 각 행에 대 한 태그가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-173">The `<TableRowEntries>` tag contains `<TableRowEntry>` tags for each row in the table.</span></span> <span data-ttu-id="4ad62-174">태그에는 `<TableRowEntry>` `<TableColumnItems>` `<TableColumnItem>` 행의 각 열에 대 한 태그가 포함 된 태그가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-174">The `<TableRowEntry>` tag contains a `<TableColumnItems>` tag that contains a `<TableColumnItem>` tag for each column in the row.</span></span> <span data-ttu-id="4ad62-175">일반적으로 `<TableColumnItem>` 태그는 `<PropertyName>` 정의 된 위치에 표시 되는 개체 속성을 식별 하는 태그 또는 `<ScriptBlock>` 위치에 표시 될 결과를 계산 하는 스크립트 코드를 포함 하는 태그를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-175">Typically, the `<TableColumnItem>` tag contains either a `<PropertyName>` tag that identifies the object property to be displayed in the defined location, or a `<ScriptBlock>` tag that contains script code that calculates a result that is to be displayed in the location.</span></span>

> [!NOTE]
> <span data-ttu-id="4ad62-176">계산 된 결과가 유용할 수 있는 위치에 스크립트 블록을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-176">Script blocks can also be used elsewhere in locations where calculated results can be useful.</span></span>

<span data-ttu-id="4ad62-177">태그에는 `<TableColumnItem>` `<FormatString>` 속성 또는 계산 된 결과가 표시 되는 방법을 지정 하는 태그가 포함 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-177">The `<TableColumnItem>` tag can also contain a `<FormatString>` tag that specifies how the property or the calculated results will be displayed.</span></span>

### <a name="listcontrol-tag"></a><span data-ttu-id="4ad62-178">이 listcontrol 태그</span><span class="sxs-lookup"><span data-stu-id="4ad62-178">ListControl tag</span></span>

<span data-ttu-id="4ad62-179">태그에는 `<ListControl>` 일반적으로 `<ListEntries>` 태그가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-179">The `<ListControl>` tag typically contains a `<ListEntries>` tag.</span></span> <span data-ttu-id="4ad62-180">태그에 `<ListEntries>` 는 `<ListEntry>` 태그가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-180">The `<ListEntries>` tag contains a `<ListEntry>` tag.</span></span> <span data-ttu-id="4ad62-181">태그에 `<ListEntry>` 는 `<ListItems>` 태그가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-181">The `<ListEntry>` tag contains a `<ListItems>` tag.</span></span> <span data-ttu-id="4ad62-182">태그는 태그를 포함 하 `<ListItems>` 는 태그를 포함 합니다 `<ListItem>` `<PropertyName>` .</span><span class="sxs-lookup"><span data-stu-id="4ad62-182">The `<ListItems>` tag contains `<ListItem>` tags, which contain `<PropertyName>` tags.</span></span> <span data-ttu-id="4ad62-183">`<PropertyName>`태그는 목록의 지정 된 위치에 표시 되는 개체 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-183">The `<PropertyName>` tags specify the object property to be displayed at the specified location in the list.</span></span> <span data-ttu-id="4ad62-184">선택 집합을 사용 하 여 뷰 선택을 정의 하는 경우 `<ListControl>` 및 `<ListEntry>` 태그는 하나 이상의 `<EntrySelectedBy>` 태그를 포함 하는 태그를 포함할 수도 있습니다 `<TypeName>` .</span><span class="sxs-lookup"><span data-stu-id="4ad62-184">If the view selection is defined using a selection set, the `<ListControl>` and `<ListEntry>` tags can also contain an `<EntrySelectedBy>` tag that contains one or more `<TypeName>` tags.</span></span> <span data-ttu-id="4ad62-185">이러한 `<TypeName>` 태그는 태그가 표시할 개체 유형을 지정 합니다 `<ListControl>` .</span><span class="sxs-lookup"><span data-stu-id="4ad62-185">These `<TypeName>` tags specify the object type that the `<ListControl>` tag is intended to display.</span></span>

### <a name="widecontrol-tag"></a><span data-ttu-id="4ad62-186">WideControl 태그</span><span class="sxs-lookup"><span data-stu-id="4ad62-186">WideControl tag</span></span>

<span data-ttu-id="4ad62-187">태그에는 `<WideControl>` 일반적으로 `<WideEntries>` 태그가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-187">The `<WideControl>` tag typically contains a `<WideEntries>` tag.</span></span> <span data-ttu-id="4ad62-188">`<WideEntries>`태그는 하나 이상의 태그를 포함 합니다 `<WideEntry>` .</span><span class="sxs-lookup"><span data-stu-id="4ad62-188">The `<WideEntries>` tag contains one or more `<WideEntry>` tags.</span></span> <span data-ttu-id="4ad62-189">태그에는 `<WideEntry>` 일반적으로 `<PropertyName>` 뷰의 지정 된 위치에 표시할 속성을 지정 하는 태그가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-189">A `<WideEntry>` tag typically contains a `<PropertyName>` tag that specifies the property to be displayed at the specified location in the view.</span></span> <span data-ttu-id="4ad62-190">태그에는 `<PropertyName>` `<FormatString>` 속성이 표시 되는 방법을 지정 하는 태그가 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-190">The `<PropertyName>` tag can contain a `<FormatString>` tag that specifies how the property is to be displayed.</span></span>

### <a name="customcontrol-tag"></a><span data-ttu-id="4ad62-191">CustomControl 태그</span><span class="sxs-lookup"><span data-stu-id="4ad62-191">CustomControl tag</span></span>

<span data-ttu-id="4ad62-192">태그를 사용 하 여 `<CustomControl>` 형식을 정의 하는 스크립트 블록을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-192">The `<CustomControl>` tag lets you use a script block to define a format.</span></span> <span data-ttu-id="4ad62-193">태그에는 `<CustomControl>` 일반적으로 `<CustomEntries>` 여러 태그를 포함 하는 태그가 포함 되어 있습니다 `<CustomEntry>` .</span><span class="sxs-lookup"><span data-stu-id="4ad62-193">A `<CustomControl>` tag typically contains a `<CustomEntries>` tag that contains multiple `<CustomEntry>` tags.</span></span> <span data-ttu-id="4ad62-194">각 `<CustomEntry>` 태그에는 `<CustomItem>` `<Text>` ,, `<Indentation>` `<ExpressionBinding>` 및 태그를 포함 하 여 보기에서 지정 된 위치의 내용과 서식을 지정 하는 다양 한 태그를 포함할 수 있는 태그가 포함 되어 있습니다 `<NewLine>` .</span><span class="sxs-lookup"><span data-stu-id="4ad62-194">Each `<CustomEntry>` tag contains a `<CustomItem>` tag that can contain a variety of tags that specify contents and formatting of the specified location in the view, including `<Text>`, `<Indentation>`, `<ExpressionBinding>`, and `<NewLine>` tags.</span></span>

## <a name="tracing-formatps1xml-file-use"></a><span data-ttu-id="4ad62-195">Xml 파일 사용 추적 Format.ps1</span><span class="sxs-lookup"><span data-stu-id="4ad62-195">Tracing Format.ps1xml file use</span></span>

<span data-ttu-id="4ad62-196">파일 로드 또는 응용 프로그램에서 오류를 검색 하려면 `Format.ps1xml` `Trace-Command` 다음 형식 구성 요소 중 하나를 **Name** 매개 변수 값으로 사용 하 여 cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-196">To detect errors in the loading or application of `Format.ps1xml` files, use the `Trace-Command` cmdlet with any of the following format components as the value of the **Name** parameter:</span></span>

- <span data-ttu-id="4ad62-197">FormatFileLoading</span><span class="sxs-lookup"><span data-stu-id="4ad62-197">FormatFileLoading</span></span>
- <span data-ttu-id="4ad62-198">FormatViewBinding</span><span class="sxs-lookup"><span data-stu-id="4ad62-198">FormatViewBinding</span></span>

<span data-ttu-id="4ad62-199">자세한 내용은 [Trace-Command](xref:Microsoft.PowerShell.Utility.Trace-Command) 및 [TraceSource](xref:Microsoft.PowerShell.Utility.Get-TraceSource)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4ad62-199">For more information, see [Trace-Command](xref:Microsoft.PowerShell.Utility.Trace-Command) and [Get-TraceSource](xref:Microsoft.PowerShell.Utility.Get-TraceSource).</span></span>

## <a name="signing-a-formatps1xml-file"></a><span data-ttu-id="4ad62-200">Format.ps1xml 파일에 서명</span><span class="sxs-lookup"><span data-stu-id="4ad62-200">Signing a Format.ps1xml file</span></span>

<span data-ttu-id="4ad62-201">파일의 사용자를 보호 하려면 `Format.ps1xml` 디지털 서명을 사용 하 여 파일에 서명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-201">To protect the users of your `Format.ps1xml` file, sign the file using a digital signature.</span></span> <span data-ttu-id="4ad62-202">자세한 내용은 [about_Signing](about_Signing.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4ad62-202">For more information, see [about_Signing](about_Signing.md).</span></span>

## <a name="sample-xml-for-a-format-table-custom-view"></a><span data-ttu-id="4ad62-203">Format-Table 사용자 지정 보기에 대 한 샘플 XML</span><span class="sxs-lookup"><span data-stu-id="4ad62-203">Sample XML for a Format-Table custom view</span></span>

<span data-ttu-id="4ad62-204">다음 XML 샘플에서는 `Format-Table` 에서 만든 **System.io.directoryinfo** 및 **system.object** 개체에 대 한 사용자 지정 뷰를 만듭니다 `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="4ad62-204">The following XML sample creates a `Format-Table` custom view for the **System.IO.DirectoryInfo** and **System.IO.FileInfo** objects created by `Get-ChildItem`.</span></span> <span data-ttu-id="4ad62-205">사용자 지정 보기의 이름을 **mygciview** 로 지정 하 고 테이블에 **CreationTime** 열을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-205">The custom view is named **mygciview** and adds the **CreationTime** column to the table.</span></span>

<span data-ttu-id="4ad62-206">사용자 지정 뷰를 만들려면 `Get-FormatData` 및 cmdlet을 사용 `Export-FormatData` 하 여 파일을 생성 `.ps1xml` 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-206">To create the custom view, use the `Get-FormatData` and `Export-FormatData` cmdlets to generate a `.ps1xml` file.</span></span> <span data-ttu-id="4ad62-207">그런 다음 파일을 편집 `.ps1xml` 하 여 사용자 지정 보기에 대 한 코드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-207">Then, edit your `.ps1xml` file to create the code for your custom view.</span></span> <span data-ttu-id="4ad62-208">`.ps1xml`PowerShell에서 액세스할 수 있는 모든 디렉터리에 파일을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-208">The `.ps1xml` file can be stored in any directory that PowerShell can access.</span></span> <span data-ttu-id="4ad62-209">예를 들어의 하위 디렉터리 `$HOME` 입니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-209">For example, a subdirectory of `$HOME`.</span></span>

<span data-ttu-id="4ad62-210">파일이 만들어진 후에는 `.ps1xml` cmdlet을 사용 `Update-FormatData` 하 여 현재 PowerShell 세션에 뷰를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-210">After the `.ps1xml` file is created, use the `Update-FormatData` cmdlet to include the view in the current PowerShell session.</span></span> <span data-ttu-id="4ad62-211">또는 모든 PowerShell 세션에서 보기를 사용할 수 있어야 하는 경우에는 update 명령을 PowerShell 프로필에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-211">Or, add the update command to your PowerShell profile if you need the view available in all PowerShell sessions.</span></span>

<span data-ttu-id="4ad62-212">이 예에서는 사용자 지정 뷰에서 테이블 형식을 사용 해야 합니다. 그렇지 않으면이 `Format-Table` 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-212">For this example, the custom view must use the table format, otherwise, `Format-Table` fails.</span></span>

<span data-ttu-id="4ad62-213">`Format-Table` **View** 매개 변수와 함께 사용 하 여 사용자 지정 보기의 이름 **mygciview** 를 지정 하 고 **CreationTime** 열을 사용 하 여 테이블의 출력 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-213">Use `Format-Table` with the **View** parameter to specify the custom view's name, **mygciview**, and format the table's output with the **CreationTime** column.</span></span> <span data-ttu-id="4ad62-214">명령이 실행 되는 방법에 대 한 예는 [서식 테이블](xref:Microsoft.PowerShell.Utility.Format-Table)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="4ad62-214">For an example of how the command is run, see [Format-Table](xref:Microsoft.PowerShell.Utility.Format-Table).</span></span>

> [!NOTE]
> <span data-ttu-id="4ad62-215">소스 코드에서 서식 XML을 가져와서 사용자 지정 보기를 만들 수 있지만 원하는 결과를 얻으려면 더 많은 개발이 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-215">Although you can get the formatting XML from the source code to create a custom view, more development might be needed to get the desired result.</span></span>

<span data-ttu-id="4ad62-216">다음 명령에는 `Get-FormatData` 모든 로컬 서식 지정 정보가 반환 되도록 **PowerShellVersion** 매개 변수에 대 한 대체 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-216">In the following `Get-FormatData` command, there's an alternative for the **PowerShellVersion** parameter to ensure that all local formatting information is returned.</span></span> <span data-ttu-id="4ad62-217">`-PowerShellVersion $PSVersionTable.PSVersion`특정 PowerShell 버전이 아닌를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4ad62-217">Use `-PowerShellVersion $PSVersionTable.PSVersion` rather than a specific PowerShell version.</span></span>

```powershell
Get-FormatData -PowerShellVersion 5.1 -TypeName System.IO.DirectoryInfo |
   Export-FormatData -Path ./Mygciview.Format.ps1xml
Update-FormatData -AppendPath ./Mygciview.Format.ps1xml
```

```xml
<?xml version="1.0" encoding="utf-8"?>
<Configuration>
  <ViewDefinitions>
    <View>
      <Name>mygciview</Name>
      <ViewSelectedBy>
        <TypeName>System.IO.DirectoryInfo</TypeName>
        <TypeName>System.IO.FileInfo</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <PropertyName>PSParentPath</PropertyName>
      </GroupBy>
      <TableControl>
        <TableHeaders>
          <TableColumnHeader>
            <Label>Mode</Label>
            <Width>7</Width>
            <Alignment>Left</Alignment>
          </TableColumnHeader>
          <TableColumnHeader>
            <Label>LastWriteTime</Label>
            <Width>26</Width>
            <Alignment>Right</Alignment>
          </TableColumnHeader>
          <TableColumnHeader>
            <Label>CreationTime</Label>
            <Width>26</Width>
            <Alignment>Right</Alignment>
          </TableColumnHeader>
          <TableColumnHeader>
            <Label>Length</Label>
            <Width>14</Width>
            <Alignment>Right</Alignment>
          </TableColumnHeader>
          <TableColumnHeader>
            <Label>Name</Label>
            <Alignment>Left</Alignment>
          </TableColumnHeader>
        </TableHeaders>
        <TableRowEntries>
          <TableRowEntry>
            <Wrap />
            <TableColumnItems>
              <TableColumnItem>
                <PropertyName>ModeWithoutHardLink</PropertyName>
              </TableColumnItem>
              <TableColumnItem>
                <PropertyName>LastWriteTime</PropertyName>
              </TableColumnItem>
              <TableColumnItem>
                <PropertyName>CreationTime</PropertyName>
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

## <a name="see-also"></a><span data-ttu-id="4ad62-218">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4ad62-218">See also</span></span>

[<span data-ttu-id="4ad62-219">Export-FormatData</span><span class="sxs-lookup"><span data-stu-id="4ad62-219">Export-FormatData</span></span>](xref:Microsoft.PowerShell.Utility.Export-FormatData)

[<span data-ttu-id="4ad62-220">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="4ad62-220">Get-FormatData</span></span>](xref:Microsoft.PowerShell.Utility.Get-FormatData)

[<span data-ttu-id="4ad62-221">Get-TraceSource</span><span class="sxs-lookup"><span data-stu-id="4ad62-221">Get-TraceSource</span></span>](xref:Microsoft.PowerShell.Utility.Get-TraceSource)

[<span data-ttu-id="4ad62-222">형식 스키마 XML 참조</span><span class="sxs-lookup"><span data-stu-id="4ad62-222">Format Schema XML Reference</span></span>](/powershell/scripting/developer/format/format-schema-xml-reference)

[<span data-ttu-id="4ad62-223">Trace-Command</span><span class="sxs-lookup"><span data-stu-id="4ad62-223">Trace-Command</span></span>](xref:Microsoft.PowerShell.Utility.Trace-Command)

[<span data-ttu-id="4ad62-224">Update-FormatData</span><span class="sxs-lookup"><span data-stu-id="4ad62-224">Update-FormatData</span></span>](xref:Microsoft.PowerShell.Utility.Update-FormatData)

[<span data-ttu-id="4ad62-225">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="4ad62-225">Writing a PowerShell Formatting File</span></span>](/powershell/scripting/developer/format/writing-a-powershell-formatting-file)
