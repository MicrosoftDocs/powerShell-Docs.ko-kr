---
title: HelpInfo XML 버전 번호를 설정 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93a00463-af58-41c8-b088-450909fa1d05
caps.latest.revision: 6
ms.openlocfilehash: 4929a5b1c9f73bb12b6df975e03fc529db3565ef
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863319"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="84863-102">HelpInfo XML 버전 번호를 설정하는 방법</span><span class="sxs-lookup"><span data-stu-id="84863-102">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="84863-103">이 항목에서는 일반적으로 "HelpInfo XML 파일입니다."로 알려진 업데이트할 수 있는 도움말 정보 파일에 버전 번호를 높이고 설정 하는 방법 설명</span><span class="sxs-lookup"><span data-stu-id="84863-103">This topic explains how to set and increase the version numbers in an Updatable Help Information file, commonly known as a "HelpInfo XML file."</span></span>

## <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="84863-104">HelpInfo XML 버전 번호를 설정하는 방법</span><span class="sxs-lookup"><span data-stu-id="84863-104">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="84863-105">HelpInfo XML 파일에 버전 번호는 업데이트할 수 있는 도움말의 작동에 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="84863-105">The version numbers in a HelpInfo XML file are critical to the operation of Updatable Help.</span></span> <span data-ttu-id="84863-106">합니다 [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) 하 고 [Save-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet 원격 HelpInfo XML 파일에는 UI 문화권에 대 한 버전 번호를 해당 UI 문화권에 대 한 버전 번호 보다 큰 경우에 새 도움말 파일을 다운로드 합니다 로컬 HelpInfo XML 또는 로컬 HelpInfo XML 파일이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="84863-106">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlets download new help files only when the version number for a UI culture in the remote HelpInfo XML file is greater than the version number for that UI culture in the local HelpInfo XML, or there is no local HelpInfo XML file.</span></span>
<span data-ttu-id="84863-107">HelpInfo XML 파일에 버전 번호는 업데이트할 수 있는 도움말의 작동에 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="84863-107">The version numbers in a HelpInfo XML file are critical to the operation of Updatable Help.</span></span> <span data-ttu-id="84863-108">합니다 [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) 하 고 [Save-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet 원격 HelpInfo XML 파일에는 UI 문화권에 대 한 버전 번호를 해당 UI 문화권에 대 한 버전 번호 보다 큰 경우에 새 도움말 파일을 다운로드 합니다 로컬 HelpInfo XML 또는 로컬 HelpInfo XML 파일이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="84863-108">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlets download new help files only when the version number for a UI culture in the remote HelpInfo XML file is greater than the version number for that UI culture in the local HelpInfo XML, or there is no local HelpInfo XML file.</span></span>

<span data-ttu-id="84863-109">HelpInfo XML 파일에 정의 된 4 부 버전 번호를 사용 합니다 **System.Version** Microsoft.NET Framework의 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="84863-109">The HelpInfo XML file uses the 4-part version number that is defined in the **System.Version** class of the Microsoft .NET Framework.</span></span> <span data-ttu-id="84863-110">형식은 `N1.N2.N3.N4`합니다.</span><span class="sxs-lookup"><span data-stu-id="84863-110">The format is `N1.N2.N3.N4`.</span></span> <span data-ttu-id="84863-111">모듈 작성자는 번호 매기기 체계에서 허용 되는 모든 버전을 사용할 수는 **System.Version** 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="84863-111">Module authors can use any version numbering scheme that is permitted by the **System.Version** class.</span></span> <span data-ttu-id="84863-112">업데이트 가능한 도움말에서는 버전 번호를 증가 하는 UI 문화권에 대 한 해당 UI 문화권에 대 한 CAB 파일의 새 버전으로 지정 된 위치에 업로드 되 면 합니다 **HelpContentURI** HelpInfo XML 파일의 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="84863-112">Updatable Help requires only that the version number for a UI culture increase when a new version of the CAB file for that UI culture is uploaded to the location that is specified by the **HelpContentURI** element in the HelpInfo XML file.</span></span>

<span data-ttu-id="84863-113">다음 예제에서는 버전 2.15.0.10 경우 독일어 (DE-DE) UI 문화권에 대 한 HelpInfo XML 파일의 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="84863-113">The following example shows the elements of the HelpInfo XML file for the German (de-DE) UI culture when the version is 2.15.0.10.</span></span>

```xml

<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

<span data-ttu-id="84863-114">UI 문화권에 대 한 버전 번호를 해당 UI 문화권에 대 한 CAB 파일의 버전을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="84863-114">The version number for a UI culture reflects the version of the CAB file for that UI culture.</span></span> <span data-ttu-id="84863-115">전체 CAB 파일에 버전 번호를 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="84863-115">The version number applies to the entire CAB file.</span></span> <span data-ttu-id="84863-116">CAB 파일에 다른 파일에 대 한 다양 한 버전 번호를 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="84863-116">You cannot set different version numbers for different files in the CAB file.</span></span> <span data-ttu-id="84863-117">각 UI 문화권에 대 한 버전 번호를 독립적으로 계산 됩니다 및 다른 모듈에서 지 원하는 UI 문화권에 대 한 버전 번호에 관련 될 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="84863-117">The version number for each UI culture is evaluated independently and need not be related to the version numbers for other UI cultures that the module supports.</span></span>