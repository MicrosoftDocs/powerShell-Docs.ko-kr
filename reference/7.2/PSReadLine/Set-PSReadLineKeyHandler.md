---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
Locale: en-US
Module Name: PSReadLine
ms.date: 02/16/2021
online version: https://docs.microsoft.com/powershell/module/psreadline/set-psreadlinekeyhandler?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSReadLineKeyHandler
ms.openlocfilehash: 86386cb8d97e16ebdd869e2ec554fc947d788f67
ms.sourcegitcommit: 4f1c2fe700b8a0544c59e371eb7cfbc6d852b185
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100563289"
---
# <span data-ttu-id="7ed01-102">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="7ed01-102">Set-PSReadLineKeyHandler</span></span>

## <span data-ttu-id="7ed01-103">개요</span><span class="sxs-lookup"><span data-stu-id="7ed01-103">SYNOPSIS</span></span>
<span data-ttu-id="7ed01-104">키를 사용자 정의 또는 PSReadLine 키 처리기 함수에 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="7ed01-104">Binds keys to user-defined or PSReadLine key handler functions.</span></span>

## <span data-ttu-id="7ed01-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7ed01-105">SYNTAX</span></span>

### <span data-ttu-id="7ed01-106">ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="7ed01-106">ScriptBlock</span></span>

```
Set-PSReadLineKeyHandler [-ScriptBlock] <ScriptBlock> [-BriefDescription <String>]
 [-Description <String>] [-Chord] <String[]> [-ViMode <ViMode>] [<CommonParameters>]
```

### <span data-ttu-id="7ed01-107">기능</span><span class="sxs-lookup"><span data-stu-id="7ed01-107">Function</span></span>

```
Set-PSReadLineKeyHandler [-Chord] <String[]> [-ViMode <ViMode>] [-Function] <String>
 [<CommonParameters>]
```

## <span data-ttu-id="7ed01-108">설명</span><span class="sxs-lookup"><span data-stu-id="7ed01-108">DESCRIPTION</span></span>

<span data-ttu-id="7ed01-109">`Set-PSReadLineKeyHandler`Cmdlet은 키 또는 키 시퀀스를 누를 때 결과를 사용자 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ed01-109">The `Set-PSReadLineKeyHandler` cmdlet customizes the result when a key or sequence of keys is pressed.</span></span> <span data-ttu-id="7ed01-110">사용자 정의 키 바인딩을 사용 하면 PowerShell 스크립트 내에서 가능한 거의 모든 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ed01-110">With user-defined key bindings, you can do almost anything that is possible from within a PowerShell script.</span></span>

## <span data-ttu-id="7ed01-111">예제</span><span class="sxs-lookup"><span data-stu-id="7ed01-111">EXAMPLES</span></span>

### <span data-ttu-id="7ed01-112">예제 1: 화살표 키를 함수에 바인딩</span><span class="sxs-lookup"><span data-stu-id="7ed01-112">Example 1: Bind the arrow key to a function</span></span>

<span data-ttu-id="7ed01-113">이 명령은 위쪽 화살표 키를 **HistorySearchBackward** 함수에 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="7ed01-113">This command binds the up arrow key to the **HistorySearchBackward** function.</span></span> <span data-ttu-id="7ed01-114">이 함수는 명령줄의 현재 내용으로 시작 하는 명령줄에 대 한 명령 기록을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ed01-114">This function searches command history for command lines that start with the current contents of the command line.</span></span>

```powershell
Set-PSReadLineKeyHandler -Chord UpArrow -Function HistorySearchBackward
```

### <span data-ttu-id="7ed01-115">예제 2: 스크립트 블록에 키 바인딩</span><span class="sxs-lookup"><span data-stu-id="7ed01-115">Example 2: Bind a key to a script block</span></span>

<span data-ttu-id="7ed01-116">이 예제에서는 단일 키를 사용 하 여 명령을 실행 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7ed01-116">This example shows how a single key can be used to run a command.</span></span> <span data-ttu-id="7ed01-117">명령은 `Ctrl+B` 줄을 지우고 "build" 라는 단어를 삽입 한 다음 줄을 허용 하는 스크립트 블록에 키를 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="7ed01-117">The command binds the key `Ctrl+B` to a script block that clears the line, inserts the word "build", and then accepts the line.</span></span>

```powershell
Set-PSReadLineKeyHandler -Chord Ctrl+B -ScriptBlock {
    [Microsoft.PowerShell.PSConsoleReadLine]::RevertLine()
    [Microsoft.PowerShell.PSConsoleReadLine]::Insert('build')
    [Microsoft.PowerShell.PSConsoleReadLine]::AcceptLine()
}
```

## <span data-ttu-id="7ed01-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7ed01-118">PARAMETERS</span></span>

### <span data-ttu-id="7ed01-119">-BriefDescription</span><span class="sxs-lookup"><span data-stu-id="7ed01-119">-BriefDescription</span></span>

<span data-ttu-id="7ed01-120">키 바인딩에 대 한 간단한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="7ed01-120">A brief description of the key binding.</span></span> <span data-ttu-id="7ed01-121">이 설명은 cmdlet에 의해 표시 됩니다 `Get-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="7ed01-121">This description is displayed by the `Get-PSReadLineKeyHandler` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: ScriptBlock
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7ed01-122">-현</span><span class="sxs-lookup"><span data-stu-id="7ed01-122">-Chord</span></span>

<span data-ttu-id="7ed01-123">함수 또는 스크립트 블록에 바인딩할 키 또는 키 시퀀스입니다.</span><span class="sxs-lookup"><span data-stu-id="7ed01-123">The key or sequence of keys to be bound to a function or script block.</span></span> <span data-ttu-id="7ed01-124">단일 바인딩을 지정 하려면 단일 문자열을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ed01-124">Use a single string to specify a single binding.</span></span> <span data-ttu-id="7ed01-125">바인딩이 키 시퀀스 인 경우 다음 예제와 같이 키를 쉼표로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ed01-125">If the binding is a sequence of keys, separate the keys by a comma, as in the following example:</span></span>

`Ctrl+X,Ctrl+L`

> [!NOTE]
> <span data-ttu-id="7ed01-126">PSReadLine 2.0.0을 기반으로 하는 **현** 매개 변수는 **대/소문자를 구분** 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ed01-126">As of PSReadLine 2.0.0, the **Chord** parameter is **case-sensitive**.</span></span> <span data-ttu-id="7ed01-127">즉, `Ctrl+X` 와 `Ctrl+x` 는 서로 다른 바인딩을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7ed01-127">Meaning, `Ctrl+X` and `Ctrl+x` will create different bindings.</span></span>

<span data-ttu-id="7ed01-128">이 매개 변수는 문자열 배열을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ed01-128">This parameter accepts an array of strings.</span></span> <span data-ttu-id="7ed01-129">각 문자열은 단일 바인딩의 키 시퀀스가 아닌 별도의 바인딩입니다.</span><span class="sxs-lookup"><span data-stu-id="7ed01-129">Each string is a separate binding, not a sequence of keys for a single binding.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Key

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7ed01-130">-Description</span><span class="sxs-lookup"><span data-stu-id="7ed01-130">-Description</span></span>

<span data-ttu-id="7ed01-131">Cmdlet의 출력에 표시 되는 키 바인딩에 대 한 자세한 설명을 지정 합니다 `Get-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="7ed01-131">Specifies a more detailed description of the key binding that is visible in the output of the `Get-PSReadLineKeyHandler` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: ScriptBlock
Aliases: LongDescription

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7ed01-132">-함수</span><span class="sxs-lookup"><span data-stu-id="7ed01-132">-Function</span></span>

<span data-ttu-id="7ed01-133">PSReadLine에서 제공 하는 기존 키 처리기의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ed01-133">Specifies the name of an existing key handler provided by PSReadLine.</span></span> <span data-ttu-id="7ed01-134">이 매개 변수를 사용 하면 기존 키 바인딩을 다시 바인딩하거나 현재 바인딩되지 않은 처리기를 바인딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ed01-134">This parameter lets you rebind existing key bindings, or bind a handler that is currently unbound.</span></span>

```yaml
Type: System.String
Parameter Sets: Function
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7ed01-135">-ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="7ed01-135">-ScriptBlock</span></span>

<span data-ttu-id="7ed01-136">동시에 입력 될 때 실행할 스크립트 블록 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ed01-136">Specifies a script block value to run when the chord is entered.</span></span> <span data-ttu-id="7ed01-137">PSReadLine은이 스크립트 블록에 하나 또는 두 개의 매개 변수를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ed01-137">PSReadLine passes one or two parameters to this script block.</span></span> <span data-ttu-id="7ed01-138">첫 번째 매개 변수는 누른 키를 나타내는 **ConsoleKeyInfo** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="7ed01-138">The first parameter is a **ConsoleKeyInfo** object representing the key pressed.</span></span> <span data-ttu-id="7ed01-139">두 번째 인수는 컨텍스트에 따라 모든 개체가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ed01-139">The second argument can be any object depending on the context.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7ed01-140">-ViMode</span><span class="sxs-lookup"><span data-stu-id="7ed01-140">-ViMode</span></span>

<span data-ttu-id="7ed01-141">바인딩이 적용 되는 vi 모드를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ed01-141">Specify which vi mode the binding applies to.</span></span>

<span data-ttu-id="7ed01-142">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7ed01-142">Valid values are:</span></span>

- <span data-ttu-id="7ed01-143">Insert</span><span class="sxs-lookup"><span data-stu-id="7ed01-143">Insert</span></span>
- <span data-ttu-id="7ed01-144">명령</span><span class="sxs-lookup"><span data-stu-id="7ed01-144">Command</span></span>

```yaml
Type: Microsoft.PowerShell.ViMode
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7ed01-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7ed01-145">CommonParameters</span></span>

<span data-ttu-id="7ed01-146">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7ed01-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7ed01-147">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7ed01-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7ed01-148">입력</span><span class="sxs-lookup"><span data-stu-id="7ed01-148">INPUTS</span></span>

### <span data-ttu-id="7ed01-149">None</span><span class="sxs-lookup"><span data-stu-id="7ed01-149">None</span></span>

<span data-ttu-id="7ed01-150">이 cmdlet에 개체를 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ed01-150">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="7ed01-151">출력</span><span class="sxs-lookup"><span data-stu-id="7ed01-151">OUTPUTS</span></span>

### <span data-ttu-id="7ed01-152">None</span><span class="sxs-lookup"><span data-stu-id="7ed01-152">None</span></span>

<span data-ttu-id="7ed01-153">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ed01-153">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="7ed01-154">참고</span><span class="sxs-lookup"><span data-stu-id="7ed01-154">NOTES</span></span>

## <span data-ttu-id="7ed01-155">관련 링크</span><span class="sxs-lookup"><span data-stu-id="7ed01-155">RELATED LINKS</span></span>

[<span data-ttu-id="7ed01-156">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="7ed01-156">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)

[<span data-ttu-id="7ed01-157">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="7ed01-157">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)

[<span data-ttu-id="7ed01-158">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="7ed01-158">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)

[<span data-ttu-id="7ed01-159">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="7ed01-159">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)
