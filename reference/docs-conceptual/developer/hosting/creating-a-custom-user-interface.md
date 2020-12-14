---
ms.date: 09/13/2016
ms.topic: reference
title: 사용자 지정 사용자 인터페이스 만들기
description: 사용자 지정 사용자 인터페이스 만들기
ms.openlocfilehash: 411165f868cd524c0cef0ba9cce3188c60a7dbdf
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645400"
---
# <a name="creating-a-custom-user-interface"></a><span data-ttu-id="4c01d-103">사용자 지정 사용자 인터페이스 만들기</span><span class="sxs-lookup"><span data-stu-id="4c01d-103">Creating a custom user interface</span></span>

<span data-ttu-id="4c01d-104">Windows PowerShell은 Windows PowerShell 엔진을 호스팅하는 사용자 지정 대화형 UI를 만들 수 있는 추상 클래스 및 인터페이스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c01d-104">Windows PowerShell provides abstract classes and interfaces that allow you to create a custom interactive UI that hosts the Windows PowerShell engine.</span></span> <span data-ttu-id="4c01d-105">사용자 지정 UI를 만들려면 [PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) 클래스를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c01d-105">To create a custom UI, you must implement the [System.Management.Automation.Host.PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) class.</span></span> <span data-ttu-id="4c01d-106">필요에 따라 [Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) 클래스 및 [Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) 및 [Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) 인터페이스를 구현할 수도 있습니다 (예를 들어,... n a m [a..](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)m a.. m a.</span><span class="sxs-lookup"><span data-stu-id="4c01d-106">Optionally, you can also implement the [System.Management.Automation.Host.Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)and [System.Management.Automation.Host.Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) classes, and the [System.Management.Automation.Host.Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) and [System.Management.Automation.Host.Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) interfaces.</span></span>
