---
title: '업데이트 가능한 도움말 작성: 단계별 | Microsoft Docs'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: fbc77cc0fafce93d239da1c459d4b761b21ef3cb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860319"
---
# <a name="updatable-help-authoring-step-by-step"></a>업데이트 가능한 도움말 작성: 단계별

이 문서는 업데이트할 수 있는 도움말 작성 단계를 나열 합니다.

## <a name="authoring-updatable-help-step-by-step"></a>업데이트 가능한 도움말을 작성 합니다. 단계별

최종 사용자에 게 업데이트할 수 있는 도움말은 그러나 모듈 작성자가 한 많은 혜택을 제공 하 고 작성기 도움말 콘텐츠를 추가 하는 기능을 포함 하 여 오류를 수정, 여러 UI 문화권의 배달 시간 후 사용자 의견 및 요청에 응답할 합니다 모듈에 제공 됩니다. 이 항목에서는 패키지 하는 방법을 설명 하 고 사용자가 다운로드 하 고 사용 하 여 설치할 수 있도록 업로드 도움말 파일을 [Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) 하 고 [Save-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet.

다음 단계를 업데이트할 수 있는 도움말 지원 프로세스의 개요를 제공 합니다.

### <a name="step-1-find-an-internet-site-for-your-help-files"></a>1단계: 도움말 파일에 대해 인터넷 사이트 찾기

업데이트 가능한 도움말을 만드는 첫 번째 단계는 모듈의 도움말 파일에 대 한 인터넷 위치를 찾는 것입니다. 실제로 두 개의 서로 다른 위치를 사용할 수 있습니다. 하나의 인터넷 위치와 다른 인터넷 위치에서 도움말 콘텐츠 CAB 파일에서 모듈의 도움말 정보 파일 (HelpInfo XML-아래에서 설명)를 유지할 수 있습니다. 모든 도움말 콘텐츠 CAB 파일을 모듈에 대 한 동일한 위치에 있어야 합니다. 동일한 위치에서 다른 모듈에 대 한 도움말 콘텐츠 CAB 파일을 배치할 수 있습니다.

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a>2단계: 프로그램 모듈 매니페스트에 HelpInfoURI 키를 추가 합니다.

추가 된 **HelpInfoURI** 프로그램 모듈 매니페스트 키입니다. 키의 값이는 리소스 URI (Uniform Identifier) 모듈에 대 한 HelpInfo XML 정보 파일의 위치입니다. 보안에 대 한 주소는 "http" 또는 "https"로 시작 해야 합니다. URI는 인터넷 위치를 지정 해야 하지만 HelpInfo XML 파일 이름을 포함 하지 않아야 합니다.

예:

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'http://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a>3단계: HelpInfo XML 파일 만들기

HelpInfo XML 정보 파일을 도움말 파일 및 지원 되는 각 UI 문화권의 모듈에 대 한 최신 도움말 파일의 버전 번호는 인터넷 위치의 URI를 포함 합니다. 모든 Windows PowerShell 모듈에는 하나의 HelpInfo XML 파일을 있습니다. 편집 하거나 HelpInfo XML 파일을 대체 하 여 도움말 파일을 업데이트 하면 다른 추가 하지 마세요. 자세한 내용은 [HelpInfo XML 파일을 만드는 방법](./how-to-create-a-helpinfo-xml-file.md)합니다.

### <a name="step-4-sign-your-help-files"></a>4단계: 도움말 파일에 서명

디지털 서명 필요 없는 되지만 모범 사례 권장 사항을 파일을 공유 하는 때마다 있습니다.

### <a name="step-5-create-cab-files"></a>5단계: CAB 파일 만들기

만들려는 MakeCab.exe 같은 캐비닛 (.cab) 파일을 만드는 도구를 사용 하 여를 합니다. 모듈에 대 한 도움말 파일이 포함 된 CAB 파일입니다. 지원 되는 각 UI 문화권의 도움말 파일에 대 한 별도 CAB 파일을 만듭니다. 자세한 내용은 [업데이트할 수 있는 도움말 CAB 파일을 준비 하는 방법을](./how-to-prepare-updatable-help-cab-files.md)합니다.

### <a name="step-6-upload-your-files"></a>6단계: 파일 업로드

새롭거나 업데이트 된 도움말 파일을 게시 하려면 지정 된 인터넷 위치에 CAB 파일을 업로드 합니다 **HelpContentUri** HelpInfo XML 파일의 요소입니다. 그런 다음 값으로 지정 된 인터넷 위치로 HelpInfo XML 파일을 업로드 합니다 **HelpInfoUri** 모듈 매니페스트 키입니다.
