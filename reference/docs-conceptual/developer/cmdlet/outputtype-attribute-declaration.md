---
ms.date: 09/13/2016
ms.topic: reference
title: OutputType 특성 선언
description: OutputType 특성 선언
ms.openlocfilehash: b5e33346e9ac29c13323781d62daffab892573a4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646452"
---
# <a name="outputtype-attribute-declaration"></a><span data-ttu-id="2199c-103">OutputType 특성 선언</span><span class="sxs-lookup"><span data-stu-id="2199c-103">OutputType Attribute Declaration</span></span>

<span data-ttu-id="2199c-104">`OutputType`특성은 cmdlet, 함수 또는 스크립트에서 반환 하는 .NET Framework 유형을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="2199c-104">The `OutputType` attribute identifies the .NET Framework types returned by a cmdlet, function, or script.</span></span>

## <a name="syntax"></a><span data-ttu-id="2199c-105">구문</span><span class="sxs-lookup"><span data-stu-id="2199c-105">Syntax</span></span>

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="2199c-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="2199c-106">Parameters</span></span>

<span data-ttu-id="2199c-107">( `string[]` 또는)를 입력 `Type[]` 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2199c-107">Type (`string[]` or `Type[]`) Required.</span></span> <span data-ttu-id="2199c-108">Cmdlet 함수 또는 스크립트에서 반환 되는 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2199c-108">Specifies the types returned by the cmdlet function, or script.</span></span>

<span data-ttu-id="2199c-109">ParameterSetName (string []) 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="2199c-109">ParameterSetName (string[]) Optional.</span></span> <span data-ttu-id="2199c-110">매개 변수에 지정 된 형식을 반환 하는 매개 변수 집합을 지정 합니다 `type` .</span><span class="sxs-lookup"><span data-stu-id="2199c-110">Specifies the parameter sets that return the types specified in the `type` parameter.</span></span>

<span data-ttu-id="2199c-111">providerCmdlet 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="2199c-111">providerCmdlet Optional.</span></span> <span data-ttu-id="2199c-112">매개 변수에 지정 된 형식을 반환 하는 공급자 cmdlet을 지정 합니다 `type` .</span><span class="sxs-lookup"><span data-stu-id="2199c-112">Specifies the provider cmdlet that returns the types specified in the `type` parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="2199c-113">관련 항목</span><span class="sxs-lookup"><span data-stu-id="2199c-113">See Also</span></span>

[<span data-ttu-id="2199c-114">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="2199c-114">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
