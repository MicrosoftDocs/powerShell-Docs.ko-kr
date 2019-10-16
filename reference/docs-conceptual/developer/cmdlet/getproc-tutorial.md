---
title: GetProc 자습서 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4663905f-560a-4e39-9b03-6db2c315c322
caps.latest.revision: 6
ms.openlocfilehash: bbd07a0d0abd30742b7e02482adedae3af43aca4
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364442"
---
# <a name="getproc-tutorial"></a><span data-ttu-id="50e29-102">GetProc 자습서</span><span class="sxs-lookup"><span data-stu-id="50e29-102">GetProc Tutorial</span></span>

<span data-ttu-id="50e29-103">이 섹션에서는 Windows PowerShell에서 제공 하는 [Get Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet과 매우 유사한 cmdlet을 만드는 방법에 대 한 자습서를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="50e29-103">This section provides a tutorial for creating a Get-Proc cmdlet that is very similar to the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="50e29-104">이 자습서에서는 cmdlet을 구현 하는 방법과 코드에 대 한 설명을 보여 주는 코드 조각을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="50e29-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="50e29-105">이 자습서의 항목</span><span class="sxs-lookup"><span data-stu-id="50e29-105">Topics in this Tutorial</span></span>

<span data-ttu-id="50e29-106">이 자습서의 항목은 순차적으로 읽을 수 있도록 설계 되었습니다. 각 항목은 이전 항목에서 설명한 내용에 대 한 정보를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="50e29-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="50e29-107">[매개 변수를 사용 하지 않고 Cmdlet 만들기](./creating-a-cmdlet-without-parameters.md) 이 섹션에서는 매개 변수를 사용 하지 않고 로컬 컴퓨터에서 정보를 검색 한 다음 파이프라인에 정보를 기록 하는 cmdlet을 만드는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="50e29-107">[Creating a Cmdlet without Parameters](./creating-a-cmdlet-without-parameters.md) This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="50e29-108">[명령줄 입력을 처리 하는 매개 변수 추가](./adding-parameters-that-process-command-line-input.md) 이 섹션에서는 cmdlet이 cmdlet에 전달 된 명시적 개체를 기반으로 하는 입력을 처리할 수 있도록 매개 변수를 Get Proc cmdlet에 추가 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="50e29-108">[Adding Parameters that Process Command-Line Input](./adding-parameters-that-process-command-line-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process input based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="50e29-109">여기에 설명 된 구현은 해당 이름에 따라 프로세스를 검색 한 다음 파이프라인에 정보를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="50e29-109">The implementation described here retrieves processes based on their name, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="50e29-110">[파이프라인 입력을 처리 하는 매개 변수 추가](./adding-parameters-that-process-pipeline-input.md) 이 섹션에서는 cmdlet이 파이프라인을 통해 전달 된 개체를 처리할 수 있도록 Get Proc cmdlet에 매개 변수를 추가 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="50e29-110">[Adding Parameters that Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process objects passed to it through the pipeline.</span></span> <span data-ttu-id="50e29-111">여기에 설명 된 구현 cmdlet은 cmdlet에 전달 된 개체를 기반으로 하는 프로세스를 검색 한 다음 파이프라인에 정보를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="50e29-111">The implementation cmdlet described here retrieves processes based on objects passed to the cmdlet, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="50e29-112">[비 종료 오류 보고를 Cmdlet에 추가](./adding-non-terminating-error-reporting-to-your-cmdlet.md) 이 섹션에서는 종료 되지 않는 오류 보고를 cmdlet에 추가 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="50e29-112">[Adding Nonterminating Error Reporting to Your Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) This section describes how to add nonterminating error reporting to a cmdlet.</span></span> <span data-ttu-id="50e29-113">여기서 설명 하는 구현에서는 입력을 처리할 때 발생 하는 종료 되지 않는 오류를 검색 하 고 오류 레코드를 오류 스트림에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="50e29-113">The implementation described here detects nonterminating errors that occur when processing input, and writes an error record to the error stream.</span></span>

## <a name="see-also"></a><span data-ttu-id="50e29-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="50e29-114">See Also</span></span>

[<span data-ttu-id="50e29-115">매개 변수를 사용 하지 않고 Cmdlet 만들기</span><span class="sxs-lookup"><span data-stu-id="50e29-115">Creating a Cmdlet without Parameters</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="50e29-116">명령줄 입력을 처리 하는 매개 변수 추가</span><span class="sxs-lookup"><span data-stu-id="50e29-116">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="50e29-117">파이프라인 입력을 처리 하는 매개 변수 추가</span><span class="sxs-lookup"><span data-stu-id="50e29-117">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="50e29-118">비 종료 오류 보고를 Cmdlet에 추가</span><span class="sxs-lookup"><span data-stu-id="50e29-118">Adding Nonterminating Error Reporting to Your Cmdlet</span></span>](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[<span data-ttu-id="50e29-119">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="50e29-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
