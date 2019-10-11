---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: 빠른 시작 - DSC를 사용하여 웹 사이트 만들기
ms.openlocfilehash: d98607939ccd3cc5e660936d8c0a6d54fce7d65f
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71955070"
---
> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="quickstart---create-a-website-with-dsc"></a>빠른 시작 - DSC를 사용하여 웹 사이트 만들기

이 연습에서는 DSC(필요한 상태 구성) 구성을 만들고 적용하는 과정을 처음부터 끝까지 자세히 설명합니다.
여기에서 사용할 예제는 서버에 `Web-Server`(IIS) 기능을 사용하며 서버의 `inetpub\wwwroot` 디렉터리에 단순한 "Hello World" 웹 사이트 콘텐츠가 있는지 확인합니다.

DSC가 무엇이며 어떻게 작동하는지에 대한 개요는 [의사 결정자를 위한 필요한 상태 구성 개요](../overview/decisionMaker.md)를 참조하세요.

## <a name="requirements"></a>요구 사항

이 예제를 실행하려면 Windows Server 2012 이상과 PowerShell 4.0 이상을 실행하는 컴퓨터가 필요합니다.

## <a name="write-and-place-the-indexhtm-file"></a>index.htm 파일 작성 및 배치

먼저, 웹 사이트 콘텐츠로 사용할 HTML 파일을 만듭니다.

루트 폴더에 `test`라는 폴더를 만듭니다.

텍스트 편집기에서 다음 텍스트를 입력합니다.

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

만들어 둔 `test` 폴더에 `index.htm`으로 저장합니다.

## <a name="write-the-configuration"></a>구성 작성

[DSC 구성](../configurations/configurations.md)은 대상 컴퓨터(노트) 하나 이상의 구성 방법을 정의하는 특수한 PowerShell 기능입니다.

PowerShell ISE에서 다음을 입력합니다.

```powershell
Configuration WebsiteTest {

    # Import the module that contains the resources we're using.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets this configuration will be applied to.
    Node 'localhost' {

        # The first resource block ensures that the Web-Server (IIS) feature is enabled.
        WindowsFeature WebServer {
            Ensure = "Present"
            Name   = "Web-Server"
        }

        # The second resource block ensures that the website content copied to the website root folder.
        File WebsiteContent {
            Ensure = 'Present'
            SourcePath = 'c:\test\index.htm'
            DestinationPath = 'c:\inetpub\wwwroot'
        }
    }
}
```

파일을 `WebsiteTest.ps1`로 저장합니다.

함수 이름 앞에 **Configuration** 키워드를 추가한 PowerShell 함수처럼 보입니다.

**Node** 블록은 구성할 대상 노드를 지정하며, 이 경우는 `localhost`입니다.

구성에서는 **WindowsFeature** 및 **File**의 두 [리소스](../resources/resources.md)를 호출합니다.
리소스는 대상 노드가 구성에 정의된 상태에 있는지 확인합니다.

## <a name="compile-the-configuration"></a>구성 컴파일

노드에 DSC 구성을 적용하려면 먼저 MOF 파일로 컴파일해야 합니다.
그러려면 구성을 함수처럼 실행합니다.
PowerShell 콘솔에서 구성을 저장한 폴더로 이동한 후 다음 명령을 실행하여 구성을 MOF 파일로 컴파일합니다.

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

그러면 다음과 같은 출력이 생성됩니다.

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

첫 번째 줄은 콘솔에서 구성 함수를 사용할 수 있도록 합니다.
두 번째 줄은 구성을 실행합니다.
그 결과 `WebsiteTest`라는 이름의 새 폴더가 현재 폴더의 하위 폴더로 생성됩니다.
`WebsiteTest` 폴더에는 `localhost.mof`라는 이름의 파일이 들어 있습니다.
이 파일을 대상 노드에 적용할 수 있습니다.

## <a name="apply-the-configuration"></a>구성 적용

이제 MOF를 컴파일했으므로 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet을 호출하여 구성을 대상 노드(이 경우 로컬 컴퓨터)에 적용할 수 있습니다.

`Start-DscConfiguration` cmdlet은 DSC의 엔진인 [LCM(로컬 구성 관리자)](../managing-nodes/metaConfig.md)에 구성을 적용하라고 지시합니다.
LCM은 DSC 리소스를 호출하여 구성을 적용합니다.

PowerShell 콘솔에서 구성을 저장한 폴더로 이동한 후 다음 명령을 실행합니다.

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a>구성 테스트

[Get-DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) cmdlet을 호출하여 구성의 성공 여부를 확인할 수 있습니다.

결과를 직접 테스트할 수도 있습니다. 이 경우는 웹 브라우저에서 `http://localhost/`를 탐색하면 됩니다.
이 예제의 첫 단계에서 생성한 "Hello World" HTML 페이지가 보입니다.

## <a name="next-steps"></a>다음 단계

- DSC 구성에 대한 자세한 내용은 [DSC 구성](../configurations/configurations.md)을 참조하세요.
- [DSC 리소스](../resources/resources.md)에서는 어떤 DSC 리소스를 사용할 수 있으며 사용자 지정 DSC 리소스를 만드는 방법은 무엇인지 확인할 수 있습니다.
- [PowerShell 갤러리](https://www.powershellgallery.com/)에서는 DSC 구성 및 리소스를 찾을 수 있습니다.
