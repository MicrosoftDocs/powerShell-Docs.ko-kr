---
title: 도움말 파일 이름 지정 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf54eac7-88c6-4108-a5f6-2f0906d1662b
caps.latest.revision: 5
ms.openlocfilehash: f65a90023df88fceafae1d1875ddf46b9088e2b8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367012"
---
# <a name="naming-help-files"></a>도움말 파일 이름 지정

이 항목에서는 [get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet에서 찾을 수 있도록 XML 기반 도움말 파일의 이름을 지정할 수 있는 방법에 대해 설명 합니다. 이름 요구 사항은 각 명령 유형에 따라 달라 집니다.

## <a name="cmdlet-help-files"></a>Cmdlet 도움말 파일

Cmdlet에 대 한 C# 도움말 파일은 cmdlet이 정의 된 어셈블리의 이름을 지정 해야 합니다. 다음 파일 이름 형식을 사용 합니다.

```
<AssemblyName>.dll-help.xml
```

어셈블리가 중첩 모듈인 경우에도 어셈블리 이름 형식이 필요 합니다.

예를 들어, [Get WinEvent; PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet은 Microsoft. PowerShell .dll 어셈블리에 정의 되어 있습니다. `Get-Help` cmdlet은 모듈 디렉터리의 dll-help 파일 에서만 `Get-WinEvent` cmdlet에 대 한 도움말 항목을 찾습니다.

## <a name="provider-help-files"></a>공급자 도움말 파일

Windows PowerShell 공급자에 대 한 도움말 파일은 공급자가 정의 된 어셈블리의 이름을 지정 해야 합니다. 다음 파일 이름 형식을 사용 합니다.

```
<AssemblyName>.dll-help.xml
```

어셈블리가 중첩 모듈인 경우에도 어셈블리 이름 형식이 필요 합니다.

예를 들어 인증서 공급자는 Microsoft. PowerShell. .dll 어셈블리에 정의 되어 있습니다. `Get-Help` cmdlet은 모듈 디렉터리의 dll-help 파일 에서만 인증서 공급자에 대 한 도움말 항목을 찾습니다.

## <a name="function-help-files"></a>함수 도움말 파일

함수는 [주석 기반 도움말](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) 을 사용 하 여 문서화 하거나 XML 도움말 파일에 문서화할 수 있습니다. 함수가 XML 파일에 문서화 된 경우 함수는 함수를 XML 파일에 연결 하는 `.ExternalHelp` comment 키워드를 포함 해야 합니다. 그렇지 않으면 `Get-Help` cmdlet이 도움말 파일을 찾을 수 없습니다.

함수 도움말 파일의 이름에 대 한 기술 요구 사항은 없습니다. 그러나 함수가 정의 된 스크립트 모듈에 대 한 도움말 파일의 이름을 지정 하는 것이 가장 좋습니다. 예를 들어 다음 함수는 MyModule 파일에 정의 되어 있습니다.

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a>CIM 명령 도움말 파일

Cim 명령의 도움말 파일은 CIM 명령이 정의 된 CDXML 파일의 이름을 지정 해야 합니다. 다음 파일 이름 형식을 사용 합니다.

```
<FileName>.cdxml-help.xml
```

CIM 명령은 모듈에 중첩 모듈로 포함 될 수 있는 CDXML 파일에 정의 됩니다. CIM 명령을 세션으로 함수로 가져오는 경우 Windows PowerShell은 함수를 CIM 명령이 정의 된 CDXML 파일에 대해 이름이 지정 된 XML 도움말 파일에 연결 하는 함수 정의에 `.ExternalHelp` comment 키워드를 추가 합니다.

## <a name="script-workflow-help-files"></a>워크플로 도움말 파일 스크립팅

모듈에 포함 된 스크립트 워크플로는 XML 기반 도움말 파일로 문서화할 수 있습니다. 도움말 파일의 이름에 대 한 기술 요구 사항은 없습니다. 그러나 스크립트 워크플로가 정의 된 스크립트 모듈에 대 한 도움말 파일의 이름을 지정 하는 것이 가장 좋습니다. 예:

```
<ScriptModule>.psm1-help.xml
```

다른 스크립팅된 명령과 달리 스크립트 워크플로에는 `.ExternalHelp` comment 키워드를 사용 하 여 도움말 파일과 연결할 필요가 없습니다. 대신 Windows PowerShell은 모듈 디렉터리의 UI 문화권 관련 하위 디렉터리에서 XML 기반 도움말 파일을 검색 하 고 모든 파일의 스크립트 워크플로에 대 한 도움말을 찾습니다. `.ExternalHelp` comment 키워드는 무시 됩니다.

`.ExternalHelp` comment 키워드는 무시 되므로 `Get-Help` cmdlet은 모듈에 포함 된 경우에만 스크립트 워크플로에 대 한 도움말을 찾을 수 있습니다.