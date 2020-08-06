---
title: 사용자 지정 사용자 인터페이스 만들기 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ebbaba4231b54d42cdcdef07a3ff665bd207d696
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779780"
---
# <a name="creating-a-custom-user-interface"></a><span data-ttu-id="c417c-102">사용자 지정 사용자 인터페이스 만들기</span><span class="sxs-lookup"><span data-stu-id="c417c-102">Creating a custom user interface</span></span>

<span data-ttu-id="c417c-103">Windows PowerShell은 Windows PowerShell 엔진을 호스팅하는 사용자 지정 대화형 UI를 만들 수 있는 추상 클래스 및 인터페이스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c417c-103">Windows PowerShell provides abstract classes and interfaces that allow you to create a custom interactive UI that hosts the Windows PowerShell engine.</span></span> <span data-ttu-id="c417c-104">사용자 지정 UI를 만들려면 [PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) 클래스를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c417c-104">To create a custom UI, you must implement the [System.Management.Automation.Host.PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) class.</span></span> <span data-ttu-id="c417c-105">필요에 따라 [Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) 클래스 및 [Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) 및 [Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) 인터페이스를 구현할 수도 있습니다 (예를 들어,... n a m [a..](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)m a.. m a.</span><span class="sxs-lookup"><span data-stu-id="c417c-105">Optionally, you can also implement the [System.Management.Automation.Host.Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)and [System.Management.Automation.Host.Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) classes, and the [System.Management.Automation.Host.Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) and [System.Management.Automation.Host.Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) interfaces.</span></span>
