---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 7a1725e3858c59a6d31699add22b042359c48463
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55680793"
---
# <a name="separation-of-node-and-configuration-ids"></a><span data-ttu-id="4bd49-102">노드 및 구성 ID의 분리</span><span class="sxs-lookup"><span data-stu-id="4bd49-102">Separation of Node and Configuration IDs</span></span>

## <a name="overview"></a><span data-ttu-id="4bd49-103">개요</span><span class="sxs-lookup"><span data-stu-id="4bd49-103">Overview</span></span>

<span data-ttu-id="4bd49-104">끌어오기 모드에서 DSC를 사용할 때 보다 유연하고 원활한 환경을 제공하기 위해 이번 릴리스에서 많은 기능을 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="4bd49-104">In order to provide a more flexible and streamlined experience when using DSC in Pull mode, we have added a number of features in this release.</span></span> <span data-ttu-id="4bd49-105">이러한 기능은 각 노드에 대해 개별적으로 상태를 추적하고 정보를 보고하면서 여러 노드 간에 구성을 쉽게 설정하고 배포할 수 있는 유연성을 제공하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4bd49-105">These features are intended to allow you to have the flexibility to easily setup and deploy configurations across multiple nodes, while still tracking status and reporting information for each node individually.</span></span>
<span data-ttu-id="4bd49-106">이러한 기능은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4bd49-106">These features are as follows:</span></span>

* <span data-ttu-id="4bd49-107">컴퓨터에 대한 구성을 식별하는 구성 이름.</span><span class="sxs-lookup"><span data-stu-id="4bd49-107">A configuration name which identifies the configuration for a computer.</span></span> <span data-ttu-id="4bd49-108">이 이름은 여러 대상 노드에서 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bd49-108">This name can be shared by multiple target nodes</span></span>
* <span data-ttu-id="4bd49-109">단일 노드를 고유하게 식별하는 에이전트 ID</span><span class="sxs-lookup"><span data-stu-id="4bd49-109">An agent ID which uniquely identifies a single node</span></span>
* <span data-ttu-id="4bd49-110">대상 노드가 끌어오기 서버에 처음으로 연결할 때만 수행되는 등록 단계</span><span class="sxs-lookup"><span data-stu-id="4bd49-110">A registration step which only occurs the first time a target node connects to a pull server</span></span>

<span data-ttu-id="4bd49-111">**참고:** 이러한 기능은 추가된 것이며 기존의 끌어오기 기능 및 개념을 대체하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4bd49-111">**Note:** These features and functionality have been added and do not replace the existing pull features and concepts.</span></span> <span data-ttu-id="4bd49-112">이번 릴리스에서 제공되는 새로운 끌어오기 서버에서는 이러한 새로운 기능이나 이전 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4bd49-112">You can use these new features or the older ones with the new pull server shipping in this release.</span></span>

<span data-ttu-id="4bd49-113">자세한 내용은 [구성 이름을 사용하여 끌어오기 클라이언트 설정](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4bd49-113">For more information, see [Setting up a pull client using configuration names](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span></span>
