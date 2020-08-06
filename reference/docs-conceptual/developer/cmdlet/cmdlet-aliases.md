---
title: Cmdlet 별칭 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: fed4055f09e01c5f3fa87584d48551918606f4eb
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784540"
---
# <a name="cmdlet-aliases"></a><span data-ttu-id="c3a5f-102">Cmdlet 별칭</span><span class="sxs-lookup"><span data-stu-id="c3a5f-102">Cmdlet Aliases</span></span>

<span data-ttu-id="c3a5f-103">Cmdlet 별칭을 사용 하 여 cmdlet 사용자 환경을 개선할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3a5f-103">You can use cmdlet aliases to improve the cmdlet user experience.</span></span> <span data-ttu-id="c3a5f-104">자주 사용 하는 cmdlet에 별칭을 추가 하 여 입력을 줄이고 신속 하 게 작업을 더 쉽게 완료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3a5f-104">You can add aliases to frequently used cmdlets to reduce typing and to make it easier to complete tasks quickly.</span></span> <span data-ttu-id="c3a5f-105">Cmdlet에 기본 제공 별칭을 포함 하거나 사용자가 고유한 사용자 지정 별칭을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3a5f-105">You can include built-in aliases in your cmdlets, or users can define their own custom aliases.</span></span>

<span data-ttu-id="c3a5f-106">예를 들어, [Get Command](/powershell/module/microsoft.powershell.core/get-command) cmdlet에는 기본 제공 별칭이 있습니다 `gcm` .</span><span class="sxs-lookup"><span data-stu-id="c3a5f-106">For example, the [Get-Command](/powershell/module/microsoft.powershell.core/get-command) cmdlet has a built-in `gcm` alias.</span></span> <span data-ttu-id="c3a5f-107">사용자가 새 명령을 학습할 필요가 없도록 별칭을 사용 하 여 다른 언어의 명령 이름을 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3a5f-107">You can also use aliases to add command names from other languages so that users do not have to learn new commands.</span></span>

## <a name="alias-guidelines"></a><span data-ttu-id="c3a5f-108">별칭 지침</span><span class="sxs-lookup"><span data-stu-id="c3a5f-108">Alias Guidelines</span></span>

<span data-ttu-id="c3a5f-109">Cmdlet에 대 한 기본 제공 별칭을 만드는 경우 다음 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="c3a5f-109">Follow these guidelines when you create built-in aliases for your cmdlets:</span></span>

- <span data-ttu-id="c3a5f-110">별칭을 할당 하기 전에 Windows PowerShell을 시작 하 고, [Get Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet을 실행 하 여 이미 사용 된 별칭을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a5f-110">Before you assign aliases, start Windows PowerShell, and then run the [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet to see the aliases that are already used.</span></span>

- <span data-ttu-id="c3a5f-111">Cmdlet 이름의 동사를 참조 하는 별칭 접두사와 cmdlet 이름의 명사를 참조 하는 별칭 접미사를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a5f-111">Include an alias prefix that references the verb of the cmdlet name and an alias suffix that references the noun of the cmdlet name.</span></span> <span data-ttu-id="c3a5f-112">예를 들어 cmdlet의 별칭은 `Import-Module` "ipmo"입니다.</span><span class="sxs-lookup"><span data-stu-id="c3a5f-112">For example, the alias for the `Import-Module` cmdlet is "ipmo".</span></span> <span data-ttu-id="c3a5f-113">모든 동사 및 해당 별칭 목록은 [Cmdlet 동사](./approved-verbs-for-windows-powershell-commands.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c3a5f-113">For a list of all the verbs and their aliases, see [Cmdlet Verbs](./approved-verbs-for-windows-powershell-commands.md).</span></span>

- <span data-ttu-id="c3a5f-114">동일한 동사가 있는 cmdlet의 경우 동일한 별칭 접두사를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a5f-114">For cmdlets that have the same verb, include the same alias prefix.</span></span> <span data-ttu-id="c3a5f-115">예를 들어 이름에 "Get" 동사가 있는 모든 Windows PowerShell cmdlet의 별칭은 "g" 접두사를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a5f-115">For example, the aliases for all the Windows PowerShell cmdlets that have the "Get" verb in their name use the "g" prefix.</span></span>

- <span data-ttu-id="c3a5f-116">동일한 명사를 포함 하는 cmdlet의 경우 동일한 별칭 접미사를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a5f-116">For cmdlets that have the same noun, include the same alias suffix.</span></span> <span data-ttu-id="c3a5f-117">예를 들어 이름에 "Session" 명사를 포함 하는 모든 Windows PowerShell cmdlet의 별칭은 "sn" 접미사를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a5f-117">For example, the aliases for all the Windows PowerShell cmdlets that have the "Session" noun in their name use the "sn" suffix.</span></span>

- <span data-ttu-id="c3a5f-118">다른 언어의 명령과 동일한 cmdlet의 경우 명령 이름을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a5f-118">For cmdlets that are equivalent to commands in other languages, use the name of the command.</span></span>

- <span data-ttu-id="c3a5f-119">일반적으로 별칭을 가능한 한 짧게 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c3a5f-119">In general, make aliases as short as possible.</span></span> <span data-ttu-id="c3a5f-120">별칭에 동사에 대해 하나 이상의 고유 문자 및 명사에 대 한 고유 문자가 하나 이상 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3a5f-120">Make sure the alias has at least one distinct character for the verb and one distinct character for the noun.</span></span> <span data-ttu-id="c3a5f-121">필요에 따라 더 많은 문자를 추가 하 여 별칭을 고유 하 게 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c3a5f-121">Add more characters as needed to make the alias unique.</span></span>

## <a name="see-also"></a><span data-ttu-id="c3a5f-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c3a5f-122">See Also</span></span>

[<span data-ttu-id="c3a5f-123">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="c3a5f-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
