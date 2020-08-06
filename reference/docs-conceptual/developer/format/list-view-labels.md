---
title: 목록 뷰 (레이블) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: da45bd8dce7ac2149de6a34c11d5419d6cb4ddb0
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773388"
---
# <a name="list-view-labels"></a><span data-ttu-id="1f264-102">목록 보기(레이블)</span><span class="sxs-lookup"><span data-stu-id="1f264-102">List View (Labels)</span></span>

<span data-ttu-id="1f264-103">이 예제에서는 목록의 각 행에 대 한 사용자 지정 레이블을 표시 하는 목록 뷰를 구현 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1f264-103">This example shows how to implement a list view that displays a custom label for each row of the list.</span></span> <span data-ttu-id="1f264-104">이 목록 보기에는 Servicecontroller의 속성이 표시 됩니다. [ Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) [cmdlet에](/powershell/module/Microsoft.PowerShell.Management/Get-Service) 의해 반환 되는 Fullname 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="1f264-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="1f264-105">목록 뷰의 구성 요소에 대 한 자세한 내용은 [목록 뷰 만들기](./creating-a-list-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1f264-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="1f264-106">이 서식 파일을 로드 하려면</span><span class="sxs-lookup"><span data-stu-id="1f264-106">To load this formatting file</span></span>

1. <span data-ttu-id="1f264-107">이 항목의 예제 섹션에서 XML을 텍스트 파일로 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f264-107">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="1f264-108">텍스트 파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="1f264-108">Save the text file.</span></span> <span data-ttu-id="1f264-109">파일에 확장명을 추가 하 여 `format.ps1xml` 서식 파일을 식별 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f264-109">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="1f264-110">Windows PowerShell을 열고 다음 명령을 실행 하 여 현재 세션에 형식 지정 파일을 로드 `Update-formatdata -prependpath PathToFormattingFile` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f264-110">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="1f264-111">이 서식 파일은 Windows PowerShell 서식 파일에 의해 이미 정의 된 개체의 표시를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f264-111">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="1f264-112">`prependPath`Cmdlet을 실행할 때 매개 변수를 사용 해야 하며,이 서식 파일을 모듈로 로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1f264-112">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="1f264-113">데모</span><span class="sxs-lookup"><span data-stu-id="1f264-113">Demonstrates</span></span>

<span data-ttu-id="1f264-114">이 서식 파일은 다음 XML 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1f264-114">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="1f264-115">뷰의 [Name](./name-element-for-view-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="1f264-115">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="1f264-116">뷰가 표시 하는 개체를 정의 하는 [Viewselectedby](./viewselectedby-element-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="1f264-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="1f264-117">뷰가 표시 하는 속성을 정의 하는 [이 listcontrol](./listcontrol-element-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="1f264-117">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="1f264-118">목록 뷰의 행에 표시 되는 항목을 정의 하는 [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="1f264-118">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="1f264-119">목록 뷰의 행에 표시 되는 항목을 정의 하는 [Label](./label-element-for-listitem-for-listcontrol-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="1f264-119">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="1f264-120">표시 되는 속성을 정의 하는 [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="1f264-120">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="1f264-121">예제</span><span class="sxs-lookup"><span data-stu-id="1f264-121">Example</span></span>

<span data-ttu-id="1f264-122">다음 XML은 각 행에 사용자 지정 레이블을 표시 하는 목록 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f264-122">The following XML defines a list view that displays a custom label in each row.</span></span> <span data-ttu-id="1f264-123">이 경우 레이블에는 각 글자가 대문자 인 속성 이름과 "property" 라는 단어가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f264-123">In this case, the label includes the property name with each letter capitalized and the word "property".</span></span> <span data-ttu-id="1f264-124">각 행에 속성의 이름이 표시 되 고 그 다음에 속성 값이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f264-124">In each row, the name of the property is displayed followed by the value of the property.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
    <View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <Label>NAME property</Label>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <Label>DISPLAYNAME property</Label>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <Label>STATUS property</Label>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <Label>SERVICETYPE property</Label>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>

  </ViewDefinitions>
</Configuration>
```

<span data-ttu-id="1f264-125">다음 예제에서는 Windows PowerShell에서 Servicecontroller를 표시 하는 방법을 보여 줍니다 [. Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController) 이 서식 파일이 로드 된 후의 Fullname 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="1f264-125">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
NAME property        : Fax
DISPLAYNAME property : Fax
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FCSAM
DISPLAYNAME property : Microsoft Antimalware Service
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : fdPHost
DISPLAYNAME property : Function Discovery Provider Host
STATUS property      : Stopped
SERVICETYPE property : Win32ShareProcess

NAME property        : FDResPub
DISPLAYNAME property : Function Discovery Resource Publication
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache
DISPLAYNAME property : Windows Font Cache Service
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache3.0.0.0
DISPLAYNAME property : Windows Presentation Foundation Font Cache 3.0.0.0
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FSysAgent
DISPLAYNAME property : Microsoft Forefront System Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : FwcAgent
DISPLAYNAME property : Firewall Client Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess
```

## <a name="see-also"></a><span data-ttu-id="1f264-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1f264-126">See Also</span></span>

[<span data-ttu-id="1f264-127">형식 지정 파일 예제</span><span class="sxs-lookup"><span data-stu-id="1f264-127">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="1f264-128">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="1f264-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
