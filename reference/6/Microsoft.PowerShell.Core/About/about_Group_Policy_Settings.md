---
description: PowerShell에 대 한 그룹 정책 설정을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/28/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_group_policy_settings?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Group_Policy_Settings
ms.openlocfilehash: 1533908be91703efd8509653b30d30de6b7c4a84
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221577"
---
# <a name="about-group-policy-settings"></a>그룹 정책 설정 정보

## <a name="short-description"></a>간단한 설명
PowerShell에 대 한 그룹 정책 설정을 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

PowerShell에는 엔터프라이즈 환경에서 Windows 컴퓨터에 대 한 일관 된 구성 값을 정의 하는 데 도움이 되는 그룹 정책 설정이 포함 되어 있습니다.

PowerShell 그룹 정책 설정의 그룹 정책 경로는 다음과 같습니다.

```
Computer Configuration\
  Administrative Templates\
    Windows Components\
      Windows PowerShell

User Configuration\
  Administrative Templates\
    Windows Components\
      Windows PowerShell
```

사용자 구성 경로의 그룹 정책 설정은 컴퓨터 구성 경로의 그룹 정책 설정 보다 우선적으로 적용 됩니다.

템플릿을 설치한 후 그룹 정책 편집기 ()에서 이러한 설정을 편집할 수 있습니다 `gpedit.msc` .

정책은 다음과 같습니다.

- 모듈 로깅 설정: 모듈의 **LogPipelineExecutionDetails** 속성을 설정 합니다.
- PowerShell 스크립트 블록 로깅 켜기: 모든 PowerShell 스크립트의 자세한 로깅을 사용합니다.
- 스크립트 실행 켜기: PowerShell 실행 정책을 설정합니다.
- PowerShell 기록 켜기: PowerShell 명령의 입력 및 출력을 텍스트 기반 기록으로 캡처하는 기능을 사용합니다.
- 의 기본 원본 경로 설정 `Update-Help` : 업데이트할 수 있는 도움말의 원본을 인터넷이 아닌 디렉터리로 설정 합니다.

다른 템플릿을 가져오고 그룹 정책을 구성 하는 방법에 대 한 자세한 내용은 [Windows에서 그룹 정책 관리 템플릿 용 중앙 저장소를 만들고 관리 하는 방법][gpstore]을 참조 하세요.

## <a name="turn-on-module-logging"></a>모듈 로깅 켜기

**모듈 로깅** 설정 정책 설정은 선택한 PowerShell 모듈에 대 한 로깅을 설정 합니다. 설정은 영향을 받는 모든 컴퓨터의 모든 세션에서 적용 됩니다.

이 정책 설정을 사용 하도록 설정 하 고 하나 이상의 모듈을 지정 하는 경우 지정 된 모듈에 대 한 파이프라인 실행 이벤트가 이벤트 뷰어의 Windows PowerShell 로그에 기록 됩니다.

이 정책 설정을 사용 하지 않도록 설정 하면 모든 PowerShell 모듈에 대해 실행 이벤트 로깅을 사용할 수 없습니다.

이 정책 설정이 구성 되지 않은 경우 각 모듈의 **LogPipelineExecutionDetails** 속성은 모듈의 실행 이벤트를 기록할지 여부를 결정 합니다. 기본적으로 모든 모듈의 **LogPipelineExecutionDetails** 속성은 False로 설정 됩니다.

모듈에 대 한 모듈 로깅을 설정 하려면 다음 명령 형식을 사용 합니다. 모듈을 세션으로 가져와야 합니다. 설정은 현재 세션 에서만 적용 됩니다.

```powershell
Import-Module <Module-Name>
(Get-Module <Module-Name>).LogPipelineExecutionDetails = $true
```

특정 컴퓨터의 모든 세션에 대 한 모듈 로깅을 설정 하려면 이전 명령을 ' 모든 사용자 ' PowerShell 프로필 ()에 추가 `$Profile.AllUsersAllHosts` 합니다.

모듈 로깅에 대 한 자세한 내용은 [about_Modules](about_Modules.md)를 참조 하세요.

## <a name="turn-on-powershell-script-block-logging"></a>PowerShell 스크립트 블록 로깅 켜기

**Powershell 스크립트 블록 로깅** 설정 정책 설정을 사용 하면 모든 powershell 스크립트 입력을 Microsoft-Windows-Powershell/운영 이벤트 로그에 기록할 수 있습니다. 이 정책 설정을 사용 하도록 설정 하는 경우 PowerShell Core는 대화형으로 호출 되었는지 아니면 자동화를 통해 명령, 스크립트 블록, 함수 및 스크립트의 처리를 기록 합니다.

이 정책 설정을 사용하지 않도록 설정하면 PowerShell 스크립트 입력 기록이 비활성화됩니다. 스크립트 블록 호출 로깅을 사용하도록 설정하면 명령, 스크립트 블록, 함수 또는 스크립트의 호출을 시작하거나 중지할 때 PowerShell에서는 이벤트를 기록합니다. 호출 로깅을 사용하도록 설정하면 많은 양의 이벤트 로그가 생성됩니다.

## <a name="turn-on-script-execution"></a>스크립트 실행 켜기

**스크립트 실행 설정** 정책 설정은 실행할 수 있는 스크립트를 결정 하는 컴퓨터 및 사용자에 대 한 실행 정책을 설정 합니다.

정책 설정을 사용 하도록 설정 하는 경우 다음 정책 설정 중에서 선택할 수 있습니다.

- **서명 된 스크립트만 허용** 을 사용 하면 신뢰할 수 있는 게시자가 서명한 스크립트만 실행할 수 있습니다. 이 정책 설정은 AllSigned 실행 정책과 동일 합니다.

- **로컬 스크립트 및 원격 서명 된 스크립트를 허용** 하면 모든 로컬 스크립트가 실행 될 수 있습니다. 인터넷에서 시작 되는 스크립트는 신뢰할 수 있는 게시자가 서명 해야 합니다. 이 정책 설정은 RemoteSigned 실행 정책과 동일 합니다.

- **모든 스크립트 허용** 을 사용 하면 모든 스크립트를 실행할 수 있습니다. 이 정책 설정은 무제한 실행 정책과 동일 합니다.

이 정책 설정을 사용 하지 않도록 설정 하면 스크립트를 실행할 수 없습니다. 이 정책 설정은 제한 된 실행 정책과 동일 합니다.

이 정책 설정을 사용 하지 않도록 설정 하거나 구성 하지 않으면 cmdlet에 의해 컴퓨터 또는 사용자에 대해 설정 된 실행 정책에서 `Set-ExecutionPolicy` 스크립트 실행이 허용 되는지 여부를 결정 합니다. 기본값은 제한 되어 있습니다.

자세한 내용은 [about_Execution_Policies](about_Execution_Policies.md)를 참조하세요.

## <a name="turn-on-powershell-transcription"></a>Powershell 기록을 켭니다.

**Powershell 기록 설정** 정책 설정을 사용 하 여 powershell 핵심 명령의 입력 및 출력을 텍스트 기반 성적 증명서로 캡처할 수 있습니다. 이 정책 설정을 사용 하도록 설정 하는 경우 powershell core는 powershell core 및 PowerShell Core 엔진을 활용 하는 다른 모든 응용 프로그램에 대 한 기록 로깅을 사용 하도록 설정 합니다. 기본적으로 PowerShell Core는 각 사용자의 내 문서 디렉터리에 ' PowerShell_transcript '을 포함 하는 파일 이름, 시작 된 컴퓨터 이름 및 시간을 포함 하는 기록 출력을 기록 합니다.
이 정책을 사용 하도록 설정 하는 것은 각 PowerShell Core 세션에서 Start-Transcript cmdlet을 호출 하는 것과 같습니다.

이 정책 설정을 사용 하지 않도록 설정 하는 경우 기록이 cmdlet을 Start-Transcript 통해를 사용할 수 있지만 PowerShell 기반 응용 프로그램의 기록 로깅은 기본적으로 사용 하지 않도록 설정 됩니다.

OutputDirectory 설정을 사용 하 여 공유 위치에 대 한 기록 로깅을 사용 하도록 설정 하는 경우 사용자가 다른 사용자 또는 컴퓨터의 성적 증명서를 보지 못하도록 해당 디렉터리에 대 한 액세스를 제한 해야 합니다.

## <a name="set-the-default-source-path-for-update-help"></a>Update-Help에 대 한 기본 원본 경로 설정

**Update-help에 대 한 기본 원본 경로 설정** 정책 설정은 Cmdlet의 **SourcePath** 매개 변수에 대 한 기본값을 설정 합니다 `Update-Help` .
이 설정은 사용자가 cmdlet을 사용 하 여 `Update-Help` 인터넷에서 도움말 파일을 다운로드 하지 못하도록 합니다.

> [!NOTE]
> 이 그룹 정책 설정은 **컴퓨터 구성** 및 **사용자 구성** 아래에 나타납니다. 그러나 **컴퓨터 구성** 에서 그룹 정책 설정만 적용 됩니다. **사용자 구성** 에서 그룹 정책 설정은 무시 됩니다.

`Update-Help`Cmdlet은 PowerShell 모듈에 대 한 최신 도움말 파일을 다운로드 하 여 설치 하 고 컴퓨터에 설치 합니다. 기본적으로에서는 `Update-Help` 모듈에 지정 된 인터넷 위치에서 새 도움말 파일을 다운로드 합니다.

그러나 cmdlet을 사용 하 여 `Save-Help` 네트워크 공유와 같은 파일 시스템 위치에 최신 도움말 파일을 다운로드 한 다음 cmdlet을 사용 `Update-Help` 하 여 파일 시스템 위치에서 도움말 파일을 가져오고 컴퓨터에 설치할 수 있습니다. Cmdlet의 **SourcePath** 매개 변수는 `Update-Help` 파일 시스템 위치를 지정 합니다.

**Sourcepath** 매개 변수에 기본값을 제공 하면이 그룹 정책 설정이 모든 명령에 **sourcepath** 매개 변수를 암시적으로 추가 합니다 `Update-Help` . 사용자는 다른 파일 시스템 위치를 입력 하 여 기본값으로 지정 된 특정 파일 시스템 위치를 재정의할 수 있습니다.
그러나 명령에서 **SourcePath** 매개 변수를 제거할 수는 없습니다 `Update-Help` .

이 정책 설정을 사용 하도록 설정 하는 경우 **SourcePath** 매개 변수의 기본값을 지정할 수 있습니다. 파일 시스템 위치를 입력 하십시오.

이 정책 설정을 사용 하지 않도록 설정 하거나 구성 하지 않으면 cmdlet의 **SourcePath** 매개 변수에 대 한 기본값이 없습니다 `Update-Help` . 사용자는 인터넷 이나 모든 파일 시스템 위치에서 도움말을 다운로드할 수 있습니다.

자세한 내용은 [about_Updatable_Help](about_Updatable_Help.md)를 참조하세요.

## <a name="keywords"></a>키워드

about_Group_Policies about_GroupPolicy

## <a name="see-also"></a>참고 항목

[about_Execution_Policies](about_Execution_Policies.md)

[about_Modules](about_Modules.md)

[about_Updatable_Help](about_Updatable_Help.md)

[Get-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[Get-Module](xref:Microsoft.PowerShell.Core.Get-Module)

[Update-Help](xref:Microsoft.PowerShell.Core.Update-Help)

[Save-Help](xref:Microsoft.PowerShell.Core.Save-Help)

<!-- link references -->
[gpstore]: https://support.microsoft.com/help/3087759
