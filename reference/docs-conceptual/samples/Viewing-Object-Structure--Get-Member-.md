---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 개체 구조 보기(Get Member)
ms.openlocfilehash: 80b36abd303a708195f12d96511e616178d11b5a
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030708"
---
# <a name="viewing-object-structure-get-member"></a><span data-ttu-id="0b7ab-103">개체 구조 보기(Get-Member)</span><span class="sxs-lookup"><span data-stu-id="0b7ab-103">Viewing Object Structure (Get-Member)</span></span>

<span data-ttu-id="0b7ab-104">Windows PowerShell에서 개체는 중요한 역할을 하므로 임의의 개체 유형에 사용할 여러 개의 기본 명령이 설계되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b7ab-104">Because objects play such a central role in Windows PowerShell, there are several native commands designed to work with arbitrary object types.</span></span> <span data-ttu-id="0b7ab-105">이러한 명령 중 가장 중요한 명령은 **Get-Member**입니다.</span><span class="sxs-lookup"><span data-stu-id="0b7ab-105">The most important one is the **Get-Member** command.</span></span>

<span data-ttu-id="0b7ab-106">명령이 반환하는 개체를 분석하는 가장 간단한 방법은 명령의 출력을 **Get-Member** cmdlet에 파이프하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0b7ab-106">The simplest technique for analyzing the objects that a command returns is to pipe the output of that command to the **Get-Member** cmdlet.</span></span> <span data-ttu-id="0b7ab-107">**Get-Member** cmdlet은 개체 유형의 정식 이름과 해당 멤버의 전체 목록을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0b7ab-107">The **Get-Member** cmdlet shows you the formal name of the object type and a complete listing of its members.</span></span> <span data-ttu-id="0b7ab-108">이때 매우 많은 요소가 반환될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b7ab-108">The number of elements that are returned can sometimes be overwhelming.</span></span> <span data-ttu-id="0b7ab-109">예를 들어 프로세스 개체에는 100개 이상의 멤버가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b7ab-109">For example, a process object can have over 100 members.</span></span>

<span data-ttu-id="0b7ab-110">프로세스 개체의 멤버를 모두 표시하고 출력을 페이징하여 해당 내용을 모두 표시하려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0b7ab-110">To see all the members of a Process object and page the output so you can view all of it, type:</span></span>

```powershell
Get-Process | Get-Member | Out-Host -Paging
```

<span data-ttu-id="0b7ab-111">이 명령을 실행하면 다음과 같은 내용이 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b7ab-111">The output from this command will look something like this:</span></span>

```output
TypeName: System.Diagnostics.Process

Name                           MemberType     Definition
----                           ----------     ----------
Handles                        AliasProperty  Handles = Handlecount
Name                           AliasProperty  Name = ProcessName
NPM                            AliasProperty  NPM = NonpagedSystemMemorySize
PM                             AliasProperty  PM = PagedMemorySize
VM                             AliasProperty  VM = VirtualMemorySize
WS                             AliasProperty  WS = WorkingSet
add_Disposed                   Method         System.Void add_Disposed(Event...
...
```

<span data-ttu-id="0b7ab-112">이 긴 정보 목록은 원하는 요소만 표시되도록 필터링하여 보다 간단하게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b7ab-112">We can make this long list of information more usable by filtering for elements we want to see.</span></span> <span data-ttu-id="0b7ab-113">**Get-Member** 명령을 사용하면 속성 멤버만 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b7ab-113">The **Get-Member** command lets you list only members that are properties.</span></span> <span data-ttu-id="0b7ab-114">속성에는 여러 가지 유형이 있는데,</span><span class="sxs-lookup"><span data-stu-id="0b7ab-114">There are several forms of properties.</span></span> <span data-ttu-id="0b7ab-115">**Get-Member MemberType** 매개 변수를 값 **Properties**로 설정하면 이 cmdlet이 모든 유형의 속성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0b7ab-115">The cmdlet displays properties of any type if we set the **Get-Member MemberType** parameter to the value **Properties**.</span></span> <span data-ttu-id="0b7ab-116">결과 목록은 다음과 같이 아직도 매우 길지만 읽기가 조금 더 쉬워집니다.</span><span class="sxs-lookup"><span data-stu-id="0b7ab-116">The resulting list is still very long, but a bit more manageable:</span></span>

```
PS> Get-Process | Get-Member -MemberType Properties

   TypeName: System.Diagnostics.Process

Name                       MemberType     Definition
----                       ----------     ----------
Handles                    AliasProperty  Handles = Handlecount
Name                       AliasProperty  Name = ProcessName
...
ExitCode                   Property       System.Int32 ExitCode {get;}
...
Handle                     Property       System.IntPtr Handle {get;}
...
CPU                        ScriptProperty System.Object CPU {get=$this.Total...
...
Path                       ScriptProperty System.Object Path {get=$this.Main...
...
```

> [!NOTE]
> <span data-ttu-id="0b7ab-117">MemberType에 사용할 수 있는 값으로는 AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet 및 All이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b7ab-117">The allowed values of MemberType are AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, and All.</span></span>

<span data-ttu-id="0b7ab-118">프로세스에는 60개 이상의 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b7ab-118">There are over 60 properties for a process.</span></span> <span data-ttu-id="0b7ab-119">Windows PowerShell이 종종 잘 알려진 개체의 속성을 일부만 표시하는 이유는 속성을 모두 표시하면 관리할 수 없는 정보의 양이 많아지기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="0b7ab-119">The reason Windows PowerShell often shows only a handful of properties for any well-known object is that showing all of them would produce an unmanageable amount of information.</span></span>

> [!NOTE]
> <span data-ttu-id="0b7ab-120">Windows PowerShell은 이름이 .format.ps1xml로 끝나는 XML 파일에 저장된 정보를 사용하여 개체의 표시 방법을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="0b7ab-120">Windows PowerShell determines how to display an object type by using information stored in XML files that have names ending in .format.ps1xml.</span></span> <span data-ttu-id="0b7ab-121">예를 들어 .NET System.Diagnostics.Process 개체인 프로세스 개체의 서식 데이터는 DotNetTypes.format.ps1xml에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b7ab-121">The formatting data for process objects, which are .NET System.Diagnostics.Process objects, is stored in DotNetTypes.format.ps1xml.</span></span>

<span data-ttu-id="0b7ab-122">Windows PowerShell이 기본적으로 표시하는 속성이 아닌 다른 속성을 보려면 출력 데이터의 형식을 사용자가 직접 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b7ab-122">If you need to look at properties other than those that Windows PowerShell displays by default, you will need to format the output data yourself.</span></span> <span data-ttu-id="0b7ab-123">이렇게 하려면 Format cmdlet을 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b7ab-123">This can be done by using the format cmdlets.</span></span>
