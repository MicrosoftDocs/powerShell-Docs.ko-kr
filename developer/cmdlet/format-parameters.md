---
title: 매개 변수 형식 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10e025c5-9aa6-45a5-b851-23d14db1f4cc
caps.latest.revision: 7
ms.openlocfilehash: 0bd3888d81aa6d1dde26c0066f7bca9dac8a8bca
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251186"
---
# <a name="format-parameters"></a><span data-ttu-id="473b2-102">형식 매개 변수</span><span class="sxs-lookup"><span data-stu-id="473b2-102">Format Parameters</span></span>

<span data-ttu-id="473b2-103">다음 표에서 권장 되는 이름 및 형식을 지정 하거나 데이터를 생성 하는 매개 변수에 대 한 기능을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="473b2-103">The following table lists recommended names and functionality for parameters that are used to format or to generate data.</span></span>

|<span data-ttu-id="473b2-104">매개 변수</span><span class="sxs-lookup"><span data-stu-id="473b2-104">Parameter</span></span>|<span data-ttu-id="473b2-105">기능</span><span class="sxs-lookup"><span data-stu-id="473b2-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="473b2-106">**As**</span><span class="sxs-lookup"><span data-stu-id="473b2-106">**As**</span></span><br><span data-ttu-id="473b2-107">데이터 형식: 키워드</span><span class="sxs-lookup"><span data-stu-id="473b2-107">Data type: Keyword</span></span>|<span data-ttu-id="473b2-108">Cmdlet 출력 형식을 지정 하려면이 매개 변수를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="473b2-108">Implement this parameter to specify the cmdlet output format.</span></span> <span data-ttu-id="473b2-109">예를 들어 가능한 값은 텍스트 또는 스크립트 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="473b2-109">For example, possible values could be Text or Script.</span></span>|
|<span data-ttu-id="473b2-110">**이진**</span><span class="sxs-lookup"><span data-stu-id="473b2-110">**Binary**</span></span><br><span data-ttu-id="473b2-111">데이터 형식: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="473b2-111">Data type: SwitchParameter</span></span>|<span data-ttu-id="473b2-112">Cmdlet에서 이진 값을 처리 하는 것을 나타내려면이 매개 변수를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="473b2-112">Implement this parameter to indicate that the cmdlet handles binary values.</span></span>|
|<span data-ttu-id="473b2-113">**인코딩**</span><span class="sxs-lookup"><span data-stu-id="473b2-113">**Encoding**</span></span><br><span data-ttu-id="473b2-114">데이터 형식: 키워드</span><span class="sxs-lookup"><span data-stu-id="473b2-114">Data type: Keyword</span></span>|<span data-ttu-id="473b2-115">지원 되는 인코딩 유형을 지정 하려면이 매개 변수를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="473b2-115">Implement this parameter to specify the type of encoding that is supported.</span></span> <span data-ttu-id="473b2-116">예를 들어 가능한 값은 ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, 바이트 및 문자열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="473b2-116">For example, possible values could be ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte, and String.</span></span>|
|<span data-ttu-id="473b2-117">**NewLine**</span><span class="sxs-lookup"><span data-stu-id="473b2-117">**NewLine**</span></span><br><span data-ttu-id="473b2-118">데이터 형식: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="473b2-118">Data type: SwitchParameter</span></span>|<span data-ttu-id="473b2-119">매개 변수를 지정 하는 줄 바꿈 문자를 사용할 수 있도록이 매개 변수를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="473b2-119">Implement this parameter so that the newline characters are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="473b2-120">**ShortName**</span><span class="sxs-lookup"><span data-stu-id="473b2-120">**ShortName**</span></span><br><span data-ttu-id="473b2-121">데이터 형식: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="473b2-121">Data type: SwitchParameter</span></span>|<span data-ttu-id="473b2-122">매개 변수를 지정 하는 경우 짧은 이름을 사용할 수 있도록이 매개 변수를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="473b2-122">Implement this parameter so that short names are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="473b2-123">**너비**</span><span class="sxs-lookup"><span data-stu-id="473b2-123">**Width**</span></span><br><span data-ttu-id="473b2-124">데이터 형식: Int32</span><span class="sxs-lookup"><span data-stu-id="473b2-124">Data type: Int32</span></span>|<span data-ttu-id="473b2-125">사용자는 출력 장치의 너비를 지정할 수 있도록이 매개 변수를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="473b2-125">Implement this parameter so that the user can specify the width of the output device.</span></span>|
|<span data-ttu-id="473b2-126">**Wrap**</span><span class="sxs-lookup"><span data-stu-id="473b2-126">**Wrap**</span></span><br><span data-ttu-id="473b2-127">데이터 형식: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="473b2-127">Data type: SwitchParameter</span></span>|<span data-ttu-id="473b2-128">매개 변수를 지정 하는 경우 텍스트 줄 바꿈을 사용할 수 있도록이 매개 변수를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="473b2-128">Implement this parameter so that text wrapping is supported when the parameter is specified.</span></span>|
## <a name="see-also"></a><span data-ttu-id="473b2-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="473b2-129">See Also</span></span>

[<span data-ttu-id="473b2-130">Cmdlet 매개 변수</span><span class="sxs-lookup"><span data-stu-id="473b2-130">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

<span data-ttu-id="473b2-131">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="473b2-131">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>

[<span data-ttu-id="473b2-132">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="473b2-132">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
