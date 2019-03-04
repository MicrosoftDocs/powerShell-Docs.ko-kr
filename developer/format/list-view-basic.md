---
title: 목록 보기 (Basic) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 918f381c-43e6-4594-a468-a40bfa8a16d6
caps.latest.revision: 7
ms.openlocfilehash: 1c683693c331ccfaf7355a0dd51801ed6fd39b3b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853309"
---
# <a name="list-view-basic"></a><span data-ttu-id="d8725-102">목록 보기(기본)</span><span class="sxs-lookup"><span data-stu-id="d8725-102">List View (Basic)</span></span>

<span data-ttu-id="d8725-103">이 예제에 표시 하는 기본 목록 보기를 구현 하는 방법을 보여 줍니다는 [System.Serviceprocess.Servicecontroller? Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController) 에서 반환 된 개체를 [Get-service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d8725-103">This example shows how to implement a basic list view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="d8725-104">목록 뷰 구성 요소에 대 한 자세한 내용은 참조 [목록 뷰를 만들면](./creating-a-list-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="d8725-104">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>
<span data-ttu-id="d8725-105">이 예제에 표시 하는 기본 목록 보기를 구현 하는 방법을 보여 줍니다는 [System.Serviceprocess.Servicecontroller? Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController) 에서 반환 된 개체를 [Get-service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d8725-105">This example shows how to implement a basic list view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="d8725-106">목록 뷰 구성 요소에 대 한 자세한 내용은 참조 [목록 뷰를 만들면](./creating-a-list-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="d8725-106">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="d8725-107">이 서식 파일을 로드 하려면</span><span class="sxs-lookup"><span data-stu-id="d8725-107">To load this formatting file</span></span>

1. <span data-ttu-id="d8725-108">이 항목의 예제 섹션에서 XML을 텍스트 파일로 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8725-108">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="d8725-109">텍스트 파일을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8725-109">Save the text file.</span></span> <span data-ttu-id="d8725-110">추가 해야 합니다 `format.ps1xml` 서식 파일로 식별 하는 파일 확장명입니다.</span><span class="sxs-lookup"><span data-stu-id="d8725-110">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="d8725-111">Windows PowerShell을 열고 현재 세션으로 서식 파일을 로드 하려면 다음 명령을 실행: `Update-formatdata -prependpath PathToFormattingFile`합니다.</span><span class="sxs-lookup"><span data-stu-id="d8725-111">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="d8725-112">이 서식 파일에는 Windows PowerShell 형식 지정 파일에서 이미 정의 되어 있는 개체의 표시를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8725-112">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="d8725-113">사용 해야 합니다는 `prependPath` 모듈로 파일 매개 변수 cmdlet을 실행 하 고 형식을 로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d8725-113">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="d8725-114">시연</span><span class="sxs-lookup"><span data-stu-id="d8725-114">Demonstrates</span></span>

<span data-ttu-id="d8725-115">이 서식 파일에 다음 XML 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d8725-115">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="d8725-116">합니다 [이름을](./name-element-for-view-format.md) 뷰에 대 한 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d8725-116">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="d8725-117">합니다 [ViewSelectedBy](./viewselectedby-element-format.md) 어떤 개체를 뷰에 표시를 정의 하는 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d8725-117">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="d8725-118">합니다 [ListControl](./listcontrol-element-format.md) 어떤 속성은 보기에서 표시를 정의 하는 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d8725-118">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="d8725-119">합니다 [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) 목록 뷰의 행에 표시 되는 항목을 정의 하는 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d8725-119">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="d8725-120">합니다 [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) 표시 되는 속성을 정의 하는 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d8725-120">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="d8725-121">예제</span><span class="sxs-lookup"><span data-stu-id="d8725-121">Example</span></span>

<span data-ttu-id="d8725-122">다음 XML의 네 가지 속성을 표시 하는 목록 뷰를 정의 합니다 [System.Serviceprocess.Servicecontroller? Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="d8725-122">The following XML defines a list view that displays four properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="d8725-123">각 행에는 속성의 이름 속성의 값 뒤에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8725-123">In each row, the name of the property is displayed followed by the value of the property.</span></span>

```xml
<Configuration>
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
              <PropertyName>Name</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>DisplayName</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>Status</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>ServiceType</PropertyName>
            </ListItem>
          </ListItems>
        </ListEntry>
      </ListEntries>
    </ListControl>
  </View>
</Configuration>
```

<span data-ttu-id="d8725-124">다음 예제에서는 Windows PowerShell의 표시 하는 방법을 보여 줍니다는 [System.Serviceprocess.Servicecontroller? Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController) 이 서식 파일 로드 된 후 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="d8725-124">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
Name        : Fax
DisplayName : Fax
Status      : Stopped
ServiceType : Win32OwnProcess

Name        : FCSAM
DisplayName : Microsoft Antimalware Service
Status      : Running
ServiceType : Win32OwnProcess

Name        : fdPHost
DisplayName : Function Discovery Provider Host
Status      : Stopped
ServiceType : Win32ShareProcess

Name        : FDResPub
DisplayName : Function Discovery Resource Publication
Status      : Running
ServiceType : Win32ShareProcess

Name        : FontCache
DisplayName : Windows Font Cache Service
Status      : Running
ServiceType : Win32ShareProcess

Name        : FontCache3.0.0.0
DisplayName : Windows Presentation Foundation Font Cache 3.0.0.0
Status      : Stopped
ServiceType : Win32OwnProcess

Name        : FSysAgent
DisplayName : Microsoft Forefront System Agent
Status      : Running
ServiceType : Win32OwnProcess

Name        : FwcAgent
DisplayName : Firewall Client Agent
Status      : Running
ServiceType : Win32OwnProcess
```

## <a name="see-also"></a><span data-ttu-id="d8725-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d8725-125">See Also</span></span>

[<span data-ttu-id="d8725-126">서식 파일의 예</span><span class="sxs-lookup"><span data-stu-id="d8725-126">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="d8725-127">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="d8725-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
