---
title: 목록 보기 (레이블) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53442bb1-74a3-49f9-9150-3bc3081a7565
caps.latest.revision: 6
ms.openlocfilehash: 27de41c88e224f7610c10a764e51524016ecc8cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065277"
---
# <a name="list-view-labels"></a><span data-ttu-id="d14aa-102">목록 보기(레이블)</span><span class="sxs-lookup"><span data-stu-id="d14aa-102">List View (Labels)</span></span>

<span data-ttu-id="d14aa-103">이 예제에서는 목록의 각 행에 대 한 사용자 지정 레이블을 표시 하는 목록 보기를 구현 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d14aa-103">This example shows how to implement a list view that displays a custom label for each row of the list.</span></span> <span data-ttu-id="d14aa-104">이 목록 보기의 속성을 표시 합니다 [System.Serviceprocess.Servicecontroller? Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController) 에서 반환 되는 개체를 [Get-service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d14aa-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="d14aa-105">목록 뷰 구성 요소에 대 한 자세한 내용은 참조 [목록 뷰를 만들면](./creating-a-list-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="d14aa-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="d14aa-106">이 서식 파일을 로드 하려면</span><span class="sxs-lookup"><span data-stu-id="d14aa-106">To load this formatting file</span></span>

1. <span data-ttu-id="d14aa-107">이 항목의 예제 섹션에서 XML을 텍스트 파일로 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="d14aa-107">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="d14aa-108">텍스트 파일을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="d14aa-108">Save the text file.</span></span> <span data-ttu-id="d14aa-109">추가 해야 합니다 `format.ps1xml` 서식 파일로 식별 하는 파일 확장명입니다.</span><span class="sxs-lookup"><span data-stu-id="d14aa-109">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="d14aa-110">Windows PowerShell을 열고 현재 세션으로 서식 파일을 로드 하려면 다음 명령을 실행: `Update-formatdata -prependpath PathToFormattingFile`합니다.</span><span class="sxs-lookup"><span data-stu-id="d14aa-110">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="d14aa-111">이 서식 파일에는 Windows PowerShell 형식 지정 파일에서 이미 정의 되어 있는 개체의 표시를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d14aa-111">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="d14aa-112">사용 해야 합니다는 `prependPath` 모듈로 파일 매개 변수 cmdlet을 실행 하 고 형식을 로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d14aa-112">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="d14aa-113">데모</span><span class="sxs-lookup"><span data-stu-id="d14aa-113">Demonstrates</span></span>

<span data-ttu-id="d14aa-114">이 서식 파일에 다음 XML 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d14aa-114">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="d14aa-115">합니다 [이름을](./name-element-for-view-format.md) 뷰에 대 한 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d14aa-115">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="d14aa-116">합니다 [ViewSelectedBy](./viewselectedby-element-format.md) 어떤 개체를 뷰에 표시를 정의 하는 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d14aa-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="d14aa-117">합니다 [ListControl](./listcontrol-element-format.md) 어떤 속성은 보기에서 표시를 정의 하는 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d14aa-117">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="d14aa-118">합니다 [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) 목록 뷰의 행에 표시 되는 항목을 정의 하는 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d14aa-118">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="d14aa-119">합니다 [레이블](./label-element-for-listitem-for-listcontrol-format.md) 목록 뷰의 행에 표시 되는 항목을 정의 하는 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d14aa-119">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="d14aa-120">합니다 [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) 표시 되는 속성을 정의 하는 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d14aa-120">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="d14aa-121">예제</span><span class="sxs-lookup"><span data-stu-id="d14aa-121">Example</span></span>

<span data-ttu-id="d14aa-122">다음 XML에는 각 행에 있는 사용자 지정 레이블을 표시 하는 목록 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d14aa-122">The following XML defines a list view that displays a custom label in each row.</span></span> <span data-ttu-id="d14aa-123">이 경우 레이블을 각 문자가 대문자를 사용 하 여 속성 이름 및 "property" 라는 단어를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="d14aa-123">In this case, the label includes the property name with each letter capitalized and the word "property".</span></span> <span data-ttu-id="d14aa-124">각 행에는 속성의 이름 속성의 값 뒤에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d14aa-124">In each row, the name of the property is displayed followed by the value of the property.</span></span>

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

<span data-ttu-id="d14aa-125">다음 예제에서는 Windows PowerShell의 표시 하는 방법을 보여 줍니다는 [System.Serviceprocess.Servicecontroller? Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController) 이 서식 파일 로드 된 후 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="d14aa-125">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d14aa-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d14aa-126">See Also</span></span>

[<span data-ttu-id="d14aa-127">서식 파일의 예</span><span class="sxs-lookup"><span data-stu-id="d14aa-127">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="d14aa-128">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="d14aa-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
