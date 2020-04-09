---
title: RunSpace08 코드 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f286201-8a02-4b00-9a2c-1b833ccdbdbf
caps.latest.revision: 7
ms.openlocfilehash: 21d7c4fe69e5026089676c43ad69a4263732cc34
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978256"
---
# <a name="runspace08-code-sample"></a><span data-ttu-id="8ae09-102">RunSpace08 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="8ae09-102">RunSpace08 Code Sample</span></span>

<span data-ttu-id="8ae09-103">다음은 [명령에 매개 변수를 추가 하는 콘솔 응용 프로그램 만들기](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba)에서 설명한 Runspace08 샘플의 소스 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="8ae09-103">Here is the source code for the Runspace08 sample described in [Creating a Console Application That Adds Parameters to a Command](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span></span>
<span data-ttu-id="8ae09-104">이 샘플 응용 프로그램은 runspace를 만들고, 파이프라인을 만들고, 파이프라인에 두 개의 명령을 추가 하 고, 두 번째 명령에 두 개의 매개 변수를 추가한 다음, 파이프라인을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ae09-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, adds two parameters to the second command, and then executes the pipeline.</span></span> <span data-ttu-id="8ae09-105">파이프라인에 추가 되는 명령은 `Get-Process` 및 `Sort-Object` cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="8ae09-105">The commands that are added to the pipeline are the `Get-Process` and `Sort-Object` cmdlets.</span></span>

## <a name="code-sample"></a><span data-ttu-id="8ae09-106">코드 예제</span><span class="sxs-lookup"><span data-stu-id="8ae09-106">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs" range="11-86":::

## <a name="see-also"></a><span data-ttu-id="8ae09-107">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8ae09-107">See Also</span></span>

[<span data-ttu-id="8ae09-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="8ae09-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
