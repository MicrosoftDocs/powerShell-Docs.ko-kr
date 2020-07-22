---
title: PowerShell 모듈에 대 한 도움말 작성
ms.date: 04/10/2020
ms.openlocfilehash: 115ea3f3c5941e74ed6ddbc8480d4a21576bc5c6
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893070"
---
# <a name="writing-help-for-powershell-modules"></a>PowerShell 모듈에 대 한 도움말 작성

PowerShell 모듈에는 모듈에 대 한 도움말 항목과 cmdlet, 공급자, 함수 및 스크립트와 같은 모듈 멤버가 포함 될 수 있습니다. `Get-Help`Cmdlet은 다른 PowerShell 항목에 대 한 도움말을 표시 하는 것과 같은 형식으로 모듈 도움말 항목을 표시 하 고, 사용자 `Get-Help` 는 표준 명령을 사용 하 여 도움말 항목을 가져옵니다.

이 문서에서는 모듈 도움말 항목의 형식 및 올바른 배치에 대해 설명 하 고 모듈 도움말 콘텐츠에 대 한 지침을 제안 합니다.

## <a name="types-of-module-help"></a>모듈 도움말 형식

모듈에는 다음과 같은 유형의 도움말이 포함 될 수 있습니다.

- **Cmdlet 도움말**. 모듈의 cmdlet에 대해 설명 하는 도움말 항목은 명령 도움말 스키마를 사용 하는 XML 파일입니다.

- **공급자 도움말**. 모듈의 공급자를 설명 하는 도움말 항목은 공급자 도움말 스키마를 사용 하는 XML 파일입니다.

- **함수 도움말**. 모듈의 함수를 설명 하는 도움말 항목은 명령 도움말 스키마를 사용 하는 XML 파일 이거나 함수 내의 주석 기반 도움말 항목 또는 스크립트 또는 스크립트 모듈 일 수 있습니다.

- **스크립트 도움말**. 모듈의 스크립트를 설명 하는 도움말 항목은 스크립트 또는 스크립트 모듈의 명령 도움말 스키마 또는 주석 기반 도움말 항목을 사용 하는 XML 파일 일 수 있습니다.

- **개념 ("About") 도움말을 참조**하십시오. 개념 ("about") 도움말 항목을 사용 하 여 모듈과 해당 멤버를 설명 하 고 멤버를 함께 사용 하 여 작업을 수행할 수 있는 방법을 설명할 수 있습니다.
  개념 도움말 항목은 유니코드 (UTF-8) 인코딩을 사용 하는 텍스트 파일입니다. 파일 이름에는 형식을 사용 해야 합니다 `about_<name>.help.txt` `about_MyModule.help.txt` . 기본적으로 PowerShell에는 이러한 개념 정보 도움말 항목의 100이 포함 되어 있으며 다음 예제와 같이 형식이 지정 됩니다.

  ```Output
  TOPIC
      about_<subject or module name>

  SHORT DESCRIPTION
      A short, one-line description of the topic contents.

  LONG DESCRIPTION
      A detailed, full description of the subject or purpose of the module.

  EXAMPLES
      Examples of how to use the module or how the subject feature works in practice.

  KEYWORDS
      Terms or titles on which you might expect your users to search for the information in this topic.

  SEE ALSO
      Text-only references for further reading. Hyperlinks cannot work in the PowerShell console.

  ```

모든 스키마 파일은 폴더에서 찾을 수 있습니다 `$PSHOME\Schemas\PSMaml` .

## <a name="placement-of-module-help"></a>모듈 도움말 배치

Cmdlet은 모듈 `Get-Help` 디렉터리의 언어별 하위 디렉터리에서 모듈 도움말 항목 파일을 찾습니다.

예를 들어 다음 디렉터리 구조 다이어그램은 SampleModule 모듈에 대 한 도움말 항목의 위치를 보여 줍니다.

```
<ModulePath>
         \SampleModule
               \<en-US>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml
               \<fr-FR>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml

```

> [!NOTE]
> 이 예에서 `<ModulePath>` 자리 표시자는 환경 변수의 경로 중 하나 (예 `PSModulePath` : `$HOME\Documents\Modules` , `$PSHOME\Modules` 또는 사용자가 지정 하는 사용자 지정 경로)를 나타냅니다.

## <a name="getting-module-help"></a>모듈 도움말 가져오기

사용자가 모듈을 세션으로 가져오면 해당 모듈에 대 한 도움말 항목을 모듈과 함께 세션으로 가져옵니다. 모듈 매니페스트의 FileList 키 값에 도움말 항목 파일을 나열할 수 있지만 도움말 항목은 cmdlet의 영향을 받지 않습니다 `Export-ModuleMember` .

다양 한 언어로 모듈 도움말 항목을 제공할 수 있습니다. 이 `Get-Help` cmdlet은 제어판의 국가 및 언어 옵션 항목에서 현재 사용자에 대해 지정 된 언어로 모듈 도움말 항목을 자동으로 표시 합니다. Windows Vista 이상 버전의에서는 `Get-Help` windows에 설정 된 언어 대체 표준에 따라 모듈 디렉터리의 언어별 하위 디렉터리에서 도움말 항목을 검색 합니다.

PowerShell 3.0부터 `Get-Help` cmdlet 또는 함수에 대해 명령을 실행 하면 모듈의 자동 가져오기가 트리거됩니다. `Get-Help`Cmdlet은 모듈에 있는 도움말 항목의 내용을 즉시 표시 합니다.

모듈에 도움말 항목이 포함 되어 있지 않고 사용자 컴퓨터에 있는 모듈의 명령에 대 한 도움말 항목이 없으면 `Get-Help` 자동 생성 된 도움말을 표시 합니다. 자동 생성 된 도움말에는 명령 구문, 매개 변수 및 입력 및 출력 형식이 포함 되어 있지만 설명이 포함 되어 있지 않습니다. 자동 생성 된 도움말에는 사용자가 cmdlet을 사용 하 여 `Update-Help` 인터넷 또는 파일 공유에서 명령에 대 한 도움말을 다운로드 하도록 지시 하는 텍스트가 포함 되어 있습니다. 또한 cmdlet의 **online** 매개 변수를 사용 하 여 `Get-Help` 온라인 버전의 도움말 항목을 가져오는 것이 좋습니다.

## <a name="supporting-updatable-help"></a>업데이트 가능한 도움말 지원

Powershell 3.0 이상 버전의 사용자는 인터넷 이나 로컬 파일 공유에서 모듈에 대해 업데이트 된 도움말 파일을 다운로드 하 여 설치할 수 있습니다. `Update-Help`및 `Save-Help` cmdlet은 사용자의 관리 세부 정보를 숨깁니다. 사용자가 cmdlet을 실행 한 `Update-Help` 다음 cmdlet을 사용 `Get-Help` 하 여 PowerShell 명령 프롬프트에서 모듈에 대 한 최신 도움말 파일을 읽습니다.
사용자는 Windows 또는 PowerShell을 다시 시작할 필요가 없습니다.

방화벽 뒤의 사용자와 인터넷에 액세스할 수 없는 사용자는 업데이트할 수 있는 도움말도 사용할 수 있습니다.
인터넷에 액세스 하는 관리자는 cmdlet을 사용 `Save-Help` 하 여 최신 도움말 파일을 다운로드 하 여 파일 공유에 설치 합니다. 그러면 사용자가 cmdlet의 **Path** 매개 변수를 사용 `Update-Help` 하 여 파일 공유에서 최신 도움말 파일을 가져옵니다.

모듈 작성자는 모듈에 도움말 파일을 포함 하 고 업데이트할 수 있는 도움말을 사용 하 여 도움말 파일을 업데이트 하거나 모듈에서 도움말 파일을 생략 하 고 업데이트할 수 있는 도움말을 사용 하 여 설치 하 고 업데이트할 수 있습니다.

업데이트할 수 있는 도움말에 대 한 자세한 내용은 업데이트할 수 있는 [도움말 지원](./supporting-updatable-help.md)을 참조 하세요.

## <a name="supporting-online-help"></a>온라인 도움말 지원

업데이트 된 도움말 파일을 컴퓨터에 설치 하거나 설치할 수 없는 사용자는 종종 모듈 도움말 항목의 온라인 버전을 사용 합니다. Cmdlet의 **online** 매개 변수는 `Get-Help` 기본 인터넷 브라우저에서 사용자에 대 한 온라인 버전의 cmdlet 또는 고급 함수 도움말 항목을 엽니다.

`Get-Help`Cmdlet은 cmdlet 또는 함수의 **HelpUri** 속성 값을 사용 하 여 도움말 항목의 온라인 버전을 찾습니다.

PowerShell 3.0부터 사용자는 cmdlet 클래스에서 HelpUri 특성을 정의 하거나 **Cmdletbinding** 특성의 **HelpUri** 속성을 정의 하 여 사용자가 cmdlet 및 함수 도움말 항목의 온라인 버전을 찾도록 도울 수 있습니다. 특성의 값은 cmdlet 또는 함수의 **HelpUri** 속성 값입니다.

자세한 내용은 [온라인 도움말 지원](./supporting-online-help.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[PowerShell 모듈 작성](../module/writing-a-windows-powershell-module.md)

[업데이트 가능한 도움말 지원](./supporting-updatable-help.md)

[온라인 도움말 지원](./supporting-online-help.md)
