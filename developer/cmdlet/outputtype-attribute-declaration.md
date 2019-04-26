---
title: OutputType 특성 선언 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a97a98ee-ffc0-42f0-a9a6-b0717b39c798
caps.latest.revision: 5
ms.openlocfilehash: 7aa6fa407e509a31c4066c4f73ae01b02b2f338c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067606"
---
# <a name="outputtype-attribute-declaration"></a><span data-ttu-id="08575-102">OutputType 특성 선언</span><span class="sxs-lookup"><span data-stu-id="08575-102">OutputType Attribute Declaration</span></span>

<span data-ttu-id="08575-103">`OutputType` 특성은 cmdlet, 함수 또는 스크립트에서 반환 되는.NET Framework 형식 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="08575-103">The `OutputType` attribute identifies the .NET Framework types returned by a cmdlet, function, or script.</span></span>

## <a name="syntax"></a><span data-ttu-id="08575-104">구문</span><span class="sxs-lookup"><span data-stu-id="08575-104">Syntax</span></span>

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="08575-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="08575-105">Parameters</span></span>

<span data-ttu-id="08575-106">형식 (`string[]` 또는 `Type[]`) 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="08575-106">Type (`string[]` or `Type[]`) Required.</span></span> <span data-ttu-id="08575-107">Cmdlet은 함수 또는 스크립트에서 반환 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="08575-107">Specifies the types returned by the cmdlet function, or script.</span></span>

<span data-ttu-id="08575-108">ParameterSetName (시간이 걸린다는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="08575-108">ParameterSetName (string[]) Optional.</span></span> <span data-ttu-id="08575-109">에 지정 된 형식을 반환 하는 매개 변수 집합을 지정 합니다 `type` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="08575-109">Specifies the parameter sets that return the types specified in the `type` parameter.</span></span>

<span data-ttu-id="08575-110">providerCmdlet 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="08575-110">providerCmdlet Optional.</span></span> <span data-ttu-id="08575-111">에 지정 된 형식을 반환 하는 공급자 cmdlet은 지정 된 `type` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="08575-111">Specifies the provider cmdlet that returns the types specified in the `type` parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="08575-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="08575-112">See Also</span></span>

<span data-ttu-id="08575-113">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="08575-113">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
