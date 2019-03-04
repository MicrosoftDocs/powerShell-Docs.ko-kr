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
ms.openlocfilehash: dbb6f7c4cbefeaaaec0747511f50192bcf08c20c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862659"
---
# <a name="comment-based-help-keywords"></a>설명 기반 도움말 키워드

이 항목에서는 나열 하 고 설명 기반 도움말 키워드를 설명 합니다.

## <a name="keywords-in-comment-based-help"></a>주석 기반 도움말 키워드

다음은 유효한 설명 기반 도움말 키워드입니다. 일반적으로 나타나는 의도 한 용도 함께 도움말 항목의 순서 대로 나열 됩니다. 이러한 키워드는 주석 기반 도움말에 임의의 순서로 나타날 수 있습니다 하 고 대/소문자 구분 없는 합니다.

`.ExternalHelp` 키워드는 다른 모든 설명 기반 도움말 키워드 보다 우선 합니다. 때 `.ExternalHelp` 가 있으면 합니다 [Microsoft.Powershell.Commands.Get 도움말](/dotnet/api/Microsoft.PowerShell.Commands.Get-Help) cmdlet 키워드의 값과 일치 하는 도움말 파일을 찾지 못하는 경우에 설명 기반 도움말을 표시 하지 않습니다.

`.Synopsis` 함수 또는 스크립트의 간략 한 설명입니다. 이 키워드는 각 항목에 한 번만 사용할 수 있습니다.

`.Description` 함수 또는 스크립트의 자세한 설명입니다. 이 키워드는 각 항목에 한 번만 사용할 수 있습니다.

`.Parameter` *\<매개 변수 이름 >* 매개 변수의 설명입니다. 포함할 수 있습니다는 `.Parameter` 함수 또는 스크립트를 각 매개 변수에 대해 키워드입니다.

`.Parameter` 키워드 주석 블록에서 순서에 관계 없이 하지만 매개 변수가 나타나는 순서에 나타날 수 있습니다는 `Param` 문 또는 함수 선언 매개 변수 도움말 항목에 표시 된 순서를 결정 합니다. 도움말 항목의 매개 변수의 순서를 변경 하려면 매개 변수 순서를 변경 합니다 `Param` 문 또는 함수 선언 합니다.

매개 변수 설명에 설명을 배치 하 여 지정할 수도 있습니다는 `Param` 문은 매개 변수 이름 바로 앞입니다. 둘 다 사용 하는 경우는 `Param` 문은 주석 및 `.Parameter` 키워드, 연결 된 설명을 합니다 `.Parameter` 키워드를 사용 및 `Param` 문을 주석이 무시 됩니다.

`.Example` 함수 또는 스크립트를 필요에 따라 샘플 출력을 설명 하는 샘플 명령입니다. 각 예제에 대 한이 키워드를 반복 합니다.

`.Inputs` Microsoft.NET Framework 형식 함수 또는 스크립트에 파이핑할 수 있는 개체입니다. 또한 입력된 개체에 대 한 설명을 포함할 수 있습니다.

`.Outputs` .NET Framework 형식 cmdlet에서 반환 하는 개체입니다. 또한 반환된 된 개체에 대 한 설명을 포함할 수 있습니다.

`.Notes` 함수 또는 스크립트에 대 한 추가 정보입니다.

`.Link` 관련된 항목의 이름입니다. 각 관련된 항목에 대 한이 키워드를 반복 합니다. 이 콘텐츠는 도움말 항목의 관련 링크 섹션에 표시 됩니다.

`.Link` 키워드 콘텐츠는 리소스 URI (Uniform Identifier)를 동일한 도움말 항목의 온라인 버전을 포함할 수도 있습니다. 온라인 버전을 사용 하는 경우 열립니다는 `Online` Get-help의 매개 변수입니다. URI는 "http" 또는 "https"로 시작 해야 합니다.

`.Component` 기술 또는 관련 된 또는 함수 또는 스크립트를 사용 하는 기능입니다. 이 콘텐츠는 Get-help 명령을 포함 하는 경우 표시 되는 `Component` Get-help의 매개 변수입니다.

`.Role` 도움말 항목에 대 한 사용자 역할입니다. 이 콘텐츠는 Get-help 명령을 포함 하는 경우 표시 되는 `Role` Get-help의 매개 변수입니다.

`.Functionality` 함수의 용도입니다. 이 콘텐츠는 Get-help 명령을 포함 하는 경우 표시 되는 `Functionality` Get-help의 매개 변수입니다.

`.ForwardHelpTargetName` `<Command-Name>` 지정된 된 명령에 대 한 도움말 항목으로 리디렉션. 함수, 스크립트, cmdlet 또는 공급자에 대 한 도움말 항목을 포함 하 여 모든 도움말 항목, 사용자를 리디렉션할 수 있습니다.

`.ForwardHelpCategory` `<Category>` ForwardHelpTargetName에서 도움말 항목의 범주를 지정합니다. 유효한 값에는 별칭, Cmdlet, HelpFile, 함수, 공급자, 일반, FAQ, 용어집, 스크립트 명령, ExternalScript, 필터 또는 모든 됩니다. 같은 이름의 명령이 있을 때 충돌을 방지 하려면이 키워드를 사용 합니다.

`.RemoteHelpRunspace` `<PSSession-variable>` 도움말 항목을 포함 하는 세션을 지정 합니다. PSSession이 포함 된 변수를 입력 합니다. 이 키워드를 사용해는 `Export-PSSession` 내보낸된 명령에 대 한 도움말 항목을 찾으려면 cmdlet.

`.ExternalHelp` `<XML Help File>` 경로 및/또는 스크립트 또는 함수에 대 한 XML 기반 도움말 파일의 이름을 지정합니다.

합니다 `.ExternalHelp` 키워드에 알립니다 합니다 [Microsoft.Powershell.Commands.Get 도움말](/dotnet/api/Microsoft.PowerShell.Commands.Get-Help) XML 기반 파일에 스크립트 또는 함수에 대 한 도움말을 보려면 cmdlet. **합니다. ExternalHelp** 키워드는 스크립트나 함수에 대 한 XML 기반 도움말 파일을 사용할 때 필요 합니다. 없으면 `Get-Help` 함수 또는 스크립트에 대 한 도움말 파일을 찾지 못합니다.

`.ExternalHelp` 키워드는 다른 모든 설명 기반 도움말 키워드 보다 우선 합니다. 때 `.ExternalHelp` 가 있으면 합니다 [Microsoft.Powershell.Commands.Get 도움말](/dotnet/api/Microsoft.PowerShell.Commands.Get-Help) cmdlet 키워드의 값과 일치 하는 도움말 파일을 찾지 못하는 경우에 설명 기반 도움말을 표시 하지 않습니다.

값을 스크립트 모듈에 의해 함수를 내보내는 경우 `.ExternalHelp` 경로 없이 파일 이름 이어야 합니다. `Get-Help` 모듈 디렉터리의 로캘별 하위 디렉터리에 파일을 찾습니다. 파일 이름에 대 한 요구 사항이 없습니다 있지만 다음 파일 이름 형식을 사용 하는 것이 좋습니다: `<ScriptModule>.psm1-help.xml`합니다.

함수 모듈에 연결 된 경우 경로 및 파일 이름을 값에 포함 된 **합니다. ExternalHelp** 키워드입니다. XML 파일에 지정된 된 경로 UI culture 별 하위 디렉터리를 포함 하는 경우 `Get-Help` 스크립트 또는 함수에 대 한 대체 (fallback) 표준을 설정 하는 언어에 따라 이름 사용 하 여 XML 파일에 대 한 하위 디렉터리가 재귀적으로 검색 Windows에서와 마찬가지로 모든 XML 기반 도움말 항목에 대 한 합니다.

Cmdlet 도움말 XML 기반 도움말 파일 형식에 대 한 자세한 내용은 참조 하세요. [쓰기 Windows PowerShell Cmdlet 도움말](./writing-help-for-windows-powershell-cmdlets.md)합니다.