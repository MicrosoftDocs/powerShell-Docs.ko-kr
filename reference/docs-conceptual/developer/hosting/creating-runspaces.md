---
title: Runspace 만들기 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0c27e2bf54e16a3bdc93c4b91629893bb1cc1e3e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779576"
---
# <a name="creating-runspaces"></a><span data-ttu-id="79fd8-102">runspace 만들기</span><span class="sxs-lookup"><span data-stu-id="79fd8-102">Creating Runspaces</span></span>

<span data-ttu-id="79fd8-103">Runspace는 호스트 응용 프로그램에서 호출 하는 명령에 대 한 운영 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="79fd8-103">A runspace is the operating environment for the commands that are invoked by a host application.</span></span> <span data-ttu-id="79fd8-104">이 환경에는 현재 존재 하는 명령 및 데이터와 현재 적용 되는 모든 언어 제한이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="79fd8-104">This environment includes the commands and data that are currently present, and any language restrictions that currently apply.</span></span>

 <span data-ttu-id="79fd8-105">호스트 응용 프로그램은 사용 가능한 모든 핵심 명령을 포함 하는 Windows PowerShell에서 제공 하는 기본 runspace를 사용 하거나 사용 가능한 명령의 하위 집합만 포함 하는 사용자 지정 runspace를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79fd8-105">Host applications can use the default runspace that is provided by Windows PowerShell, which includes all available core commands, or create a custom runspace that includes only a subset of the available commands.</span></span> <span data-ttu-id="79fd8-106">사용자 지정 runspace를 만들려면 [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 개체를 만들고 runspace에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="79fd8-106">To create a customized runspace, you create an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object and assign it to your runspace.</span></span>

## <a name="runspace-tasks"></a><span data-ttu-id="79fd8-107">Runspace 작업</span><span class="sxs-lookup"><span data-stu-id="79fd8-107">Runspace tasks</span></span>

1. [<span data-ttu-id="79fd8-108">InitialSessionState 만들기</span><span class="sxs-lookup"><span data-stu-id="79fd8-108">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

2. [<span data-ttu-id="79fd8-109">제한된 runspace 만들기</span><span class="sxs-lookup"><span data-stu-id="79fd8-109">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)

3. [<span data-ttu-id="79fd8-110">여러 runspace 만들기</span><span class="sxs-lookup"><span data-stu-id="79fd8-110">Creating multiple runspaces</span></span>](./creating-multiple-runspaces.md)

## <a name="see-also"></a><span data-ttu-id="79fd8-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="79fd8-111">See Also</span></span>
