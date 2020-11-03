---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/wait-debugger?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Debugger
ms.openlocfilehash: f1488f65cf5ce48efe9d6459952653ff6570aa25
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2020
ms.locfileid: "93209353"
---
# <span data-ttu-id="130b3-103">Wait-Debugger</span><span class="sxs-lookup"><span data-stu-id="130b3-103">Wait-Debugger</span></span>

## <span data-ttu-id="130b3-104">개요</span><span class="sxs-lookup"><span data-stu-id="130b3-104">SYNOPSIS</span></span>
<span data-ttu-id="130b3-105">스크립트에서 다음 문을 실행 하기 전에 디버거에서 스크립트를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="130b3-105">Stops a script in the debugger before running the next statement in the script.</span></span>

## <span data-ttu-id="130b3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="130b3-106">SYNTAX</span></span>

```
Wait-Debugger [<CommonParameters>]
```

## <span data-ttu-id="130b3-107">설명</span><span class="sxs-lookup"><span data-stu-id="130b3-107">DESCRIPTION</span></span>

<span data-ttu-id="130b3-108">Cmdlet 바로 뒤의 지점에서 PowerShell 스크립트 실행 엔진을 중지 `Wait-Debugger` 하 고 디버거가 연결 될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="130b3-108">Stops the PowerShell script execution engine at the point immediately after the `Wait-Debugger` cmdlet and waits for a debugger to be attached.</span></span> <span data-ttu-id="130b3-109">이는 DSC 리소스에서를 사용 하는 것과 유사 `Enable-RunspaceDebug -BreakAll` 하지만 스크립트의 특정 지점에서 중단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="130b3-109">This is similar to using `Enable-RunspaceDebug -BreakAll` in a DSC resource but breaks at a specific point in the script.</span></span>

> [!CAUTION]
> <span data-ttu-id="130b3-110">완료 된 후 줄을 제거 해야 `Wait-Debugger` 합니다.</span><span class="sxs-lookup"><span data-stu-id="130b3-110">Make sure you remove the `Wait-Debugger` lines after you are done.</span></span> <span data-ttu-id="130b3-111">실행 중인 스크립트가에서 중지 되 면 멈춘 것 처럼 보입니다 `Wait-Debugger` .</span><span class="sxs-lookup"><span data-stu-id="130b3-111">A running script appears to be hung when it is stopped at a `Wait-Debugger`.</span></span>

## <span data-ttu-id="130b3-112">예제</span><span class="sxs-lookup"><span data-stu-id="130b3-112">EXAMPLES</span></span>

### <span data-ttu-id="130b3-113">예제 1: 디버깅을 위한 중단점 삽입</span><span class="sxs-lookup"><span data-stu-id="130b3-113">Example 1: Insert breakpoint for debugging</span></span>

```
[DscResource()]
class FileResource
{
    [DscProperty(Key)]
    [string] $Path

    [DscProperty(Mandatory)]
    [Ensure] $Ensure

    [DscProperty(Mandatory)]
    [string] $SourcePath

    [DscProperty(NotConfigurable)]
    [Nullable[datetime]] $CreationTime


    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)
        if ($this.ensure -eq [Ensure]::Present)
        {
            if (! $fileExists)
            {
               $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    [bool] Test()
    {
        $present = Test-Path -LiteralPath $this.Path

        if ($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
        {
            return (! $present)
        }
    }

    [FileResource] Get()
    {
        $present = Test-Path -Path $this.Path

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }

        return $this
    }

    [void] CopyFile()
    {
        # Testing only - Remove before deployment!
        Wait-Debugger

        if (! (Test-Path -LiteralPath $this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose "Copying $($this.SourcePath) to $($this.Path)"

        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
}
```

## <span data-ttu-id="130b3-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="130b3-114">PARAMETERS</span></span>

### <span data-ttu-id="130b3-115">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="130b3-115">CommonParameters</span></span>

<span data-ttu-id="130b3-116">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="130b3-116">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="130b3-117">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="130b3-117">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="130b3-118">입력</span><span class="sxs-lookup"><span data-stu-id="130b3-118">INPUTS</span></span>

### <span data-ttu-id="130b3-119">없음</span><span class="sxs-lookup"><span data-stu-id="130b3-119">None</span></span>

## <span data-ttu-id="130b3-120">출력</span><span class="sxs-lookup"><span data-stu-id="130b3-120">OUTPUTS</span></span>

### <span data-ttu-id="130b3-121">없음</span><span class="sxs-lookup"><span data-stu-id="130b3-121">None</span></span>

## <span data-ttu-id="130b3-122">참고</span><span class="sxs-lookup"><span data-stu-id="130b3-122">NOTES</span></span>

## <span data-ttu-id="130b3-123">관련 링크</span><span class="sxs-lookup"><span data-stu-id="130b3-123">RELATED LINKS</span></span>

[<span data-ttu-id="130b3-124">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="130b3-124">Enable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)
