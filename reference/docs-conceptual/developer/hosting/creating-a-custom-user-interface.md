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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367632"
---
# <a name="creating-a-custom-user-interface"></a>사용자 지정 사용자 인터페이스 만들기

Windows PowerShell은 Windows PowerShell 엔진을 호스팅하는 사용자 지정 대화형 UI를 만들 수 있는 추상 클래스 및 인터페이스를 제공 합니다. 사용자 지정 UI를 만들려면 [PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) 클래스를 구현 해야 합니다. 필요에 따라 [System.Management.Automation.Host.Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)과 [System.Management.Automation.Host.Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) 클래스를 구현할 수 있고, [System.Management.Automation.Host.Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession)과 [System.Management.Automation.Host.Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) 인터페이스도 구현할 수 있습니다.
