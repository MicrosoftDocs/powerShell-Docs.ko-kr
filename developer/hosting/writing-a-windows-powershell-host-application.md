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
ms.openlocfilehash: 2039e181becd1b39fc3d6cf0cdbcf0c20e9fc206
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863179"
---
# <a name="writing-a-windows-powershell-host-application"></a><span data-ttu-id="7fe13-102">Windows PowerShell 호스트 애플리케이션 작성</span><span class="sxs-lookup"><span data-stu-id="7fe13-102">Writing a Windows PowerShell Host Application</span></span>

<span data-ttu-id="7fe13-103">응용 프로그램에서 Windows PowerShell을 호스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe13-103">You can host Windows PowerShell in your application.</span></span> <span data-ttu-id="7fe13-104">호스트 응용 프로그램 명령을 실행 하 고 로컬 또는 원격 컴퓨터에서 세션을 열고 동기적 또는 비동기적으로 응용 프로그램의 요구에 따라 명령을 호출할 수 있는 runspace를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe13-104">The host application can define the runspace where commands are run, open sessions on a local or remote computer, and invoke the commands either synchronously or asynchronously based on the needs of the application.</span></span>

<span data-ttu-id="7fe13-105">다음 항목에서 호스팅하는 응용 프로그램을 만드는 방법 설명</span><span class="sxs-lookup"><span data-stu-id="7fe13-105">The following topics explain how to create an application that hosts</span></span>

## <a name="in-this-section"></a><span data-ttu-id="7fe13-106">이 섹션의 내용</span><span class="sxs-lookup"><span data-stu-id="7fe13-106">In This Section</span></span>

<span data-ttu-id="7fe13-107">[Windows PowerShell 호스트 퀵 스타트](./windows-powershell-host-quickstart.md) 하기 위한 지침을 제공 및 코드 샘플 호스트 응용 프로그램 만들기를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe13-107">[Windows PowerShell Host Quickstart](./windows-powershell-host-quickstart.md) Provides instructions and code samples to get you started creating host applications.</span></span>

<span data-ttu-id="7fe13-108">[Runspace를 만드는](./creating-runspaces.md) 호스트 응용 프로그램에서 Windows PowerShell 명령을 실행 하는 runspace를 만드는 방법을 설명 하는 항목의 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe13-108">[Creating Runspaces](./creating-runspaces.md) A set of topics that explain how to create runspaces to run Windows PowerShell command in a host application.</span></span>

<span data-ttu-id="7fe13-109">[추가한 명령을 호출](./adding-and-invoking-commands.md) 만들고 호스트 응용 프로그램에서 명령 파이프라인을 실행 하는 방법을 설명...</span><span class="sxs-lookup"><span data-stu-id="7fe13-109">[Adding and invoking commands](./adding-and-invoking-commands.md) Explains how to create and run a command pipeline in your host application..</span></span>

<span data-ttu-id="7fe13-110">[원격 runspace를 만드는](./creating-remote-runspaces.md) Expains runspace 원격 컴퓨터에 연결 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe13-110">[Creating remote runspaces](./creating-remote-runspaces.md) Expains how to connect a runspace to a remote computer.</span></span>

<span data-ttu-id="7fe13-111">[사용자 지정 사용자 인터페이스 만들기](./creating-a-custom-user-interface.md) 소개 사용자 지정 사용자 인터페이스 및 예제에 대 한 링크를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe13-111">[Creating a custom user interface](./creating-a-custom-user-interface.md) Introduces custom user interfaces and provides links to examples.</span></span>

<span data-ttu-id="7fe13-112">[호스트 응용 프로그램 샘플](./host-application-samples.md) 이 섹션에서는 호스트 응용 프로그램의 샘플을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe13-112">[Host Application Samples](./host-application-samples.md) This section includes samples of complete host applications.</span></span>

## <a name="see-also"></a><span data-ttu-id="7fe13-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7fe13-113">See Also</span></span>

[<span data-ttu-id="7fe13-114">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7fe13-114">Windows PowerShell</span></span>](http://msdn.microsoft.com/en-us/b41a2af3-aec1-402d-8e18-c2c26be461ff)