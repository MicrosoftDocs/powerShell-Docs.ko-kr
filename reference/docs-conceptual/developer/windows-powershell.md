---
title: Windows PowerShell SDK
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: 7627ab336ddc40ab47c3017eed77c78bbdac4e7f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366062"
---
# <a name="windows-powershell"></a><span data-ttu-id="c000b-102">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c000b-102">Windows PowerShell</span></span>

<span data-ttu-id="c000b-103">업데이트 날짜: 2013 년 7 월 8 일</span><span class="sxs-lookup"><span data-stu-id="c000b-103">Updated: July 8, 2013</span></span>

<span data-ttu-id="c000b-104">Windows PowerShell®은 시스템 관리용으로 특별히 설계된 작업 기반 명령줄 셸 및 스크립트 언어입니다.</span><span class="sxs-lookup"><span data-stu-id="c000b-104">Windows PowerShell® is a task-based command-line shell and scripting language designed especially for system administration.</span></span> <span data-ttu-id="c000b-105">.NET Framework을 기반으로 하는 Windows PowerShell®를 사용 하면 IT 전문가와 고급 사용자가 windows 운영 체제 및 windows에서 실행 되는 응용 프로그램의 관리를 제어 하 고 자동화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c000b-105">Built on the .NET Framework, Windows PowerShell® helps IT professionals and power users control and automate the administration of the Windows operating system and applications that run on Windows.</span></span>

<span data-ttu-id="c000b-106">여기에 게시 된 문서는 Windows PowerShell에서 제공 하는 Api에 대 한 참조 정보를 필요로 하는 cmdlet, 공급자 및 호스트 응용 프로그램 개발자를 위해 주로 작성 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c000b-106">The documents published here are written primarily for cmdlet, provider, and host application developers who require reference information about the APIs provided by Windows PowerShell.</span></span>
<span data-ttu-id="c000b-107">그러나 시스템 관리자는 이러한 문서에서 제공 하는 정보를 유용 하 게 찾을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c000b-107">However, system administrators might also find the information provided by these documents useful.</span></span>

<span data-ttu-id="c000b-108">Windows PowerShell 사용을 시작 하는 데 필요한 기본 정보는 Windows PowerShell 시작을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c000b-108">For the basic information needed to start using Windows PowerShell, see Getting Started with Windows PowerShell .</span></span>

## <a name="windows-powershell-documents-on-msdn"></a><span data-ttu-id="c000b-109">MSDN의 Windows PowerShell 문서</span><span class="sxs-lookup"><span data-stu-id="c000b-109">Windows PowerShell Documents on MSDN</span></span>

- <span data-ttu-id="c000b-110">[Windows POWERSHELL SDK 설치](./installing-the-windows-powershell-sdk.md) Windows PowerShell SDK를 설치 하는 방법에 대 한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c000b-110">[Installing the Windows PowerShell SDK](./installing-the-windows-powershell-sdk.md) Provides information about how to install the Windows PowerShell SDK.</span></span>

- <span data-ttu-id="c000b-111">[Windows PowerShell 모듈 작성](./module/writing-a-windows-powershell-module.md) Windows PowerShell 솔루션을 패키지 하 고 배포 해야 하는 관리자, 스크립트 개발자 및 cmdlet 개발자를 위한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c000b-111">[Writing a Windows PowerShell Module](./module/writing-a-windows-powershell-module.md) Provides information for administrators, script developers, and cmdlet developers who need to package and distribute their Windows PowerShell solutions.</span></span>

- <span data-ttu-id="c000b-112">[Windows PowerShell Cmdlet 작성](./cmdlet/writing-a-windows-powershell-cmdlet.md) Cmdlet 디자인 및 구현에 대 한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c000b-112">[Writing a Windows PowerShell Cmdlet](./cmdlet/writing-a-windows-powershell-cmdlet.md) Provides information for designing and implementing cmdlets.</span></span>

- <span data-ttu-id="c000b-113">[Windows PowerShell 공급자 작성](./provider/writing-a-windows-powershell-provider.md) Windows PowerShell 공급자 디자인 및 구현에 대 한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c000b-113">[Writing a Windows PowerShell Provider](./provider/writing-a-windows-powershell-provider.md) Provides information for designing and implementing Windows PowerShell providers.</span></span> <span data-ttu-id="c000b-114">Windows PowerShell 공급자의 작동 방식을 이해 하는 데 도움이 되며, 사용자가 직접 공급자를 디자인 하거나 작성 하는 데 사용할 수 있는 샘플 코드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c000b-114">It will help you understand how Windows PowerShell providers work, and it provides sample code that you can use to start designing or writing your own providers.</span></span>

- <span data-ttu-id="c000b-115">[Windows PowerShell 호스트 응용 프로그램 작성](./hosting/writing-a-windows-powershell-host-application.md) 호스트 응용 프로그램을 디자인 하는 프로그램 관리자와 해당 응용 프로그램을 구현 하는 개발자가 사용할 수 있는 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c000b-115">[Writing a Windows PowerShell Host Application](./hosting/writing-a-windows-powershell-host-application.md) Provides information that can be used by program managers who are designing host applications and by developers who are implementing them.</span></span> <span data-ttu-id="c000b-116">호스트 응용 프로그램은 명령이 실행 되는 runspace를 정의 하 고, 로컬 또는 원격 컴퓨터에서 세션을 열고, 응용 프로그램의 필요에 따라 동기적으로 또는 비동기적으로 명령을 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c000b-116">The host application can, define the runspace where commands are run, open sessions on a local or remote computer, and invoke the commands either synchronously or asynchronously based on the needs of the application.</span></span>

- <span data-ttu-id="c000b-117">[PowerShell 서식 파일 작성](./format/writing-a-powershell-formatting-file.md) 명령 (cmdlet, 함수 및 스크립트)에서 반환 되는 개체의 표시 형식을 제어 하는 서식 파일 작성에 대 한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c000b-117">[Writing a PowerShell Formatting File](./format/writing-a-powershell-formatting-file.md) Provides information for the authoring of formatting files, which control the display format for the objects that are returned by commands (cmdlets, functions, and scripts).</span></span>

- <span data-ttu-id="c000b-118">[Windows PowerShell 참조](./windows-powershell-reference.md) Cmdlet, 공급자 및 호스트 응용 프로그램 뿐만 아니라 지원 되는 다른 Api를 작성 하는 데 사용 되는 Api에 대 한 참조 콘텐츠를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c000b-118">[Windows PowerShell Reference](./windows-powershell-reference.md) Provides reference content for the APIs used in writing cmdlets, providers, and host applications, as well as other supporting APIs.</span></span>
