---
ms.date: 02/03/2020
ms.topic: reference
title: PowerShell 모듈 가져오기
description: PowerShell 모듈 가져오기
ms.openlocfilehash: 688509c0943a9a0289e75b80543f278e16cfedfe
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658785"
---
# <a name="importing-a-powershell-module"></a>PowerShell 모듈 가져오기

시스템에 모듈을 설치한 후에는 모듈을 가져올 수 있습니다. 가져오기는 사용자가 PowerShell 세션에서 해당 모듈에 액세스할 수 있도록 모듈을 활성 메모리에 로드 하는 프로세스입니다. PowerShell 2.0에서는 [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet에 대 한 호출을 사용 하 여 새로 설치 된 PowerShell 모듈을 가져올 수 있습니다. PowerShell 3.0에서 PowerShell은 모듈의 함수 또는 cmdlet 중 하나를 사용자가 호출 하는 경우 모듈을 암시적으로 가져올 수 있습니다. 두 버전 모두 PowerShell에서 찾을 수 있는 위치에 모듈을 설치 한다고 가정 합니다. 자세한 내용은 [PowerShell 모듈 설치](./installing-a-powershell-module.md)를 참조 하세요.
모듈 매니페스트를 사용 하 여 내보낼 모듈 부분을 제한할 수 있으며 호출 매개 변수를 사용 하 여 `Import-Module` 가져올 파트를 제한할 수 있습니다.

## <a name="importing-a-snap-in-powershell-10"></a>Snap-In 가져오기 (PowerShell 1.0)

PowerShell 1.0에 모듈이 없습니다. 대신 스냅인을 등록 하 고 사용 해야 합니다. 그러나이 시점에서 모듈을 설치 하 고 가져오는 것이 일반적 이므로이 기술은 사용 하지 않는 것이 좋습니다. 자세한 내용은 [Windows PowerShell 스냅인을 만드는 방법](../cmdlet/how-to-create-a-windows-powershell-snap-in.md)을 참조 하십시오.

## <a name="importing-a-module-with-import-module-powershell-20"></a>Import-Module를 사용 하 여 모듈 가져오기 (PowerShell 2.0)

PowerShell 2.0은 적절 하 게 명명 된 [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet을 사용 하 여 모듈을 가져옵니다. 이 cmdlet을 실행 하면 Windows PowerShell은 변수에 지정 된 디렉터리에서 지정 된 모듈을 검색 합니다 `PSModulePath` . 지정 된 디렉터리가 있으면 Windows PowerShell은 모듈 매니페스트 파일 (. psd1), 스크립트 모듈 파일 (. .psm1), 이진 모듈 파일 (.dll) 순서로 파일을 검색 합니다. 검색에 디렉터리를 추가 하는 방법에 대 한 자세한 내용은 [PSModulePath 설치 경로 수정](./modifying-the-psmodulepath-installation-path.md)을 참조 하세요.
다음 코드에서는 모듈을 가져오는 방법을 설명 합니다.

```powershell
Import-Module myModule
```

MyModule이에 있는 것으로 가정 하면 `PSModulePath` PowerShell은 myModule를 활성 메모리에 로드 합니다. MyModule가 경로에 없는 경우 `PSModulePath` PowerShell에서 찾을 위치를 명시적으로 알 수 있습니다.

```powershell
Import-Module -Name C:\myRandomDirectory\myModule -Verbose
```

매개 변수를 사용 하 여 `-Verbose` 모듈에서 내보내지는 항목 및 활성 메모리로 가져오는 항목을 식별할 수도 있습니다. 내보내기와 가져오기는 모두 사용자에 게 노출 되는 항목을 제한 합니다. 차이점은 표시 여부를 제어 하는 사용자입니다. 기본적으로 내보내기는 모듈 내의 코드에 의해 제어 됩니다. 이와 대조적으로 가져오기는 호출에 의해 제어 됩니다 `Import-Module` . 자세한 내용은 아래의 **가져오는 구성원 제한** 을 참조 하세요.

## <a name="implicitly-importing-a-module-powershell-30"></a>암시적으로 모듈 가져오기 (PowerShell 3.0)

Windows PowerShell 3.0부터 모듈은 명령에서 cmdlet 또는 모듈의 함수를 사용할 경우 자동으로 가져옵니다. 이 기능은 **PSModulePath** 환경 변수의 값에 포함 된 디렉터리의 모든 모듈에서 작동 합니다. 그러나 모듈을 유효한 경로에 저장 하지 않는 경우에도 위에 설명 된 명시적 [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) 옵션을 사용 하 여 모듈을 로드할 수 있습니다.

다음 작업은 모듈의 자동 가져오기를 트리거하 며 "모듈 자동 로드" 라고도 합니다.

- 명령에서 cmdlet 사용 예를 들어를 입력 하면 `Get-ExecutionPolicy` cmdlet이 포함 된 Microsoft. PowerShell. Security 모듈이 가져오기 됩니다. `Get-ExecutionPolicy`

- 명령을 사용 하 [여 명령을 가져옵니다](/powershell/module/Microsoft.PowerShell.Core/Get-Command) . 예를 들어를 입력 하면 `Get-Command Get-JobTrigger` cmdlet이 포함 된 **PSScheduledJob** 모듈을 가져옵니다 `Get-JobTrigger` . `Get-Command`와일드 카드 문자를 포함 하는 명령은 검색으로 간주 되며 모듈 가져오기를 트리거하지 않습니다.

- [Get help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet을 사용 하 여 cmdlet에 대 한 도움말을 가져옵니다. 예를 들어를 입력 하면 `Get-Help Get-WinEvent` cmdlet이 포함 된 Microsoft. PowerShell 진단 모듈이 가져오기 됩니다. `Get-WinEvent`

모듈의 자동 가져오기를 지원 하기 위해 `Get-Command` cmdlet은 모듈을 세션으로 가져오지 않은 경우에도 모든 설치 된 모듈의 모든 cmdlet 및 함수를 가져옵니다. 자세한 내용은 [get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet에 대 한 도움말 항목을 참조 하세요.

## <a name="the-importing-process"></a>가져오기 프로세스

모듈을 가져올 때 모듈에 대해 새 세션 상태가 만들어지고, 메모리에는 [system.web](/dotnet/api/System.Management.Automation.PSModuleInfo) . p. a p. 가져오는 각 모듈에 대해 세션 상태가 생성 됩니다 (루트 모듈과 모든 중첩 된 모듈 포함). 중첩 된 모듈에서 루트 모듈로 내보낸 멤버를 포함 하 여 루트 모듈에서 내보낸 멤버를 호출자의 세션 상태로 가져옵니다.

모듈에서 내보낸 멤버의 메타 데이터에는 ModuleName 속성이 있습니다. 이 속성은 내보낸 모듈의 이름으로 채워집니다.

> [!WARNING]
> 내보낸 멤버의 이름이 승인 되지 않은 동사를 사용 하거나 멤버 이름에 제한 된 문자를 사용 하는 경우 [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet이 실행 될 때 경고가 표시 됩니다.

기본적으로 [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet은 파이프라인에 개체를 반환 하지 않습니다. 그러나이 cmdlet은 가져온 각 모듈에 대해 [system.object](/dotnet/api/System.Management.Automation.PSModuleInfo) 를 반환 하는 데 사용할 수 있는 **PassThru** 매개 변수를 지원 합니다. 호스트에 출력을 보내려면 사용자는 [쓰기 호스트](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet을 실행 해야 합니다.

## <a name="restricting--the-members-that-are-imported"></a>가져오는 구성원 제한

[Import-module cmdlet을](/powershell/module/Microsoft.PowerShell.Core/Import-Module) 사용 하 여 모듈을 가져올 때 기본적으로 내보낸 모든 모듈 멤버는 중첩 된 모듈에 의해 모듈로 내보낸 모든 명령을 포함 하 여 세션으로 가져옵니다. 기본적으로 변수 및 별칭은 내보내지지 않습니다. 내보내는 멤버를 제한 하려면 [모듈 매니페스트](./how-to-write-a-powershell-module-manifest.md)를 사용 합니다.
가져오는 멤버를 제한 하려면 cmdlet의 다음 매개 변수를 사용 합니다 `Import-Module` .

- **Function**:이 매개 변수는 내보내는 함수를 제한 합니다. 모듈 매니페스트를 사용 하는 경우 FunctionsToExport 키를 참조 하세요.

- `**Cmdlet**:이 매개 변수는 내보내는 cmdlet을 제한 합니다 (모듈 매니페스트를 사용 하는 경우 CmdletsToExport 키 참조).

- **Variable**:이 매개 변수는 내보내는 변수를 제한 합니다 (모듈 매니페스트를 사용 하는 경우 VariablesToExport 키 참조).

- **Alias**:이 매개 변수는 내보내는 별칭을 제한 합니다 (모듈 매니페스트를 사용 하는 경우 AliasesToExport 키 참조).

## <a name="see-also"></a>참고 항목

[Windows PowerShell 모듈 작성](./writing-a-windows-powershell-module.md)
