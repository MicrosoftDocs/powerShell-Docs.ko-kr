---
title: 설명 기반 도움말 키워드
ms.custom: ''
ms.date: 06/09/2020
ms.topic: article
ms.openlocfilehash: 674d0f99800595cbbd64a80d0e0c5aed22f3b45c
ms.sourcegitcommit: 4a283fe5419f47102e6c1de7060880a934842ee9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84671379"
---
# <a name="comment-based-help-keywords"></a>설명 기반 도움말 키워드

이 항목에서는 주석 기반 도움말의 키워드를 나열 하 고 설명 합니다.

## <a name="keywords-in-comment-based-help"></a>주석 기반 도움말의 키워드

다음은 유효한 주석 기반 도움말 키워드입니다. 이러한 항목은 일반적으로 원하는 용도와 함께 도움말 항목에 표시 되는 순서 대로 나열 됩니다. 이러한 키워드는 주석 기반 도움말에서 순서에 관계 없이 나타날 수 있으며 대/소문자를 구분 하지 않습니다.

`.EXTERNALHELP`키워드는 다른 모든 주석 기반 도움말 키워드 보다 우선적으로 적용 됩니다.
`.EXTERNALHELP`가 있는 경우 [GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet은 키워드의 값과 일치 하는 도움말 파일을 찾을 수 없는 경우에도 주석 기반 도움말을 표시 하지 않습니다.

## <a name="synopsis"></a>. 개요

함수 또는 스크립트에 대 한 간단한 설명입니다. 이 키워드는 각 항목에서 한 번만 사용할 수 있습니다.

## <a name="description"></a>. 한

함수 또는 스크립트에 대 한 자세한 설명입니다. 이 키워드는 각 항목에서 한 번만 사용할 수 있습니다.

## <a name="parameter-parameter-name"></a>. 변수에\<Parameter-Name>

매개 변수에 대 한 설명입니다. `.PARAMETER`함수 또는 스크립트의 각 매개 변수에 대 한 키워드를 포함할 수 있습니다.

`.PARAMETER`키워드는 주석 블록에서 임의의 순서로 표시 될 수 있지만 매개 변수가 문이나 함수 선언에 표시 되는 순서에 `Param` 따라 매개 변수가 도움말 항목에 표시 되는 순서가 결정 됩니다. 도움말 항목의 매개 변수 순서를 변경 하려면 문이나 함수 선언에서 매개 변수의 순서를 변경 `Param` 합니다.

`Param`문에 주석을 매개 변수 이름 바로 앞에 배치 하 여 매개 변수 설명을 지정할 수도 있습니다. 문 주석과 키워드를 모두 사용 하는 경우 `Param` `.PARAMETER` 키워드와 연결 된 설명이 사용 되 `.PARAMETER` 고 `Param` 문 주석은 무시 됩니다.

## <a name="example"></a>. 예 들어

함수 또는 스크립트를 사용 하 고 선택적으로 샘플 출력과 설명을 차례로 사용 하는 샘플 명령입니다. 각 예제에 대해이 키워드를 반복 합니다.

## <a name="inputs"></a>. 내용

함수 또는 스크립트로 파이프 될 수 있는 개체의 Microsoft .NET 프레임 워크 형식입니다. 입력 개체에 대 한 설명을 포함할 수도 있습니다.

## <a name="outputs"></a>. 출력

Cmdlet이 반환 하는 개체의 .NET Framework 형식입니다. 반환 된 개체에 대 한 설명을 포함할 수도 있습니다.

## <a name="notes"></a>. 메모란

함수 또는 스크립트에 대 한 추가 정보입니다.

## <a name="link"></a>. 링크나

관련 항목의 이름입니다. 관련 된 각 항목에 대해이 키워드를 반복 합니다. 이 콘텐츠는 도움말 항목의 관련 링크 섹션에 나타납니다.

`.LINK`키워드 콘텐츠에는 동일한 도움말 항목의 온라인 버전에 대 한 URI (Uniform Resource Identifier)가 포함 될 수도 있습니다. 의 매개 변수를 사용할 때 온라인 버전이 열립니다 `Online` `Get-Help` . URI는 "http" 또는 "https"로 시작 해야 합니다.

## <a name="component"></a>. 구성 요소

함수나 스크립트에서 사용 하는 기술 또는 기능의 이름 또는 관련 된 기능입니다.
의 **구성 요소** 매개 변수는 `Get-Help` 이 값을 사용 하 여에서 반환 되는 검색 결과를 필터링 합니다 `Get-Help` .

## <a name="role"></a>. 역할

도움말 항목에 대 한 사용자 역할의 이름입니다. 의 **Role** 매개 변수는 `Get-Help` 이 값을 사용 하 여에서 반환 되는 검색 결과를 필터링 합니다 `Get-Help` .

## <a name="functionality"></a>. 기능성

함수의 용도를 설명 하는 키워드입니다. 의 **기능** 매개 변수는 `Get-Help` 이 값을 사용 하 여에서 반환 되는 검색 결과를 필터링 합니다 `Get-Help` .

## <a name="forwardhelptargetname-command-name"></a>. FORWARDHELPTARGETNAME\<Command-Name>

지정 된 명령에 대 한 도움말 항목으로 리디렉션합니다. 함수, 스크립트, cmdlet 또는 공급자에 대 한 도움말 항목을 포함 하 여 사용자를 도움말 항목으로 리디렉션할 수 있습니다.

## <a name="forwardhelpcategory-category"></a>. FORWARDHELPCATEGORY\<Category>

항목의 도움말 범주를 지정 합니다 `.FORWARDHELPTARGETNAME` . 동일한 이름을 가진 명령이 있는 경우 충돌을 방지 하려면이 키워드를 사용 합니다.

유효한 값은 다음과 같습니다.

- Alias
- Cmdlet
- HelpFile
- 함수
- 공급자
- 일반
- FAQ
- 용어
- ScriptCommand
- ExternalScript
- 필터
- 모두

## <a name="remotehelprunspace-pssession-variable"></a>. REMOTEHELPRUNSPACE\<PSSession-variable>

도움말 항목을 포함 하는 세션을 지정 합니다. PSSession이 포함 된 변수를 입력 합니다. 이 키워드는 `Export-PSSession` cmdlet에서 내보낸 명령에 대 한 도움말 항목을 찾는 데 사용 됩니다.

## <a name="externalhelp-xml-help-file"></a>. .EXTERNALHELP 설명을\<XML Help File>

스크립트나 함수에 대 한 XML 기반 도움말 파일의 경로 및/또는 이름을 지정 합니다.

`.EXTERNALHELP`키워드는 XML 기반 파일에서 스크립트나 함수에 대 한 도움말을 가져오기 위해 [GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet에 지시 합니다. `.EXTERNALHELP`키워드는 스크립트나 함수에 대 한 XML 기반 도움말 파일을 사용 하는 경우에 필요 합니다. 없는 경우 `Get-Help` 는 함수 또는 스크립트에 대 한 도움말 파일을 찾을 수 없습니다.

`.EXTERNALHELP`키워드는 다른 모든 주석 기반 도움말 키워드 보다 우선적으로 적용 됩니다. `.EXTERNALHELP`가 있는 경우 [GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet은 키워드의 값과 일치 하는 도움말 파일을 찾을 수 없는 경우에도 주석 기반 도움말을 표시 하지 않습니다.

스크립트 모듈에서 함수를 내보내는 경우 값은 `.EXTERNALHELP` 경로 없이 파일 이름 이어야 합니다. `Get-Help`모듈 디렉터리의 로캘별 하위 디렉터리에서 파일을 찾습니다. 파일 이름에 대 한 요구 사항은 없지만 파일 이름 형식를 사용 하는 것이 가장 좋습니다 `<ScriptModule>.psm1-help.xml` .

함수가 모듈과 연결 되어 있지 않으면 키워드의 값에 경로 및 파일 이름을 포함 `.EXTERNALHELP` 합니다. XML 파일에 대 한 지정 된 경로에 UI 문화권별 하위 디렉터리가 포함 된 경우는 `Get-Help` 모든 xml 기반 도움말 항목과 마찬가지로 Windows에 설정 된 언어 대체 표준에 따라 스크립트나 함수 이름을 사용 하 여 하위 디렉터리에서 xml 파일을 재귀적으로 검색 합니다.

Cmdlet 도움말 XML 기반 도움말 파일 형식에 대 한 자세한 내용은 [Windows PowerShell Cmdlet 도움말 작성](./writing-help-for-windows-powershell-cmdlets.md)을 참조 하세요.
