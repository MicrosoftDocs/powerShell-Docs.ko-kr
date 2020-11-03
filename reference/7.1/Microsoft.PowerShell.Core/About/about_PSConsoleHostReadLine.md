---
description: 콘솔 프롬프트에서 PowerShell에서 입력을 읽는 방법을 사용자 지정 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/04/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_psconsolehostreadline?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSConsoleHostReadLine
ms.openlocfilehash: 143fa763c109b5645f992c3bb0a3097a8b2d9e90
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93220873"
---
# <a name="about_psconsolehostreadline"></a>about_PSConsoleHostReadLine

## <a name="short-description"></a>간단한 설명
콘솔 프롬프트에서 PowerShell에서 입력을 읽는 방법을 사용자 지정 하는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명

Windows PowerShell 3.0부터 콘솔 입력이 처리 되는 기본 방법을 재정의 하는 PSConsoleHostReadLine 라는 함수를 작성할 수 있습니다.

### <a name="examples"></a>예제

다음 예제에서는 메모장을 시작 하 고 사용자가 만드는 텍스트 파일에서 입력을 가져옵니다.

```powershell
function PSConsoleHostReadLine
{
  $inputFile = Join-Path $env:TEMP PSConsoleHostReadLine
  Set-Content $inputFile "PS > "

  # Notepad opens. Enter your command in it, save the file, and then exit.
  notepad $inputFile | Out-Null
  $userInput = Get-Content $inputFile
  $resultingCommand = $userInput.Replace("PS >", "")
  $resultingCommand
}
```

### <a name="remarks"></a>REMARKS

기본적으로 PowerShell은 Windows 콘솔 하위 시스템이 모든 keypresses, F7 메뉴 및 기타 입력을 처리 하는 "가공 된 모드" 라고 하는 콘솔에서 입력을 읽습니다. Enter 또는 Tab 키를 누르면 PowerShell에서 해당 지점까지 입력 한 텍스트를 가져옵니다. Enter 또는 Tab 키를 누르기 전에 Ctrl + R, Ctrl + A, Ctrl + E 또는 다른 키를 눌렀음을 확인할 수 있는 방법은 없습니다. Windows PowerShell 3.0에서 PSConsoleHostReadLine 함수는이 문제를 해결 합니다. PowerShell 콘솔 호스트에서 PSConsoleHostReadline 이라는 함수를 정의 하는 경우 PowerShell은 "가공 된 Mode" 입력 메커니즘 대신 해당 함수를 호출 합니다.

### <a name="see-also"></a>참고 항목

[about_Prompts](about_Prompts.md)

