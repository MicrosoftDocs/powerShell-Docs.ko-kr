---
title: Windows PowerShell API 샘플 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d7232bb16851f1d568cbdfc4374e287d0875adc8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780171"
---
# <a name="windows-powershell-api-samples"></a><span data-ttu-id="5d44b-102">Windows PowerShell API 샘플</span><span class="sxs-lookup"><span data-stu-id="5d44b-102">Windows PowerShell API Samples</span></span>

<span data-ttu-id="5d44b-103">이 섹션에는 기능을 제한 하는 runspace를 만드는 방법 및 runspace 풀을 사용 하 여 runspace를 제공 하 여 비동기적으로 명령을 실행 하는 방법을 보여 주는 샘플 코드가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d44b-103">This section includes sample code that shows how to create runspaces that restrict functionality, and how to asynchronously run commands by using a runspace pool to supply the runspaces.</span></span> <span data-ttu-id="5d44b-104">Microsoft Visual Studio를 사용 하 여 콘솔 응용 프로그램을 만든 후이 섹션의 항목에서 호스트 응용 프로그램으로 코드를 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d44b-104">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="5d44b-105">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="5d44b-105">In This Section</span></span>

<span data-ttu-id="5d44b-106">[PowerShell01 샘플](./windows-powershell01-sample.md) 이 샘플에서는 [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 개체를 사용 하 여 runspace의 기능을 제한 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5d44b-106">[PowerShell01 Sample](./windows-powershell01-sample.md) This sample shows how to use an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to limit the functionality of a runspace.</span></span> <span data-ttu-id="5d44b-107">이 샘플의 출력에서는 runspace의 언어 모드를 제한 하는 방법, cmdlet을 비공개로 표시 하는 방법, cmdlet 및 공급자를 추가 및 제거 하는 방법, 프록시 명령을 추가 하는 방법 등을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5d44b-107">The output of this sample demonstrates how to restrict the language mode of the runspace, how to mark a cmdlet as private, how to add and remove cmdlets and providers, how to add a proxy command, and more.</span></span>

<span data-ttu-id="5d44b-108">[PowerShell02 샘플](./windows-powershell02-sample.md) 이 샘플에서는 runspace 풀의 runspace을 사용 하 여 비동기적으로 명령을 실행 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5d44b-108">[PowerShell02 Sample](./windows-powershell02-sample.md) This sample shows how to run commands asynchronously by using the runspaces of a runspace pool.</span></span> <span data-ttu-id="5d44b-109">이 샘플에서는 명령 목록을 생성 한 다음, Windows PowerShell 엔진이 필요할 때 풀에서 runspace를 열 때 해당 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d44b-109">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>
