---
title: SelectStr 자습서
ms.date: 09/13/2016
ms.openlocfilehash: 500cf055afe1ccc04f6a4a28f92abb80886dfa43
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786495"
---
# <a name="selectstr-tutorial"></a><span data-ttu-id="70553-102">SelectStr 자습서</span><span class="sxs-lookup"><span data-stu-id="70553-102">SelectStr Tutorial</span></span>

<span data-ttu-id="70553-103">이 섹션에서는 Windows PowerShell에서 제공 하는 [선택 문자열](/powershell/module/microsoft.powershell.utility/select-string) cmdlet과 매우 유사한 선택 Str cmdlet을 만드는 방법에 대 한 자습서를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="70553-103">This section provides a tutorial for creating the Select-Str cmdlet, which is very similar to the [Select-String](/powershell/module/microsoft.powershell.utility/select-string) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="70553-104">이 자습서에서는 cmdlet을 구현 하는 방법과 코드에 대 한 설명을 보여 주는 코드 조각을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="70553-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topic-in-this-tutorial"></a><span data-ttu-id="70553-105">이 자습서의 항목</span><span class="sxs-lookup"><span data-stu-id="70553-105">Topic in this Tutorial</span></span>

<span data-ttu-id="70553-106">[Cmdlet을 만들어 데이터 저장소 액세스](./creating-a-cmdlet-to-access-a-data-store.md) 이 섹션에서는 파일이 나 개체에 있는 문자열을 선택 하는 cmdlet을 만드는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="70553-106">[Creating a Cmdlet to Access a Data Store](./creating-a-cmdlet-to-access-a-data-store.md) This section describes how to create a cmdlet that selects strings that are in a file or object.</span></span>

## <a name="see-also"></a><span data-ttu-id="70553-107">참고 항목</span><span class="sxs-lookup"><span data-stu-id="70553-107">See Also</span></span>

[<span data-ttu-id="70553-108">데이터 저장소에 액세스하는 Cmdlet 만들기</span><span class="sxs-lookup"><span data-stu-id="70553-108">Creating a Cmdlet to Access a Data Store</span></span>](./creating-a-cmdlet-to-access-a-data-store.md)

[<span data-ttu-id="70553-109">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="70553-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
