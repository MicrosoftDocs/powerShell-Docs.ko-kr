---
title: Windows PowerShell 모듈 이해 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4e38235-9987-4347-afd2-0f7d1dc8f64a
caps.latest.revision: 19
ms.openlocfilehash: 77d328bc1cb8cb42d5a10f107a149c05ab270ce3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082110"
---
# <a name="understanding-a-windows-powershell-module"></a>Windows PowerShell 모듈 이해

A *모듈* 집합이 관련된 Windows PowerShell 기능을 편리한 단위 (일반적으로 하나의 디렉터리에 저장 됨)으로 그룹화 합니다. 모듈로 관련된 스크립트 파일, 어셈블리 및 관련 된 리소스 집합을 정의 하 여 고 참조할 수 있습니다, 로드, 유지 하 고, 그렇지 않은 경우 보다 훨씬 더 쉽게 코드를 공유 합니다.

모듈의 주 목적은 Windows PowerShell 코드를 모듈화 (ie, 재사용 및 추상화) 수 있도록 합니다. 예를 들어, 모듈을 만드는 가장 기본적인 방법은 단순히 Windows PowerShell 스크립트를. psm1 파일을 저장 하려면 것입니다. 이렇게 하면 따라서 제어할 수 있습니다 (즉, 공개 또는 개인) 함수 및 스크립트에 포함 된 변수입니다. 또한. psm1 파일로 스크립트를 저장할 특정 변수의 범위를 제어할 수 있습니다. 마지막으로 사용할 수도 있습니다 cmdlet와 같은 [Install-module](/powershell/module/PowershellGet/Install-Module) 구성 하 고, 설치 및 구성 요소로 스크립트를 사용 하 여 더 큰 솔루션에 대 한 합니다.

## <a name="module-components-and-types"></a>모듈 구성 요소 및 형식

모듈은 네 가지 기본 구성 요소로 구성 됩니다.

1. 일부 정렬 PowerShell 스크립트 또는 관리 되는 cmdlet 어셈블리 코드 파일의-일반적으로 합니다.

2. 위 코드 파일의 수 있는 다른 모든 항목을 추가 어셈블리와 같은 도움 파일 또는 스크립트입니다.

3. 위의 파일에 설명 뿐만 아니라 작성자 및 버전 관리 정보 같은 메타 데이터를 저장 하는 매니페스트 파일...

4. 위의 내용을 모두 포함 하는 디렉터리는 PowerShell 합리적으로 찾을 수 있습니다.

   단독으로 이러한 구성 요소 모두가 실제로 필요한 참고 합니다. 예를 들어 모듈. psm1 파일에 저장 하는 스크립트만 기술적으로 수 있습니다. 모듈을 구성 목적에 주로 사용 되는 매니페스트 파일로 할 수도 있습니다. 또한 동적으로 모듈을 만들고 같이 실제로 필요가에서 모든 항목을 저장할 디렉터리를 하는 스크립트를 작성할 수 있습니다. 다음 섹션에서는 혼합 및 일치 하는 모듈의 다른 가능한 부분을 함께 얻을 수 있습니다 하는 모듈의 형식을 설명 합니다.

### <a name="script-modules"></a>스크립트 모듈

이름에서 알 수 있듯이 *스크립트 모듈* 은 모든 유효한 Windows PowerShell 코드를 포함 하는 파일 (.psm1)입니다. 스크립트 개발자와 관리자 함수, 변수 및 멤버를 포함 하는 모듈을 만들려면이 유형의 모듈을 사용할 수 있습니다. 핵심, 스크립트 모듈을 가져오기, 내보내기 및 관리 함수를 사용 하는 관리자 수 있는 다른 확장을 사용 하 여 Windows PowerShell 스크립트 단순히은.

또한 데이터 파일, 다른 종속 모듈 또는 런타임 스크립트와 같은 모듈에서 다른 리소스를 포함 하도록 매니페스트 파일을 사용할 수 있습니다. 매니페스트 파일 작성 및 버전 관리 정보 같은 메타 데이터를 추적에 유용 합니다.

마지막으로, 동적으로 생성 되지 않습니다는 다른 모듈 처럼 스크립트 모듈을 PowerShell 합리적으로 검색할 수 있는 폴더에 저장 해야 합니다. 일반적으로이 PowerShell 모듈 경로입니다. 하지만 필요한 경우 명시적으로 설명할 수 있습니다 모듈 설치 되어 있는 합니다. 자세한 내용은 [PowerShell 스크립트 모듈을 작성 하는 방법을](./how-to-write-a-powershell-script-module.md)합니다.

### <a name="binary-modules"></a>이진 모듈

A *이진 모듈* 와 같은 컴파일된 코드를 포함 하는.NET Framework 어셈블리 (.dll) C#합니다. Cmdlet 개발자는 cmdlet, 공급자 및 공유 하려면이 유형의 모듈을 사용할 수 있습니다. (기존 스냅인 데도 사용할 수 있습니다 이진 모듈로.) 스크립트 모듈에 비해, 이진 모듈에서는 빠릅니다 또는 기능을 사용 하는 cmdlet를 만들 수 있습니다 (같은 다중 스레딩)는 Windows PowerShell 스크립트에서 코드를 쉽게 합니다.

스크립트 모듈을 모듈에 사용 하는 추가 리소스를 설명 하 고 모듈에 대 한 메타 데이터를 추적 하려면 매니페스트 파일을 포함할 수 있습니다. 마찬가지로, 아마도 설치 해야 이진 모듈 PowerShell 모듈 경로 따라 어딘가에 폴더에 있습니다. 자세한 내용은 참조 하는 방법 [PowerShell 이진 모듈을 작성 하는 방법을](./how-to-write-a-powershell-binary-module.md)합니다.

### <a name="manifest-modules"></a>매니페스트 모듈

A *매니페스트 모듈* 은 모든 해당 구성 요소를 설명 하기 위해 매니페스트 파일을 사용 하지만 모든 종류의 핵심 어셈블리 또는 스크립트는 모듈입니다. (매니페스트 모듈을 유지 하는 공식적으로 항목의 `ModuleToProcess` 또는 `RootModule` 빈 매니페스트의 요소입니다.) 그러나 모듈의 경우 종속 어셈블리를 로드 하거나 자동으로 특정 전처리 스크립트를 실행 하는 기능 등의 다른 기능을 계속 사용할 수 있습니다. 또한 중첩된 모듈, 어셈블리, 형식 또는 형식 등 다른 모듈을 사용 하는 리소스를 패키지 하는 편리한 방법으로 매니페스트 모듈을 사용할 수 있습니다. 자세한 내용은 [PowerShell 모듈 매니페스트 작성 방법](./how-to-write-a-powershell-module-manifest.md)합니다.

### <a name="dynamic-modules"></a>동적 모듈

A *동적 모듈* 는 모듈에서 로드 되지 않았거나 파일에 저장 합니다. 스크립트를 통해 동적으로 생성 된 대신 사용 하는 [New-module](/powershell/module/Microsoft.PowerShell.Core/New-Module) cmdlet. 이 형식은 모듈의 스크립트를를 로드 하거나 영구 저장소에 저장할 필요가 없습니다 주문형 모듈을 만들 수 있습니다. 기본적으로 동적 모듈을 단기 실행 요구 사항과 위한 것 이며에서 액세스할 수 없습니다는 `Get-Module` cmdlet. 마찬가지로, 일반적으로 필요 하지 않은 모듈 매니페스트 그럴 필요도 가능성이 관련된 어셈블리를 저장할 영구 폴더입니다.

## <a name="module-manifests"></a>모듈 매니페스트

A *모듈 매니페스트* 해시 테이블을 포함 하는. psd1 파일입니다. 키 및 해시 테이블의 값에는 다음 작업을 수행 합니다.

- 내용 및 모듈의 특성에 설명 합니다.

- 필수 구성 요소를 정의 합니다.

- 구성 요소를 처리 하는 방법을 결정 합니다.

  매니페스트는 모듈에 필요하지 않습니다. 모듈 수 스크립트 파일 (.ps1) 참조, 스크립트 모듈 파일 (.psm1)에 매니페스트 파일 (. psd1), 서식 지정 및 파일 (.ps1xml), cmdlet 및 공급자 어셈블리 (.dll), 리소스 파일, 도움말 파일, 지역화 파일 또는 다른 유형의 파일 또는 리소스를 입력 하는 모듈의 일부로 제공 됩니다. 국제화 된 스크립트를 모듈 폴더도 메시지 카탈로그 파일 집합이 포함 됩니다. 모듈 폴더에 매니페스트 파일을 추가 하는 경우 매니페스트를 참조 하 여 단일 단위로 여러 파일을 참조할 수 있습니다.

  매니페스트 자체에서는 다음과 같은 범주의 정보를 설명합니다.

- 모듈 버전 번호, 작성자 및 설명 같은 모듈에 대 한 메타 데이터입니다.

- Windows PowerShell 버전, 공용 언어 런타임 (CLR) 버전에 필요한 모듈 등 모듈을 가져오는 데 필요한 필수 구성 요소입니다.

- 처리 지시문, 스크립트, 형식 및 형식 같은 처리 합니다.

- 에 대 한 제한 멤버를 내보내도록 모듈에, 별칭, 함수, 변수 및 내보내려면 cmdlet 등.

  자세한 내용은 [PowerShell 모듈 매니페스트 작성 방법](./how-to-write-a-powershell-module-manifest.md)합니다.

## <a name="storing-and-installing-a-module"></a>저장 및 모듈 설치

스크립트, 이진 또는 매니페스트 모듈을 만든 후 액세스할 수 있습니다 다른 회사 위치에 저장할 수 있습니다. 예를 들어, 모듈은 Windows PowerShell이 설치 하거나 사용자 폴더에 저장할 수 있는 시스템 폴더에 저장할 수 있습니다.

모듈에 저장 된 경로 중 하나를 사용 하 여 설치 위치를 확인할 수는 일반적으로 `$ENV:PSModulePath` 변수입니다. 이러한 경로 중 하나를 사용 하는 PowerShell 파일을 사용자가 해당 코드에서를 호출할 때 모듈을 로드를 의미 합니다. 명시적으로 호출할 때 매개 변수로 모듈의 위치에 전달 하 여 알고 있어야 하는 PowerShell 모듈 다른 곳에 저장 하면 수 `Install-Module`입니다.

그럼에도 불구 하 고 폴더의 경로 라고 합니다 *기본* (ModuleBase) 모듈 및 스크립트의 이름, 이진 또는 매니페스트 모듈 파일 동일 해야 다음 예외를 사용 하 여 모듈 폴더 이름으로:

- 만든 동적 모듈을 `New-Module` 를 사용 하 여 cmdlet를 명명할 수 있습니다는 `Name` cmdlet의 매개 변수입니다.

- 어셈블리 개체에서 가져온 모듈을  **`Import-Module` -어셈블리** 명령 구문을 따라 명명 되: `"dynamic_code_module_" + assembly.GetName()`합니다.

  자세한 내용은 [PowerShell 모듈 설치](./installing-a-powershell-module.md) 하 고 [PSModulePath 설치 경로 수정](./modifying-the-psmodulepath-installation-path.md)합니다.

## <a name="module-cmdlets-and-variables"></a>모듈 Cmdlet 및 변수

다음 cmdlet 및 변수를 생성 및 관리 모듈에 대 한 Windows PowerShell에서 제공 됩니다.

[새 모듈](/powershell/module/Microsoft.PowerShell.Core/New-Module) cmdlet이이 cmdlet는 메모리에만 존재 하는 새 동적 모듈을 만듭니다. 모듈 스크립트 블록에서 생성 되 고 해당 함수 및 변수 등 해당 내보낸된 멤버를 세션에서 즉시 사용할 수 있으며 세션을 닫을 때까지 계속 사용할 수 있습니다.

[새 ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet이 cmdlet이은 새 모듈 매니페스트 (.psd1) 파일을 만듭니다의 값을 채운 및 지정된 된 경로에 매니페스트 파일을 저장 합니다. 이 cmdlet는에서 수동으로 입력할 수 있는 모듈 매니페스트 템플릿을 만드는 데도 사용할 수 있습니다.

[Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet이 cmdlet이은 현재 세션에 하나 이상의 모듈을 추가 합니다.

[Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet이 cmdlet이은 된 또는 현재 세션으로 가져올 수 있는 모듈에 대 한 정보를 검색 합니다.

[Export-modulemember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) cmdlet이 cmdlet이은 모듈 멤버를 지정 합니다 (예: cmdlet, 함수, 변수 및 별칭)를 사용 하 여 만든 동적 모듈 또는 스크립트 모듈 (.psm1) 파일에서 내보낸 된 `New-Module` cmdlet.

[Remove-module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) cmdlet이 cmdlet이은 현재 세션에서 모듈을 제거 합니다.

[Test-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest) cmdlet이 cmdlet이은 모듈 매니페스트를 지정된 된 경로에서 모듈 매니페스트 파일 (.psd1)에에서 나열 된 파일이 실제로 있는지 확인 하 여 모듈의 구성 요소를 정확 하 게 설명 하는지 확인 합니다.

$PSScriptRoot이이 변수는 스크립트 모듈을 실행 중인 디렉터리를 포함 합니다. 모듈 경로 사용 하 여 다른 리소스에 액세스 하는 스크립트를 사용 합니다.

$env: PSModulePath 환경 변수에이 저장 되는 Windows PowerShell 모듈 디렉터리의 목록을 포함 합니다. Windows PowerShell 모듈을 자동으로 가져오기 및 모듈에 대 한 도움말 항목을 업데이트 하는 경우이 변수의 값을 사용 합니다.

## <a name="see-also"></a>참고 항목

[Windows PowerShell 모듈 작성](./writing-a-windows-powershell-module.md)
