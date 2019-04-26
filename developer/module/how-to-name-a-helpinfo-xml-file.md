---
title: HelpInfo XML 파일의 이름을 지정 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64e85b53-5aeb-4d6c-903c-af4ab62f11c1
caps.latest.revision: 7
ms.openlocfilehash: 462cd7bd486a5924bb2bc43e0ac8d1558e30e657
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082399"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="dbffe-102">HelpInfo XML 파일 이름을 지정하는 방법</span><span class="sxs-lookup"><span data-stu-id="dbffe-102">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="dbffe-103">이 항목에서는 HelpInfo XML 파일 이라는 일반적으로 업데이트할 수 있는 도움말 정보 파일에 대 한 필수 이름 형식에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbffe-103">This topic explains the required name format for the Updatable Help Information files, commonly known as HelpInfo XML files.</span></span>

## <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="dbffe-104">HelpInfo XML 파일 이름을 지정하는 방법</span><span class="sxs-lookup"><span data-stu-id="dbffe-104">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="dbffe-105">HelpInfo XML 파일을 다음 형식으로 이름이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbffe-105">A HelpInfo XML file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

<span data-ttu-id="dbffe-106">이름의 요소는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dbffe-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="dbffe-107">ModuleName 값의를 **이름** 의 속성을 **ModuleInfo** 개체를 [Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet이 반환.</span><span class="sxs-lookup"><span data-stu-id="dbffe-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="dbffe-108">ModuleGUID 값의 합니다 **GUID** 모듈 매니페스트 키입니다.</span><span class="sxs-lookup"><span data-stu-id="dbffe-108">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="dbffe-109">예를 들어, 모듈 이름 "TestModule" 이며 모듈 GUID 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, 하는 경우 모듈에 대 한 HelpInfo XML 파일의 이름을 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dbffe-109">For example, if the module name is "TestModule" and the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, the name of the HelpInfo XML file for the module would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`