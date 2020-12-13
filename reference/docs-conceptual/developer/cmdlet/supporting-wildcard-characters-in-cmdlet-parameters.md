---
ms.date: 08/26/2019
ms.topic: reference
title: Cmdlet 매개 변수에서 와일드카드 문자 지원
description: Cmdlet 매개 변수에서 와일드카드 문자 지원
ms.openlocfilehash: 06693c62cd2613050bdeb9d6b12ad6e9597a9894
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646399"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a><span data-ttu-id="8348c-103">Cmdlet 매개 변수에서 와일드카드 문자 지원</span><span class="sxs-lookup"><span data-stu-id="8348c-103">Supporting Wildcard Characters in Cmdlet Parameters</span></span>

<span data-ttu-id="8348c-104">단일 리소스 대신 리소스 그룹에 대해 실행 되도록 cmdlet을 디자인 해야 하는 경우가 종종 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8348c-104">Often, you will have to design a cmdlet to run against a group of resources rather than against a single resource.</span></span> <span data-ttu-id="8348c-105">예를 들어 cmdlet은 이름이 나 확장명이 같은 데이터 저장소의 모든 파일을 찾아야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8348c-105">For example, a cmdlet might need to locate all the files in a data store that have the same name or extension.</span></span> <span data-ttu-id="8348c-106">리소스 그룹에 대해 실행 될 cmdlet을 디자인할 때 와일드 카드 문자에 대 한 지원을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8348c-106">You must provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

> [!NOTE]
> <span data-ttu-id="8348c-107">*와일드 카드 사용* 라고도 하는 와일드 카드 문자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8348c-107">Using wildcard characters is sometimes referred to as *globbing*.</span></span>

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a><span data-ttu-id="8348c-108">와일드 카드를 사용 하는 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8348c-108">Windows PowerShell Cmdlets That Use Wildcards</span></span>

 <span data-ttu-id="8348c-109">많은 Windows PowerShell cmdlet은 해당 매개 변수 값에 와일드 카드 문자를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="8348c-109">Many Windows PowerShell cmdlets support wildcard characters for their parameter values.</span></span> <span data-ttu-id="8348c-110">예를 들어 또는 매개 변수가 있는 거의 모든 cmdlet은 `Name` `Path` 이러한 매개 변수에 대해 와일드 카드 문자를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="8348c-110">For example, almost every cmdlet that has a `Name` or `Path` parameter supports wildcard characters for these parameters.</span></span> <span data-ttu-id="8348c-111">매개 변수를 포함 하는 대부분의 cmdlet에는 `Path` `LiteralPath` 와일드 카드 문자를 지원 하지 않는 매개 변수도 있습니다. 다음 명령은 와일드 카드 문자를 사용 하 여 이름에 Get 동사가 포함 된 현재 세션의 모든 cmdlet을 반환 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8348c-111">(Although most cmdlets that have a `Path` parameter also have a `LiteralPath` parameter that does not support wildcard characters.) The following command shows how a wildcard character is used to return all the cmdlets in the current session whose name contains the Get verb.</span></span>

 `Get-Command get-*`

## <a name="supported-wildcard-characters"></a><span data-ttu-id="8348c-112">지원 되는 와일드 카드 문자</span><span class="sxs-lookup"><span data-stu-id="8348c-112">Supported Wildcard Characters</span></span>

<span data-ttu-id="8348c-113">Windows PowerShell은 다음 와일드 카드 문자를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="8348c-113">Windows PowerShell supports the following wildcard characters.</span></span>

| <span data-ttu-id="8348c-114">와일드카드</span><span class="sxs-lookup"><span data-stu-id="8348c-114">Wildcard</span></span> |                             <span data-ttu-id="8348c-115">설명</span><span class="sxs-lookup"><span data-stu-id="8348c-115">Description</span></span>                             |  <span data-ttu-id="8348c-116">예제</span><span class="sxs-lookup"><span data-stu-id="8348c-116">Example</span></span>   |     <span data-ttu-id="8348c-117">일치하는 항목</span><span class="sxs-lookup"><span data-stu-id="8348c-117">Matches</span></span>      | <span data-ttu-id="8348c-118">일치하지 않는 항목</span><span class="sxs-lookup"><span data-stu-id="8348c-118">Does not match</span></span> |
| -------- | ------------------------------------------------------------------- | ---------- | ---------------- | -------------- |
| *        | <span data-ttu-id="8348c-119">지정 된 위치에서 시작 하 여 0 개 이상의 문자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8348c-119">Matches zero or more characters, starting at the specified position</span></span> | `a*`       | <span data-ttu-id="8348c-120">A, ag, Apple</span><span class="sxs-lookup"><span data-stu-id="8348c-120">A, ag, Apple</span></span>     |                |
| <span data-ttu-id="8348c-121">?</span><span class="sxs-lookup"><span data-stu-id="8348c-121">?</span></span>        | <span data-ttu-id="8348c-122">지정 된 위치의 모든 문자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8348c-122">Matches any character at the specified position</span></span>                     | `?n`       | <span data-ttu-id="8348c-123">, In, on</span><span class="sxs-lookup"><span data-stu-id="8348c-123">An, in, on</span></span>       | <span data-ttu-id="8348c-124">되었음</span><span class="sxs-lookup"><span data-stu-id="8348c-124">ran</span></span>            |
| <span data-ttu-id="8348c-125">[ ]</span><span class="sxs-lookup"><span data-stu-id="8348c-125">[ ]</span></span>      | <span data-ttu-id="8348c-126">문자 범위를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8348c-126">Matches a range of characters</span></span>                                       | `[a-l]ook` | <span data-ttu-id="8348c-127">책, 쿡, 모양</span><span class="sxs-lookup"><span data-stu-id="8348c-127">book, cook, look</span></span> | <span data-ttu-id="8348c-128">nook, 걸린 시간</span><span class="sxs-lookup"><span data-stu-id="8348c-128">nook, took</span></span>     |
| <span data-ttu-id="8348c-129">[ ]</span><span class="sxs-lookup"><span data-stu-id="8348c-129">[ ]</span></span>      | <span data-ttu-id="8348c-130">지정 된 문자와 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="8348c-130">Matches the specified characters</span></span>                                    | `[bn]ook`  | <span data-ttu-id="8348c-131">서적, nook</span><span class="sxs-lookup"><span data-stu-id="8348c-131">book, nook</span></span>       | <span data-ttu-id="8348c-132">쿡, 살펴보기</span><span class="sxs-lookup"><span data-stu-id="8348c-132">cook, look</span></span>     |

<span data-ttu-id="8348c-133">와일드 카드 문자를 지 원하는 cmdlet을 디자인 하는 경우 와일드 카드 문자 조합을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8348c-133">When you design cmdlets that support wildcard characters, allow for combinations of wildcard characters.</span></span> <span data-ttu-id="8348c-134">예를 들어 다음 명령은 cmdlet을 사용 하 여 `Get-ChildItem` c:\Techdocs 폴더에 있고 문자 "a"부터 "l"로 시작 하는 모든 .txt 파일을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="8348c-134">For example, the following command uses the `Get-ChildItem` cmdlet to retrieve all the .txt files that are in the c:\Techdocs folder and that begin with the letters "a" through "l."</span></span>

`Get-ChildItem c:\techdocs\[a-l]\*.txt`

<span data-ttu-id="8348c-135">이전 명령은 range 와일드 카드를 사용 하 여 `[a-l]` 파일 이름이 문자 "a"부터 "l"로 시작 하 고, 파일 이름 `*` 및 **.txt** 확장명의 첫 문자 사이에 있는 모든 문자에 대 한 자리 표시자로 와일드 카드 문자를 사용 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8348c-135">The previous command uses the range wildcard `[a-l]` to specify that the file name should begin with the characters "a" through "l" and uses the `*` wildcard character as a placeholder for any characters between the first letter of the filename and the **.txt** extension.</span></span>

<span data-ttu-id="8348c-136">다음 예제에서는 "d" 문자를 제외 하 고 "a"부터 "f" 까지의 다른 모든 문자를 포함 하는 범위 와일드 카드 패턴을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8348c-136">The following example uses a range wildcard pattern that excludes the letter "d" but includes all the other letters from "a" through "f."</span></span>

`Get-ChildItem c:\techdocs\[a-cef]\*.txt`

## <a name="handling-literal-characters-in-wildcard-patterns"></a><span data-ttu-id="8348c-137">와일드 카드 패턴의 리터럴 문자 처리</span><span class="sxs-lookup"><span data-stu-id="8348c-137">Handling Literal Characters in Wildcard Patterns</span></span>

<span data-ttu-id="8348c-138">지정 하는 와일드 카드 패턴에 와일드 카드 문자로 interpretted 서는 안 되는 리터럴 문자가 포함 된 경우에는 억음 문자 ( `` ` `` )를 이스케이프 문자로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8348c-138">If the wildcard pattern you specify contains literal characters that should not be interpretted as wildcard characters, use the backtick character (`` ` ``) as an escape character.</span></span> <span data-ttu-id="8348c-139">PowerShell API에서 리터럴 문자를 지정 하는 경우 단일 backtick을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8348c-139">When you specify literal characters int the PowerShell API, use a single backtick.</span></span> <span data-ttu-id="8348c-140">PowerShell 명령 프롬프트에서 리터럴 문자를 지정 하는 경우 두 개의 backticks을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8348c-140">When you specify literal characters at the PowerShell command prompt, use two backticks.</span></span>

<span data-ttu-id="8348c-141">예를 들어 다음 패턴에는 문자 그대로 수행 해야 하는 두 개의 대괄호가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8348c-141">For example, the following pattern contains two brackets that must be taken literally.</span></span>

<span data-ttu-id="8348c-142">PowerShell API에서 사용 하는 경우 다음을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8348c-142">When used in the PowerShell API use:</span></span>

- <span data-ttu-id="8348c-143">"John Smith \` [\* ']"</span><span class="sxs-lookup"><span data-stu-id="8348c-143">"John Smith \`[\*\`]"</span></span>

<span data-ttu-id="8348c-144">PowerShell 명령 프롬프트에서 사용 되는 경우:</span><span class="sxs-lookup"><span data-stu-id="8348c-144">When used from the PowerShell command prompt:</span></span>

- <span data-ttu-id="8348c-145">"John Smith \` \` [\* \` ']"</span><span class="sxs-lookup"><span data-stu-id="8348c-145">"John Smith \`\`[\*\`\`]"</span></span>

<span data-ttu-id="8348c-146">이 패턴은 "John Smith [Marketing]" 또는 "John Smith [Development]"와 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="8348c-146">This pattern matches "John Smith [Marketing]" or "John Smith [Development]".</span></span> <span data-ttu-id="8348c-147">예를 들어:</span><span class="sxs-lookup"><span data-stu-id="8348c-147">For example:</span></span>

```
PS> "John Smith [Marketing]" -like "John Smith ``[*``]"
True

PS> "John Smith [Development]" -like "John Smith ``[*``]"
True
```

## <a name="cmdlet-output-and-wildcard-characters"></a><span data-ttu-id="8348c-148">Cmdlet 출력 및 와일드 카드 문자</span><span class="sxs-lookup"><span data-stu-id="8348c-148">Cmdlet Output and Wildcard Characters</span></span>

<span data-ttu-id="8348c-149">Cmdlet 매개 변수가 와일드 카드 문자를 지 원하는 경우이 작업은 일반적으로 배열 출력을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="8348c-149">When cmdlet parameters support wildcard characters, the operation usually generates an array output.</span></span>
<span data-ttu-id="8348c-150">사용자가 단일 항목만 사용할 수 있기 때문에 경우에 따라 배열 출력을 지 원하는 것은 바람직하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8348c-150">Occasionally, it makes no sense to support an array output because the user might use only a single item.</span></span> <span data-ttu-id="8348c-151">예를 들어 `Set-Location` 사용자가 단일 위치만 설정 하므로 cmdlet은 배열 출력을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8348c-151">For example, the `Set-Location` cmdlet does not support array output because the user sets only a single location.</span></span> <span data-ttu-id="8348c-152">이 인스턴스에서 cmdlet은 여전히 와일드 카드 문자를 지원 하지만 단일 위치에 대해 해상도를 강제 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8348c-152">In this instance, the cmdlet still supports wildcard characters, but it forces resolution to a single location.</span></span>

## <a name="see-also"></a><span data-ttu-id="8348c-153">관련 항목</span><span class="sxs-lookup"><span data-stu-id="8348c-153">See Also</span></span>

[<span data-ttu-id="8348c-154">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="8348c-154">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="8348c-155">WildcardPattern 클래스</span><span class="sxs-lookup"><span data-stu-id="8348c-155">WildcardPattern Class</span></span>](/dotnet/api/system.management.automation.wildcardpattern)
