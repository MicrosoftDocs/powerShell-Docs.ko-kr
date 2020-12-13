---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc 자습서
description: GetProc 자습서
ms.openlocfilehash: 9379e791dd5361fcf5b79061bf0a601ebeb84f42
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652779"
---
# <a name="getproc-tutorial"></a><span data-ttu-id="77f26-103">GetProc 자습서</span><span class="sxs-lookup"><span data-stu-id="77f26-103">GetProc Tutorial</span></span>

<span data-ttu-id="77f26-104">이 섹션에서는 Windows PowerShell에서 제공 하는 [Get Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet과 매우 유사한 Get-Proc cmdlet을 만드는 방법에 대 한 자습서를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="77f26-104">This section provides a tutorial for creating a Get-Proc cmdlet that is very similar to the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="77f26-105">이 자습서에서는 cmdlet을 구현 하는 방법과 코드에 대 한 설명을 보여 주는 코드 조각을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="77f26-105">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="77f26-106">이 자습서의 항목</span><span class="sxs-lookup"><span data-stu-id="77f26-106">Topics in this Tutorial</span></span>

<span data-ttu-id="77f26-107">이 자습서의 항목은 순차적으로 읽을 수 있도록 설계 되었습니다. 각 항목은 이전 항목에서 설명한 내용에 대 한 정보를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="77f26-107">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="77f26-108">[매개 변수를 사용 하지 않고 Cmdlet 만들기](./creating-a-cmdlet-without-parameters.md) 이 섹션에서는 매개 변수를 사용 하지 않고 로컬 컴퓨터에서 정보를 검색 한 다음 파이프라인에 정보를 기록 하는 cmdlet을 만드는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="77f26-108">[Creating a Cmdlet without Parameters](./creating-a-cmdlet-without-parameters.md) This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="77f26-109">[Command-Line 입력을 처리 하는 매개 변수 추가](./adding-parameters-that-process-command-line-input.md) 이 섹션에서는 cmdlet이 cmdlet에 전달 된 명시적 개체를 기반으로 하는 입력을 처리할 수 있도록 Get-Proc cmdlet에 매개 변수를 추가 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="77f26-109">[Adding Parameters that Process Command-Line Input](./adding-parameters-that-process-command-line-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process input based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="77f26-110">여기에 설명 된 구현은 해당 이름에 따라 프로세스를 검색 한 다음 파이프라인에 정보를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="77f26-110">The implementation described here retrieves processes based on their name, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="77f26-111">[파이프라인 입력을 처리 하는 매개 변수 추가](./adding-parameters-that-process-pipeline-input.md) 이 섹션에서는 cmdlet이 파이프라인을 통해 전달 된 개체를 처리할 수 있도록 Get-Proc cmdlet에 매개 변수를 추가 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="77f26-111">[Adding Parameters that Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process objects passed to it through the pipeline.</span></span> <span data-ttu-id="77f26-112">여기에 설명 된 구현 cmdlet은 cmdlet에 전달 된 개체를 기반으로 하는 프로세스를 검색 한 다음 파이프라인에 정보를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="77f26-112">The implementation cmdlet described here retrieves processes based on objects passed to the cmdlet, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="77f26-113">[비 종료 오류 보고를 Cmdlet에 추가](./adding-non-terminating-error-reporting-to-your-cmdlet.md) 이 섹션에서는 종료 되지 않는 오류 보고를 cmdlet에 추가 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="77f26-113">[Adding Nonterminating Error Reporting to Your Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) This section describes how to add nonterminating error reporting to a cmdlet.</span></span> <span data-ttu-id="77f26-114">여기서 설명 하는 구현에서는 입력을 처리할 때 발생 하는 종료 되지 않는 오류를 검색 하 고 오류 레코드를 오류 스트림에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="77f26-114">The implementation described here detects nonterminating errors that occur when processing input, and writes an error record to the error stream.</span></span>

## <a name="see-also"></a><span data-ttu-id="77f26-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="77f26-115">See Also</span></span>

[<span data-ttu-id="77f26-116">매개 변수 없이 Cmdlet 만들기</span><span class="sxs-lookup"><span data-stu-id="77f26-116">Creating a Cmdlet without Parameters</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="77f26-117">Command-Line 입력을 처리 하는 매개 변수 추가</span><span class="sxs-lookup"><span data-stu-id="77f26-117">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="77f26-118">파이프라인 입력을 처리하는 매개 변수 추가</span><span class="sxs-lookup"><span data-stu-id="77f26-118">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="77f26-119">비 종료 오류 보고를 Cmdlet에 추가</span><span class="sxs-lookup"><span data-stu-id="77f26-119">Adding Nonterminating Error Reporting to Your Cmdlet</span></span>](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[<span data-ttu-id="77f26-120">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="77f26-120">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
