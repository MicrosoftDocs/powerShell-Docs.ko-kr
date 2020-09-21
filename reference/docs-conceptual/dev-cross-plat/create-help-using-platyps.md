---
title: PlatyPS를 사용하여 XML 기반 도움말 만들기
description: PlatyPS를 사용하면 XML 기반 도움말을 빠르고 효율적으로 만들 수 있습니다.
ms.date: 07/21/2020
ms.openlocfilehash: 79cf8c077a07bf1e7aa8ea1ea799be5f8d4af12c
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "86972583"
---
# <a name="create-xml-based-help-using-platyps"></a>PlatyPS를 사용하여 XML 기반 도움말 만들기

PowerShell 모듈을 만들 때 만드는 cmdlet에 관한 자세한 도움말을 포함하는 것이 좋습니다. 컴파일된 코드에서 cmdlet을 구현하는 경우에는 XML 기반 도움말을 사용해야 합니다. 해당 XML 형식을 MAML(Microsoft Assistance Markup Language)이라고 합니다.

레거시 PowerShell SDK 설명서에서는 모듈에 패키지된 PowerShell cmdlet에 관한 도움말을 만드는 방법을 자세히 설명합니다. 그러나 PowerShell은 XML 기반 도움말을 만들기 위한 도구를 제공하지 않습니다. SDK 설명서에서는 MAML 도움말의 구조를 설명하지만 복잡하고 깊게 중첩된 MAML 콘텐츠는 사용자가 만들어야 합니다.

해당 작업에는 [PlatyPS][] 모듈이 도움이 될 수 있습니다.

## <a name="what-is-platyps"></a>PlatyPS란?

PlatyPS는 MAML을 더 쉽게 만들고 유지 관리할 수 있도록 ‘해커톤’ 프로젝트로 시작한 [오픈 소스][platyps-repo] 도구입니다. PlatyPS는 모듈에서 각 cmdlet의 매개 변수 세트 및 개별 매개 변수에 관한 구문을 문서화합니다. PlatyPS는 구문 정보를 포함하는 구조화된 [Markdown][] 파일을 만듭니다. 설명을 만들거나 예제를 제공할 수 없습니다.

PlatyPS는 설명 및 예제를 입력할 자리 표시자를 만듭니다. 필요한 정보를 추가한 후 PlatyPS는 Markdown 파일을 MAML 파일로 컴파일합니다. PowerShell의 도움말 시스템에서는 일반 텍스트 개념 도움말 파일(정보 항목)도 사용할 수 있습니다. PlatyPS에는 새 ‘정보’ 파일의 구조화된 Markdown 템플릿을 만드는 cmdlet이 있지만, 해당 `about_*.help.txt` 파일은 수동으로 유지 관리해야 합니다.

모듈에 MAML 및 텍스트 도움말 파일을 포함할 수 있습니다. PlatyPS를 사용하여 도움말 파일을 업데이트 가능한 도움말용으로 호스트될 수 있는 CAB 패키지로 컴파일할 수도 있습니다.

## <a name="get-started-using-platyps"></a>PlatyPS를 사용하여 시작

먼저 PowerShell 갤러리에서 PlatyPS를 설치해야 합니다.

```powershell
Install-Module platyps -Force
Import-Module platyps
```

다음 순서도는 PowerShell 참조 콘텐츠를 만들거나 업데이트하는 프로세스를 간략하게 설명합니다.

:::image type="content" source="./media/create-help-using-platyps/cmdlet-ref-flow-v2.png" alt-text="PlatyPS를 사용하여 XML 기반 도움말을 만드는 워크플로":::

##  <a name="create-markdown-content-for-a-powershell-module"></a>PowerShell 모듈의 Markdown 콘텐츠 만들기

1. 새 모듈을 세션으로 가져옵니다. 문서화해야 하는 각 모듈에 대해 해당 단계를 반복합니다.

   다음 명령을 실행하여 모듈을 가져옵니다.

   ```powershell
   Import-Module <your module name>
   ```

1. PlatyPS를 사용하여 모듈 페이지 및 모듈 내에 있는 모든 관련 cmdlet의 의 Markdown 파일을 생성합니다. 문서화해야 하는 각 모듈에 대해 해당 단계를 반복합니다.

   ```powershell
   $OutputFolder = <output path>
   $parameters = @{
       Module = <ModuleName>
       OutputFolder = $OutputFolder
       AlphabeticParamsOrder = $true
       WithModulePage = $true
       ExcludeDontShow = $true
       Encoding = 'UTF8BOM'
   }
   New-MarkdownHelp @parameters

   New-MarkdownAboutHelp -OutputFolder $OutputFolder -AboutName "topic_name"
   ```

   출력 폴더가 없으면 `New-MarkdownHelp`가 해당 폴더를 만듭니다. 이 예제에서 `New-MarkdownHelp`는 모듈에 있는 각 cmdlet의 Markdown 파일을 만듭니다. 또한 `<ModuleName>.md`이라는 파일에 ‘모듈 페이지’를 만듭니다. 해당 모듈 페이지에는 모듈에 포함된 cmdlet 목록과 **개요** 설명의 자리 표시자가 포함됩니다. 모듈 페이지의 메타데이터는 모듈 매니페스트에서 가져오며 PlatyPS에서 HelpInfo XML 파일을 만드는 데 사용됩니다([아래](#creating-an-updateable-help-package) 설명된 대로).

   `New-MarkdownAboutHelp`는 `about_topic_name.md`라는 새 ‘정보’ 파일을 만듭니다.

   자세한 내용은 [New-MarkdownHelp][] 및 [New-MarkdownAboutHelp][]를 참조하세요.

### <a name="update-existing-markdown-content-when-the-module-changes"></a>모듈이 변경될 때 기존 Markdown 콘텐츠 업데이트

PlatyPS는 모듈의 기존 Markdown 파일도 업데이트할 수 있습니다. 해당 단계를 사용하여 새 cmdlet, 새 매개 변수 또는 변경된 매개 변수가 있는 기존 모듈을 업데이트할 수 있습니다.

1. 새 모듈을 세션으로 가져옵니다. 문서화해야 하는 각 모듈에 대해 해당 단계를 반복합니다.

   다음 명령을 실행하여 모듈을 가져옵니다.

   ```powershell
   Import-Module <your module name>
   ```

1. PlatyPS를 사용하여 모듈 방문 페이지 및 모듈 내 모든 관련 cmdlet의 Markdown 파일을 업데이트합니다. 문서화해야 하는 각 모듈에 대해 해당 단계를 반복합니다.

   ```powershell
   $parameters = @{
       Path = <folder with Markdown>
       RefreshModulePage = $true
       AlphabeticParamsOrder = $true
       UpdateInputOutput = $true
       ExcludeDontShow = $true
       LogPath = <path to store log file>
       Encoding = 'UTF8BOM'
   }
   Update-MarkdownHelpModule @parameters
   ```

   `Update-MarkdownHelpModule`은 지정된 폴더에서 cmdlet 및 모듈 Markdown 파일을 업데이트합니다.
   `about_*.md` 파일은 업데이트하지 않습니다. 모듈 파일(`ModuleName.md`)은 cmdlet 파일에 추가된 새 **개요** 텍스트를 수신합니다. cmdlet 파일의 업데이트에는 다음 변경 내용이 포함됩니다.

   - 새 매개 변수 세트
   - 새 매개 변수
   - 업데이트된 매개 변수 메타데이터
   - 업데이트된 입력 및 출력 형식 정보

   자세한 내용은 [Update-MarkdownHelpModule][]을 참조하세요.

## <a name="edit-the-new-or-updated-markdown-files"></a>새로운 또는 업데이트된 Markdown 파일 편집

PlatyPS는 매개 변수 세트 및 개별 매개 변수의 구문을 문서화합니다. 설명을 만들거나 예제를 제공할 수 없습니다. 콘텐츠가 필요한 특정 영역은 중괄호에 포함됩니다. `{{ Fill in the Description }}`

:::image type="content" source="./media/create-help-using-platyps/placeholders-example.png" alt-text="VS Code의 자리 표시자를 보여 주는 Markdown 템플릿":::

개요, cmdlet 설명, 각 매개 변수 설명 및 하나 이상의 예제를 추가해야 합니다.

PowerShell 콘텐츠를 작성하는 방법에 관한 자세한 내용은 다음 문서를 참조하세요.

- [PowerShell 스타일 가이드](/powershell/scripting/community/contributing/powershell-style-guide)
- [참조 문서 편집](/powershell/scripting/community/contributing/editing-cmdlet-ref)

> [!NOTE]
> PlatyPS에는 cmdlet 참조에 사용되는 특정 스키마가 있습니다. 해당 스키마는 문서의 특정 섹션에서 특정 Markdown 블록만 허용합니다. 콘텐츠를 잘못된 위치에 배치하면 PlatyPS 빌드 단계가 실패합니다. 자세한 내용은 PlatyPS 리포지토리에서 [스키마][] 설명서를 참조하세요. 잘 구성된(Well-Formed) cmdlet 참조의 전체 예제는 [Get-Item][]을 참조하세요.

각 cmdlet에 필요한 콘텐츠를 제공한 후에는 모듈 방문 페이지를 업데이트해야 합니다. `<module-name>.md` 파일의 YAML 메타데이터에서 모듈에 올바른 `Module Guid` 및 `Download Help Link` 값이 있는지 확인합니다. 누락된 메타데이터를 추가합니다.

또한 일부 cmdlet에는 **개요**(‘간단한 설명’)가 없을 수 있습니다. 다음 명령은 **개요** 설명 텍스트를 사용하여 모듈 방문 페이지를 업데이트합니다. 모듈 방문 페이지를 열어 설명을 확인합니다.

```powershell
Update-MarkdownHelpModule –Path <full path output folder> -RefreshModulePage
```

모든 콘텐츠를 입력했으므로 PowerShell 콘솔에서 `Get-Help`를 통해 표시되는 MAML 도움말 파일을 만들 수 있습니다.

## <a name="create-the-external-help-files"></a>외부 도움말 파일 만들기

해당 단계에서는 PowerShell 콘솔에서 `Get-Help`를 통해 표시되는 MAML 도움말 파일을 만듭니다.

MAML 파일을 빌드하려면 다음 명령을 실행합니다.

```powershell
New-ExternalHelp –Path <folder with MDs> -OutputPath <output help folder>
```

`New-ExternalHelp`는 모든 cmdlet Markdown 파일을 하나 이상의 MAML 파일로 변환합니다. 정보 파일은 `about_topic_name.help.txt` 이름 형식의 일반 텍스트 파일로 변환됩니다.
Markdown 콘텐츠는 PlatyPS 스키마의 요구 사항을 충족해야 합니다. 콘텐츠가 스키마를 따르지 않으면 `New-ExternalHelp`가 종료됩니다. 스키마 위반을 해결하려면 파일을 편집해야 합니다.

> [!CAUTION]
> PlatyPS는 `about_*.md` 파일을 일반 텍스트로 변환하는 작업을 제대로 수행하지 못합니다. 적합한 결과를 얻으려면 매우 간단한 Markdown을 사용해야 합니다. PlatyPS가 변환하도록 허용하지 않고 일반 텍스트 `about_topic_name.help.txt` 형식으로 파일을 유지 관리할 수 있습니다.

해당 단계가 완료되면 대상 출력 폴더에 `*-help.xml` 및 `about_*.help.txt` 파일이 표시됩니다.

자세한 내용은 [New-ExternalHelp][]를 참조하세요.

### <a name="test-the-compiled-help-files"></a>컴파일된 도움말 파일 테스트

[Get-HelpPreview][] cmdlet을 사용하여 콘텐츠를 확인할 수 있습니다.

```powershell
Get-HelpPreview -Path "<ModuleName>-Help.xml"
```

cmdlet은 컴파일된 MAML 파일을 읽고 `Get-Help`에서 받은 동일한 형식으로 콘텐츠를 출력합니다. 이렇게 하면 결과를 검사하여 Markdown 파일이 제대로 컴파일되었는지 확인하고 원하는 결과를 생성할 수 있습니다. 오류가 발견되면 Markdown 파일을 다시 컴파일하고 MAML를 다시 컴파일합니다.

이제 도움말 파일을 게시할 준비가 되었습니다.

## <a name="publishing-your-help"></a>도움말 게시

이제 Markdown 파일을 PowerShell 도움말 파일로 컴파일했으므로 사용자가 파일을 사용할 수 있도록 설정할 준비가 되었습니다. PowerShell 콘솔에서 도움말을 제공하는 두 가지 옵션이 있습니다.

- 모듈을 사용하여 도움말 파일 패키지
- `Update-Help` cmdlet을 사용하여 사용자가 설치하는 업데이트 가능한 도움말 패키지 만들기

### <a name="packaging-help-with-the-module"></a>모듈의 도움말 패키지

도움말 파일은 모듈과 함께 패키지할 수 있습니다. 폴더 구조에 관한 자세한 내용은 [모듈의 도움말 작성][]을 참조하세요. 모듈 매니페스트의 **FileList** 키 값에 도움말 파일 목록을 포함해야 합니다.

### <a name="creating-an-updateable-help-package"></a>업데이트 가능한 도움말 패키지 만들기

개략적으로 업데이트 가능한 도움말을 만드는 단계는 다음과 같습니다.

1. 도움말 파일을 호스트할 인터넷 사이트 찾기
1. 모듈 매니페스트에 **HelpInfoURI** 키 추가
1. HelpInfo XML 파일 만들기
1. CAB 파일 만들기
1. 파일 업로드

자세한 내용은 [업데이트 가능한 도움말 지원: 단계별][step-by-step]을 참조하세요.

PlatyPS는 해당 단계 중 일부를 지원합니다.

**HelpInfoURI**는 인터넷에서 도움말 파일이 호스트되는 위치를 가리키는 URL입니다. 해당 값은 모듈 매니페스트에서 구성됩니다. `Update-Help`는 모듈 매니페스트를 읽어서 해당 URL을 가져오고 업데이트 가능한 도움말 콘텐츠를 다운로드합니다. 해당 URL은 개별 파일이 아닌 폴더 위치만 가리켜야 합니다. `Update-Help`는 모듈 매니페스트 및 HelpInfo XML 파일의 기타 정보에 따라 다운로드할 파일 이름을 생성합니다.

> [!IMPORTANT]
> **HelpInfoURI**는 슬래시 문자(`/`)로 끝나야 합니다. 해당 문자가 없으면 `Update-Help`는 콘텐츠를 다운로드할 올바른 파일 경로를 생성할 수 없습니다. 또한 대부분의 HTTP 기반 파일 서비스는 대/소문자를 구분합니다. HelpInfo XML 파일의 모듈 메타데이터에는 적절한 대/소문자가 포함되어야 합니다.

`New-ExternalHelp` cmdlet은 출력 폴더에 HelpInfo XML 파일을 만듭니다. HelpInfo XML 파일은 모듈 Markdown 파일(`ModuleName.md`)에 포함된 YAML 메타데이터를 사용하여 빌드됩니다.

`New-ExternalHelpCab` cmdlet은 컴파일한 MAML 및 `about_*.help.txt` 파일을 포함하는 ZIP 및 CAB 파일을 만듭니다. CAB 파일은 모든 버전의 PowerShell과 호환됩니다.
PowerShell 6 이상은 ZIP 파일을 사용할 수 있습니다.

```powershell
$helpCabParameters = @{
    CabFilesFolder = $MamlOutputFolder
    LandingPagePath = $LandingPage
    OutputFolder = $CabOutputFolder
}
New-ExternalHelpCab @helpCabParameters
```

ZIP 및 CAB 파일을 만든 후 ZIP, CAB 및 HelpInfo XML 파일을 HTTP 파일 서버에 업로드합니다. **HelpInfoURI**에 지정된 위치에 파일을 넣습니다.

자세한 내용은 [New-ExternalHelpCab][]를 참조하세요.

### <a name="other-publishing-options"></a>기타 게시 옵션

Markdown은 게시를 위해 다른 형식으로 쉽게 변환할 수 있는 다양한 형식입니다. [Pandoc][] 같은 도구를 사용하여 Markdown 도움말 파일을 일반 텍스트, HTML, PDF 및 Office 문서 형식을 포함한 다양한 문서 형식으로 변환할 수 있습니다.

또한 PowerShell 6 이상에서 cmdlet [ConvertFrom-Markdown][] 및 [Show-Markdown][]을 사용하여 Markdown를 HTML로 변환하거나 PowerShell 콘솔에서 다채로운 표시를 만들 수 있습니다.

## <a name="known-issues"></a>알려진 문제

PlatyPS는 만들고 컴파일하는 Markdown 파일 구조의 [스키마][]에 매우 민감합니다. 해당 스키마를 위반하는 매우 쓰기 쉬운 유효한 Markdown입니다. 자세한 내용은 [PowerShell 스타일 가이드][] 및 [참조 문서 편집][]을 참조하세요.

<!-- link references -->
[platyps-repo]: https://github.com/PowerShell/platyps
[PlatyPS]: https://www.powershellgallery.com/packages/platyPS/
[Markdown]: https://commonmark.org
[markdig]: https://github.com/lunet-io/markdig
[schema]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[Get-Item]: https://github.com/MicrosoftDocs/PowerShell-Docs/blob/staging/reference/7.0/Microsoft.PowerShell.Management/Get-Item.md
[New-MarkdownHelp]: https://github.com/PowerShell/platyPS/blob/master/docs/New-MarkdownHelp.md
[Update-MarkdownHelpModule]: https://github.com/PowerShell/platyPS/blob/master/docs/Update-MarkdownHelpModule.md
[New-MarkdownAboutHelp]: https://github.com/PowerShell/platyPS/blob/master/docs/New-MarkdownAboutHelp.md
[New-ExternalHelp]: https://github.com/PowerShell/platyPS/blob/master/docs/New-ExternalHelp.md
[Get-HelpPreview]: https://github.com/PowerShell/platyPS/blob/master/docs/Get-HelpPreview.md
[New-ExternalHelpCab]: https://github.com/PowerShell/platyPS/blob/master/docs/New-ExternalHelpCab.md
[PowerShell 스타일 가이드]: /powershell/scripting/community/contributing/powershell-style-guide
[참조 문서 편집]: /powershell/scripting/community/contributing/editing-cmdlet-ref
[모듈에 관한 도움말 작성]: /powershell/scripting/developer/help/writing-help-for-windows-powershell-modules
[step-by-step]: /powershell/scripting/developer/help/updatable-help-authoring-step-by-step
[Pandoc]: https://pandoc.org
[ConvertFrom-Markdown]: /powershell/module/microsoft.powershell.utility/convertfrom-markdown
[Show-Markdown]: /powershell/module/microsoft.powershell.utility/show-markdown
