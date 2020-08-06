---
title: OutputType 특성 선언 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a4cc874031bba092cfef6041bef0e19e6af3f09c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786546"
---
# <a name="outputtype-attribute-declaration"></a><span data-ttu-id="b6594-102">OutputType 특성 선언</span><span class="sxs-lookup"><span data-stu-id="b6594-102">OutputType Attribute Declaration</span></span>

<span data-ttu-id="b6594-103">`OutputType`특성은 cmdlet, 함수 또는 스크립트에서 반환 하는 .NET Framework 유형을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6594-103">The `OutputType` attribute identifies the .NET Framework types returned by a cmdlet, function, or script.</span></span>

## <a name="syntax"></a><span data-ttu-id="b6594-104">구문</span><span class="sxs-lookup"><span data-stu-id="b6594-104">Syntax</span></span>

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="b6594-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="b6594-105">Parameters</span></span>

<span data-ttu-id="b6594-106">( `string[]` 또는)를 입력 `Type[]` 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6594-106">Type (`string[]` or `Type[]`) Required.</span></span> <span data-ttu-id="b6594-107">Cmdlet 함수 또는 스크립트에서 반환 되는 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6594-107">Specifies the types returned by the cmdlet function, or script.</span></span>

<span data-ttu-id="b6594-108">ParameterSetName (string []) 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="b6594-108">ParameterSetName (string[]) Optional.</span></span> <span data-ttu-id="b6594-109">매개 변수에 지정 된 형식을 반환 하는 매개 변수 집합을 지정 합니다 `type` .</span><span class="sxs-lookup"><span data-stu-id="b6594-109">Specifies the parameter sets that return the types specified in the `type` parameter.</span></span>

<span data-ttu-id="b6594-110">providerCmdlet 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="b6594-110">providerCmdlet Optional.</span></span> <span data-ttu-id="b6594-111">매개 변수에 지정 된 형식을 반환 하는 공급자 cmdlet을 지정 합니다 `type` .</span><span class="sxs-lookup"><span data-stu-id="b6594-111">Specifies the provider cmdlet that returns the types specified in the `type` parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="b6594-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b6594-112">See Also</span></span>

[<span data-ttu-id="b6594-113">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="b6594-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
