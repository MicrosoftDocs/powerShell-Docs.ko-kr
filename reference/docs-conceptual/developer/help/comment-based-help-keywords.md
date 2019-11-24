---
title: 주석 기반 도움말 키워드 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab90ec96-77f5-42e3-9c7e-2f4156ec207f
caps.latest.revision: 6
ms.openlocfilehash: 534a6c9a43326c8a01b2181c7a799286fa4d3997
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361362"
---
# <a name="comment-based-help-keywords"></a>설명 기반 도움말 키워드

이 항목에서는 주석 기반 도움말의 키워드를 나열 하 고 설명 합니다.

## <a name="keywords-in-comment-based-help"></a>주석 기반 도움말의 키워드

다음은 유효한 주석 기반 도움말 키워드입니다. 이러한 항목은 일반적으로 원하는 용도와 함께 도움말 항목에 표시 되는 순서 대로 나열 됩니다. 이러한 키워드는 주석 기반 도움말에서 순서에 관계 없이 나타날 수 있으며 대/소문자를 구분 하지 않습니다.

`.ExternalHelp` 키워드는 다른 모든 주석 기반 도움말 키워드 보다 우선적으로 적용 됩니다. `.ExternalHelp` 있는 경우 [GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet은 키워드의 값과 일치 하는 도움말 파일을 찾을 수 없는 경우에도 주석 기반 도움말을 표시 하지 않습니다.

함수 또는 스크립트에 대 한 간략 한 설명을 `.Synopsis` 합니다. 이 키워드는 각 항목에서 한 번만 사용할 수 있습니다.

함수 또는 스크립트에 대 한 자세한 설명을 `.Description` 합니다. 이 키워드는 각 항목에서 한 번만 사용할 수 있습니다.

매개 변수에 대 한 설명 *>\<매개 변수 이름* `.Parameter` 합니다. 함수 또는 스크립트의 각 매개 변수에 대 한 `.Parameter` 키워드를 포함할 수 있습니다.

`.Parameter` 키워드는 주석 블록에서 순서에 관계 없이 나타날 수 있지만 `Param` 문이나 함수 선언에 매개 변수가 나타나는 순서에 따라 매개 변수가 도움말 항목에 표시 되는 순서가 결정 됩니다. 도움말 항목의 매개 변수 순서를 변경 하려면 `Param` 문이나 함수 선언에서 매개 변수의 순서를 변경 합니다.

`Param` 문에 주석을 매개 변수 이름 바로 앞에 배치 하 여 매개 변수 설명을 지정할 수도 있습니다. `Param` 문 주석과 `.Parameter` 키워드를 모두 사용 하는 경우 `.Parameter` 키워드와 연결 된 설명이 사용 되며, `Param` 문 주석은 무시 됩니다.

함수 또는 스크립트를 사용 하 고 선택적으로 샘플 출력과 설명으로 이어지는 샘플 명령을 `.Example` 합니다. 각 예제에 대해이 키워드를 반복 합니다.

함수 또는 스크립트로 파이프 될 수 있는 개체의 Microsoft .NET Framework 형식을 `.Inputs` 합니다. 입력 개체에 대 한 설명을 포함할 수도 있습니다.

cmdlet이 반환 하는 개체의 .NET Framework 유형을 `.Outputs` 합니다. 반환 된 개체에 대 한 설명을 포함할 수도 있습니다.

함수 또는 스크립트에 대 한 추가 정보를 `.Notes` 합니다.

관련 항목의 이름을 `.Link` 합니다. 관련 된 각 항목에 대해이 키워드를 반복 합니다. 이 콘텐츠는 도움말 항목의 관련 링크 섹션에 나타납니다.

`.Link` 키워드 콘텐츠에는 동일한 도움말 항목의 온라인 버전에 대 한 URI (Uniform Resource Identifier)가 포함 될 수도 있습니다. Get-help의 `Online` 매개 변수를 사용 하면 온라인 버전이 열립니다. URI는 "http" 또는 "https"로 시작 해야 합니다.

함수나 스크립트에서 사용 하는 기술 또는 기능 또는 관련 된 기능을 `.Component` 합니다. Get-help 명령에 Get-help의 `Component` 매개 변수가 포함 되어 있으면이 콘텐츠가 표시 됩니다.

도움말 항목에 대 한 사용자 역할을 `.Role` 합니다. Get-help 명령에 Get-help의 `Role` 매개 변수가 포함 되어 있으면이 콘텐츠가 표시 됩니다.

함수의 용도를 `.Functionality` 합니다. Get-help 명령에 Get-help의 `Functionality` 매개 변수가 포함 되어 있으면이 콘텐츠가 표시 됩니다.

`.ForwardHelpTargetName` `<Command-Name>` 지정 된 명령에 대 한 도움말 항목으로 리디렉션됩니다. 함수, 스크립트, cmdlet 또는 공급자에 대 한 도움말 항목을 포함 하 여 사용자를 도움말 항목으로 리디렉션할 수 있습니다.

`.ForwardHelpCategory` `<Category>`는 ForwardHelpTargetName에 항목의 도움말 범주를 지정 합니다. 유효한 값은 Alias, Cmdlet, HelpFile, Function, Provider, General, FAQ, 용어집, ScriptCommand, ExternalScript, Filter 또는 All입니다. 동일한 이름을 가진 명령이 있는 경우 충돌을 방지 하려면이 키워드를 사용 합니다.

`.RemoteHelpRunspace` `<PSSession-variable>`는 도움말 항목을 포함 하는 세션을 지정 합니다. PSSession이 포함 된 변수를 입력 합니다. 이 키워드는 `Export-PSSession` cmdlet에서 내보낸 명령에 대 한 도움말 항목을 찾는 데 사용 됩니다.

`<XML Help File>` `.ExternalHelp` 스크립트나 함수에 대 한 XML 기반 도움말 파일의 경로 및/또는 이름을 지정 합니다.

`.ExternalHelp` 키워드는 XML 기반 파일에서 스크립트나 함수에 대 한 도움말을 가져오기 위해 [GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet에 지시 합니다. **입니다.** 스크립트 또는 함수에 XML 기반 도움말 파일을 사용 하는 경우에는 ExternalHelp 키워드가 필요 합니다. 이 파일을 사용 하지 않으면 `Get-Help` 함수 또는 스크립트에 대 한 도움말 파일을 찾을 수 없습니다.

`.ExternalHelp` 키워드는 다른 모든 주석 기반 도움말 키워드 보다 우선적으로 적용 됩니다. `.ExternalHelp` 있는 경우 [GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet은 키워드의 값과 일치 하는 도움말 파일을 찾을 수 없는 경우에도 주석 기반 도움말을 표시 하지 않습니다.

스크립트 모듈에서 함수를 내보내는 경우 `.ExternalHelp` 값은 경로 없이 파일 이름 이어야 합니다. `Get-Help` 모듈 디렉터리의 로캘별 하위 디렉터리에서 파일을 찾습니다. 파일 이름에 대 한 요구 사항은 없지만 파일 이름 형식 `<ScriptModule>.psm1-help.xml`를 사용 하는 것이 가장 좋습니다.

함수가 모듈과 연결 되지 않은 경우의 값에 경로 및 파일 이름을 포함 **합니다. ExternalHelp** 키워드입니다. XML 파일에 대 한 지정 된 경로에 UI 문화권별 하위 디렉터리가 포함 된 경우 `Get-Help`은 모든 XML 기반 도움말 항목과 마찬가지로 Windows에 설정 된 언어 대체 표준에 따라 스크립트나 함수 이름을 사용 하 여 하위 디렉터리에서 XML 파일을 재귀적으로 검색 합니다.

Cmdlet 도움말 XML 기반 도움말 파일 형식에 대 한 자세한 내용은 [Windows PowerShell Cmdlet 도움말 작성](./writing-help-for-windows-powershell-cmdlets.md)을 참조 하세요.