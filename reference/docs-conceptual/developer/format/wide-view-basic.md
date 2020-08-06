---
title: 넓은 보기 (기본) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d92c29c33c5104b6186ae53ccf544be197d657b1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772402"
---
# <a name="wide-view-basic"></a><span data-ttu-id="81320-102">넓게 보기(기본)</span><span class="sxs-lookup"><span data-stu-id="81320-102">Wide View (Basic)</span></span>

<span data-ttu-id="81320-103">이 예제에서는 Servicecontroller를 표시 하는 기본 넓은 뷰를 구현 하는 방법을 보여 줍니다 [. Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController) cmdlet에서 반환 되는 Fullname 개체 `Get-Service` 입니다.</span><span class="sxs-lookup"><span data-stu-id="81320-103">This example shows how to implement a basic wide view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="81320-104">넓은 보기의 구성 요소에 대 한 자세한 내용은 [넓은 뷰 만들기](./creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="81320-104">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="81320-105">이 서식 파일을 로드 하려면</span><span class="sxs-lookup"><span data-stu-id="81320-105">To load this formatting file</span></span>

1. <span data-ttu-id="81320-106">이 항목의 예제 섹션에서 XML을 텍스트 파일로 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="81320-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="81320-107">텍스트 파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="81320-107">Save the text file.</span></span> <span data-ttu-id="81320-108">파일에 확장명을 추가 하 여 `format.ps1xml` 서식 파일을 식별 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="81320-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="81320-109">Windows PowerShell을 열고 다음 명령을 실행 하 여 현재 세션에 형식 지정 파일을 로드 `Update-formatdata -prependpath PathToFormattingFile` 합니다.</span><span class="sxs-lookup"><span data-stu-id="81320-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="81320-110">이 서식 파일은 Windows PowerShell 서식 파일에 의해 이미 정의 된 개체의 표시를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="81320-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="81320-111">`prependPath`Cmdlet을 실행할 때 매개 변수를 사용 해야 하며,이 서식 파일을 모듈로 로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="81320-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="81320-112">데모</span><span class="sxs-lookup"><span data-stu-id="81320-112">Demonstrates</span></span>

<span data-ttu-id="81320-113">이 서식 파일은 다음 XML 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="81320-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="81320-114">뷰의 [Name](./name-element-for-view-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="81320-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="81320-115">뷰가 표시 하는 개체를 정의 하는 [Viewselectedby](./viewselectedby-element-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="81320-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="81320-116">뷰가 표시 하는 속성을 정의 하는 [WideItem](./wideitem-element-for-widecontrol-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="81320-116">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="81320-117">예제</span><span class="sxs-lookup"><span data-stu-id="81320-117">Example</span></span>

<span data-ttu-id="81320-118">다음 XML은 [Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) 속성의 값을 표시 하는 넓은 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="81320-118">The following XML defines a wide view that displays the value of the [System.Serviceprocess.Servicecontroller.Servicename](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) property.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Configuration>
  <ViewDefinitions>
    <View>
      <Name>ServiceWideView</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
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

<span data-ttu-id="81320-119">다음 예제에서는 Windows PowerShell에서 Servicecontroller를 표시 하는 방법을 보여 줍니다 [. Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController) 이 서식 파일이 로드 된 후의 Fullname 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="81320-119">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
Fax                      FCSAM
fdPHost                  FDResPub
FontCache                FontCache3.0.0.0
FSysAgent                FwcAgent
```

## <a name="see-also"></a><span data-ttu-id="81320-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="81320-120">See Also</span></span>

[<span data-ttu-id="81320-121">형식 지정 파일 예제</span><span class="sxs-lookup"><span data-stu-id="81320-121">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="81320-122">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="81320-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
