---
title: Windows PowerShell 스냅인을 만드는 방법 | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- snap-ins [PowerShell SDK], examples
ms.openlocfilehash: 4150ba582544d1daa4a898f0ff20b169c24a0ee0
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787328"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a><span data-ttu-id="f4e8d-102">Windows PowerShell 스냅인을 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="f4e8d-102">How to Create a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="f4e8d-103">Windows PowerShell 스냅인은 cmdlet의 집합과 다른 Windows PowerShell 공급자를 셸에 등록 하는 메커니즘을 제공 하므로 셸의 기능을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e8d-103">A Windows PowerShell snap-in provides a mechanism for registering sets of cmdlets and another Windows PowerShell provider with the shell, thus extending the functionality of the shell.</span></span> <span data-ttu-id="f4e8d-104">Windows PowerShell 스냅인은 모든 cmdlet 및 공급자를 단일 어셈블리에 등록 하거나 특정 cmdlet 및 공급자 목록을 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4e8d-104">A Windows PowerShell snap-in can register all the cmdlets and providers in a single assembly, or it can register a specific list of cmdlets and providers.</span></span>

<span data-ttu-id="f4e8d-105">스냅인 어셈블리는 다른 운영 체제와 마찬가지로 보호 된 디렉터리에 설치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4e8d-105">Snap-in assemblies should be installed in a protected directory, just as they would be with other operating systems.</span></span> <span data-ttu-id="f4e8d-106">그렇지 않으면 악의적인 사용자가 안전 하지 않은 코드로 어셈블리를 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4e8d-106">Otherwise, malicious users can replace an assembly with unsafe code.</span></span>

## <a name="windows-powershell-snap-in-classes"></a><span data-ttu-id="f4e8d-107">Windows PowerShell 스냅인 클래스</span><span class="sxs-lookup"><span data-stu-id="f4e8d-107">Windows PowerShell Snap-in Classes</span></span>

<span data-ttu-id="f4e8d-108">모든 Windows PowerShell 스냅인 클래스는 [add-pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) 또는 [Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) 클래스에서 파생 됩니다 .이 클래스는</span><span class="sxs-lookup"><span data-stu-id="f4e8d-108">All Windows PowerShell snap-in classes derive from the [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) or [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classes.</span></span>

## <a name="examples"></a><span data-ttu-id="f4e8d-109">예</span><span class="sxs-lookup"><span data-stu-id="f4e8d-109">Examples</span></span>

<span data-ttu-id="f4e8d-110">[Windows PowerShell 스냅인 작성](./writing-a-windows-powershell-snap-in.md):이 예제에서는 어셈블리의 모든 cmdlet 및 공급자를 등록 하는 데 사용 되는 스냅인을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f4e8d-110">[Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md): This example shows how to create a snap-in that is used to register all the cmdlets and providers in an assembly.</span></span>

<span data-ttu-id="f4e8d-111">[사용자 지정 Windows PowerShell 스냅인 작성](./writing-a-custom-windows-powershell-snap-in.md):이 예제에서는 단일 어셈블리에 있을 수도 있고 없을 수도 있는 특정 cmdlet 및 공급자 집합을 등록 하는 데 사용 되는 사용자 지정 스냅인을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f4e8d-111">[Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md): This example shows how to create a custom snap-in that is used to register a specific set of cmdlets and providers that might or might not exist in a single assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="f4e8d-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f4e8d-112">See Also</span></span>

[<span data-ttu-id="f4e8d-113">Add-pssnapin.</span><span class="sxs-lookup"><span data-stu-id="f4e8d-113">System.Management.Automation.PSSnapIn</span></span>](/dotnet/api/System.Management.Automation.PSSnapIn)

[<span data-ttu-id="f4e8d-114">Custompssnapin.</span><span class="sxs-lookup"><span data-stu-id="f4e8d-114">System.Management.Automation.Custompssnapin</span></span>](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[<span data-ttu-id="f4e8d-115">Cmdlet 등록</span><span class="sxs-lookup"><span data-stu-id="f4e8d-115">Registering Cmdlets</span></span>](./registering-cmdlets.md)

[<span data-ttu-id="f4e8d-116">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="f4e8d-116">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
