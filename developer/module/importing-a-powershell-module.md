---
title: PowerShell 모듈을 가져올 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 697791b3-2135-4a39-b9d7-8566ed67acf2
caps.latest.revision: 13
ms.openlocfilehash: bb5d036e5658c365a4fafa2cac05c0bba9f87019
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854059"
---
# <a name="importing-a-powershell-module"></a>PowerShell 모듈 가져오기

한 번에 모듈을 설치한 시스템에서 가능성이 하려는 모듈을 가져옵니다. 가져오기는 것은 사용자가 PowerShell 세션에서 해당 모듈에 액세스할 수 있는 활성 메모리에 모듈을 로드 하는 프로세스입니다. PowerShell 2.0에서에 대 한 호출을 사용 하 여 새로 설치 된 PowerShell 모듈을 가져올 수 있습니다 [Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet. PowerShell 3.0에서 PowerShell은 함수 또는 모듈의 cmdlet 중 하나는 사용자가 호출 될 때 암시적으로 모듈을 가져올 수 있습니다. 두 버전 모두 PowerShell은; 찾을 수 있는 위치에 모듈을 설치 하는 가정 하 고 자세한 내용은 [PowerShell 모듈 설치](./installing-a-powershell-module.md)합니다. 모듈 매니페스트를 사용 하 여 모듈의 어느 부분을 내보낸 제한 하 고 매개 변수를 사용할 수는 `Import-Module` 이식 될 부분을 제한 하는 호출 합니다.

## <a name="importing-a-snap-in-powershell-10"></a>스냅인 (PowerShell 1.0) 가져오기

모듈에에서 없습니다. PowerShell 1.0: 등록 하 고 스냅인을 사용 해야 대신 합니다. 그러나는 것이 시점에서이 기술을 사용 하는 모듈은 일반적으로 쉽게 설치 하 고 가져옵니다. 자세한 내용은 [Windows PowerShell 스냅인을 만드는 방법](../cmdlet/how-to-create-a-windows-powershell-snap-in.md)합니다.

## <a name="importing-a-module-with-import-module-powershell-20"></a>Import-module (PowerShell 2.0)를 사용 하 여 모듈 가져오기

PowerShell 2.0은 적절 하 게 라는 [Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet 모듈을 가져옵니다. 이 cmdlet을 실행 하는 경우 Windows PowerShell 검색에서 지정한 디렉터리 내에서 지정된 된 모듈의 `PSModulePath` 변수입니다. Windows PowerShell의 순서로 파일을 검색할 지정된 된 디렉터리를 찾으면: 모듈 매니페스트 파일 (. psd1), 스크립트 모듈 파일 (.psm1), 이진 모듈 파일 (.dll). 검색 디렉터리를 추가 하는 방법에 대 한 자세한 내용은 참조 하세요. [PSModulePath 설치 경로 수정](./modifying-the-psmodulepath-installation-path.md)합니다. 다음 코드 모듈을 가져오는 방법을 설명 합니다.

```powershell
Import-Module myModule
```

에 있는 myModule 가정는 `PSModulePath`, PowerShell myModule 활성 메모리에 로드 합니다. MyModule 되었습니다에 없는 경우는 `PSModulePath` 경로 확인할 수 있습니다 명시적으로 PowerShell 찾는 위치:

```powershell
Import-Module -Name C:\myRandomDirectory\myModule -Verbose
```

사용할 수도 있습니다-verbose 매개 변수에서 모듈을 내보내는 중입니다 및 활성 메모리로 가져오고 무엇을 식별 합니다. 내보내기 및 가져오기가 모두 사용자에 게 노출 된 것을 제한 합니다: 차이점은 표시 여부를 제어 하는 합니다. 기본적으로 내보내기는 모듈 내의 코드에 의해 제어 됩니다. Imports에 의해 제어 되는 반면,는 `Import-Module` 호출 합니다. 자세한 내용은 **제한 멤버를 가져왔는지**아래.

## <a name="implicitly-importing-a-module-powershell-30"></a>암시적으로 (PowerShell 3.0) 모듈을 가져오기

Windows PowerShell 3.0부터 모듈은 자동으로 가져옵니다 명령에서 cmdlet 또는 모듈의 함수를 사용할 경우. 이 기능은 모든 모듈의 값에 포함 된 디렉터리에 대해 작동 합니다 **PSModulePath** 환경 변수입니다. 하지만 저장 하지 않으면 모듈에서 올바른 경로, 경우 로드할 수 있습니다를 명시적으로 사용 하 여 [Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) 위에 설명 된 옵션입니다.

다음 작업을 라고도 "모듈 자동 로드 합니다." 모듈의 자동 가져오기를 트리거합니다.

- 명령에서 cmdlet을 사용합니다. 예를 들어 입력 `Get-ExecutionPolicy` 포함 하는 Microsoft.PowerShell.Security 모듈을 가져옵니다는 `Get-ExecutionPolicy` cmdlet.

- 사용 하는 [Get-command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) 명령을 가져오려는 cmdlet.  예를 들어 입력 `Get-Command Get-JobTrigger` 가져옵니다 합니다 **PSScheduledJob** 포함 된 모듈의 `Get-JobTrigger` cmdlet. `Get-Command` 와일드 카드 문자를 포함 하는 명령을 검색 것으로 간주 됩니다 및 모듈 가져오기를 트리거하지 않습니다.

- 사용 하는 [Get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet에 대 한 도움말을 보려면 cmdlet. 예를 들어 입력 `Get-Help Get-WinEvent` 포함 된 Microsoft.PowerShell.Diagnostics 모듈을 가져옵니다는 `Get-WinEvent` cmdlet.

모듈 자동 가져오기를 지원 하도록는 `Get-Command` 모듈을 세션으로 가져오지 않은 경우에 cmdlet은 모든 cmdlet 아 기능에서 설치 된 모든 모듈을 가져옵니다. 자세한 내용은 도움말 항목을 참조 합니다 [Get-command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet.

## <a name="the-importing-process"></a>가져오기 프로세스

새 세션 상태 모듈에 대해 만들어집니다 모듈을 가져올 때와 [System.Management.Automation.PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo) 개체가 메모리에 생성 됩니다. 세션 상태를 가져온 각 모듈에 대해 생성 됩니다 (루트 모듈 및 모든 중첩 된 모듈 포함). 그런 다음 모든 중첩된 모듈에 의해 루트 모듈에 내보낸 멤버를 포함 하 여 루트 모듈에서 내보낸 멤버 호출자의 세션 상태로 가져옵니다.

모듈에서 내보낸 멤버의 메타 데이터는 ModuleName 속성을 가집니다. 이 속성을 내보낸 된 모듈의 이름으로 채워집니다.

> [!WARNING]
> 내보낸된 멤버의 이름에 승인 되지 않은 동사를 사용 하 여 또는 멤버의 이름을 제한 문자를 사용 하는 경우 경고를 표시 하는 경우 때 합니다 [Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet을 실행 합니다.

기본적으로 [Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet은 파이프라인에 개체를 반환 하지 않습니다. 하지만 Cmdlet을 지원를 `PassThru` 반환할 수 있는 매개 변수를 [System.Management.Automation.PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo) 가져온 각 모듈에 대 한 개체입니다. 호스트에 출력을 보내도록 사용자 실행 해야 합니다 [Write-host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet.

## <a name="restricting--the-members-that-are-imported"></a>가져온 멤버를 제한 합니다.

사용 하 여 모듈을 가져오도록 하는 경우는 [Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet을 기본적으로 모든 내보낸된 모듈 멤버는 세션으로 가져온 모든 명령을 포함 하 여 내보낸 중첩된 모듈에서 모듈에 있습니다. 기본적으로 변수와 별칭 내보내지 않습니다. 내보낸 멤버를 제한 하려면 사용 된 [모듈 매니페스트](./how-to-write-a-powershell-module-manifest.md)합니다. 가져온 멤버를 제한 하려면 다음 매개 변수를 사용 하 여는 `Import-Module` cmdlet.

- `Function`: 이 매개 변수는 내보낸 함수를 제한 합니다. (모듈 매니페스트를 사용 하는 경우 참조 FunctionsToExport 키).

- `Cmdlet`: 이 매개 변수 제한 (사용 하는 모듈 매니페스트 참조 CmdletsToExport 키) 하는 경우 내보낸 cmdlet

- `Variable`: 이 매개 변수 (사용 하는 모듈 매니페스트 참조 VariablesToExport 키) 하는 경우 내보내는 변수를 제한 합니다.

- `Alias`: 이 매개 변수 제한 (사용 하는 모듈 매니페스트 참조 AliasesToExport 키) 하는 경우 내보낸 별칭

## <a name="see-also"></a>참고 항목

[Windows PowerShell 모듈 작성](./writing-a-windows-powershell-module.md)
