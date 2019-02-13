---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: ISEFile 개체
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
ms.openlocfilehash: 24549720b8bc35435882533b0eb138de432ede65
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55680395"
---
# <a name="the-isefile-object"></a><span data-ttu-id="59205-103">ISEFile 개체</span><span class="sxs-lookup"><span data-stu-id="59205-103">The ISEFile Object</span></span>

<span data-ttu-id="59205-104">**ISEFile** 개체는 Windows PowerShell® ISE(통합 스크립팅 환경)에 있는 파일을 나타내며,</span><span class="sxs-lookup"><span data-stu-id="59205-104">An **ISEFile** object represents a file in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="59205-105">Microsoft.PowerShell.Host.ISE.ISEFile 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="59205-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span> <span data-ttu-id="59205-106">이 항목에는 멤버 메서드 및 멤버 속성이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="59205-106">This topic lists its member methods and member properties.</span></span> <span data-ttu-id="59205-107">**$psISE.CurrentFile**과 PowerShell 탭의 파일 컬렉션에 있는 파일이 Microsoft.PowerShell.Host.ISE.ISEFile 클래스의 전체 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="59205-107">The **$psISE.CurrentFile** and the files in the Files collection in a PowerShell tab are all instances of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span>

## <a name="methods"></a><span data-ttu-id="59205-108">메서드</span><span class="sxs-lookup"><span data-stu-id="59205-108">Methods</span></span>

### <a name="save-saveencoding-"></a><span data-ttu-id="59205-109">Save\( \[saveEncoding\] \)</span><span class="sxs-lookup"><span data-stu-id="59205-109">Save\( \[saveEncoding\] \)</span></span>

<span data-ttu-id="59205-110">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="59205-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="59205-111">파일을 디스크에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="59205-111">Saves the file to disk.</span></span>

<span data-ttu-id="59205-112">**\[saveEncoding\]** - 선택적 [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx). 저장된 파일에 사용할 선택적 문자 인코딩 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="59205-112">**\[saveEncoding\]** - optional [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="59205-113">기본값은 **UTF8**입니다.</span><span class="sxs-lookup"><span data-stu-id="59205-113">The default value is **UTF8**.</span></span>

### <a name="exceptions"></a><span data-ttu-id="59205-114">예외</span><span class="sxs-lookup"><span data-stu-id="59205-114">Exceptions</span></span>

- <span data-ttu-id="59205-115">**System.IO.IOException**: 파일을 저장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="59205-115">**System.IO.IOException**: The file could not be saved.</span></span>

```powershell
# Save the file using the default encoding (UTF8)
$psISE.CurrentFile.Save()

# Save the file as ASCII.
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)

# Gets the current encoding.
$myfile = $psISE.CurrentFile
$myfile.Encoding
```

### <a name="saveasfilename-saveencoding"></a><span data-ttu-id="59205-116">SaveAs\(filename, \[saveEncoding\]\)</span><span class="sxs-lookup"><span data-stu-id="59205-116">SaveAs\(filename, \[saveEncoding\]\)</span></span>

<span data-ttu-id="59205-117">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="59205-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="59205-118">지정한 파일 이름 및 인코딩으로 파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="59205-118">Saves the file with the specified file name and encoding.</span></span>

<span data-ttu-id="59205-119">**filename** - 파일을 저장하는 데 사용할 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="59205-119">**filename** - String The name to be used to save the file.</span></span>

<span data-ttu-id="59205-120">**\[saveEncoding\]** - 선택적 [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx). 저장된 파일에 사용할 선택적 문자 인코딩 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="59205-120">**\[saveEncoding\]** - optional [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="59205-121">기본값은 **UTF8**입니다.</span><span class="sxs-lookup"><span data-stu-id="59205-121">The default value is **UTF8**.</span></span>

### <a name="exceptions"></a><span data-ttu-id="59205-122">예외</span><span class="sxs-lookup"><span data-stu-id="59205-122">Exceptions</span></span>

- <span data-ttu-id="59205-123">**System.ArgumentNullException**: 합니다 **filename** 매개 변수가 null입니다.</span><span class="sxs-lookup"><span data-stu-id="59205-123">**System.ArgumentNullException**: The **filename** parameter is null.</span></span>
- <span data-ttu-id="59205-124">**System.ArgumentException**: 합니다 **filename** 매개 변수가 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59205-124">**System.ArgumentException**: The **filename** parameter is empty.</span></span>
- <span data-ttu-id="59205-125">**System.IO.IOException**: 파일을 저장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="59205-125">**System.IO.IOException**: The file could not be saved.</span></span>

```powershell
# Save the file with a full path and name.
$fullpath = "c:\temp\newname.txt"
$psISE.CurrentFile.SaveAs($fullPath)
# Save the file with a full path and name and explicitly as UTF8.
$psISE.CurrentFile.SaveAs($fullPath, [System.Text.Encoding]::UTF8)
```

## <a name="properties"></a><span data-ttu-id="59205-126">속성</span><span class="sxs-lookup"><span data-stu-id="59205-126">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="59205-127">DisplayName</span><span class="sxs-lookup"><span data-stu-id="59205-127">DisplayName</span></span>

<span data-ttu-id="59205-128">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="59205-128">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="59205-129">이 파일의 표시 이름을 포함하는 문자열을 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="59205-129">The read-only property that gets the string that contains the display name of this file.</span></span> <span data-ttu-id="59205-130">이름은 편집기의 맨 위에 있는 **파일** 탭에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="59205-130">The name is shown on the **File** tab at the top of the editor.</span></span> <span data-ttu-id="59205-131">이름의 끝에 별표(\(\*\))가 있다면 파일에 저장되지 않은 변경 내용이 있다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="59205-131">The presence of an asterisk \(\*\) at the end of the name indicates that the file has changes that have not been saved.</span></span>

```powershell
# Shows the display name of the file.
$psISE.CurrentFile.DisplayName
```

### <a name="editor"></a><span data-ttu-id="59205-132">편집기</span><span class="sxs-lookup"><span data-stu-id="59205-132">Editor</span></span>

<span data-ttu-id="59205-133">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="59205-133">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="59205-134">지정된 파일에 사용되는 [편집기 개체](The-ISEEditor-Object.md)를 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="59205-134">The read-only property that gets the [editor object](The-ISEEditor-Object.md) that is used for the specified file.</span></span>

```powershell
# Gets the editor and the text.
$psISE.CurrentFile.Editor.Text
```

### <a name="encoding"></a><span data-ttu-id="59205-135">인코딩</span><span class="sxs-lookup"><span data-stu-id="59205-135">Encoding</span></span>

<span data-ttu-id="59205-136">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="59205-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="59205-137">원래 파일 인코딩을 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="59205-137">The read-only property that gets the original file encoding.</span></span> <span data-ttu-id="59205-138">**System.Text.Encoding** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="59205-138">This is a **System.Text.Encoding** object.</span></span>

```powershell
# Shows the encoding for the file.
$psISE.CurrentFile.Encoding
```

### <a name="fullpath"></a><span data-ttu-id="59205-139">FullPath</span><span class="sxs-lookup"><span data-stu-id="59205-139">FullPath</span></span>

<span data-ttu-id="59205-140">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="59205-140">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="59205-141">열려 있는 파일의 전체 경로를 지정하는 문자열을 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="59205-141">The read-only property that gets the string that specifies the full path of the opened file.</span></span>

```powershell
# Shows the full path for the file.
$psISE.CurrentFile.FullPath
```

### <a name="issaved"></a><span data-ttu-id="59205-142">IsSaved</span><span class="sxs-lookup"><span data-stu-id="59205-142">IsSaved</span></span>

<span data-ttu-id="59205-143">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="59205-143">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="59205-144">파일이 마지막으로 수정한 후 저장된 경우 **$true**를 반환하는 읽기 전용 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="59205-144">The read-only Boolean property that returns **$true** if the file has been saved after it was last modified.</span></span>

```powershell
# Determines whether the file has been saved since it was last modified.
$myfile = $psISE.CurrentFile
$myfile.IsSaved
```

### <a name="isuntitled"></a><span data-ttu-id="59205-145">IsUntitled</span><span class="sxs-lookup"><span data-stu-id="59205-145">IsUntitled</span></span>

<span data-ttu-id="59205-146">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="59205-146">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="59205-147">파일에 제목이 지정된 적이 없는 경우 **$true**를 반환하는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="59205-147">The read-only property that returns **$true** if the file has never been given a title.</span></span>

```powershell
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled
```

## <a name="see-also"></a><span data-ttu-id="59205-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="59205-148">See Also</span></span>

- [<span data-ttu-id="59205-149">The ISEFileCollectionObject</span><span class="sxs-lookup"><span data-stu-id="59205-149">The ISEFileCollectionObject</span></span>](The-ISEFileCollection-Object.md)
- [<span data-ttu-id="59205-150">Windows PowerShell ISE 스크립팅 개체 모델의 용도</span><span class="sxs-lookup"><span data-stu-id="59205-150">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="59205-151">ISE 개체 모델 계층 구조</span><span class="sxs-lookup"><span data-stu-id="59205-151">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)