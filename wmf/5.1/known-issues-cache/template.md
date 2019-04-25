---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.topic: conceptual
title: 알려진 문제 및 제한 사항 기록에 대한 예제 템플릿
ms.openlocfilehash: 8c1004e16f78913174af2e519e451f6fd9f30ff7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055550"
---
 ><span data-ttu-id="3893e-103">참고: 제안된 설명이 포함된 제목과 간단한 설명을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3893e-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="3893e-104">예: 잘못된 ExecutionPolicy 오류</span><span class="sxs-lookup"><span data-stu-id="3893e-104">Example: Erroneous ExecutionPolicy errors</span></span>
<span data-ttu-id="3893e-105">Windows 7에서 PowerShell 모듈 및 DSC 리소스를 사용하면 ExecutionPolicy에 대해 오류가 보고될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3893e-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="3893e-106">해결 방법</span><span class="sxs-lookup"><span data-stu-id="3893e-106">Resolution</span></span>

<span data-ttu-id="3893e-107">해결하려면 다음 명령을 관리자 권한 PowerShell 세션에서 실행(관리자 권한으로 실행)하여 **ExecutionPolicy**를 **RemoteSigned**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3893e-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```
