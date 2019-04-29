---
title: Cmdlet 별칭 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0d70864-33fb-49ce-8054-c41ba19fd554
caps.latest.revision: 11
ms.openlocfilehash: 32f45702cc0d28e6652ef61ebdbe085291013408
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068724"
---
# <a name="cmdlet-aliases"></a><span data-ttu-id="d9f5c-102">Cmdlet 별칭</span><span class="sxs-lookup"><span data-stu-id="d9f5c-102">Cmdlet Aliases</span></span>

<span data-ttu-id="d9f5c-103">Cmdlet은 사용자 환경을 개선 하기 위해 cmdlet 별칭을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9f5c-103">You can use cmdlet aliases to improve the cmdlet user experience.</span></span> <span data-ttu-id="d9f5c-104">입력을 줄이고 쉽게 작업을 완료 하려면 신속 하 게 자주 사용 되는 cmdlet 별칭을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9f5c-104">You can add aliases to frequently used cmdlets to reduce typing and to make it easier to complete tasks quickly.</span></span> <span data-ttu-id="d9f5c-105">기본 제공 별칭, cmdlet에서 포함 하거나 사용자가 자신의 사용자 지정 별칭을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9f5c-105">You can include built-in aliases in your cmdlets, or users can define their own custom aliases.</span></span>

<span data-ttu-id="d9f5c-106">예를 들어 합니다 [Get-command](/powershell/module/microsoft.powershell.core/get-command) cmdlet에는 기본 제공 `gcm` 별칭입니다.</span><span class="sxs-lookup"><span data-stu-id="d9f5c-106">For example, the [Get-Command](/powershell/module/microsoft.powershell.core/get-command) cmdlet has a built-in `gcm` alias.</span></span> <span data-ttu-id="d9f5c-107">또한 사용자가 새 명령에 알아보기 하지 않아도 되도록 명령 이름을 다른 언어에서 추가 별칭을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9f5c-107">You can also use aliases to add command names from other languages so that users do not have to learn new commands.</span></span>

## <a name="alias-guidelines"></a><span data-ttu-id="d9f5c-108">별칭 지침</span><span class="sxs-lookup"><span data-stu-id="d9f5c-108">Alias Guidelines</span></span>

<span data-ttu-id="d9f5c-109">Cmdlet에 대 한 기본 제공 별칭을 만들 때 다음이 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="d9f5c-109">Follow these guidelines when you create built-in aliases for your cmdlets:</span></span>

- <span data-ttu-id="d9f5c-110">별칭을 할당 하기 전에 Windows PowerShell을 시작 하 고 실행 합니다 [Get-alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet을 이미 사용 되는 별칭을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="d9f5c-110">Before you assign aliases, start Windows PowerShell, and then run the [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet to see the aliases that are already used.</span></span>

- <span data-ttu-id="d9f5c-111">Cmdlet 이름 및 별칭 접미사가 cmdlet 이름의 명사를 참조 하는 동사를 참조 하는 별칭 접두사를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9f5c-111">Include an alias prefix that references the verb of the cmdlet name and an alias suffix that references the noun of the cmdlet name.</span></span> <span data-ttu-id="d9f5c-112">예를 들어,에 대 한 별칭을 `Import-Module` cmdlet은 "ipmo"입니다.</span><span class="sxs-lookup"><span data-stu-id="d9f5c-112">For example, the alias for the `Import-Module` cmdlet is "ipmo".</span></span> <span data-ttu-id="d9f5c-113">모든 동사 및 해당 별칭의 목록을 참조 하세요 [Cmdlet 동사](./approved-verbs-for-windows-powershell-commands.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="d9f5c-113">For a list of all the verbs and their aliases, see [Cmdlet Verbs](./approved-verbs-for-windows-powershell-commands.md).</span></span>

- <span data-ttu-id="d9f5c-114">동일한 동사는 cmdlet에 대해 같은 별칭 접두사를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9f5c-114">For cmdlets that have the same verb, include the same alias prefix.</span></span> <span data-ttu-id="d9f5c-115">예를 들어, 해당 이름에 "Get" 동사가 포함 된 모든 Windows PowerShell cmdlet의 별칭을 "g" 접두사를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9f5c-115">For example, the aliases for all the Windows PowerShell cmdlets that have the "Get" verb in their name use the "g" prefix.</span></span>

- <span data-ttu-id="d9f5c-116">동일한 명사가 있는 cmdlet에 대해 같은 별칭 접미사를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9f5c-116">For cmdlets that have the same noun, include the same alias suffix.</span></span> <span data-ttu-id="d9f5c-117">예를 들어 이름에 "세션" 명사가 있는 모든 Windows PowerShell cmdlet의 별칭을 "sn" 접미사를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9f5c-117">For example, the aliases for all the Windows PowerShell cmdlets that have the "Session" noun in their name use the "sn" suffix.</span></span>

- <span data-ttu-id="d9f5c-118">명령의 이름을 다른 언어로 명령에 해당 하는 cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9f5c-118">For cmdlets that are equivalent to commands in other languages, use the name of the command.</span></span>

- <span data-ttu-id="d9f5c-119">일반적으로 짧게 별칭을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9f5c-119">In general, make aliases as short as possible.</span></span> <span data-ttu-id="d9f5c-120">별칭 명사에 대 한 하나의 고유한 문자 및 동사에 대 한 고유 문자를 하나 이상 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9f5c-120">Make sure the alias has at least one distinct character for the verb and one distinct character for the noun.</span></span> <span data-ttu-id="d9f5c-121">별칭 고유 하 게 필요에 따라 더 많은 문자를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9f5c-121">Add more characters as needed to make the alias unique.</span></span>

## <a name="see-also"></a><span data-ttu-id="d9f5c-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d9f5c-122">See Also</span></span>

<span data-ttu-id="d9f5c-123">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="d9f5c-123">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
