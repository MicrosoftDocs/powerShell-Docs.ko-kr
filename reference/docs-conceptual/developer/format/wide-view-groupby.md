---
ms.date: 09/13/2016
ms.topic: reference
title: 넓게 보기(GroupBy)
description: 넓게 보기(GroupBy)
ms.openlocfilehash: 807bea2a5d44c38e2c9977f792bea2fb9bca0fc3
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667677"
---
# <a name="wide-view-groupby"></a><span data-ttu-id="4f257-103">넓게 보기(GroupBy)</span><span class="sxs-lookup"><span data-stu-id="4f257-103">Wide View (GroupBy)</span></span>

<span data-ttu-id="4f257-104">이 예제에서는 Servicecontroller의 그룹을 표시 하는 넓은 뷰를 구현 하는 방법을 보여 줍니다 [. Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController) cmdlet에서 반환 되는 Fullname 개체 `Get-Service` 입니다.</span><span class="sxs-lookup"><span data-stu-id="4f257-104">This example shows how to implement a wide view that displays groups of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="4f257-105">넓은 보기의 구성 요소에 대 한 자세한 내용은 [넓은 뷰 만들기](./creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4f257-105">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="4f257-106">이 서식 파일을 로드 하려면</span><span class="sxs-lookup"><span data-stu-id="4f257-106">To load this formatting file</span></span>

1. <span data-ttu-id="4f257-107">이 항목의 예제 섹션에서 XML을 텍스트 파일로 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f257-107">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="4f257-108">텍스트 파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="4f257-108">Save the text file.</span></span> <span data-ttu-id="4f257-109">파일에 확장명을 추가 하 여 `format.ps1xml` 서식 파일을 식별 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f257-109">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="4f257-110">Windows PowerShell을 열고 다음 명령을 실행 하 여 현재 세션에 형식 지정 파일을 로드 `Update-formatdata -prependpath PathToFormattingFile` 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f257-110">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="4f257-111">이 서식 파일은 Windows PowerShell 형식 지정 파일에 의해 이미 정의 된 개체의 표시를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f257-111">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting files.</span></span> <span data-ttu-id="4f257-112">`prependPath`Cmdlet을 실행할 때 매개 변수를 사용 해야 하며,이 서식 파일을 모듈로 로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4f257-112">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="4f257-113">데모</span><span class="sxs-lookup"><span data-stu-id="4f257-113">Demonstrates</span></span>

<span data-ttu-id="4f257-114">이 서식 파일은 다음 XML 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4f257-114">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="4f257-115">뷰의 [Name](./name-element-for-view-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4f257-115">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="4f257-116">뷰가 표시 하는 개체를 정의 하는 [Viewselectedby](./viewselectedby-element-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4f257-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="4f257-117">새 그룹이 표시 되는 시기를 정의 하는 [GroupBy](./groupby-element-for-view-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4f257-117">The [GroupBy](./groupby-element-for-view-format.md) element that defines when a new group is displayed.</span></span>

- <span data-ttu-id="4f257-118">뷰가 표시 하는 속성을 정의 하는 [WideItem](./wideitem-element-for-widecontrol-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4f257-118">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="4f257-119">예제</span><span class="sxs-lookup"><span data-stu-id="4f257-119">Example</span></span>

<span data-ttu-id="4f257-120">다음 XML은 개체 그룹을 표시 하는 넓은 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f257-120">The following XML defines a wide view that displays groups of objects.</span></span> <span data-ttu-id="4f257-121">[Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) 속성 값이 변경 되 면 각 새 그룹이 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f257-121">Each new group is started when the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Configuration>
  <ViewDefinitions>
    <View>
      <Name>ServiceWideView</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <Label>Service Type</Label>
        <PropertyName>ServiceType</PropertyName>
      </GroupBy>
      <WideControl>
        <WideEntries>
          <WideEntry>
            <WideItem>
              <PropertyName>ServiceName</PropertyName>
            </WideItem>
          </WideEntry>
        </WideEntries>
      </WideControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

<span data-ttu-id="4f257-122">다음 예제에서는 Windows PowerShell에서 Servicecontroller를 표시 하는 방법을 보여 줍니다 [. Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController) 이 서식 파일이 로드 된 후의 Fullname 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="4f257-122">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
   Service Type: Win32OwnProcess

Fax                             FCSAM

   Service Type: Win32ShareProcess

fdPHost                         FDResPub
FontCache

   Service Type: Win32OwnProcess

FontCache3.0.0.0                FSysAgent
FwcAgent
```

## <a name="see-also"></a><span data-ttu-id="4f257-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4f257-123">See Also</span></span>

[<span data-ttu-id="4f257-124">형식 지정 파일 예제</span><span class="sxs-lookup"><span data-stu-id="4f257-124">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="4f257-125">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="4f257-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
