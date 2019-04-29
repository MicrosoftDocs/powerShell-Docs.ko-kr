---
title: 사용자 지정 사용자 인터페이스 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d7286443-eed4-43d5-b809-50cdcdcba088
caps.latest.revision: 4
ms.openlocfilehash: 23518c625fe1138e1bd2bcc895274cb21d7daf8a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083045"
---
# <a name="creating-a-custom-user-interface"></a><span data-ttu-id="c7964-102">사용자 지정 사용자 인터페이스 만들기</span><span class="sxs-lookup"><span data-stu-id="c7964-102">Creating a custom user interface</span></span>

<span data-ttu-id="c7964-103">Windows PowerShell Windows PowerShell 엔진을 호스트 하는 사용자 지정 대화형 UI를 만들 수 있는 추상 클래스와 인터페이스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7964-103">Windows PowerShell provides abstract classes and interfaces that allow you to create a custom interactive UI that hosts the Windows PowerShell engine.</span></span> <span data-ttu-id="c7964-104">사용자 지정 UI를 만들려면를 구현 해야 합니다 [System.Management.Automation.Host.PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="c7964-104">To create a custom UI, you must implement the [System.Management.Automation.Host.PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) class.</span></span> <span data-ttu-id="c7964-105">필요에 따라 구현할 수도 있습니다는 [System.Management.Automation.Host.Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)하 고 [System.Management.Automation.Host.Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) 클래스 및 합니다 [System.Management.Automation.Host.Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) 하 고 [System.Management.Automation.Host.Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="c7964-105">Optionally, you can also implement the [System.Management.Automation.Host.Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)and [System.Management.Automation.Host.Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) classes, and the [System.Management.Automation.Host.Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) and [System.Management.Automation.Host.Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) interfaces.</span></span>
