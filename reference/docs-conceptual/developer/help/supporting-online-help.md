---
ms.date: 09/13/2016
ms.topic: reference
title: 온라인 도움말 지원
description: 온라인 도움말 지원
ms.openlocfilehash: 0164b5e6c6c8d66a6ab2467a8adfb7efffe0fe17
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645426"
---
# <a name="supporting-online-help"></a>온라인 도움말 지원

PowerShell 3.0부터 `Get-Help` powershell 명령에 대 한 온라인 기능을 지 원하는 두 가지 방법이 있습니다. 이 항목에서는 다양 한 명령 유형에 대해이 기능을 구현 하는 방법을 설명 합니다.

## <a name="about-online-help"></a>온라인 도움말 정보

온라인 도움말은 항상 PowerShell의 중요 한 부분입니다. Cmdlet은 `Get-Help` 명령 프롬프트에서 도움말 항목을 표시 하지만 많은 사용자가 커뮤니티 콘텐츠 및 wiki 기반 문서에서 색 구분, 하이퍼링크 및 아이디어 공유를 포함 하 여 온라인 읽기 환경을 선호 합니다. 가장 중요 한 점은 업데이트할 수 있는 도움말을 제공 하기 전에 온라인 도움말에서 최신 버전의 도움말 파일을 제공 하는 것입니다.

PowerShell 3.0에서 업데이트할 수 있는 도움말을 사용 하 여 온라인 도움말에서 여전히 중요 한 역할을 합니다. 유연한 사용자 환경 외에도 온라인 도움말은 업데이트할 수 있는 도움말 항목을 다운로드 하는 데 사용할 수 없는 사용자를 위한 도움말을 제공 합니다.

## <a name="how-get-help--online-works"></a>Get-Help-온라인 작동 방법

사용자가 명령에 대 한 온라인 도움말 항목을 찾을 수 있도록 명령에는 `Get-Help` 사용자의 기본 인터넷 브라우저에서 명령에 대 한 온라인 버전의 도움말 항목을 여는 온라인 매개 변수가 있습니다.

예를 들어 다음 명령은 cmdlet에 대 한 온라인 도움말 항목을 엽니다 `Invoke-Command` .

```powershell
Get-Help Invoke-Command -Online
```

을 구현 하기 위해 `Get-Help -Online` 이 `Get-Help` cmdlet은 다음 위치의 온라인 버전 도움말 항목에 대 한 URI (Uniform resource Identifier)를 찾습니다.

- 명령에 대 한 도움말 항목의 **관련 링크** 섹션에 있는 첫 번째 링크입니다. 사용자의 컴퓨터에 도움말 항목이 설치 되어 있어야 합니다. 이 기능은 PowerShell 2.0에서 도입 되었습니다.

- 모든 명령의 **HelpUri** 속성입니다. **HelpUri** 속성은 사용자의 컴퓨터에 명령에 대 한 도움말 항목이 설치 되어 있지 않은 경우에도 액세스할 수 있습니다. 이 기능은 PowerShell 3.0에서 도입 되었습니다.

  `Get-Help`**HelpUri** 속성 값을 가져오기 전에 **관련 링크** 섹션의 첫 번째 항목에서 URI를 찾습니다. 속성 값이 잘못 되었거나 변경 된 경우 첫 번째 관련 링크에 다른 값을 입력 하 여 재정의할 수 있습니다. 그러나 첫 번째 관련 링크는 도움말 항목이 사용자의 컴퓨터에 설치 된 경우에만 작동 합니다.

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a>명령 도움말 항목의 첫 번째 관련 링크에 URI 추가

`Get-Help -Online`명령에 대 한 XML 기반 도움말 항목의 **관련 링크** 섹션에 있는 첫 번째 항목에 유효한 URI를 추가 하 여 명령을 지원할 수 있습니다. 이 옵션은 XML 기반 도움말 항목에만 사용할 수 있으며 도움말 항목이 사용자의 컴퓨터에 설치 된 경우에만 사용할 수 있습니다. 도움말 항목을 설치 하 고 URI를 채우면이 값이 명령의 **HelpUri** 속성 보다 우선적으로 적용 됩니다.

이 기능을 지원 하려면 URI가 `maml:uri` 요소의 첫 번째 요소 아래에 있는 요소에 표시 되어야 합니다 `maml:relatedLinks/maml:navigationLink` `maml:relatedLinks` .

다음 XML은 URI의 올바른 배치를 보여 줍니다. `Online version:` `maml:linkText` 요소의 텍스트가 가장 좋은 방법 이지만 반드시 필요한 것은 아닙니다.

```xml
<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>https://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a>명령에 HelpUri 속성 추가

이 섹션에서는 HelpUri 속성을 다른 형식의 명령에 추가 하는 방법을 보여 줍니다.

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a>Cmdlet에 HelpUri 속성 추가

C #으로 작성 된 cmdlet의 경우 **cmdlet** 클래스에 **HelpUri** 특성을 추가 합니다. 특성의 값은 또는로 시작 하는 URI 여야 합니다 `http` `https` .

다음 코드에서는 cmdlet 클래스의 **HelpUri** 특성을 보여 줍니다 `Get-History` .

```csharp
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "https://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a>고급 함수에 HelpUri 속성 추가

고급 함수의 경우 **Cmdletbinding** 특성에 **HelpUri** 속성을 추가 합니다. 속성의 값은 "http" 또는 "https"로 시작 하는 URI 여야 합니다.

다음 코드에서는 함수의 **HelpUri** 특성을 보여 줍니다. `New-Calendar`

```powershell
function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="https://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a>CIM 명령에 HelpUri 특성 추가

CIM 명령의 경우 CDXML 파일의 **Cmdletmetadata** 요소에 **HelpUri** 특성을 추가 합니다.
특성의 값은 또는로 시작 하는 URI 여야 합니다 `http` `https` .

다음 코드는 CIM 명령의 HelpUri 특성을 보여 줍니다. `Start-Debug`

```xml
<CmdletMetadata Verb="Debug" HelpUri="https://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a>워크플로에 HelpUri 특성 추가

PowerShell 언어로 작성 된 워크플로의 경우를 추가 **합니다.** 워크플로 코드에 대 한 ExternalHelp 주석 지시문입니다. 지시문의 값은 또는로 시작 하는 URI 여야 합니다 `http` `https` .

> [!NOTE]
> HelpUri 속성은 PowerShell의 XAML 기반 워크플로에 대해 지원 되지 않습니다.

다음 코드에서는을 보여 줍니다. 워크플로 파일의 ExternalHelp 지시문입니다.

```powershell
# .ExternalHelp "https://go.microsoft.com/fwlink/?LinkID=138338"
```
