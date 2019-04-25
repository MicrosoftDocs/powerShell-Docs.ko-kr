---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 여러 개체에 대해 작업 반복(ForEach Object)
ms.assetid: 6697a12d-2470-4ed6-b5bb-c35e5d525eb6
ms.openlocfilehash: 64d85edad4a6931b2376b95b6d1f5b4d5194399f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086173"
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a><span data-ttu-id="3ed6b-103">여러 개체에 대해 작업 반복(ForEach-Object)</span><span class="sxs-lookup"><span data-stu-id="3ed6b-103">Repeating a Task for Multiple Objects (ForEach-Object)</span></span>

<span data-ttu-id="3ed6b-104">**ForEach-Object** cmdlet을 사용하면 현재 파이프라인 개체의 스크립트 블록과 `$_` 설명자를 통해 파이프라인에 있는 각 개체에 대해 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ed6b-104">The **ForEach-Object** cmdlet uses script blocks and the `$_` descriptor for the current pipeline object to let you run a command on each object in the pipeline.</span></span> <span data-ttu-id="3ed6b-105">이 cmdlet을 사용하여 몇 가지 복잡한 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ed6b-105">This can be used to perform some complicated tasks.</span></span>

<span data-ttu-id="3ed6b-106">이 cmdlet은 데이터를 조작하여 보다 사용하기 쉽게 만드는 데 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ed6b-106">One situation where this can be useful is manipulating data to make it more useful.</span></span> <span data-ttu-id="3ed6b-107">예를 들어 WMI의 Win32_LogicalDisk 클래스를 사용하여 각 로컬 디스크의 사용 가능한 공간 정보를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ed6b-107">For example, the Win32_LogicalDisk class from WMI can be used to return free space information for each local disk.</span></span> <span data-ttu-id="3ed6b-108">그러나 이 정보는 다음과 같이 쉽게 읽을 수 없는 바이트 단위로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ed6b-108">The data is returned in terms of bytes, however, which makes it difficult to read:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 50665070592
Size         : 203912880128
VolumeName   : Local Disk
```

<span data-ttu-id="3ed6b-109">FreeSpace 값을 1024로 차례로 두 번 나누면 MB 단위로 변환할 수 있습니다. 즉, 첫 번째 나누기에서 KB 단위로 변환되고 두 번째 나누기에서 MB 단위로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ed6b-109">We can convert the FreeSpace value to megabytes by dividing each value by 1024 twice; after the first division, the data is in kilobytes, and after the second division it is megabytes.</span></span> <span data-ttu-id="3ed6b-110">다음과 같이 입력하면 ForEach-Object 스크립트 블록에서 이렇게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ed6b-110">You can do that in a ForEach-Object script block by typing:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {($_.FreeSpace)/1024.0/1024.0}
48318.01171875
```

<span data-ttu-id="3ed6b-111">그러나 이 출력에는 데이터를 나타내는 레이블이 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3ed6b-111">Unfortunately, the output is now data with no associated label.</span></span> <span data-ttu-id="3ed6b-112">이러한 WMI 속성은 읽기 전용이므로 직접 FreeSpace를 변환할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3ed6b-112">Because WMI properties such as this are read-only, you cannot directly convert FreeSpace.</span></span> <span data-ttu-id="3ed6b-113">예를 들어 다음과 같이 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ed6b-113">If you type this:</span></span>

```powershell
Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

<span data-ttu-id="3ed6b-114">그러면 다음과 같은 오류 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="3ed6b-114">You get an error message:</span></span>

```output
"FreeSpace" is a ReadOnly property.
At line:1 char:70
+ Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.F <<<< r
eeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

<span data-ttu-id="3ed6b-115">고급 기술을 사용하여 데이터를 다시 구성할 수도 있지만 **Select-Object**를 사용하여 새 개체를 만드는 것이 훨씬 더 간단합니다.</span><span class="sxs-lookup"><span data-stu-id="3ed6b-115">You could reorganize the data by using some advanced techniques, but a simpler approach is to create a new object, by using **Select-Object**.</span></span>