---
ms.date: 09/13/2016
ms.topic: reference
title: 사용자 지정 호스트 샘플
description: 사용자 지정 호스트 샘플
ms.openlocfilehash: 939b9f5d6bbc3ccf1ac95343e897ecffef0a2f42
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649312"
---
# <a name="custom-host-samples"></a><span data-ttu-id="3518d-103">사용자 지정 호스트 샘플</span><span class="sxs-lookup"><span data-stu-id="3518d-103">Custom Host Samples</span></span>

<span data-ttu-id="3518d-104">이 섹션에는 사용자 지정 호스트를 작성 하는 샘플 코드가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3518d-104">This section includes sample code for writing a custom host.</span></span> <span data-ttu-id="3518d-105">Microsoft Visual Studio를 사용 하 여 콘솔 응용 프로그램을 만든 후이 섹션의 항목에서 호스트 응용 프로그램으로 코드를 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3518d-105">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="3518d-106">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="3518d-106">In This Section</span></span>

 <span data-ttu-id="3518d-107">[Host01 샘플](./host01-sample.md) 이 샘플에서는 기본 사용자 지정 호스트를 사용 하는 호스트 응용 프로그램을 구현 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3518d-107">[Host01 Sample](./host01-sample.md) This sample shows how to implement a host application that uses a basic custom host.</span></span>

 <span data-ttu-id="3518d-108">[Host02 샘플](./host02-sample.md) 이 샘플에서는 사용자 지정 호스트 구현과 함께 Windows PowerShell 런타임을 사용 하는 호스트 응용 프로그램을 작성 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3518d-108">[Host02 Sample](./host02-sample.md) This sample shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span> <span data-ttu-id="3518d-109">호스트 응용 프로그램은 호스트 문화권을 독일어로 설정 하 고, [Get Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet을 실행 한 다음 pwrsh.exe를 사용 하 여 표시 되는 것 처럼 결과를 표시 한 다음 현재 데이터와 시간을 독일어로 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3518d-109">The host application sets the host culture to German, runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet and displays the results as you would see them using pwrsh.exe, and then prints out the current data and time in German.</span></span>

 <span data-ttu-id="3518d-110">[Host03 샘플](./host03-sample.md) 이 샘플에서는 명령줄에서 명령을 읽고 명령을 실행 한 다음 결과를 콘솔에 표시 하는 대화형 콘솔 기반 호스트 응용 프로그램을 빌드하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3518d-110">[Host03 Sample](./host03-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>

 <span data-ttu-id="3518d-111">[Host04 샘플](./host04-sample.md) 이 샘플에서는 명령줄에서 명령을 읽고 명령을 실행 한 다음 결과를 콘솔에 표시 하는 대화형 콘솔 기반 호스트 응용 프로그램을 빌드하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3518d-111">[Host04 Sample](./host04-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="3518d-112">이 호스트 애플리케이션은 사용자가 여러 선택 항목을 지정할 수 있는 프롬프트 표시도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="3518d-112">This host application also supports displaying prompts that allow the user to specify multiple choices.</span></span>

 <span data-ttu-id="3518d-113">[Host05 샘플](./host05-sample.md) 이 샘플에서는 명령줄에서 명령을 읽고 명령을 실행 한 다음 결과를 콘솔에 표시 하는 대화형 콘솔 기반 호스트 응용 프로그램을 빌드하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3518d-113">[Host05 Sample](./host05-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="3518d-114">이 호스트 응용 프로그램은 또한 [Enter-pssession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) 및 [종료 pssession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlet을 사용 하 여 원격 컴퓨터에 대 한 호출을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="3518d-114">This host application also supports calls to remote computers by using the [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) and [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets</span></span>

 <span data-ttu-id="3518d-115">[Host06 샘플](./host06-sample.md) 이 샘플에서는 명령줄에서 명령을 읽고 명령을 실행 한 다음 결과를 콘솔에 표시 하는 대화형 콘솔 기반 호스트 응용 프로그램을 빌드하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3518d-115">[Host06 Sample](./host06-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="3518d-116">또한 이 샘플에서는 토크나이저 API를 사용하여 사용자가 입력하는 텍스트의 색을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3518d-116">In addition, this sample uses the Tokenizer APIs to specify the color of the text that is entered by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="3518d-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3518d-117">See Also</span></span>
