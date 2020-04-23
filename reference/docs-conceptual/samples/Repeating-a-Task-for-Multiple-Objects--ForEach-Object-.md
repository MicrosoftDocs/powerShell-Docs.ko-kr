---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 여러 개체에 대해 작업 반복(ForEach Object)
ms.openlocfilehash: bf89070fd9b006fa9b0b262ab63ffadd81072ecc
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736882"
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a><span data-ttu-id="dd113-103">여러 개체에 대해 작업 반복(ForEach-Object)</span><span class="sxs-lookup"><span data-stu-id="dd113-103">Repeating a Task for Multiple Objects (ForEach-Object)</span></span>

<span data-ttu-id="dd113-104">`ForEach-Object` cmdlet을 사용하면 현재 파이프라인 개체의 스크립트 블록과 `$_` 설명자를 통해 파이프라인에 있는 각 개체에 대해 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd113-104">The `ForEach-Object` cmdlet uses script blocks and the `$_` descriptor for the current pipeline object to let you run a command on each object in the pipeline.</span></span> <span data-ttu-id="dd113-105">이 cmdlet을 사용하여 몇 가지 복잡한 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd113-105">This can be used to perform some complicated tasks.</span></span>

<span data-ttu-id="dd113-106">이 cmdlet은 데이터를 조작하여 보다 사용하기 쉽게 만드는 데 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd113-106">One situation where this can be useful is manipulating data to make it more useful.</span></span> <span data-ttu-id="dd113-107">예를 들어 WMI의 **Win32_LogicalDisk** 클래스를 사용하여 각 로컬 디스크의 사용 가능한 공간 정보를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd113-107">For example, the **Win32_LogicalDisk** class from WMI can be used to return free space information for each local disk.</span></span> <span data-ttu-id="dd113-108">그러나 이 정보는 다음과 같이 쉽게 읽을 수 없는 바이트 단위로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd113-108">The data is returned in terms of bytes, however, which makes it difficult to read:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk
```

```Output
DeviceID DriveType ProviderName VolumeName Size          FreeSpace
-------- --------- ------------ ---------- ----          ---------
C:       3                      Local Disk 203912880128  50665070592
```

<span data-ttu-id="dd113-109">각 값을 1MB로 나누어 **FreeSpace** 값을 메가바이트 단위로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd113-109">We can convert the **FreeSpace** value to megabytes by dividing each value by 1MB.</span></span> <span data-ttu-id="dd113-110">다음과 같이 입력하면 `ForEach-Object` 스크립트 블록에서 이렇게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd113-110">You can do that in a `ForEach-Object` script block by typing:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {($_.FreeSpace)/1MB}
```

```Output
48318.01171875
```

<span data-ttu-id="dd113-111">그러나 이 출력에는 데이터를 나타내는 레이블이 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dd113-111">Unfortunately, the output is now data with no associated label.</span></span> <span data-ttu-id="dd113-112">이러한 WMI 속성은 읽기 전용이므로 직접 **FreeSpace**를 변환할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dd113-112">Because WMI properties such as this are read-only, you cannot directly convert **FreeSpace**.</span></span> <span data-ttu-id="dd113-113">예를 들어 다음과 같이 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd113-113">If you type this:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
```

<span data-ttu-id="dd113-114">그러면 다음과 같은 오류 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="dd113-114">You get an error message:</span></span>

```Output
"FreeSpace" is a ReadOnly property.
At line:2 char:28
+   ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
+                            ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : NotSpecified: (:) [], SetValueException
+ FullyQualifiedErrorId : ReadOnlyCIMProperty
```

<span data-ttu-id="dd113-115">고급 기술을 사용하여 데이터를 다시 구성할 수도 있지만 `Select-Object`를 사용하여 새 개체를 만드는 것이 훨씬 더 간단합니다.</span><span class="sxs-lookup"><span data-stu-id="dd113-115">You could reorganize the data by using some advanced techniques, but a simpler approach is to create a new object, by using `Select-Object`.</span></span>
