---
ms.date: 09/12/2016
ms.topic: reference
title: HelpInfo XML 버전 번호를 설정하는 방법
description: HelpInfo XML 버전 번호를 설정하는 방법
ms.openlocfilehash: 9ef1940ca05d8aa9b04770013287490b71c8065a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658839"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="63e3d-103">HelpInfo XML 버전 번호를 설정하는 방법</span><span class="sxs-lookup"><span data-stu-id="63e3d-103">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="63e3d-104">이 항목에서는 일반적으로 "HelpInfo XML file" 이라는 업데이트 가능한 도움말 정보 파일에서 버전 번호를 설정 하 고 늘리는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="63e3d-104">This topic explains how to set and increase the version numbers in an Updatable Help Information file, commonly known as a "HelpInfo XML file."</span></span>

## <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="63e3d-105">HelpInfo XML 버전 번호를 설정하는 방법</span><span class="sxs-lookup"><span data-stu-id="63e3d-105">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="63e3d-106">HelpInfo XML 파일의 버전 번호는 업데이트할 수 있는 도움말의 작업에 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="63e3d-106">The version numbers in a HelpInfo XML file are critical to the operation of Updatable Help.</span></span> <span data-ttu-id="63e3d-107">[업데이트-도움말](/powershell/module/Microsoft.PowerShell.Core/Update-Help) 및 [저장-도움말](/powershell/module/Microsoft.PowerShell.Core/Save-Help) CMDLET은 원격 HELPINFO xml 파일의 ui 문화권에 대 한 버전 번호가 로컬 HELPINFO xml의 해당 ui 문화권에 대 한 버전 번호 보다 크거나 로컬 HelpInfo xml 파일이 없는 경우에만 새 도움말 파일을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="63e3d-107">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets download new help files only when the version number for a UI culture in the remote HelpInfo XML file is greater than the version number for that UI culture in the local HelpInfo XML, or there is no local HelpInfo XML file.</span></span>

<span data-ttu-id="63e3d-108">HelpInfo XML 파일은 Microsoft .NET Framework의 **system.object** 클래스에 정의 된 네 부분으로 구성 된 버전 번호를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="63e3d-108">The HelpInfo XML file uses the 4-part version number that is defined in the **System.Version** class of the Microsoft .NET Framework.</span></span> <span data-ttu-id="63e3d-109">형식은 `N1.N2.N3.N4`입니다.</span><span class="sxs-lookup"><span data-stu-id="63e3d-109">The format is `N1.N2.N3.N4`.</span></span> <span data-ttu-id="63e3d-110">모듈 작성자는 **system.object** 클래스에서 허용 하는 모든 버전 번호 지정 체계를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63e3d-110">Module authors can use any version numbering scheme that is permitted by the **System.Version** class.</span></span> <span data-ttu-id="63e3d-111">업데이트할 수 있는 도움말을 사용 하려면 해당 UI 문화권에 대 한 새 버전의 CAB 파일을 HelpInfo XML 파일의 **Helpcontenturi** 요소로 지정 된 위치에 업로드할 때 ui 문화권의 버전 번호를 늘려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63e3d-111">Updatable Help requires only that the version number for a UI culture increase when a new version of the CAB file for that UI culture is uploaded to the location that is specified by the **HelpContentURI** element in the HelpInfo XML file.</span></span>

<span data-ttu-id="63e3d-112">다음 예제에서는 버전이 2.15.0.10 인 경우 독일어 (de-de) UI 문화권에 대 한 HelpInfo XML 파일의 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="63e3d-112">The following example shows the elements of the HelpInfo XML file for the German (de-DE) UI culture when the version is 2.15.0.10.</span></span>

```xml
<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

<span data-ttu-id="63e3d-113">UI 문화권의 버전 번호는 해당 UI 문화권에 대 한 CAB 파일의 버전을 반영 합니다.</span><span class="sxs-lookup"><span data-stu-id="63e3d-113">The version number for a UI culture reflects the version of the CAB file for that UI culture.</span></span> <span data-ttu-id="63e3d-114">버전 번호는 전체 CAB 파일에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63e3d-114">The version number applies to the entire CAB file.</span></span> <span data-ttu-id="63e3d-115">CAB 파일의 다른 파일에 다른 버전 번호를 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="63e3d-115">You cannot set different version numbers for different files in the CAB file.</span></span> <span data-ttu-id="63e3d-116">각 UI 문화권의 버전 번호는 독립적으로 평가 되며 모듈에서 지 원하는 다른 UI 문화권의 버전 번호와 관련 될 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="63e3d-116">The version number for each UI culture is evaluated independently and need not be related to the version numbers for other UI cultures that the module supports.</span></span>
