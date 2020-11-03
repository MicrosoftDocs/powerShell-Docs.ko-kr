---
Download Help Link: https://aka.ms/powershell71-help
Help Version: 7.1.0.0
Locale: en-US
Module Guid: 0e7b895d-2fec-43f7-8cae-11e8d16f6e40
Module Name: ThreadJob
ms.date: 07/09/2019
title: ThreadJob 모듈
ms.openlocfilehash: 4a6abe107ac041f0ce5fa3e5d776bb0ac352685c
ms.sourcegitcommit: 84fcc90bd018ab76ac4e964d53e7c9c2b5a7b6c6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93218866"
---
# <span data-ttu-id="74ced-102">ThreadJob 모듈</span><span class="sxs-lookup"><span data-stu-id="74ced-102">ThreadJob Module</span></span>

## <span data-ttu-id="74ced-103">설명</span><span class="sxs-lookup"><span data-stu-id="74ced-103">Description</span></span>
<span data-ttu-id="74ced-104">이 모듈은 새 스레드 기반 **Threadjob** 작업을 포함 하도록 기존 PowerShell BackgroundJob를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="74ced-104">This module extends the existing PowerShell BackgroundJob to include a new thread based **ThreadJob** job.</span></span> <span data-ttu-id="74ced-105">이는 기존 PowerShell 작업 인프라 내에서 작동 하는 동시 PowerShell 스크립트를 실행 하는 데 사용할 수 있는 더 간단한 솔루션입니다.</span><span class="sxs-lookup"><span data-stu-id="74ced-105">This is a lighter weight solution for running concurrent PowerShell scripts that works within the existing PowerShell job infrastructure.</span></span>

## <span data-ttu-id="74ced-106">ThreadJob Cmdlet</span><span class="sxs-lookup"><span data-stu-id="74ced-106">ThreadJob Cmdlets</span></span>

### [<span data-ttu-id="74ced-107">Start-ThreadJob</span><span class="sxs-lookup"><span data-stu-id="74ced-107">Start-ThreadJob</span></span>](Start-ThreadJob.md)
<span data-ttu-id="74ced-108">Cmdlet과 비슷한 백그라운드 작업을 만듭니다 `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="74ced-108">Creates background jobs similar to the `Start-Job` cmdlet.</span></span>
