---
ms.date: 09/13/2016
ms.topic: reference
title: 형식 매개 변수
description: 형식 매개 변수
ms.openlocfilehash: 5f970683fedc71b208ff6becad761d94611a91a6
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652815"
---
# <a name="format-parameters"></a><span data-ttu-id="40657-103">형식 매개 변수</span><span class="sxs-lookup"><span data-stu-id="40657-103">Format Parameters</span></span>

<span data-ttu-id="40657-104">다음 표에서는 데이터를 포맷 하거나 생성 하는 데 사용 되는 매개 변수의 권장 이름 및 기능을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="40657-104">The following table lists recommended names and functionality for parameters that are used to format or to generate data.</span></span>

|<span data-ttu-id="40657-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="40657-105">Parameter</span></span>|<span data-ttu-id="40657-106">기능</span><span class="sxs-lookup"><span data-stu-id="40657-106">Functionality</span></span>|
|---|---|
|<span data-ttu-id="40657-107">**는**</span><span class="sxs-lookup"><span data-stu-id="40657-107">**As**</span></span><br><span data-ttu-id="40657-108">데이터 형식: 키워드</span><span class="sxs-lookup"><span data-stu-id="40657-108">Data type: Keyword</span></span>|<span data-ttu-id="40657-109">Cmdlet 출력 형식을 지정 하려면이 매개 변수를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="40657-109">Implement this parameter to specify the cmdlet output format.</span></span> <span data-ttu-id="40657-110">예를 들어 가능한 값은 텍스트 또는 스크립트 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40657-110">For example, possible values could be Text or Script.</span></span>|
|<span data-ttu-id="40657-111">**이진**</span><span class="sxs-lookup"><span data-stu-id="40657-111">**Binary**</span></span><br><span data-ttu-id="40657-112">데이터 형식: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="40657-112">Data type: SwitchParameter</span></span>|<span data-ttu-id="40657-113">Cmdlet이 이진 값을 처리 함을 나타내려면이 매개 변수를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="40657-113">Implement this parameter to indicate that the cmdlet handles binary values.</span></span>|
|<span data-ttu-id="40657-114">**인코딩**</span><span class="sxs-lookup"><span data-stu-id="40657-114">**Encoding**</span></span><br><span data-ttu-id="40657-115">데이터 형식: 키워드</span><span class="sxs-lookup"><span data-stu-id="40657-115">Data type: Keyword</span></span>|<span data-ttu-id="40657-116">이 매개 변수를 구현 하 여 지원 되는 인코딩 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="40657-116">Implement this parameter to specify the type of encoding that is supported.</span></span> <span data-ttu-id="40657-117">예를 들어 가능한 값은 ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte 및 String 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40657-117">For example, possible values could be ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte, and String.</span></span>|
|<span data-ttu-id="40657-118">**줄**</span><span class="sxs-lookup"><span data-stu-id="40657-118">**NewLine**</span></span><br><span data-ttu-id="40657-119">데이터 형식: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="40657-119">Data type: SwitchParameter</span></span>|<span data-ttu-id="40657-120">매개 변수를 지정할 때 줄 바꿈 문자가 지원 되도록이 매개 변수를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="40657-120">Implement this parameter so that the newline characters are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="40657-121">**ShortName**</span><span class="sxs-lookup"><span data-stu-id="40657-121">**ShortName**</span></span><br><span data-ttu-id="40657-122">데이터 형식: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="40657-122">Data type: SwitchParameter</span></span>|<span data-ttu-id="40657-123">매개 변수를 지정할 때 짧은 이름이 지원 되도록이 매개 변수를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="40657-123">Implement this parameter so that short names are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="40657-124">**Width**</span><span class="sxs-lookup"><span data-stu-id="40657-124">**Width**</span></span><br><span data-ttu-id="40657-125">데이터 형식: Int32</span><span class="sxs-lookup"><span data-stu-id="40657-125">Data type: Int32</span></span>|<span data-ttu-id="40657-126">사용자가 출력 장치의 너비를 지정할 수 있도록이 매개 변수를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="40657-126">Implement this parameter so that the user can specify the width of the output device.</span></span>|
|<span data-ttu-id="40657-127">**래핑**</span><span class="sxs-lookup"><span data-stu-id="40657-127">**Wrap**</span></span><br><span data-ttu-id="40657-128">데이터 형식: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="40657-128">Data type: SwitchParameter</span></span>|<span data-ttu-id="40657-129">매개 변수를 지정할 때 텍스트 줄 바꿈이 지원 되도록 하려면이 매개 변수를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="40657-129">Implement this parameter so that text wrapping is supported when the parameter is specified.</span></span>|
## <a name="see-also"></a><span data-ttu-id="40657-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="40657-130">See Also</span></span>

[<span data-ttu-id="40657-131">Cmdlet 매개 변수</span><span class="sxs-lookup"><span data-stu-id="40657-131">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

<span data-ttu-id="40657-132">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="40657-132">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>

[<span data-ttu-id="40657-133">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="40657-133">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
