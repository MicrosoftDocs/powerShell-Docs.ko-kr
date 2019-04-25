---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Linux용 DSC nxSshAuthorizedKeys 리소스
ms.openlocfilehash: d4cdb727a94a5e89e8401769f24977d49bcf4929
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077707"
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a><span data-ttu-id="c7706-103">Linux용 DSC nxSshAuthorizedKeys 리소스</span><span class="sxs-lookup"><span data-stu-id="c7706-103">DSC for Linux nxSshAuthorizedKeys Resource</span></span>

<span data-ttu-id="c7706-104">PowerShell DSC(필요한 상태 구성)의 **nxAuthorizedKeys** 리소스에서는 지정된된 사용자에 대한 권한 있는 ssh 키를 관리하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c7706-104">The **nxAuthorizedKeys** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage authorized ssh keys for a specified user.</span></span>

## <a name="syntax"></a><span data-ttu-id="c7706-105">구문</span><span class="sxs-lookup"><span data-stu-id="c7706-105">Syntax</span></span>

```
nxAuthorizedKeys <string> #ResourceName
{
    KeyComment = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Username = <string> ]
    [ Key = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="c7706-106">속성</span><span class="sxs-lookup"><span data-stu-id="c7706-106">Properties</span></span>

|  <span data-ttu-id="c7706-107">속성</span><span class="sxs-lookup"><span data-stu-id="c7706-107">Property</span></span> |  <span data-ttu-id="c7706-108">설명</span><span class="sxs-lookup"><span data-stu-id="c7706-108">Description</span></span> |
|---|---|
| <span data-ttu-id="c7706-109">KeyComment</span><span class="sxs-lookup"><span data-stu-id="c7706-109">KeyComment</span></span>| <span data-ttu-id="c7706-110">키에 대한 고유 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="c7706-110">A unique comment for the key.</span></span> <span data-ttu-id="c7706-111">이 속성은 키를 고유하게 식별하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7706-111">This is used to uniquely identify keys.</span></span>|
| <span data-ttu-id="c7706-112">Ensure</span><span class="sxs-lookup"><span data-stu-id="c7706-112">Ensure</span></span>| <span data-ttu-id="c7706-113">키가 정의되어 있는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c7706-113">Specifies whether the key is defined.</span></span> <span data-ttu-id="c7706-114">키가 사용자의 권한 있는 키 파일에 존재하지 않도록 하려면 이 속성을 "Absent"으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c7706-114">Set this property to "Absent" to ensure the key does not exist in the user’s authorized keys file.</span></span> <span data-ttu-id="c7706-115">키가 사용자의 권한 있는 키 파일에 정의되어 있도록 하려면 이 속성을 "Present"으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c7706-115">Set it to "Present" to ensure the key is defined in the user’s authorized key file.</span></span>|
| <span data-ttu-id="c7706-116">Username</span><span class="sxs-lookup"><span data-stu-id="c7706-116">Username</span></span>| <span data-ttu-id="c7706-117">ssh 권한 있는 키 파일을 관리할 사용자 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="c7706-117">The username to manage ssh authorized keys for.</span></span> <span data-ttu-id="c7706-118">정의되지 않은 경우, 기본 사용자는 "root"입니다.</span><span class="sxs-lookup"><span data-stu-id="c7706-118">If not defined, the default user is "root".</span></span>|
| <span data-ttu-id="c7706-119">키</span><span class="sxs-lookup"><span data-stu-id="c7706-119">Key</span></span>| <span data-ttu-id="c7706-120">키의 내용입니다.</span><span class="sxs-lookup"><span data-stu-id="c7706-120">The contents of the key.</span></span> <span data-ttu-id="c7706-121">**Ensure**가 "Present"으로 설정되어 있을 경우 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="c7706-121">This is required if **Ensure** is set to "Present".</span></span>|
| <span data-ttu-id="c7706-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="c7706-122">DependsOn</span></span> | <span data-ttu-id="c7706-123">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c7706-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c7706-124">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 **ID**가 **ResourceName**이고 해당 형식이 **ResourceType**일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="c7706-124">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="c7706-125">예제</span><span class="sxs-lookup"><span data-stu-id="c7706-125">Example</span></span>

<span data-ttu-id="c7706-126">다음 예제에서는 사용자 "monuser"에 대한 공개 ssh 권한이 있는 키를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c7706-126">The following example defines a public ssh authorized key for the user "monuser".</span></span>

```
Import-DSCResource -Module nx

Node $node {

nxSshAuthorizedKeys myKey{
   KeyComment = "myKey"
   Ensure = "Present"
   Key = 'ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEA0b+0xSd07QXRifm3FXj7Pn/DblA6QI5VAkDm6OivFzj3U6qGD1VJ6AAxWPCyMl/qhtpRtxZJDu/TxD8AyZNgc8aN2CljN1hOMbBRvH2q5QPf/nCnnJRaGsrxIqZjyZdYo9ZEEzjZUuMDM5HI1LA9B99k/K6PK2Bc1NLivpu7nbtVG2tLOQs+GefsnHuetsRMwo/+c3LtwYm9M0XfkGjYVCLO4CoFuSQpvX6AB3TedUy6NZ0iuxC0kRGg1rIQTwSRcw+McLhslF0drs33fw6tYdzlLBnnzimShMuiDWiT37WqCRovRGYrGCaEFGTG2e0CN8Co8nryXkyWc6NSDNpMzw== rsa-key-20150401'
   UserName = "monuser"
}
}
```