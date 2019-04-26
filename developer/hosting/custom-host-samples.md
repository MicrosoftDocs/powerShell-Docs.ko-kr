---
title: 사용자 지정 호스트 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55aee25b-bbcb-4d41-a4c0-fb8e30c4cdc1
caps.latest.revision: 11
ms.openlocfilehash: 1e58b74cf1c37c70ebfb0f4970cfbf8a8263ec5c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082926"
---
# <a name="custom-host-samples"></a><span data-ttu-id="92f9d-102">사용자 지정 호스트 샘플</span><span class="sxs-lookup"><span data-stu-id="92f9d-102">Custom Host Samples</span></span>

<span data-ttu-id="92f9d-103">이 섹션에서는 사용자 지정 호스트를 작성 하기 위한 샘플 코드를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="92f9d-103">This section includes sample code for writing a custom host.</span></span> <span data-ttu-id="92f9d-104">콘솔 응용 프로그램을 만들고 다음 호스트 응용 프로그램에이 섹션의 항목에서 코드를 복사 하려면 Microsoft Visual Studio를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="92f9d-104">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="92f9d-105">이 섹션의 내용</span><span class="sxs-lookup"><span data-stu-id="92f9d-105">In This Section</span></span>

 <span data-ttu-id="92f9d-106">[Host01 샘플](./host01-sample.md) 이 샘플에서는 기본 사용자 지정 호스트를 사용 하는 호스트 응용 프로그램을 구현 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="92f9d-106">[Host01 Sample](./host01-sample.md) This sample shows how to implement a host application that uses a basic custom host.</span></span>

 <span data-ttu-id="92f9d-107">[Host02 샘플](./host02-sample.md) 이 샘플에서는 사용자 지정 호스트 구현과 함께 Windows PowerShell 런타임을 사용 하는 호스트 응용 프로그램을 작성 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="92f9d-107">[Host02 Sample](./host02-sample.md) This sample shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span> <span data-ttu-id="92f9d-108">독일어로 실행은 호스트 문화권을 설정 하는 호스트 응용 프로그램을 [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet 및 표시 하면 결과 보았을 pwrsh.exe를 및 현재 날짜와 시간을 다음 출력을 사용 하 여 독일어로 합니다.</span><span class="sxs-lookup"><span data-stu-id="92f9d-108">The host application sets the host culture to German, runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet and displays the results as you would see them using pwrsh.exe, and then prints out the current data and time in German.</span></span>

 <span data-ttu-id="92f9d-109">[Host03 샘플](./host03-sample.md) 이 샘플에서는 명령줄에서 명령을 읽고 명령을 실행 하 고 다음 콘솔에 결과 표시 하는 대화형 콘솔 기반 호스트 응용 프로그램을 빌드하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="92f9d-109">[Host03 Sample](./host03-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>

 <span data-ttu-id="92f9d-110">[Host04 샘플](./host04-sample.md) 이 샘플에서는 명령줄에서 명령을 읽고 명령을 실행 하 고 다음 콘솔에 결과 표시 하는 대화형 콘솔 기반 호스트 응용 프로그램을 빌드하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="92f9d-110">[Host04 Sample](./host04-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="92f9d-111">이 호스트 애플리케이션은 사용자가 여러 선택 항목을 지정할 수 있는 프롬프트 표시도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="92f9d-111">This host application also supports displaying prompts that allow the user to specify multiple choices.</span></span>

 <span data-ttu-id="92f9d-112">[Host05 샘플](./host05-sample.md) 이 샘플에서는 명령줄에서 명령을 읽고 명령을 실행 하 고 다음 콘솔에 결과 표시 하는 대화형 콘솔 기반 호스트 응용 프로그램을 빌드하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="92f9d-112">[Host05 Sample](./host05-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="92f9d-113">또한이 호스트 응용 프로그램 사용 하 여 원격 컴퓨터에 대 한 호출을 지원 합니다 [Enter-pssession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) 하 고 [Exit-pssession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlet</span><span class="sxs-lookup"><span data-stu-id="92f9d-113">This host application also supports calls to remote computers by using the [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) and [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets</span></span>

 <span data-ttu-id="92f9d-114">[Host06 샘플](./host06-sample.md) 이 샘플에서는 명령줄에서 명령을 읽고 명령을 실행 하 고 다음 콘솔에 결과 표시 하는 대화형 콘솔 기반 호스트 응용 프로그램을 빌드하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="92f9d-114">[Host06 Sample](./host06-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="92f9d-115">또한 이 샘플에서는 토크나이저 API를 사용하여 사용자가 입력하는 텍스트의 색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="92f9d-115">In addition, this sample uses the Tokenizer APIs to specify the color of the text that is entered by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="92f9d-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="92f9d-116">See Also</span></span>
