---
title: 목록 뷰 (GroupBy) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7956d13e196454a3f6da185e9be74f9d3cb8ef63
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773405"
---
# <a name="list-view-groupby"></a><span data-ttu-id="9da90-102">목록 보기(GroupBy)</span><span class="sxs-lookup"><span data-stu-id="9da90-102">List View (GroupBy)</span></span>

<span data-ttu-id="9da90-103">이 예제에서는 목록의 행을 그룹으로 구분 하는 목록 뷰를 구현 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9da90-103">This example shows how to implement a list view that separates the rows of the list into groups.</span></span> <span data-ttu-id="9da90-104">이 목록 보기에는 Servicecontroller의 속성이 표시 됩니다. [ Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) [cmdlet에서](/powershell/module/Microsoft.PowerShell.Management/Get-Service) 반환 되는 Fullname 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="9da90-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="9da90-105">목록 뷰의 구성 요소에 대 한 자세한 내용은 [목록 뷰 만들기](./creating-a-list-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9da90-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="9da90-106">이 서식 파일을 로드 하려면</span><span class="sxs-lookup"><span data-stu-id="9da90-106">To load this formatting file</span></span>

1. <span data-ttu-id="9da90-107">이 항목의 예제 섹션에서 XML을 텍스트 파일로 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="9da90-107">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="9da90-108">텍스트 파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="9da90-108">Save the text file.</span></span> <span data-ttu-id="9da90-109">파일에 확장명을 추가 하 여 `format.ps1xml` 서식 파일을 식별 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9da90-109">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="9da90-110">Windows PowerShell을 열고 다음 명령을 실행 하 여 현재 세션에 형식 지정 파일을 로드 `Update-formatdata -prependpath PathToFormattingFile` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9da90-110">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="9da90-111">이 서식 파일은 Windows PowerShell 서식 파일에 의해 이미 정의 된 개체의 표시를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9da90-111">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="9da90-112">`prependPath`Cmdlet을 실행할 때 매개 변수를 사용 해야 하며,이 서식 파일을 모듈로 로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9da90-112">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="9da90-113">데모</span><span class="sxs-lookup"><span data-stu-id="9da90-113">Demonstrates</span></span>

<span data-ttu-id="9da90-114">이 서식 파일은 다음 XML 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9da90-114">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="9da90-115">뷰의 [Name](./name-element-for-view-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="9da90-115">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="9da90-116">뷰가 표시 하는 개체를 정의 하는 [Viewselectedby](./viewselectedby-element-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="9da90-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="9da90-117">새 개체 그룹이 표시 되는 방법을 정의 하는 [GroupBy](./viewselectedby-element-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="9da90-117">The [GroupBy](./viewselectedby-element-format.md) element that defines how a new group of objects is displayed.</span></span>

- <span data-ttu-id="9da90-118">뷰가 표시 하는 속성을 정의 하는 [이 listcontrol](./listcontrol-element-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="9da90-118">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="9da90-119">목록 뷰의 행에 표시 되는 항목을 정의 하는 [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="9da90-119">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="9da90-120">표시 되는 속성을 정의 하는 [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="9da90-120">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="9da90-121">예제</span><span class="sxs-lookup"><span data-stu-id="9da90-121">Example</span></span>

<span data-ttu-id="9da90-122">다음 XML은 [Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController.Status) 속성 값이 변경 될 때마다 새 그룹을 시작 하는 목록 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9da90-122">The following XML defines a list view that starts a new group whenever the value of the [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) property changes.</span></span> <span data-ttu-id="9da90-123">각 그룹을 시작 하면 속성의 새 값을 포함 하는 사용자 지정 레이블이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9da90-123">When each group is started, a custom label is displayed that includes the new value of the property.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <Name>System.ServiceProcess.ServiceController</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <PropertyName>Status</PropertyName>
        <Label>New Service Status</Label>
      </GroupBy>
      <ListControl>
        <ListEntries>
          <ListEntry>
            <ListItems>
              <ListItem>
                <PropertyName>Name</PropertyName>
              </ListItem>
              <ListItem>
                <PropertyName>DisplayName</PropertyName>
              </ListItem>
              <ListItem>
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

<span data-ttu-id="9da90-124">다음 예제에서는 Windows PowerShell에서 Servicecontroller를 표시 하는 방법을 보여 줍니다 [. Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController) 이 서식 파일이 로드 된 후의 Fullname 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="9da90-124">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span> <span data-ttu-id="9da90-125">그룹 레이블 앞과 뒤에 추가 된 빈 줄은 Windows PowerShell에 의해 자동으로 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9da90-125">The blank lines added before and after the group label are automatically added by Windows PowerShell.</span></span>

```powershell
Get-Service f*
```

```output
   New Service Status: Stopped

Name        : Fax
DisplayName : Fax
ServiceType : Win32OwnProcess

   New Service Status: Running

Name        : FCSAM
DisplayName : Microsoft Antimalware Service
ServiceType : Win32OwnProcess

   New Service Status: Stopped

Name        : fdPHost
DisplayName : Function Discovery Provider Host
ServiceType : Win32ShareProcess

   New Service Status: Running

Name        : FDResPub
DisplayName : Function Discovery Resource Publication
ServiceType : Win32ShareProcess

Name        : FontCache
DisplayName : Windows Font Cache Service
ServiceType : Win32ShareProcess

   New Service Status: Stopped

Name        : FontCache3.0.0.0
DisplayName : Windows Presentation Foundation Font Cache 3.0.0.0
ServiceType : Win32OwnProcess

   New Service Status: Running

Name        : FSysAgent
DisplayName : Microsoft Forefront System Agent
ServiceType : Win32OwnProcess

Name        : FwcAgent
DisplayName : Firewall Client Agent
ServiceType : Win32OwnProcess
```

## <a name="see-also"></a><span data-ttu-id="9da90-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9da90-126">See Also</span></span>

[<span data-ttu-id="9da90-127">형식 지정 파일 예제</span><span class="sxs-lookup"><span data-stu-id="9da90-127">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="9da90-128">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="9da90-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
