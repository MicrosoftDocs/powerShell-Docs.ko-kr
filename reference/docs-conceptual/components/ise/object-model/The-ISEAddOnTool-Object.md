---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: ISEAddOnTool 개체
ms.openlocfilehash: c71602d200b941ed4fb142b9c35f0fe68982e3e9
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67028989"
---
# <a name="the-iseaddontool-object"></a><span data-ttu-id="04c90-103">ISEAddOnTool 개체</span><span class="sxs-lookup"><span data-stu-id="04c90-103">The ISEAddOnTool Object</span></span>

<span data-ttu-id="04c90-104">**ISEAddonTool** 개체는 Windows PowerShell ISE에 추가적인 기능을 제공하는 설치된 추가 기능 도구를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="04c90-104">An **ISEAddonTool** object represents an installed add-on tool that provides additional functionality toWindows PowerShell ISE.</span></span> <span data-ttu-id="04c90-105">예제는 **보기**를 클릭한 다음, **명령 추가 기능 표시**를 클릭하여 표시할 수 있는 **명령** 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="04c90-105">An example is the **Commands** tool that you can display by clicking **View**, then **Show Command Add-on**.</span></span> <span data-ttu-id="04c90-106">그런 다음 사용 가능한 다양한 **ISEAddOnTool** 개체를 조작하여 이 도구에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c90-106">This tool is then accessible to you by manipulating the various available **ISEAddOnTool** objects.</span></span>

<span data-ttu-id="04c90-107">각 추가 기능 도구는 세로 창이나 가로 창과 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c90-107">Each add-on tool can be associated with either the vertical pane or the horizontal pane.</span></span> <span data-ttu-id="04c90-108">세로 창은 Windows PowerShell ISE의 오른쪽 가장자리에 도킹됩니다.</span><span class="sxs-lookup"><span data-stu-id="04c90-108">The vertical pane is docked to the right edge of Windows PowerShell ISE.</span></span> <span data-ttu-id="04c90-109">가로 창은 아래쪽 가장자리에 도킹됩니다.</span><span class="sxs-lookup"><span data-stu-id="04c90-109">The horizontal pane is docked to the bottom edge.</span></span>

<span data-ttu-id="04c90-110">Windows PowerShell ISE의 각 PowerShell 탭에는 자체의 추가 기능 도구가 설치되어 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c90-110">Each PowerShell tab in Windows PowerShell ISE can have its own set of add-on tools installed.</span></span> <span data-ttu-id="04c90-111">[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md) 컬렉션 개체에 있는 **PowerShellTab** 개체에서 현재 선택한 탭이나 동일한 속성에 사용할 수 있는 도구 컬렉션에 액세스하려면 [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-PowerShellTab-Object.md) 및 [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-PowerShellTab-Object.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="04c90-111">See [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-PowerShellTab-Object.md) and [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-PowerShellTab-Object.md) to access the collection of tools available to the currently selected tab or the same properties on any of the **PowerShellTab** objects in the [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md) collection object.</span></span>

## <a name="methods"></a><span data-ttu-id="04c90-112">메서드</span><span class="sxs-lookup"><span data-stu-id="04c90-112">Methods</span></span>

<span data-ttu-id="04c90-113">이 클래스의 개체에 사용할 수 있는 Windows PowerShell ISE 관련 메서드는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="04c90-113">There are no Windows PowerShell ISE-specific methods available for objects of this class.</span></span>

## <a name="properties"></a><span data-ttu-id="04c90-114">속성</span><span class="sxs-lookup"><span data-stu-id="04c90-114">Properties</span></span>

### <a name="control"></a><span data-ttu-id="04c90-115">컨트롤</span><span class="sxs-lookup"><span data-stu-id="04c90-115">Control</span></span>

<span data-ttu-id="04c90-116">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="04c90-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="04c90-117">**컨트롤** 속성은 명령 추가 기능 도구의 세부 정보 중 많은 부분에 대한 읽기 권한을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="04c90-117">The **Control** property provides read access to many of the details of the Commands add-on tool.</span></span>

```powershell
# View the properties of the Commands add-on tool.
# (assumes that it is visible in the vertical pane)
$psISE.CurrentVisibleVerticalTool.Control
HostObject                  : Microsoft.PowerShell.Host.ISE.ObjectModelRoot
Content                     :
HasContent                  :
ContentTemplate             :
ContentTemplateSelector     :
ContentStringFormat         :
BorderBrush                 :
BorderThickness             :
Background                  :
Foreground                  :
FontFamily                  :
FontSize                    :
FontStretch                 :
FontStyle                   :
FontWeight                  :
HorizontalContentAlignment  :
VerticalContentAlignment    :
TabIndex                    :
IsTabStop                   :
Padding                     :
Template                    : System.Windows.Controls.ControlTemplate
Style                       :
OverridesDefaultStyle       :
UseLayoutRounding           :
Triggers                    : {}
TemplatedParent             :
Resources                   : {System.Windows.Controls.TabItem}
DataContext                 :
BindingGroup                :
Language                    :
Name                        :
Tag                         :
InputScope                  :
ActualWidth                 : 370.75
ActualHeight                : 676.559097412109
LayoutTransform             :
Width                       :
MinWidth                    :
MaxWidth                    :
Height                      :
MinHeight                   :
MaxHeight                   :
FlowDirection               : LeftToRight
Margin                      :
HorizontalAlignment         :
VerticalAlignment           :
FocusVisualStyle            :
Cursor                      :
ForceCursor                 :
IsInitialized               : True
IsLoaded                    :
ToolTip                     :
ContextMenu                 :
Parent                      :
HasAnimatedProperties       :
InputBindings               :
CommandBindings             :
AllowDrop                   :
DesiredSize                 : 227.66,676.559097412109
IsMeasureValid              : True
IsArrangeValid              : True
RenderSize                  : 370.75,676.559097412109
RenderTransform             :
RenderTransformOrigin       :
IsMouseDirectlyOver         : False
IsMouseOver                 : False
IsStylusOver                : False
IsKeyboardFocusWithin       : False
IsMouseCaptured             :
IsMouseCaptureWithin        : False
IsStylusDirectlyOver        : False
IsStylusCaptured            :
IsStylusCaptureWithin       : False
IsKeyboardFocused           : False
IsInputMethodEnabled        :
Opacity                     :
OpacityMask                 :
BitmapEffect                :
Effect                      :
BitmapEffectInput           :
CacheMode                   :
Uid                         :
Visibility                  : Visible
ClipToBounds                : False
Clip                        :
SnapsToDevicePixels         : False
IsFocused                   :
IsEnabled                   :
IsHitTestVisible            :
IsVisible                   : True
Focusable                   :
PersistId                   : 1
IsManipulationEnabled       :
AreAnyTouchesOver           : False
AreAnyTouchesDirectlyOver   :
AreAnyTouchesCapturedWithin : False
AreAnyTouchesCaptured       :
TouchesCaptured             : {}
TouchesCapturedWithin       : {}
TouchesOver                 : {}
TouchesDirectlyOver         : {}
DependencyObjectType        : System.Windows.DependencyObjectType
IsSealed                    : False
Dispatcher                  : System.Windows.Threading.Dispatcher
```

### <a name="isvisible"></a><span data-ttu-id="04c90-118">IsVisible</span><span class="sxs-lookup"><span data-stu-id="04c90-118">IsVisible</span></span>

<span data-ttu-id="04c90-119">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="04c90-119">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="04c90-120">추가 기능 도구가 현재 할당된 해당 창에 표시되는지 여부를 나타내는 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="04c90-120">The Boolean property that indicates whether the add-on tool is currently visible in its assigned pane.</span></span> <span data-ttu-id="04c90-121">표시되는 경우, **IsVisible** 속성을 **$false**로 설정하여 도구를 숨기거나, **IsVisible** 속성을 **$true**로 설정하여 추가 기능이 PowerShell 탭에 표시되도록 할 수 있습니다. 추가 기능 도구가 숨겨지면 더 이상 **CurrentVisibleHorizontalTool** 또는 **CurrentVisibleVerticalTool** 개체를 통해 액세스할 수 없으며, 따라서 해당 개체에서 이 속성을 사용하여 표시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="04c90-121">If it is visible, you can set the **IsVisible** property to **$false** to hide the tool, or set the **IsVisible** property to **$true** to make an add-on tool visible on its PowerShell tab. Note that after an add-on tool is hidden, it is no longer accessible through the **CurrentVisibleHorizontalTool** or **CurrentVisibleVerticalTool** objects, and therefore cannot be made visible by using this property on that object.</span></span>

```powershell
# Hide the current tool in the vertical tool pane
$psISE.CurrentVisibleVerticalTool.IsVisible = $false
# Show the first tool on the currently selected PowerShell tab
$psISE.CurrentPowerShellTab.VerticalAddOnTools[0].IsVisible = $true
```

### <a name="name"></a><span data-ttu-id="04c90-122">이름</span><span class="sxs-lookup"><span data-stu-id="04c90-122">Name</span></span>

<span data-ttu-id="04c90-123">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="04c90-123">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="04c90-124">추가 기능 도구의 이름을 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="04c90-124">The read-only property that gets the name of the add-on tool.</span></span>

```powershell
# Gets the name of the visible vertical pane add-on tool.
$psISE.CurrentVisibleVerticalTool.Name
Commands
```

## <a name="see-also"></a><span data-ttu-id="04c90-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="04c90-125">See Also</span></span>

- [<span data-ttu-id="04c90-126">ISEAddOnToolCollection 개체</span><span class="sxs-lookup"><span data-stu-id="04c90-126">The ISEAddOnToolCollection Object</span></span>](The-ISEAddOnToolCollection-Object.md)
- [<span data-ttu-id="04c90-127">Windows PowerShell ISE 스크립팅 개체 모델의 용도</span><span class="sxs-lookup"><span data-stu-id="04c90-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="04c90-128">ISE 개체 모델 계층 구조</span><span class="sxs-lookup"><span data-stu-id="04c90-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
