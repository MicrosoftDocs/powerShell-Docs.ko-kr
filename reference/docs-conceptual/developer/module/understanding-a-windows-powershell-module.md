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
ms.openlocfilehash: b42ba6b2bf42a74213eb78f2db22e16de7e90583
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360642"
---
# <a name="understanding-a-windows-powershell-module"></a>Windows PowerShell 모듈 이해

*모듈* 은 편리한 단위 (일반적으로 단일 디렉터리에 저장 됨)로 함께 그룹화 된 관련 Windows PowerShell 기능의 집합입니다. 관련 스크립트 파일, 어셈블리 및 관련 리소스 집합을 모듈로 정의 하면 코드를 더 쉽게 참조, 로드, 유지 및 공유할 수 있습니다.

모듈의 주요 목적은 Windows PowerShell 코드의 모듈화 (ie, 재사용 및 추상화)를 허용 하는 것입니다. 예를 들어 모듈을 만드는 가장 기본적인 방법은 Windows PowerShell 스크립트를 .psm1 파일로 저장 하는 것입니다. 이렇게 하면 스크립트에 포함 된 함수 및 변수를 제어할 수 있습니다 (즉, 공용 또는 개인으로 설정). 스크립트를 .psm1 파일로 저장 하면 특정 변수의 범위를 제어할 수도 있습니다. 마지막으로, [모듈](/powershell/module/PowershellGet/Install-Module) 등의 cmdlet을 사용 하 여 스크립트를 구성 하 고, 설치 하 고, 더 큰 솔루션의 구성 요소로 사용할 수도 있습니다.

## <a name="module-components-and-types"></a>모듈 구성 요소 및 유형

모듈은 네 가지 기본 구성 요소로 구성 됩니다.

1. 일종의 코드 파일-일반적으로 PowerShell 스크립트나 관리 되는 cmdlet 어셈블리입니다.

2. 추가 어셈블리, 도움말 파일 또는 스크립트와 같이 위의 코드 파일에 필요할 수 있는 다른 모든 항목입니다.

3. 위의 파일을 설명 하는 매니페스트 파일 뿐만 아니라 작성자 및 버전 관리 정보와 같은 메타 데이터를 저장 합니다.

4. 위의 모든 콘텐츠를 포함 하는 디렉터리 이며 PowerShell에서 적절 하 게 찾을 수 있는 위치에 있습니다.

   이러한 구성 요소는 실제로 실제로 필요 하지 않습니다. 예를 들어 모듈은 기술적으로 .psm1 파일에 저장 된 스크립트만 될 수 있습니다. 구성 용도로 주로 사용 되는 매니페스트 파일은 아니지만 모듈을 포함할 수도 있습니다. 또한 모듈을 동적으로 만드는 스크립트를 작성할 수 있으며,이 경우에는 실제로 아무것도 저장할 디렉터리가 필요 하지 않습니다. 다음 섹션에서는 모듈의 가능한 여러 부분을 함께 결합 하 고 일치 시켜 가져올 수 있는 모듈의 유형에 대해 설명 합니다.

### <a name="script-modules"></a>스크립트 모듈

이름에서 알 수 있듯이 *스크립트 모듈* 은 유효한 Windows PowerShell 코드를 포함 하는 파일 (. .psm1)입니다. 스크립트 개발자와 관리자는이 유형의 모듈을 사용 하 여 해당 멤버에 함수, 변수 등이 포함 된 모듈을 만들 수 있습니다. 그와 동시에 스크립트 모듈은 관리자가 가져오기, 내보내기 및 관리 기능을 사용할 수 있도록 하는 확장명이 다른 Windows PowerShell 스크립트입니다.

또한 매니페스트 파일을 사용 하 여 데이터 파일, 기타 종속 모듈 또는 런타임 스크립트와 같은 다른 리소스를 모듈에 포함할 수 있습니다. 매니페스트 파일은 작성 및 버전 관리 정보와 같은 메타 데이터를 추적 하는 데에도 유용 합니다.

마지막으로, 동적으로 생성 되지 않은 다른 모듈과 마찬가지로 스크립트 모듈은 PowerShell에서 합리적으로 검색할 수 있는 폴더에 저장 해야 합니다. 일반적으로 PowerShell 모듈 경로에 있습니다. 그러나 필요한 경우 모듈이 설치 된 위치를 명시적으로 설명할 수 있습니다. 자세한 내용은 [PowerShell 스크립트 모듈을 작성 하는 방법](./how-to-write-a-powershell-script-module.md)을 참조 하세요.

### <a name="binary-modules"></a>이진 모듈

*이진 모듈* 은와 C#같은 컴파일된 코드를 포함 하는 .NET Framework 어셈블리 (.dll)입니다. Cmdlet 개발자는이 유형의 모듈을 사용 하 여 cmdlet, 공급자 등을 공유할 수 있습니다. (기존 스냅인을 이진 모듈로 사용할 수도 있습니다.) 스크립트 모듈과 비교할 때 이진 모듈을 사용 하면 Windows PowerShell 스크립트에서 코드를 사용 하는 것이 쉽지 않은 더 빠른 cmdlet (예: 다중 스레딩)을 만들 수 있습니다.

스크립트 모듈과 마찬가지로 매니페스트 파일을 포함 하 여 모듈에서 사용 하는 추가 리소스를 설명 하 고 모듈에 대 한 메타 데이터를 추적할 수 있습니다. 마찬가지로, PowerShell 모듈 경로를 따라 어딘가에 있는 폴더에 이진 모듈을 설치 해야 할 수도 있습니다. 자세한 내용은 [PowerShell 이진 모듈을 작성](./how-to-write-a-powershell-binary-module.md)하는 방법을 참조 하세요.

### <a name="manifest-modules"></a>매니페스트 모듈

*매니페스트 모듈* 은 매니페스트 파일을 사용 하 여 모든 구성 요소를 설명 하지만 어떠한 종류의 핵심 어셈블리나 스크립트도 포함 하지 않는 모듈입니다. (공식적으로 매니페스트 모듈은 매니페스트의 `ModuleToProcess` 또는 `RootModule` 요소를 비워 둡니다.) 그러나 종속 어셈블리를 로드 하거나 특정 전처리 스크립트를 자동으로 실행 하는 기능과 같은 모듈의 다른 기능을 계속 사용할 수 있습니다. 매니페스트 모듈을 사용 하 여 다른 모듈에서 사용할 리소스 (예: 중첩 모듈, 어셈블리, 형식 또는 형식)를 패키지할 수도 있습니다. 자세한 내용은 [PowerShell 모듈 매니페스트를 작성 하는 방법](./how-to-write-a-powershell-module-manifest.md)을 참조 하세요.

### <a name="dynamic-modules"></a>동적 모듈

*동적 모듈* 은 파일에서 로드 되거나 파일에 저장 되지 않은 모듈입니다. 대신, [새 모듈](/powershell/module/Microsoft.PowerShell.Core/New-Module) cmdlet을 사용 하 여 스크립트에 의해 동적으로 만들어집니다. 이 유형의 모듈을 사용 하면 스크립트를 사용 하 여 영구 저장소에 로드 하거나 저장할 필요가 없는 모듈을 주문형으로 만들 수 있습니다. 이러한 특성을 사용 하는 경우 동적 모듈은 수명이 짧아야 하므로 `Get-Module` cmdlet으로 액세스할 수 없습니다. 마찬가지로 일반적으로 모듈 매니페스트가 필요 하지 않으며 관련 어셈블리를 저장 하는 데 영구적인 폴더가 필요할 수 있습니다.

## <a name="module-manifests"></a>모듈 매니페스트

*모듈 매니페스트* 는 해시 테이블을 포함 하는 psd1 파일입니다. 해시 테이블의 키와 값은 다음 작업을 수행 합니다.

- 모듈의 내용 및 특성을 설명 합니다.

- 필수 구성 요소를 정의 합니다.

- 구성 요소를 처리 하는 방법을 결정 합니다.

  매니페스트는 모듈에 필요하지 않습니다. 모듈은 스크립트 파일 (ps1), 스크립트 모듈 파일 (. .psm1), 매니페스트 파일 (. psd1), 형식 지정 및 형식 파일 (. types.ps1xml), cmdlet 및 공급자 어셈블리 (.dll), 리소스 파일, 도움말 파일, 지역화 파일 또는 기타 형식의 파일 또는 리소스를 참조할 수 있습니다. 는 모듈의 일부로 번들로 제공 됩니다. 국제화 된 스크립트의 경우 module 폴더에도 메시지 카탈로그 파일 집합이 포함 되어 있습니다. 모듈 폴더에 매니페스트 파일을 추가 하는 경우 매니페스트를 참조 하 여 여러 파일을 단일 단위로 참조할 수 있습니다.

  매니페스트 자체는 다음과 같은 범주의 정보를 설명 합니다.

- 모듈 버전 번호, 저자 및 설명과 같은 모듈에 대 한 메타 데이터입니다.

- Windows PowerShell 버전, CLR (공용 언어 런타임) 버전 및 필수 모듈과 같은 모듈을 가져오는 데 필요한 필수 구성 요소입니다.

- 처리할 스크립트, 형식 및 형식과 같은 처리 지시문

- 내보낼 모듈의 멤버에 대 한 제한 (예: 내보낼 별칭, 함수, 변수 및 cmdlet).

  자세한 내용은 [PowerShell 모듈 매니페스트를 작성 하는 방법](./how-to-write-a-powershell-module-manifest.md)을 참조 하세요.

## <a name="storing-and-installing-a-module"></a>모듈 저장 및 설치

스크립트, 이진 또는 매니페스트 모듈을 만든 후에는 다른 사용자가 액세스할 수 있는 위치에 작업을 저장할 수 있습니다. 예를 들어 Windows PowerShell이 설치 된 시스템 폴더에 모듈을 저장 하거나 사용자 폴더에 저장할 수 있습니다.

일반적으로 `$ENV:PSModulePath` 변수에 저장 된 경로 중 하나를 사용 하 여 모듈을 설치 해야 하는 위치를 결정할 수 있습니다. 이러한 경로 중 하나를 사용 하면 사용자가 코드에서 모듈을 호출할 때 PowerShell에서 자동으로 모듈을 찾아 로드할 수 있습니다. 다른 위치에 모듈을 저장 하는 경우 `Install-Module`를 호출할 때 모듈의 위치를 매개 변수로 전달 하 여 PowerShell이 명시적으로 표시 되도록 할 수 있습니다.

폴더 경로는 모듈 (ModuleBase)의 *기반* 으로 참조 되며 스크립트, 이진 또는 매니페스트 모듈 파일의 이름은 모듈 폴더 이름과 동일 해야 합니다. 단, 다음과 같은 경우는 예외입니다.

- Cmdlet의 `Name` 매개 변수를 사용 하 여 `New-Module` cmdlet에서 만든 동적 모듈의 이름을 지정할 수 있습니다.

- 어셈블리 개체에서 가져온 모듈은 다음 구문에 따라 이름이 지정 됩니다. `"dynamic_code_module_" + assembly.GetName()` **`Import-Module`** .

  자세한 내용은 [PowerShell 모듈 설치](./installing-a-powershell-module.md) 및 [PSModulePath 설치 경로 수정](./modifying-the-psmodulepath-installation-path.md)을 참조 하세요.

## <a name="module-cmdlets-and-variables"></a>모듈 Cmdlet 및 변수

모듈을 만들고 관리 하기 위해 Windows PowerShell에서 제공 하는 cmdlet 및 변수는 다음과 같습니다.

[새 모듈](/powershell/module/Microsoft.PowerShell.Core/New-Module) cmdlet이 cmdlet은 메모리에만 있는 새 동적 모듈을 만듭니다. 모듈은 스크립트 블록에서 만들어지며, 해당 함수 및 변수와 같은 내보낸 멤버는 세션에서 즉시 사용할 수 있으며 세션이 닫힐 때까지 계속 사용할 수 있습니다.

[New-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet이 cmdlet은 새 모듈 매니페스트 (. psd1) 파일을 만들고 해당 값을 채운 다음 매니페스트 파일을 지정 된 경로에 저장 합니다. 이 cmdlet을 사용 하 여 수동으로 채울 수 있는 모듈 매니페스트 템플릿을 만들 수도 있습니다.

[Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet이 cmdlet은 하나 이상의 모듈을 현재 세션에 추가 합니다.

[Import-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet이 cmdlet은 현재 세션으로 가져올 수 있거나 현재 세션으로 가져올 수 있는 모듈에 대 한 정보를 검색 합니다.

[Export-modulemember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) cmdlet이 cmdlet은 스크립트 모듈 (.psm1) 파일 또는 `New-Module` cmdlet을 사용 하 여 만든 동적 모듈에서 내보낸 모듈 멤버 (예: cmdlet, 함수, 변수 및 별칭)를 지정 합니다.

이 cmdlet은 [모듈을 제거](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) 합니다 .이 cmdlet은 현재 세션에서 모듈을 제거 합니다.

[New-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest) cmdlet이 cmdlet은 모듈 매니페스트 파일 (. psd1)에 나열 된 파일이 지정 된 경로에 실제로 존재 하는지 확인 하 여 모듈 매니페스트가 모듈의 구성 요소를 정확 하 게 설명 하는지 확인 합니다.

이 변수에는 스크립트 모듈이 실행 되는 디렉터리가 포함 되어 $PSScriptRoot. 이를 통해 스크립트는 모듈 경로를 사용 하 여 다른 리소스에 액세스할 수 있습니다.

$env:P SModulePath이 환경 변수는 Windows PowerShell 모듈을 저장 하는 디렉터리 목록을 포함 합니다. Windows PowerShell은 모듈을 자동으로 가져올 때이 변수의 값을 사용 하 고 모듈에 대 한 도움말 항목을 업데이트 합니다.

## <a name="see-also"></a>참고 항목

[Windows PowerShell 모듈 작성](./writing-a-windows-powershell-module.md)
