---
ms.date: 09/13/2016
ms.topic: reference
title: 업데이트할 수 있는 도움말 제작-단계별
description: 업데이트할 수 있는 도움말 제작-단계별
ms.openlocfilehash: c4aecdb801cac16c9cb07853317835fd87e6a0a8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658811"
---
# <a name="updatable-help-authoring-step-by-step"></a>업데이트 가능한 도움말 작성: 단계별

이 문서에는 업데이트할 수 있는 도움말을 작성 하는 과정의 단계가 나와 있습니다.

## <a name="authoring-updatable-help-step-by-step"></a>업데이트할 수 있는 도움말 작성: 단계별

업데이트할 수 있는 도움말은 최종 사용자를 위해 설계 되었지만, 모듈 작성자와 도움말 작성자에 게는 콘텐츠를 추가 하 고, 오류를 수정 하 고, 여러 UI 문화권을 제공 하 고, 모듈을 배송 한 후에도 사용자 주석과 요청에 응답 하는 기능을 포함 하 여 다양 한 이점을 제공 합니다. 이 [항목에서는 사용자가 update-help 및 get-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) [cmdlet을](/powershell/module/Microsoft.PowerShell.Core/Save-Help) 사용 하 여 도움말 파일을 다운로드 하 고 설치할 수 있도록 도움말 파일을 패키지 하 고 업로드 하는 방법에 대해 설명 합니다.

다음 단계는 업데이트할 수 있는 도움말을 지 원하는 프로세스에 대 한 개요를 제공 합니다.

### <a name="step-1-find-an-internet-site-for-your-help-files"></a>1 단계: 도움말 파일에 대 한 인터넷 사이트 찾기

업데이트할 수 있는 도움말을 만드는 첫 번째 단계는 모듈의 도움말 파일에 대 한 인터넷 위치를 찾는 것입니다. 실제로는 서로 다른 두 위치를 사용할 수 있습니다. 모듈의 도움말 정보 파일 (아래에 설명 되어 있음)을 한 인터넷 위치에 보관 하 고 다른 인터넷 위치에 도움말 콘텐츠 CAB 파일을 HelpInfo 수 있습니다. 모듈에 대 한 모든 도움말 콘텐츠 CAB 파일은 동일한 위치에 있어야 합니다. 서로 다른 모듈에 대 한 도움말 콘텐츠 CAB 파일을 동일한 위치에 둘 수 있습니다.

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a>2 단계: 모듈 매니페스트에 HelpInfoURI 키 추가

모듈 매니페스트에 **HelpInfoURI** 키를 추가 합니다. 키의 값은 모듈에 대 한 HelpInfo XML 정보 파일의 위치에 대 한 URI (Uniform Resource Identifier)입니다. 보안을 위해 주소는 "http" 또는 "https"로 시작 해야 합니다. URI는 인터넷 위치를 지정 해야 하지만 HelpInfo XML 파일 이름을 포함 하지 않아야 합니다.

예를 들어:

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'https://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a>3 단계: HelpInfo XML 파일 만들기

HelpInfo XML 정보 파일에는 도움말 파일의 인터넷 위치 URI와 지원 되는 각 UI 문화권의 모듈에 대 한 최신 도움말 파일의 버전 번호가 포함 되어 있습니다. 모든 Windows PowerShell 모듈에는 하나의 HelpInfo XML 파일이 있습니다. 도움말 파일을 업데이트할 때 HelpInfo XML 파일을 편집 하거나 바꿉니다. 다른 항목은 추가 하지 않습니다. 자세한 내용은 [How To Create a HELPINFO XML File](./how-to-create-a-helpinfo-xml-file.md)항목을 참조 하세요.

### <a name="step-4-create-cab-files"></a>4 단계: CAB 파일 만들기

와 같은 캐비닛 () 파일을 만드는 도구를 사용 `.cab` `MakeCab.exe` 하 여 모듈에 대 한 도움말 파일이 포함 된 CAB 파일을 만듭니다. 지원 되는 각 UI 문화권에서 도움말 파일에 대 한 별도의 CAB 파일을 만듭니다. 자세한 내용은 [업데이트할 수 있는 도움말 CAB 파일을 준비 하는 방법](./how-to-prepare-updatable-help-cab-files.md)을 참조 하세요.

### <a name="step-5-upload-your-files"></a>5 단계: 파일 업로드

새 도움말 파일이 나 업데이트 된 도움말 파일을 게시 하려면 HelpInfo XML 파일의 **Helpcontenturi** 요소로 지정 된 인터넷 위치에 CAB 파일을 업로드 합니다. 그런 다음 모듈 매니페스트의 **HelpInfoUri** 키 값으로 지정 된 인터넷 위치에 HelpInfo XML 파일을 업로드 합니다.
