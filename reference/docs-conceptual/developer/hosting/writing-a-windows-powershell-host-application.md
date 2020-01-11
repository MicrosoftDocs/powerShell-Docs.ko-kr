---
title: Windows PowerShell 호스트 응용 프로그램 작성 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81aeafad-dbc3-4712-8bb9-e6a417be260f
caps.latest.revision: 15
ms.openlocfilehash: fe0393634a1e5bb1a3d4a98ccf245e199beb0f16
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75869914"
---
# <a name="writing-a-windows-powershell-host-application"></a><span data-ttu-id="aa419-102">Windows PowerShell 호스트 애플리케이션 작성</span><span class="sxs-lookup"><span data-stu-id="aa419-102">Writing a Windows PowerShell Host Application</span></span>

<span data-ttu-id="aa419-103">응용 프로그램에서 Windows PowerShell을 호스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa419-103">You can host Windows PowerShell in your application.</span></span> <span data-ttu-id="aa419-104">호스트 응용 프로그램은 명령이 실행 되는 runspace를 정의 하 고, 로컬 또는 원격 컴퓨터에서 세션을 열고, 응용 프로그램의 필요에 따라 동기적으로 또는 비동기적으로 명령을 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa419-104">The host application can define the runspace where commands are run, open sessions on a local or remote computer, and invoke the commands either synchronously or asynchronously based on the needs of the application.</span></span>

<span data-ttu-id="aa419-105">다음 항목에서는 Windows PowerShell을 호스팅하는 응용 프로그램을 만드는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa419-105">The following topics explain how to create an application that hosts Windows PowerShell.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="aa419-106">이 섹션의 내용</span><span class="sxs-lookup"><span data-stu-id="aa419-106">In This Section</span></span>

<span data-ttu-id="aa419-107">[Windows PowerShell 호스트 빠른](./windows-powershell-host-quickstart.md) 시작 호스트 응용 프로그램 만들기를 시작할 수 있는 지침과 코드 샘플을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa419-107">[Windows PowerShell Host Quickstart](./windows-powershell-host-quickstart.md) Provides instructions and code samples to get you started creating host applications.</span></span>

<span data-ttu-id="aa419-108">[Runspace 만들기](./creating-runspaces.md) 호스트 응용 프로그램에서 Windows PowerShell 명령을 실행 하는 runspace를 만드는 방법을 설명 하는 항목의 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="aa419-108">[Creating Runspaces](./creating-runspaces.md) A set of topics that explain how to create runspaces to run Windows PowerShell command in a host application.</span></span>

<span data-ttu-id="aa419-109">[명령 추가 및 호출](./adding-and-invoking-commands.md) 호스트 응용 프로그램에서 명령 파이프라인을 만들고 실행 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa419-109">[Adding and invoking commands](./adding-and-invoking-commands.md) Explains how to create and run a command pipeline in your host application..</span></span>

<span data-ttu-id="aa419-110">[원격 Runspace 만들기](./creating-remote-runspaces.md) Runspace를 원격 컴퓨터에 연결 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa419-110">[Creating remote runspaces](./creating-remote-runspaces.md) Explains how to connect a runspace to a remote computer.</span></span>

<span data-ttu-id="aa419-111">[사용자 지정 사용자 인터페이스 만들기](./creating-a-custom-user-interface.md) 사용자 지정 사용자 인터페이스를 소개 하 고 예제에 대 한 링크를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa419-111">[Creating a custom user interface](./creating-a-custom-user-interface.md) Introduces custom user interfaces and provides links to examples.</span></span>

<span data-ttu-id="aa419-112">[호스트 응용 프로그램 샘플](./host-application-samples.md) 이 섹션에는 전체 호스트 응용 프로그램의 샘플이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa419-112">[Host Application Samples](./host-application-samples.md) This section includes samples of complete host applications.</span></span>
