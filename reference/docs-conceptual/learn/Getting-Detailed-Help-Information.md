---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: 자세한 도움말 정보 보기
ms.openlocfilehash: e722eb8a0ca13e3d2de864314775a0a9fa578390
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "74417665"
---
# <a name="getting-detailed-help-information"></a>자세한 도움말 정보 보기

PowerShell에는 PowerShell 개념과 PowerShell 언어를 설명하는 자세한 도움말 문서가 포함되어 있습니다. 각 cmdlet 및 공급자에 대한 도움말 문서와 많은 함수 및 스크립트에 대한 도움말 문서도 있습니다.

명령 프롬프트에서 이러한 도움말 문서를 표시하거나 [PowerShell](/powershell/scripting/overview)온라인 설명서에서 이러한 문서의 가장 최근 업데이트 버전을 볼 수 있습니다.

## <a name="getting-help-for-cmdlets"></a>cmdlet에 대한 도움말 보기

PowerShell cmdlet에 대한 도움말을 보려면 [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) cmdlet을 사용합니다. 예를 들어 `Get-ChildItem` cmdlet에 대한 도움말을 보려면 다음과 같이 입력합니다.

```powershell
Get-Help Get-ChildItem
```

또는

```powershell
Get-ChildItem -?
```

Get-Help cmdlet에 대한 도움말을 볼 수도 있습니다. 다음은 그 예입니다.

```powershell
Get-Help Get-Help
```

세션에 있는 모든 cmdlet 도움말 문서의 목록을 보려면 다음과 같이 입력합니다.

```powershell
Get-Help -Category Cmdlet
```

각 도움말 문서를 한 번에 한 페이지씩 표시하려면 `help` 함수 또는 해당 별칭 `man`을 사용합니다.
예를 들어 `Get-ChildItem` cmdlet에 대한 도움말을 표시하려면 다음과 같이 입력합니다.

```powershell
man Get-ChildItem
```

또는

```powershell
help Get-ChildItem
```

자세한 정보를 표시하려면 **cmdlet의**Detailed`Get-Help` 매개 변수를 사용합니다. 예를 들어 `Get-ChildItem` cmdlet에 대한 자세한 정보를 보려면 다음과 같이 입력합니다.

```powershell
Get-Help Get-ChildItem -Detailed
```

도움말 문서의 모든 내용을 표시하려면 **cmdlet의**Full`Get-Help` 매개 변수를 사용합니다. 예를 들어 `Get-ChildItem` cmdlet에 대한 도움말 문서의 모든 내용을 표시하려면 다음과 같이 입력합니다.

```powershell
Get-Help Get-ChildItem -Full
```

cmdlet의 매개 변수에 대한 자세한 도움말을 보려면 **cmdlet의**Parameter`Get-Help` 매개 변수를 사용합니다. 예를 들어 `Get-ChildItem` cmdlet의 모든 매개 변수에 대한 자세한 도움말을 보려면 다음과 같이 입력합니다.

```powershell
Get-Help Get-ChildItem -Parameter *
```

도움말 문서의 예제만 표시하려면 **의** Example`Get-Help` 매개 변수를 사용합니다.
예를 들어 `Get-ChildItem` cmdlet에 대한 도움말 문서의 예제만 표시하려면 다음과 같이 입력합니다.

```powershell
Get-Help Get-ChildItem -Examples
```

작성하는 cmdlet의 도움말 문서를 작성하는 방법에 대한 자세한 내용은 [Cmdlet 도움말 작성 방법](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)을 참조하세요.

## <a name="getting-conceptual-help"></a>개념 도움말 보기

`Get-Help` cmdlet은 PowerShell 언어에 대한 문서를 포함하여 PowerShell의 개념 항목에 대한 정보도 표시합니다. 개념 도움말 문서는 "about_" 접두사로 시작합니다(예: about_line_editing). 개념 문서의 이름은 영어가 아닌 PowerShell 버전에서도 영어로 입력해야 합니다.

개념 문서 목록을 표시하려면 다음과 같이 입력합니다.

```powershell
Get-Help about_*
```

특정 도움말 문서를 표시하려면 다음과 같이 문서 이름을 입력합니다.

```powershell
Get-Help about_command_syntax
```

`Get-Help`Detailed **,** Parameter**및**Examples**와 같은** 의 매개 변수는 개념 도움말 문서의 표시에 영향을 주지 않습니다.

## <a name="getting-help-about-providers"></a>공급자에 대한 도움말 보기

`Get-Help` cmdlet은 PowerShell 공급자에 대한 정보를 표시합니다. 공급자에 대한 도움말을 보려면 "`Get-Help`"를 입력한 다음, 공급자 이름을 입력합니다. 예를 들어 레지스트리 공급자에 대한 도움말을 보려면 다음과 같이 입력합니다.

```powershell
Get-Help registry
```

세션에 있는 모든 공급자 도움말 문서의 목록을 보려면 다음과 같이 입력합니다.

```powershell
Get-Help -Category provider
```

`Get-Help`Detailed **,** Parameter**및**Examples**와 같은** 의 매개 변수는 공급자 도움말 문서의 표시에 영향을 주지 않습니다.

## <a name="getting-help-about-scripts-and-functions"></a>스크립트 및 함수에 대한 도움말 보기

PowerShell의 많은 스크립트 및 함수에는 도움말 문서가 있습니다. `Get-Help` cmdlet을 사용하여 스크립트 및 함수에 대한 도움말 문서를 표시할 수 있습니다.

함수에 대한 도움말을 표시하려면 "`Get-Help`"를 입력한 다음, 함수 이름을 입력합니다. 예를 들어 `Disable-PSRemoting` 함수에 대한 도움말을 보려면 다음과 같이 입력합니다.

```powershell
Get-Help Disable-PSRemoting
```

스크립트에 대한 도움말을 표시하려면 스크립트 파일의 경로를 입력합니다. 스크립트가 Path 환경 변수에 나열된 경로에 없는 경우 정규화된 경로를 사용해야 합니다.

예를 들어 C:\\PS-Test 디렉터리에 "TestScript.ps1"이라는 스크립트가 있는 경우 이 스크립트의 도움말 문서를 표시하려면 다음과 같이 입력합니다.

```powershell
Get-Help c:\ps-test\TestScript.ps1
```

cmdlet 도움말을 표시하도록 디자인된 매개 변수는 스크립트 및 함수 도움말에도 작동합니다. 그러나 `Get-Help *`를 표시할 때 함수 및 스크립트에 대한 도움말은 표시되지 않습니다.

함수 및 스크립트에 대한 도움말 문서 작성에 대한 내용은 다음 문서를 참조하세요.

- [about_Functions](/powershell/module/microsoft.powershell.core/about/about_functions)
- [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)

## <a name="getting-help-online"></a>온라인 도움말 보기

온라인 도움말 문서는 도움말을 보는 가장 좋은 방법 중 하나입니다. 온라인 문서는 업데이트하기가 더 쉽고 가장 최신 콘텐츠를 제공합니다.

온라인 도움말을 보려면 **cmdlet의**Online`Get-Help` 매개 변수를 사용합니다. 공급자 도움말 및 개념(정보) 도움말을 포함하여 Powershell에 함께 제공되는 모든 도움말 문서는 온라인 [PowerShell](/powershell/scripting/powershell-scripting) 설명서에서 볼 수 있습니다.

> [!NOTE]
> 개념(about_ **) 또는 공급자 도움말 문서에서는** Online\* 매개 변수를 사용할 수 없습니다.
> 온라인 도움말은 선택 항목이기 때문에 일부 cmdlet, 함수 또는 스크립트에는 작동하지 않습니다.

예를 들어 `Get-ChildItem` cmdlet에 대한 온라인 버전의 도움말 문서를 보려면 다음과 같이 입력합니다.

```powershell
Get-Help Get-ChildItem -Online
```

PowerShell은 기본 브라우저에서 문서를 엽니다. 도움말 문서에 대해 온라인 도움말이 지원되는 경우 도움말 문서의 URL도 볼 수 있습니다. URL은 도움말 문서의 관련 링크 섹션에 나타납니다.

예를 들어 Add-Computer cmdlet의 온라인 버전에 대한 URL을 보려면 다음과 같이 입력합니다.

```powershell
Get-Help Add-Computer
```

문서의 관련 링크 섹션에 있는 첫 번째 줄은 아래와 같이 표시됩니다.

```Output
Online version: https://go.microsoft.com/fwlink/?LinkId=821564
```

도움말 문서에 대한 온라인 지원을 제공하는 방법에 대한 내용은 [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)를 참조하세요.

## <a name="see-also"></a>참고 항목

- [about_Functions](/powershell/module/microsoft.powershell.core/about/about_functions)
- [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)
- [Get-Help](/powershell/module/microsoft.powershell.core/get-help)
