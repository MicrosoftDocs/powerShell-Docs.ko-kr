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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082183"
---
# <a name="naming-help-files"></a>도움말 파일 이름 지정

이 항목에서는 XML 기반 도움말 파일을 이름을 지정 하는 방법에 설명 하는 [Get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet에서 찾을 수 있습니다. 이름 요구 사항 명령 유형 마다 다릅니다.

## <a name="cmdlet-help-files"></a>Cmdlet 도움말 파일

에 대 한 도움말 파일을 C# cmdlet은 cmdlet가 정의 된 어셈블리 이름을 지정 해야 합니다. 다음 파일 이름 형식을 사용 합니다.

```
<AssemblyName>.dll-help.xml
```

어셈블리 이름 형식은 중첩된 모듈 어셈블리가 있는 경우에 필요 합니다.

예를 들어를 [Get-winevent; PSITPro5_Diagnostic; ](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet Microsoft.PowerShell.Diagnostics.dll 어셈블리에 정의 됩니다. 합니다 `Get-Help` cmdlet에 대 한 도움말 항목을 찾습니다는 `Get-WinEvent` cmdlet 모듈 디렉터리에는 Microsoft.PowerShell.Diagnostics.dll help.xml 파일에만 합니다.

## <a name="provider-help-files"></a>공급자 도움말 파일

공급자가 정의 된 어셈블리에 대 한 Windows PowerShell 공급자에 대 한 도움말 파일을 지정 해야 합니다. 다음 파일 이름 형식을 사용 합니다.

```
<AssemblyName>.dll-help.xml
```

어셈블리 이름 형식은 중첩된 모듈 어셈블리가 있는 경우에 필요 합니다.

예를 들어 인증서 공급자는 Microsoft.PowerShell.Security.dll 어셈블리에 정의 됩니다. `Get-Help` 모듈 디렉터리에는 Microsoft.PowerShell.Security.dll help.xml 파일에만 인증서 공급자에 대 한 cmdlet 도움말 항목을 찾습니다.

## <a name="function-help-files"></a>함수 도움말 파일

함수를 사용 하 여 문서화할 수 [설명 기반 도움말](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) 또는 XML 도움말 파일에 설명 되어 있습니다. 함수는 XML 파일에 문서화 하는 경우 함수가 있어야는 `.ExternalHelp` 키워드 XML 파일을 사용 하 여 함수를 연결 하는 주석 처리 합니다. 그렇지 않은 경우는 `Get-Help` cmdlet 도움말 파일을 찾을 수 없습니다.

요구 사항은 없습니다 기술 이름에 대 한 도움말 파일을 함수입니다. 그러나 함수 정의 되는 스크립트 모듈에 대 한 도움말 파일 이름을 지정 하는 것이 좋습니다. 예를 들어, 다음 함수는 MyModule.psm1 파일에 정의 됩니다.

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a>CIM 명령 도움말 파일

CIM 명령 정의 되어 있는 CDXML 파일에 대 한 CIM 명령에 대 한 도움말 파일을 지정 해야 합니다. 다음 파일 이름 형식을 사용 합니다.

```
<FileName>.cdxml-help.xml
```

CIM 명령은 중첩된 모듈을 모듈에 포함 될 수 있는 CDXML 파일에서 정의 됩니다. CIM 명령의 함수로 세션으로 가져오면 Windows PowerShell 추가 `.ExternalHelp` 키워드를 XML 도움말을 사용 하 여 함수를 연결 하는 함수 정의를 파일 주석 CIM 명령 정의 되어 있는 CDXML 파일 이름으로 지정 합니다.

## <a name="script-workflow-help-files"></a>스크립트 워크플로에 도움말 파일

스크립트 워크플로 모듈에 포함 된 XML 기반 도움말 파일에 문서화할 수 있습니다. 요구 사항은 없습니다 기술 이름에 대 한 도움말 파일입니다. 그러나 스크립트 워크플로에 정의 되는 스크립트 모듈에 대 한 도움말 파일 이름을 지정 하는 것이 좋습니다. 예:

```
<ScriptModule>.psm1-help.xml
```

다른 스크립트 명령은 달리 스크립트 워크플로에 필요 하지 않습니다는 `.ExternalHelp` 도움말 파일에 연결할 키워드를 주석 처리 합니다. 대신 Windows PowerShell XML 기반 도움말 파일에 대 한 모듈 디렉터리의 UI Culture 별 하위 디렉터리를 검색 하 고 모든 파일의 스크립트 워크플로에 대 한 도움말을 찾습니다. `.ExternalHelp` 주석 키워드는 무시 됩니다.

때문에 합니다 `.ExternalHelp` 주석 키워드가 무시 되는 `Get-Help` cmdlet 도움말을 찾을 수 스크립트 워크플로에 대 한 모듈에 포함 된 경우에 합니다.