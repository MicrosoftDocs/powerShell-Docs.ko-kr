---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Linux용 기본 제공 필요한 상태 구성 리소스
ms.openlocfilehash: ea700d24c7ff4377af671944184abb3f201852e8
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047706"
---
# <a name="built-in-desired-state-configuration-resources-for-linux"></a><span data-ttu-id="5e817-103">Linux용 기본 제공 필요한 상태 구성 리소스</span><span class="sxs-lookup"><span data-stu-id="5e817-103">Built-In Desired State Configuration Resources for Linux</span></span>

<span data-ttu-id="5e817-104">리소스는 PowerShell DSC(필요한 상태 구성) 스크립트를 작성하는 데 사용할 수 있는 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="5e817-104">Resources are building blocks that you can use to write a PowerShell Desired State Configuration (DSC) script.</span></span> <span data-ttu-id="5e817-105">Linux용 DSC는 파일 및 폴더, 패키지, 환경 변수, 서비스 및 프로세스와 같은 리소스를 구성하기 위한 기본 제공 기능 집합과 함께 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e817-105">DSC for Linux comes with a set of built-in functionality for configuring resources such as files and folders, packages, environment variables, and services and processes.</span></span>

## <a name="built-in-resources"></a><span data-ttu-id="5e817-106">기본 제공 리소스</span><span class="sxs-lookup"><span data-stu-id="5e817-106">Built-in resources</span></span>

<span data-ttu-id="5e817-107">다음 표에서는 이러한 리소스와 이에 대해 자세히 설명하는 항목에 대한 링크 목록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5e817-107">The following table provides a list of these resources and links to topics that describe them in detail.</span></span>

* <span data-ttu-id="5e817-108">[nxArchive Resource](lnxArchiveResource.md)--특정 경로에 있는 보관 파일(.tar, .zip)의 압축을 푸는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5e817-108">[nxArchive Resource](lnxArchiveResource.md)--Provides a mechanism to unpack archive (.tar, .zip) files at a specific path.</span></span>
* <span data-ttu-id="5e817-109">[nxEnvironment Resource](lnxEnvironmentResource.md)--대상 노드에 대한 환경 변수를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="5e817-109">[nxEnvironment Resource](lnxEnvironmentResource.md)--Manages environment variables on target nodes.</span></span>
* <span data-ttu-id="5e817-110">[nxFile Resource](lnxFileResource.md)--Linux 파일 및 디렉터리를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="5e817-110">[nxFile Resource](lnxFileResource.md)--Manages Linux files and directories.</span></span>
* <span data-ttu-id="5e817-111">[nxFileLine Resource](lnxFileLineResource.md)--Linux 파일에 있는 개별 줄을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="5e817-111">[nxFileLine Resource](lnxFileLineResource.md)--Manages individual lines in a Linux file.</span></span>
* <span data-ttu-id="5e817-112">[nxGroup Resource](lnxGroupResource.md)--로컬 Linux 그룹을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="5e817-112">[nxGroup Resource](lnxGroupResource.md)--Manages local Linux groups.</span></span>
* <span data-ttu-id="5e817-113">[nxPackage Resource](lnxPackageResource.md)--Linux 노드에 있는 패키지를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="5e817-113">[nxPackage Resource](lnxPackageResource.md)--Manages packages on Linux nodes.</span></span>
* <span data-ttu-id="5e817-114">[nxScript Resource](lnxScriptResource.md)--대상 노드에서 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5e817-114">[nxScript Resource](lnxScriptResource.md)--Runs scripts on target nodes.</span></span>
* <span data-ttu-id="5e817-115">[nxService Resource](lnxServiceResource.md)--Linux 서비스를 관리합니다(데몬).</span><span class="sxs-lookup"><span data-stu-id="5e817-115">[nxService Resource](lnxServiceResource.md)--Manages Linux services (daemons).</span></span>
* <span data-ttu-id="5e817-116">[nxSshAuthorizedKeys Resource](lnxSshAuthorizedKeysResource.md)--Linux 사용자에 대한 공용 ssh 키를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="5e817-116">[nxSshAuthorizedKeys Resource](lnxSshAuthorizedKeysResource.md)--Manages public ssh keys for a Linux user.</span></span>
* <span data-ttu-id="5e817-117">[nxUser Resource](lnxUserResource.md)--로컬 Linux 사용자를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="5e817-117">[nxUser Resource](lnxUserResource.md)--Manages local Linux users.</span></span>