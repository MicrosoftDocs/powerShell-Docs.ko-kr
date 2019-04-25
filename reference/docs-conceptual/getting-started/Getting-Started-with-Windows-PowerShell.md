---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Windows PowerShell 시작
ms.assetid: b0e2ad92-875f-421d-b612-f624e644aa69
ms.openlocfilehash: 8a158427d319e43ec011898fe4e1826d48d5b951
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086581"
---
# <a name="getting-started-with-windows-powershell"></a><span data-ttu-id="f77fb-103">Windows PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="f77fb-103">Getting Started with Windows PowerShell</span></span>
<span data-ttu-id="f77fb-104">Windows PowerShell은 시스템 관리자를 위해 특별히 설계된 Windows 명령줄 셸입니다.</span><span class="sxs-lookup"><span data-stu-id="f77fb-104">Windows PowerShell is a Windows command-line shell designed especially for system administrators.</span></span> <span data-ttu-id="f77fb-105">Windows PowerShell에는 독립적으로 또는 함께 사용할 수 있는 대화형 프롬프트 및 스크립팅 환경이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f77fb-105">Windows PowerShell includes an interactive prompt and a scripting environment that can be used independently or in combination.</span></span>

<span data-ttu-id="f77fb-106">텍스트를 사용하고 반환하는 대부분의 셸과 달리 Windows PowerShell은 .NET Framework CLR(공용 언어 런타임) 및 .NET Framework를 기반으로 하며 .NET Framework 개체를 사용하고 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f77fb-106">Unlike most shells, which accept and return text, Windows PowerShell is built on top of the .NET Framework common language runtime (CLR) and the .NET Framework, and accepts and returns .NET Framework objects.</span></span> <span data-ttu-id="f77fb-107">이러한 환경의 근본적인 변화로 인해 Windows 관리 및 구성에 완전히 새로운 도구와 방법이 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f77fb-107">This fundamental change in the environment brings entirely new tools and methods to the management and configuration of Windows.</span></span>

<span data-ttu-id="f77fb-108">Windows PowerShell은 셸에 기본 제공되는 간단한 단일 함수 명령줄 도구인 cmdlet("커맨드렛"으로 읽음)의 개념을 도입합니다.</span><span class="sxs-lookup"><span data-stu-id="f77fb-108">Windows PowerShell introduces the concept of a cmdlet (pronounced "command-let"), a simple, single-function command-line tool built into the shell.</span></span> <span data-ttu-id="f77fb-109">각 cmdlet을 개별적으로 사용할 수 있지만, 이러한 간단한 도구를 함께 사용하여 복잡한 작업을 수행할 때 그 능력이 실현됩니다.</span><span class="sxs-lookup"><span data-stu-id="f77fb-109">You can use each cmdlet separately, but their power is realized when you use these simple tools in combination to perform complex tasks.</span></span> <span data-ttu-id="f77fb-110">Windows PowerShell에는 100개가 넘는 기본 핵심 cmdlet이 포함되어 있으며, 사용자가 직접 cmdlet을 작성하고 다른 사용자와 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f77fb-110">Windows PowerShell includes more than one hundred basic core cmdlets, and you can write your own cmdlets and share them with other users.</span></span>

<span data-ttu-id="f77fb-111">많은 셸과 마찬가지로, Windows PowerShell을 통해 컴퓨터의 파일 시스템에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f77fb-111">Like many shells, Windows PowerShell gives you access to the file system on the computer.</span></span> <span data-ttu-id="f77fb-112">또한 Windows PowerShell *공급자*를 통해 레지스트리 및 디지털 서명 인증서 저장소와 같은 다른 데이터 저장소를 파일 시스템만큼 쉽게 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f77fb-112">In addition, Windows PowerShell *providers* enable you to access other data stores, such as the registry and the digital signature certificate stores, as easily as you access the file system.</span></span>

<span data-ttu-id="f77fb-113">이 시작 가이드에서는 언어, cmdlet, 공급자 및 개체 사용을 포함하여 Windows PowerShell을 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="f77fb-113">This Getting Started guide provides an introduction to Windows PowerShell: the language, the cmdlets, the providers, and the use of objects.</span></span>

<span data-ttu-id="f77fb-114">이 항목의 내용:</span><span class="sxs-lookup"><span data-stu-id="f77fb-114">In this topic:</span></span>

- [<span data-ttu-id="f77fb-115">Windows PowerShell 시스템 요구 사항</span><span class="sxs-lookup"><span data-stu-id="f77fb-115">Windows PowerShell System Requirements</span></span>](../setup/Windows-PowerShell-System-Requirements.md)

- [<span data-ttu-id="f77fb-116">Windows PowerShell 설치</span><span class="sxs-lookup"><span data-stu-id="f77fb-116">Installing Windows PowerShell</span></span>](../setup/Installing-Windows-PowerShell.md)

- [<span data-ttu-id="f77fb-117">Windows PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="f77fb-117">Starting Windows PowerShell</span></span>](../setup/Starting-Windows-PowerShell.md)
