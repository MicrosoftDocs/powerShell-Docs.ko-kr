---
title: Windows PowerShell Cmdlet 작성 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a82aba91-71af-447d-b9ef-b6b6ac7d9de4
caps.latest.revision: 19
ms.openlocfilehash: d1abdca9ecbb5ab0a13593072e6dcb0d647b0b14
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066994"
---
# <a name="writing-a-windows-powershell-cmdlet"></a><span data-ttu-id="61b40-102">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="61b40-102">Writing a Windows PowerShell Cmdlet</span></span>

<span data-ttu-id="61b40-103">"Windows PowerShell Cmdlet 작성" 있고 cmdlet를 디자인 하는 프로그램 관리자에 대 한 cmdlet 코드를 구현 하는 개발자입니다.</span><span class="sxs-lookup"><span data-stu-id="61b40-103">"Writing a Windows PowerShell Cmdlet" is for program managers who are designing cmdlets and for developers who are implementing cmdlet code.</span></span> <span data-ttu-id="61b40-104">Cmdlet의 작동 방식을 이해 하는 데 도움이 됩니다, cmdlet 작성을 시작 하는 데 사용할 수 있는 샘플 코드를 제공 하 고 cmdlet 코드 숨김 기초를 배울 사용할 수 있는 자습서가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="61b40-104">It will help you understand how cmdlets work, it provides sample code that you can use to start writing cmdlets, and it includes tutorials that you can use to learn the fundamentals behind the cmdlet code.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="61b40-105">이 섹션의 내용</span><span class="sxs-lookup"><span data-stu-id="61b40-105">In This Section</span></span>

<span data-ttu-id="61b40-106">[Cmdlet 개요](./cmdlet-overview.md) 이 항목에서는 어떤 cmdlet은의 개요를 제공 하 고 알아야 할 몇 가지 중요 용어입니다.</span><span class="sxs-lookup"><span data-stu-id="61b40-106">[Cmdlet Overview](./cmdlet-overview.md) This topic provides an overview of what a cmdlet is and of some important terms you need to know.</span></span>

<span data-ttu-id="61b40-107">[Windows PowerShell Cmdlet 개념](./windows-powershell-cmdlet-concepts.md) cmdlet 이란 무엇 이며 작동 방식에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="61b40-107">[Windows PowerShell Cmdlet Concepts](./windows-powershell-cmdlet-concepts.md) This section describes what cmdlets are and how they work.</span></span>

<span data-ttu-id="61b40-108">[Cmdlet 코드 예가](./examples-of-cmdlet-code.md) 이 섹션에서는 사용자 고유의 cmdlet을 작성 하려면 사용할 수 있는 예제 코드를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="61b40-108">[Examples of Cmdlet Code](./examples-of-cmdlet-code.md) This section contains example code that you can use to start writing your own cmdlets.</span></span>

<span data-ttu-id="61b40-109">[Cmdlet 출력 서식 지정 예가](https://msdn.microsoft.com/en-us/65829249-124d-47d0-9bf3-8e397dc55855) 이 섹션에서는 cmdlet 출력의 서식을 지정 하는 방법을 보여주는 예제를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="61b40-109">[Examples of Formatting Cmdlet Output](https://msdn.microsoft.com/en-us/65829249-124d-47d0-9bf3-8e397dc55855) This section contains examples that demonstrate how to format cmdlet output.</span></span>

<span data-ttu-id="61b40-110">[쓰기 Cmdlet에 대 한 자습서](./tutorials-for-writing-cmdlets.md) 이 섹션에서는 cmdlet 코드와 관련 기본 사항에 대해 자세히 알아보려면 사용할 수 있는 자습서가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="61b40-110">[Tutorials for Writing Cmdlets](./tutorials-for-writing-cmdlets.md) This section contains tutorials that you can use to learn about the fundamentals behind the cmdlet code.</span></span>

<span data-ttu-id="61b40-111">[Cmdlet 샘플](./cmdlet-samples.md) 이 섹션에서는 전체 cmdlet 샘플이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="61b40-111">[Cmdlet Samples](./cmdlet-samples.md) This section contains samples of complete cmdlets.</span></span>

## <a name="reference"></a><span data-ttu-id="61b40-112">참조</span><span class="sxs-lookup"><span data-stu-id="61b40-112">Reference</span></span>

[<span data-ttu-id="61b40-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="61b40-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
