---
title: 온라인 도움말 지원 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: b76f45299d11dc10c8b16ed80f87c7f1fcc5ed65
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857919"
---
# <a name="supporting-online-help"></a>온라인 도움말 지원

Windows PowerShell 3.0 부터는 두 가지 지원 하기는 `Get-Help` Windows PowerShell 명령에 대 한 온라인 기능입니다. 이 항목에서는 다양 한 명령 형식에 대 한이 기능을 구현 하는 방법에 설명 합니다.

## <a name="about-online-help"></a>온라인 도움말에 대 한

온라인 도움말 때는 항상 Windows PowerShell의 필수적인 부분 였습니다. 하지만 `Get-Help` cmdlet은 명령 프롬프트에서 도움말 항목을 표시, 많은 사용자가 색, 하이퍼링크 및 커뮤니티 콘텐츠 및 wiki 기반 문서 공유 아이디어 등의 온라인 읽기 환경을 선호 합니다. 가장 중요 한 점은 도입 되기 전에 업데이트할 수 있는 도움말, 온라인 도움말 도움말 파일의 최신 버전을 제공합니다.

도입 되면서 Windows PowerShell 3.0에서 업데이트 가능한 도움말, 온라인 도움말 여전히 중요 한 역할을 수행 합니다. 유연한 사용자 환경 외에도 온라인 도움말 설치 하지 않았거나 도움말 항목을 다운로드 하는 데 업데이트할 수 있는 도움말을 사용할 수 없습니다는 사용자에 게 도움말을 제공 합니다.

## <a name="how-get-help--online-works"></a>어떻게 Get-help-Online 작동

명령에 대 한 온라인 도움말 항목을 찾을 수 있도록는 `Get-Help` 명령에는 온라인 매개 변수를 명령에 대 한 도움말 항목의 온라인 버전을 사용자의 기본 인터넷 브라우저에서 엽니다.

예를 들어 다음 명령은 엽니다에 대 한 온라인 도움말 항목을 `Invoke-Command` cmdlet.

```powershell
Get-Help Invoke-Command -Online
```

구현 `Get-Help` -온라인으로 `Get-Help` cmdlet에 대 한는 리소스 URI (Uniform Identifier) 다음 위치에서 온라인 버전 도움말 항목을 찾습니다.

- 명령에 대 한 도움말 항목의 관련 링크 섹션에 첫 번째 링크입니다. 도움말 항목을 사용자의 컴퓨터에 설치 되어야 합니다. 이 기능은 Windows PowerShell 2.0에서 도입 되었습니다.

- 모든 명령의 HelpUri 속성입니다. HelpUri 속성은 명령에 대 한 도움말 항목을 사용자의 컴퓨터에 설치 되지 경우에 액세스할 수 있습니다. 이 기능은 Windows PowerShell 3.0에서 도입 되었습니다.

  `Get-Help` HelpUri 속성 값을 가져오기 전에 관련 링크 섹션에 첫 번째 항목의 URI를 찾습니다. 속성 값을 잘못 되었거나 변경 된, 경우에 첫 번째 관련 링크에 다른 값을 입력 하 여 재정의할 수 있습니다. 그러나 첫 번째 관련 링크를 사용자의 컴퓨터에 설치 된 도움말 항목을 제공 하는 경우에 작동 합니다.

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a>명령 도움말 항목의 첫 번째 관련된 링크 URI 추가

지원할 수 있습니다 `Get-Help` -유효한 URI를 명령에 대 한 XML 기반 도움말 항목의 관련 링크 섹션에 첫 번째 항목을 추가 하 여 모든 명령에 대 한 온라인입니다. 이 옵션은 XML 기반 도움말 항목에만 유효 및 도움말 항목을 사용자의 컴퓨터에 설치 된 경우에 작동 합니다. 도움말 항목을 설치 되어 있고 URI 채워져 하는 경우이 값 보다 우선 합니다 **HelpUri** 명령의 속성입니다. 명령에 대 한 XML 기반 도움말 항목에 대 한 정보를 참조 하세요 [명령에 대 한 도움말 항목 Writing XML-Based](../help/writing-xml-based-help-topics-for-commands.md)합니다.

이 기능을 지원 하려면 URI에 표시 되어야 합니다는 `maml:uri` 요소 아래에 있는 첫 번째 `maml:relatedLinks/maml:navigationLink` 요소에는 `maml:relatedLinks` 요소입니다.

다음 XML에서는 URI의 정확한 위치를 보여 줍니다. "온라인 버전:" 텍스트에는 `maml:linkText` 요소 가장 좋은 방법은 되지만 필수 사항은 아닙니다.

```xml

<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>http://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a>명령에 HelpUri 속성 추가

이 섹션에서는 다양 한 종류의 명령에 HelpUri 속성을 추가 하는 방법을 보여 줍니다.

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a>Cmdlet에 HelpUri 속성 추가

작성 된 cmdlet에 대 한 C#, 추가 **HelpUri** 특성을 Cmdlet 클래스입니다. 특성의 값에는 "http" 또는 "https"로 시작 하는 URI 여야 합니다.

다음 코드에서는 HelpUri 특성을 `Get-History` cmdlet 클래스입니다.

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "http://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a>고급 기능에 HelpUri 속성 추가

고급 함수에 대 한 추가 **HelpUri** 속성을 합니다 **CmdletBinding** 특성입니다. 속성의 값에는 "http" 또는 "https"로 시작 하는 URI 여야 합니다.

다음 코드는 새로 만들기-일정 함수의 HelpUri 특성을 보여 줍니다.

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="http://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a>CIM 명령에 HelpUri 특성 추가

CIM 명령에 대 한 추가 **HelpUri** 특성을 합니다 **CmdletMetadata** CDXML 파일의 요소입니다. 특성의 값에는 "http" 또는 "https"로 시작 하는 URI 여야 합니다.

다음 코드를 디버그 시작 CIM 명령의 HelpUri 특성을 보여 줍니다.

```
<CmdletMetadata Verb="Debug" HelpUri="http://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a>HelpUri 특성을 워크플로에 추가

추가 Windows PowerShell 언어로 작성 된 워크플로 **합니다. ExternalHelp** 를 워크플로 코드 comment 지시문입니다. 지시문의 값에는 "http" 또는 "https"로 시작 하는 URI 여야 합니다.

> [!NOTE]
> HelpUri 속성 XAML 기반 Windows PowerShell 워크플로에 대 한 지원 되지 않습니다.

다음 코드에서는 합니다. 워크플로 파일 ExternalHelp 지시문입니다.

```powershell
# .ExternalHelp "http://go.microsoft.com/fwlink/?LinkID=138338"
```