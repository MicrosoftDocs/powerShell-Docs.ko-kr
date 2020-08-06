---
title: Format 매개 변수 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c8e031f62aa8bcb0e9d5b900b2eace7187b1f3dd
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784285"
---
# <a name="format-parameters"></a><span data-ttu-id="89481-102">형식 매개 변수</span><span class="sxs-lookup"><span data-stu-id="89481-102">Format Parameters</span></span>

<span data-ttu-id="89481-103">다음 표에서는 데이터를 포맷 하거나 생성 하는 데 사용 되는 매개 변수의 권장 이름 및 기능을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="89481-103">The following table lists recommended names and functionality for parameters that are used to format or to generate data.</span></span>

|<span data-ttu-id="89481-104">매개 변수</span><span class="sxs-lookup"><span data-stu-id="89481-104">Parameter</span></span>|<span data-ttu-id="89481-105">기능</span><span class="sxs-lookup"><span data-stu-id="89481-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="89481-106">**는**</span><span class="sxs-lookup"><span data-stu-id="89481-106">**As**</span></span><br><span data-ttu-id="89481-107">데이터 형식: 키워드</span><span class="sxs-lookup"><span data-stu-id="89481-107">Data type: Keyword</span></span>|<span data-ttu-id="89481-108">Cmdlet 출력 형식을 지정 하려면이 매개 변수를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="89481-108">Implement this parameter to specify the cmdlet output format.</span></span> <span data-ttu-id="89481-109">예를 들어 가능한 값은 텍스트 또는 스크립트 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89481-109">For example, possible values could be Text or Script.</span></span>|
|<span data-ttu-id="89481-110">**이진**</span><span class="sxs-lookup"><span data-stu-id="89481-110">**Binary**</span></span><br><span data-ttu-id="89481-111">데이터 형식: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="89481-111">Data type: SwitchParameter</span></span>|<span data-ttu-id="89481-112">Cmdlet이 이진 값을 처리 함을 나타내려면이 매개 변수를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="89481-112">Implement this parameter to indicate that the cmdlet handles binary values.</span></span>|
|<span data-ttu-id="89481-113">**인코딩**</span><span class="sxs-lookup"><span data-stu-id="89481-113">**Encoding**</span></span><br><span data-ttu-id="89481-114">데이터 형식: 키워드</span><span class="sxs-lookup"><span data-stu-id="89481-114">Data type: Keyword</span></span>|<span data-ttu-id="89481-115">이 매개 변수를 구현 하 여 지원 되는 인코딩 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="89481-115">Implement this parameter to specify the type of encoding that is supported.</span></span> <span data-ttu-id="89481-116">예를 들어 가능한 값은 ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte 및 String 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89481-116">For example, possible values could be ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte, and String.</span></span>|
|<span data-ttu-id="89481-117">**줄**</span><span class="sxs-lookup"><span data-stu-id="89481-117">**NewLine**</span></span><br><span data-ttu-id="89481-118">데이터 형식: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="89481-118">Data type: SwitchParameter</span></span>|<span data-ttu-id="89481-119">매개 변수를 지정할 때 줄 바꿈 문자가 지원 되도록이 매개 변수를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="89481-119">Implement this parameter so that the newline characters are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="89481-120">**ShortName**</span><span class="sxs-lookup"><span data-stu-id="89481-120">**ShortName**</span></span><br><span data-ttu-id="89481-121">데이터 형식: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="89481-121">Data type: SwitchParameter</span></span>|<span data-ttu-id="89481-122">매개 변수를 지정할 때 짧은 이름이 지원 되도록이 매개 변수를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="89481-122">Implement this parameter so that short names are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="89481-123">**Width**</span><span class="sxs-lookup"><span data-stu-id="89481-123">**Width**</span></span><br><span data-ttu-id="89481-124">데이터 형식: Int32</span><span class="sxs-lookup"><span data-stu-id="89481-124">Data type: Int32</span></span>|<span data-ttu-id="89481-125">사용자가 출력 장치의 너비를 지정할 수 있도록이 매개 변수를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="89481-125">Implement this parameter so that the user can specify the width of the output device.</span></span>|
|<span data-ttu-id="89481-126">**래핑**</span><span class="sxs-lookup"><span data-stu-id="89481-126">**Wrap**</span></span><br><span data-ttu-id="89481-127">데이터 형식: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="89481-127">Data type: SwitchParameter</span></span>|<span data-ttu-id="89481-128">매개 변수를 지정할 때 텍스트 줄 바꿈이 지원 되도록 하려면이 매개 변수를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="89481-128">Implement this parameter so that text wrapping is supported when the parameter is specified.</span></span>|
## <a name="see-also"></a><span data-ttu-id="89481-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="89481-129">See Also</span></span>

[<span data-ttu-id="89481-130">Cmdlet 매개 변수</span><span class="sxs-lookup"><span data-stu-id="89481-130">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="89481-131">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="89481-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="89481-132">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="89481-132">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
