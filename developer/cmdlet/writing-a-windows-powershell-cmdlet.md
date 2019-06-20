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
ms.openlocfilehash: 743efcf23174a9521925c5c19dd670979bc0c523
ms.sourcegitcommit: 13f24786ed39ca1c07eff2b73a1974c366e31cb8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2019
ms.locfileid: "67263819"
---
# <a name="writing-a-windows-powershell-cmdlet"></a><span data-ttu-id="ffc40-102">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="ffc40-102">Writing a Windows PowerShell Cmdlet</span></span>

<span data-ttu-id="ffc40-103">"Windows PowerShell Cmdlet 작성" 있고 cmdlet를 디자인 하는 프로그램 관리자에 대 한 cmdlet 코드를 구현 하는 개발자입니다.</span><span class="sxs-lookup"><span data-stu-id="ffc40-103">"Writing a Windows PowerShell Cmdlet" is for program managers who are designing cmdlets and for developers who are implementing cmdlet code.</span></span> <span data-ttu-id="ffc40-104">Cmdlet의 작동 방식을 이해 하는 데 도움이 됩니다, cmdlet 작성을 시작 하는 데 사용할 수 있는 샘플 코드를 제공 하 고 cmdlet 코드 숨김 기초를 배울 사용할 수 있는 자습서가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ffc40-104">It will help you understand how cmdlets work, it provides sample code that you can use to start writing cmdlets, and it includes tutorials that you can use to learn the fundamentals behind the cmdlet code.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="ffc40-105">이 섹션의 내용</span><span class="sxs-lookup"><span data-stu-id="ffc40-105">In This Section</span></span>

<span data-ttu-id="ffc40-106">[Cmdlet 개요](./cmdlet-overview.md) 이 항목에서는 어떤 cmdlet은의 개요를 제공 하 고 알아야 할 몇 가지 중요 용어입니다.</span><span class="sxs-lookup"><span data-stu-id="ffc40-106">[Cmdlet Overview](./cmdlet-overview.md) This topic provides an overview of what a cmdlet is and of some important terms you need to know.</span></span>

<span data-ttu-id="ffc40-107">[Windows PowerShell Cmdlet 개념](./windows-powershell-cmdlet-concepts.md) cmdlet 이란 무엇 이며 작동 방식에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffc40-107">[Windows PowerShell Cmdlet Concepts](./windows-powershell-cmdlet-concepts.md) This section describes what cmdlets are and how they work.</span></span>

<span data-ttu-id="ffc40-108">[Cmdlet 코드 예가](./examples-of-cmdlet-code.md) 이 섹션에서는 사용자 고유의 cmdlet을 작성 하려면 사용할 수 있는 예제 코드를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffc40-108">[Examples of Cmdlet Code](./examples-of-cmdlet-code.md) This section contains example code that you can use to start writing your own cmdlets.</span></span>

<span data-ttu-id="ffc40-109">[Cmdlet 출력에 대 한 서식 파일을 쓰는](../format/writing-a-powershell-formatting-file.md) 이 섹션에서는 서식 파일을 만드는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffc40-109">[Writing Formatting Files for Cmdlet Output](../format/writing-a-powershell-formatting-file.md) This section describe how to create formatting files.</span></span> <span data-ttu-id="ffc40-110">서식 파일 PowerShell 명령줄에서 개체를 표시 하는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffc40-110">Formatting files define how PowerShell displays objects at the command line.</span></span>

<span data-ttu-id="ffc40-111">[쓰기 Cmdlet에 대 한 자습서](./tutorials-for-writing-cmdlets.md) 이 섹션에서는 cmdlet 코드와 관련 기본 사항에 대해 자세히 알아보려면 사용할 수 있는 자습서가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ffc40-111">[Tutorials for Writing Cmdlets](./tutorials-for-writing-cmdlets.md) This section contains tutorials that you can use to learn about the fundamentals behind the cmdlet code.</span></span>

<span data-ttu-id="ffc40-112">[Cmdlet 샘플](./cmdlet-samples.md) 이 섹션에서는 전체 cmdlet 샘플이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ffc40-112">[Cmdlet Samples](./cmdlet-samples.md) This section contains samples of complete cmdlets.</span></span>

## <a name="reference"></a><span data-ttu-id="ffc40-113">참조</span><span class="sxs-lookup"><span data-stu-id="ffc40-113">Reference</span></span>

[<span data-ttu-id="ffc40-114">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ffc40-114">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
