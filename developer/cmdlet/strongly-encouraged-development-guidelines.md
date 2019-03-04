---
title: 좋습니다 개발 지침 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d68a8f3-fba0-44c5-97b9-9fc191d269a5
caps.latest.revision: 13
ms.openlocfilehash: 2bf2447eba07b74f8cc14c9820fc1c1774370b2f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854009"
---
# <a name="strongly-encouraged-development-guidelines"></a>적극 권장되는 개발 지침

이 섹션에서는 cmdlet을 작성 하는 경우 따라야 하는 지침을 설명 합니다. Cmdlet 및 cmdlet 코드 작성에 대 한 지침을 디자인 하기 위한 지침으로 구분 됩니다. 이러한 지침은 모든 시나리오에 적용 되지 않았는지 확인할 수 있습니다. 그러나 적용지 않습니다 하 고 다음이 지침을 따르지 않는 경우 사용자에 게 있을 열악 한 환경이 cmdlet를 사용 하는 경우.

## <a name="design-guidelines"></a>디자인 지침

- [특정 명사를 사용 하 여 Cmdlet 이름의 (SD01)](./strongly-encouraged-development-guidelines.md#use-a-specific-noun-for-a-cmdlet-name-sd01)

- [Cmdlet 이름 (SD02)에 대 한 파스칼식 대 / 소문자를 사용 하 여](./strongly-encouraged-development-guidelines.md#use-pascal-case-for-cmdlet-names-sd02)

- [매개 변수 디자인 지침 (SD03)](./strongly-encouraged-development-guidelines.md#parameter-design-guidelines-sd03)

- [(SD04) 사용자에 게 피드백을 제공 합니다.](./strongly-encouraged-development-guidelines.md#provide-feedback-to-the-user-sd04)

- [Cmdlet 도움말 파일 (SD05) 만들기](./strongly-encouraged-development-guidelines.md#create-a-cmdlet-help-file-sd05)

## <a name="code-guidelines"></a>코드 지침

- [코딩 매개 변수 (SC01)](./strongly-encouraged-development-guidelines.md#coding-parameters-sc01)

- [잘 정의 된 파이프라인 입력 (SC02)를 지원 합니다.](./strongly-encouraged-development-guidelines.md#support-well-defined-pipeline-input-sc02)

- [파이프라인 (SC03)에 단일 레코드 기록](./strongly-encouraged-development-guidelines.md#write-single-records-to-the-pipeline-sc03)

- [Cmdlet을 대/소문자 확인 대소 문자가 구분 (SC04) 및](./strongly-encouraged-development-guidelines.md#make-cmdlets-case-insensitive-and-case-preserving-sc04)

## <a name="design-guidelines"></a>디자인 지침

Cmdlet 및 기타 cmdlet을 사용 하 여 간에 일관 된 사용자 환경을 보장 하려면 cmdlet을 디자인할 때 다음 지침을 따라야 합니다. 상황에 적용 되는 디자인 지침을 찾으면 유사한 지침에 대 한 코드 지침 확인 해야 합니다.

### <a name="use-a-specific-noun-for-a-cmdlet-name-sd01"></a>특정 명사를 사용 하 여 Cmdlet 이름의 (SD01)

Cmdlet에 사용 되는 명사 사용자 cmdlet를 검색할 수 있도록 매우 구체적인 되도록 해야 합니다. 제품 이름의 약식된 버전을 사용 하 여 "server"와 같은 제네릭 명사 접두사입니다. 예를 들어 명사는 Microsoft SQL Server 인스턴스를 실행 하는 서버를 가리키는 경우 "SQLServer"와 같은 명사를 사용 합니다. 짧은 목록을 승인 된 동사와 특정 명사 조합 신속 하 게 검색 하 고 cmdlet 이름 간에 중복을 방지 하는 동안 기능을 예상할 수 있도록 합니다.

사용자 경험을 강화 하려면 cmdlet 이름에 대해 선택한 명사 단 수 있어야 합니다. 예를 들어 이름을 사용 하 여 `Get-Process` of **Get 프로세스**합니다. Cmdlet은 둘 이상의 항목을 작업할 가능성이 있는 경우에 모든 cmdlet 이름에 대 한이 규칙을 따라야 하는 것이 좋습니다.

### <a name="use-pascal-case-for-cmdlet-names-sd02"></a>Cmdlet 이름 (SD02)에 대 한 파스칼식 대 / 소문자를 사용 하 여

매개 변수 이름에 파스칼식 대 / 소문자를 사용 합니다. 즉, 동사와 명사에 사용 된 모든 용어 첫 번째 글자를 대문자로 표시 합니다. 예를 들어, "`Clear-ItemProperty`"입니다.

### <a name="parameter-design-guidelines-sd03"></a>매개 변수 디자인 지침 (SD03)

Cmdlet 매개 변수는 작동 해야, 데이터를 수신 하는 하며 작업의 특징을 결정 하는 데 사용 되는 정보를 나타내는 매개 변수입니다. 예를 들어 cmdlet 있을 수 있습니다는 `Name` 파이프라인 및 cmdlet에서 데이터를 수신 하는 매개 변수에 사용할 수 있습니다를 `Force` 매개 변수를 해당 작업을 수행 하는 cmdlet를 강제로 적용할 수 있습니다. Cmdlet을 정의할 수 있는 매개 변수 개수 제한은 없습니다.

#### <a name="use-standard-parameter-names"></a>표준 매개 변수 이름을 사용합니다

Cmdlet에 사용자 특정 매개 변수에 의미를 빠르게 확인할 수 있도록 표준 매개 변수 이름을 사용 해야 합니다. 보다 구체적인 이름을 필요한 경우 표준 매개 변수 이름을 사용 하 고 별칭으로 더 구체적인 이름을 지정 합니다. 예를 들어 합니다 `Get-Service` cmdlet에는 일반 이름이 지정 된 매개 변수 (`Name`) 및 보다 구체적인 별칭 (`ServiceName`). 매개 변수를 지정 하려면 두 용어를 사용할 수 있습니다.

매개 변수 이름과 해당 데이터 형식에 대 한 자세한 내용은 참조 하세요. [Cmdlet 매개 변수 이름 및 기능 지침](./standard-cmdlet-parameter-names-and-types.md)합니다.

#### <a name="use-singular-parameter-names"></a>단일 매개 변수 이름을 사용합니다

매개 변수 값은 단일 요소에 대 한 복수형 이름을 사용 하지 마십시오. 이 배열을 사용 하는 매개 변수를 포함 하거나 배열 또는 목록 요소를 하나만 사용 하 여 사용자를 제공할 수도 있으므로 나열 합니다.

매개 변수의 값은 여러 요소 값을 항상 이러한 경우에만 복수형 매개 변수 이름은 사용 해야 합니다. 이러한 경우에는 여러 요소를 제공 하 고 여러 요소를 제공 하지 않으면 cmdlet은 사용자에 게 경고가 표시 됩니다 cmdlet은 확인 해야 합니다.

#### <a name="use-pascal-case-for-parameter-names"></a>매개 변수 이름에 파스칼식 대 / 소문자를 사용 하 여

매개 변수 이름에 파스칼식 대 / 소문자를 사용 합니다. 즉, 이름의 첫 번째 문자를 포함 하는 매개 변수 이름에서 각 단어의 첫 번째 글자를 대문자로 바꿉니다. 예를 들어, 매개 변수 이름을 `ErrorAction` 올바른 대/소문자를 사용 합니다. 다음 매개 변수 이름은 대/소문자를 사용합니다.

- `errorAction`

- `erroraction`

#### <a name="parameters-that-take-a-list-of-options"></a>옵션의 목록을 사용 하는 매개 변수

두 가지 방법으로 옵션 집합에서 값을 선택할 수 있습니다 하는 매개 변수를 만듭니다.

- 열거형을 정의 합니다 (또는 기존 열거형 형식을 사용 하 여) 하는 유효한 값을 지정 합니다. 그런 다음 해당 형식 매개 변수를 만들려면 열거형을 사용 합니다.

- 추가 된 **ValidateSet** 특성을 매개 변수 선언 합니다. 이 특성에 대 한 자세한 내용은 참조 하세요. [ValidateSet 특성 선언을](./validateset-attribute-declaration.md)합니다.

#### <a name="use-standard-types-for-parameters"></a>매개 변수를 사용 하 여 표준 형식

다른 cmdlet 사용 하 여 일관성을 보장 하려면 여기서 때 가능한 표준 형식 매개 변수에 대 한 사용 합니다. 다른 매개 변수를 사용 해야 하는 형식에 대 한 자세한 내용은 참조 하세요. [표준 Cmdlet 매개 변수 이름 및 형식을](./standard-cmdlet-parameter-names-and-types.md)합니다. 이 항목에서는 이름과 "활동 매개 변수"와 같은 표준 매개 변수는 그룹에 대 한.NET Framework 형식을 설명 하는 몇 가지 항목에 대 한 링크를 제공 합니다.

#### <a name="use-strongly-typed-net-framework-types"></a>강력한 형식의.NET Framework 형식을 사용합니다

매개 변수는 더 나은 매개 변수 유효성 검사를 위해.NET Framework 형식으로 정의 되어야 합니다. 예를 들어, 매개 변수 값 집합에서 하나의 값으로 제한 되는 열거형 형식으로 정의 되어야 합니다. 를 지원 하기 위해 리소스 URI (Uniform Identifier) 값으로 매개 변수를 정의 된 [System.Uri](/dotnet/api/System.Uri) 형식입니다. 자유 형식 제외한 모든 텍스트 속성에 대 한 기본 문자열 매개 변수를 방지 합니다.

#### <a name="use-consistent-parameter-types"></a>일관 된 매개 변수 형식을 사용 하 여

동일한 매개 변수는 여러 cmdlet 사용, 항상 동일한 매개 변수 형식을 사용 합니다.  예를 들어 경우는 `Process` 매개 변수는는 [System.Int16](/dotnet/api/System.Int16) cmdlet에 대 한 입력을 수행 하지는 `Process` 다른 cmdlet에 대 한 매개 변수를 [System.Uint16](/dotnet/api/System.UInt16) 형식입니다.

#### <a name="parameters-that-take-true-and-false"></a>매개 변수는 True 및 False

매개 변수만 사용 하는 경우 `true` 하 고 `false`, 형식으로 매개 변수를 정의 [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter)합니다. 스위치 매개 변수는 취급 `true` 명령에 지정 된 경우. Windows PowerShell 고려 되도록 매개 변수의 매개 변수를 명령에 포함 되지 않으면, `false`합니다. 부울 매개 변수를 정의 하지 않습니다.

매개 변수 3 개 값을 구분 하는 경우: $true, $false 및 "unspecified" Nullable 형식의 매개 변수를 정의 합니다\<bool >.  타사에 대 한 필요는 "알 수 없는" 값 cmdlet은 개체의 부울 속성을 수정할 수 있습니다 때에 일반적으로 발생 합니다. 이 경우 "알 수 없는" 이면 속성의 현재 값이 변경 되지 됩니다.

#### <a name="support-arrays-for-parameters"></a>배열 매개 변수에 대 한 지원

대부분의 경우 사용자가 여러 인수에 대해 동일한 작업을 수행 해야 합니다. 이러한 사용자에 대 한 cmdlet Windows PowerShell 변수를 매개 변수로 사용자 인수를 전달할 수 있도록 입력 매개 변수로 배열을 수락 해야 합니다. 예를 들어 합니다 [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet은 검색 프로세스의 이름을 식별 하는 문자열 배열을 사용 합니다.
대부분의 경우 사용자가 여러 인수에 대해 동일한 작업을 수행 해야 합니다. 이러한 사용자에 대 한 cmdlet Windows PowerShell 변수를 매개 변수로 사용자 인수를 전달할 수 있도록 입력 매개 변수로 배열을 수락 해야 합니다. 예를 들어 합니다 [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet은 검색 프로세스의 이름을 식별 하는 문자열 배열을 사용 합니다.

#### <a name="support-the-passthru-parameter"></a>PassThru 매개 변수를 지원 합니다.

기본적으로 많은 cmdlet을 수정 하는 시스템 같은 합니다 [Stop-process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet을 개체에 대 한 "싱크"로 작동 하 고 결과 반환 하지 않습니다. 이러한 cmdlet을 구현 해야 합니다 `PassThru` cmdlet이 개체를 반환 하도록 매개 변수입니다. 경우는 `PassThru` 매개 변수에 지정 된 경우 cmdlet에 대 한 호출을 사용 하 여 개체를 반환 합니다.는 [System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 메서드. 예를 들어, 다음 명령을 Calc 프로세스를 중지 하 고 결과 프로세스를 파이프라인으로 전달 합니다.

```powershell
Stop-Process calc -passthru
```

대부분의 경우, 추가, 집합 및 새 cmdlet을 지원 해야는 `PassThru` 매개 변수입니다.

#### <a name="support-parameter-sets"></a>매개 변수 집합을 지원 합니다.

한 가지 목적을 위해 cmdlet 것입니다. 그러나 방법이 자주 둘 이상의 작업 또는 작업 대상에 설명 합니다. 예를 들어, 프로세스 이름으로, 해당 식별자 또는 프로세스 개체를 식별 될 수 있습니다. Cmdlet은 해당 대상 적절 한 표현의 지원 해야 합니다. 일반적으로 cmdlet은 함께 작동 하는 매개 변수 (매개 변수 집합이 라고도 함) 집합을 지정 하 여이 요구 사항을 충족 합니다. 단일 매개 변수는 임의 개수의 매개 변수 집합에 속할 수 있습니다. 매개 변수 집합에 대 한 자세한 내용은 참조 하세요. [Cmdlet 매개 변수 설정](./cmdlet-parameter-sets.md)합니다.

매개 변수 집합을 지정 하면 ValueFromPipeline 집합에 하나의 매개 변수를 설정 합니다. 선언 하는 방법에 대 한 자세한 내용은 합니다 **매개 변수** 특성을 참조 하십시오 [ParameterAttribute 선언](./parameter-attribute-declaration.md)합니다.

기본 매개 변수 집합을 정의한 매개 변수 집합을 사용 하는 경우는 **Cmdlet** 특성입니다. 기본 매개 변수 집합에는 대화형 Windows PowerShell 세션에서 사용할 가능성이 가장 높은 매개 변수를 포함 해야 합니다. 선언 하는 방법에 대 한 자세한 내용은 합니다 **Cmdlet** 특성을 참조 하십시오 [CmdletAttribute 선언의](./cmdlet-attribute-declaration.md)합니다.

### <a name="provide-feedback-to-the-user-sd04"></a>(SD04) 사용자에 게 피드백을 제공 합니다.

사용자에 게 피드백을 제공 하려면이 섹션의 지침을 따르세요. 이 피드백 사용자를 시스템에서 발생 하는 일을 이용 하 고 잘 관리 결정을 내릴 수 있습니다.

Windows PowerShell 런타임에 각 호출의 출력을 처리 하는 방법을 지정할 수 있습니다는 `Write` 메서드를 기본 설정 변수를 설정 합니다. 시스템 정보 및 추가 작업을 수행 하기 전에 시스템 사용자를 쿼리하려면 해야 하는지 여부를 결정 하는 변수를 표시할 것인지 여부를 결정 하는 변수를 비롯 한 몇 가지 기본 설정 변수를 설정할 수 있습니다.

#### <a name="support-the-writewarning-writeverbose-and-writedebug-methods"></a>WriteWarning, WriteVerbose를 및 WriteDebug 메서드 지원

Cmdlet을 호출 해야 합니다 [System.Management.Automation.Cmdlet.Writewarning*](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) cmdlet 의도 하지 않은 결과 가질 수 있는 작업을 수행 하려고 할 때 메서드. 예를 들어, 경우 cmdlet에 대 한 읽기 전용 파일을 덮어쓸지 cmdlet이이 메서드를 호출 해야 합니다.

Cmdlet을 호출 해야 합니다 [System.Management.Automation.Cmdlet.Writeverbose*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) cmdlet가 무엇을 수행 하는 방법에 대 한 일부 세부 정보를 표시할지 메서드. 예를 들어 cmdlet 작성자는 cmdlet가 무엇을 수행 하는 방법에 대 한 자세한 정보가 필요할 수 있는 시나리오는 판단 하는 경우 cmdlet이이 정보를 호출 해야 합니다.

Cmdlet을 호출 해야 합니다 [System.Management.Automation.Cmdlet.Writedebug*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) 메서드 개발자나 제품 지원 엔지니어가 cmdlet 작업 손상 무엇을 이해 해야 합니다. 필요 없는 cmdlet에 대 한 호출을 [System.Management.Automation.Cmdlet.Writedebug*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) 메서드를 호출 하는 동일한 코드를 [System.Management.Automation.Cmdlet.Writeverbose*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) 메서드 때문에 `Debug` 매개 변수는 두 가지 정보를 제공 합니다.

#### <a name="support-writeprogress-for-operations-that-take-a-long-time"></a>WriteProgress 시간이 오래 걸릴 수 있는 작업에 대 한 지원

Cmdlet은 작업 백그라운드에서 실행할 수 없습니다 하 고 완료 하는 데 시간이 오래 사용 하는 진행률에 대 한 주기적인 호출을 통해 보고를 지원 해야 합니다 [System.Management.Automation.Cmdlet.Writeprogress*](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) 메서드.

#### <a name="use-the-host-interfaces"></a>호스트 인터페이스를 사용 합니다.

경우에 따라 cmdlet와 통신 해야 직접 대신 사용자를 사용 하 여 다양 한 쓰거나에서 지 원하는 메서드를 해야 합니다 [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) 클래스입니다. Cmdlet에서 파생 되어야이 경우에 [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) 클래스 및 사용 합니다 [System.Management.Automation.Pscmdlet.Host*](/dotnet/api/System.Management.Automation.PSCmdlet.Host) 속성. 이 속성에는 서로 다른 수준의 PromptForChoice, 프롬프트 및 WriteLine/ReadLine 형식을 비롯 한 통신 형식 지원 합니다. 가장 특정 수준도 제공 개별 키를 읽고 하 고 버퍼를 사용 하 여 처리 방법은 합니다.

이 cmdlet은 그래픽 사용자 인터페이스 (GUI)를 생성 하도록 설계 된, 경우가 아니면 사용 하 여 호스트를 우회 하지는 해야 합니다 [System.Management.Automation.Pscmdlet.Host*](/dotnet/api/System.Management.Automation.PSCmdlet.Host) 속성입니다. GUI를 생성 하도록 설계 된 cmdlet의 예로 [Out-gridview](/powershell/module/Microsoft.PowerShell.Utility/Out-GridView) cmdlet.

> [!NOTE]
> Cmdlet을 사용 하지 않아야 합니다 [System.Console](/dotnet/api/System.Console) API.

### <a name="create-a-cmdlet-help-file-sd05"></a>Cmdlet 도움말 파일 (SD05) 만들기

각 cmdlet 어셈블리에 대 한 cmdlet에 대 한 정보를 포함 하는 Help.xml 파일을 만듭니다. 이 정보에는 cmdlet, cmdlet의 매개 변수 설명, cmdlet의 사용 등의 예제에 대 한 설명을 포함합니다.

## <a name="code-guidelines"></a>코드 지침

Cmdlet 및 기타 cmdlet을 사용 하 여 간에 일관 된 사용자 환경을 보장 하려면 cmdlet을 코딩 하는 경우 다음 지침을 따라야 합니다. 상황에 적용 되는 코드 지침을 찾으면 유사한 지침에 대 한 디자인 지침 확인 해야 합니다.

### <a name="coding-parameters-sc01"></a>코딩 매개 변수 (SC01)

로 데코레이팅된는 cmdlet 클래스의 공용 속성을 선언 하 여 매개 변수를 정의 합니다 **매개 변수** 특성입니다. 매개 변수는 cmdlet에 대 한 파생된.NET Framework 클래스의 정적 멤버를 사용할 필요가 없습니다. 선언 하는 방법에 대 한 자세한 내용은 합니다 **매개 변수** 특성을 참조 하십시오 [매개 변수 특성 선언](./parameter-attribute-declaration.md)합니다.

#### <a name="support-windows-powershell-paths"></a>Windows PowerShell 경로 지원 합니다.

Windows PowerShell 경로 네임 스페이스에 대 한 액세스를 정규화 하는 것에 대 한 메커니즘입니다. Cmdlet에서 매개 변수는 Windows PowerShell 경로 할당 하면 사용자는 사용자 지정 역할을 특정 경로 대 한 바로 가기를 "드라이브"를 정의할 수 있습니다. 드라이브를 지정 하는 사용자를 레지스트리에서 데이터와 같은 저장 된 데이터에 일관 된 방식으로 사용할 수 있습니다.

형식의 매개 변수를 정의 해야 cmdlet에서는 사용자의 파일 또는 데이터 원본을 지정 하는 경우 [System.String](/dotnet/api/System.String)합니다. 둘 이상의 드라이브가 지원 되는지, 하는 경우 형식 배열 이어야 합니다. 매개 변수의 이름 이어야 합니다 `Path`의 별칭을 사용 하 여 `PSPath`입니다. 또한는 `Path` 매개 변수는 와일드 카드 문자를 지원 해야 합니다. 경우 와일드 카드 문자 필요 하지 않습니다. 지원, 정의 `LiteralPath` 매개 변수입니다.

Cmdlet을 읽거나 쓰는 데이터 파일에 cmdlet은 Windows PowerShell 경로 입력을 허용 해야 하 고 cmdlet을 사용 해야 합니다 [System.Management.Automation.Sessionstate.Path](/dotnet/api/System.Management.Automation.SessionState.Path) 는 Windows를 변환 하는 속성 PowerShell 파일 시스템에서 인식 하는 경로에 대 한 경로입니다. 다음 메서드를 포함 하는 특정 메커니즘.

- [System.Management.Automation.Pscmdlet.Getresolvedproviderpathfrompspath](/dotnet/api/System.Management.Automation.PSCmdlet.GetResolvedProviderPathFromPSPath)

- [System.Management.Automation.Pscmdlet.Getunresolvedproviderpathfrompspath](/dotnet/api/System.Management.Automation.PSCmdlet.GetUnresolvedProviderPathFromPSPath)

- [System.Management.Automation.Pathintrinsics.Getresolvedproviderpathfrompspath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetResolvedProviderPathFromPSPath)

- [System.Management.Automation.Pathintrinsics.Getunresolvedproviderpathfrompspath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetUnresolvedProviderPathFromPSPath)

데이터를 읽거나 쓰는 cmdlet만 경우 cmdlet은 파일 대신 문자열 집합이 공급자 콘텐츠 정보를 사용할지 (`Content` 멤버) 읽기 및 쓰기입니다. 이 정보를 가져옵니다 합니다 [System.Management.Automation.Provider.Cmdletprovider.Invokeprovider*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.InvokeProvider) 속성입니다. 이러한 메커니즘 다른 데이터 저장소에 읽기 및 쓰기 데이터의 참여를 허용 합니다.

#### <a name="support-wildcard-characters"></a>와일드 카드 문자를 지원 합니다.

Cmdlet는 가능한 경우 와일드 카드 문자를 지원 해야 합니다. 와일드 카드 문자에 대 한 지원 (특히 경우는 매개 변수는 개체 집합에서 하나의 개체를 식별 하는 문자열) cmdlet의 여러 위치에서 발생 합니다. 예를 들어, 샘플 **중지 Proc** 에서 cmdlet을 [StopProc 자습서](./stopproc-tutorial.md) 정의 `Name` 프로세스 이름을 나타내는 문자열을 처리 하는 매개 변수. 이 매개 변수는 사용자 프로세스 중지를 쉽게 지정할 수 있도록 와일드 카드 문자를 지원 합니다.

와일드 카드를 지 원하는 경우 문자를 사용할 수 있는 cmdlet은 작업에는 일반적으로 배열을 생성 합니다. 경우에 따라 사용자는 한 번에 하나의 항목만 사용할 수 있으므로 배열을 지원을 만들지 않습니다. 예를 들어 합니다 [Set-location](/powershell/module/Microsoft.PowerShell.Management/Set-Location) cmdlet만 단일 위치를 설정 하는 사용자 것 때문에 배열을 지원 하지 않아도 됩니다. 이 예에서는 cmdlet을 계속 와일드 카드 문자를 지원 하지만 단일 위치를 확인 하 게 하기.

와일드 카드-문자 패턴에 대 한 자세한 내용은 참조 하세요. [Cmdlet 매개 변수에서 와일드 카드 문자를 지 원하는](./supporting-wildcard-characters-in-cmdlet-parameters.md)합니다.

#### <a name="defining-objects"></a>개체를 정의합니다.

이 섹션에서는 기존 개체를 확장 한 cmdlet에 대 한 개체를 정의 하기 위한 지침을 포함 합니다.

##### <a name="define-standard-members"></a>표준 멤버를 정의 합니다.

사용자 지정 (사용 하 여 Windows PowerShell Types.ps1xml 파일을 템플릿으로) Types.ps1xml 파일에는 개체 형식을 확장 하 여 표준 멤버를 정의 합니다. 표준 멤버 이름의 PSStandardMembers 노드에 의해 정의 됩니다. 이러한 정의 다른 cmdlet 및 일관 된 방식으로 개체를 사용 하는 Windows PowerShell 런타임에 허용 합니다.

##### <a name="define-objectmembers-to-be-used-as-parameters"></a>매개 변수로 사용할 ObjectMembers 정의

Cmdlet에 대 한 개체를 디자인 하는 경우 해당 멤버를 사용 하는 cmdlet의 매개 변수에 직접 매핑합니다 있는지 확인 합니다. 이 매핑은 다른 cmdlet에서 전달할 개체를 파이프라인에 쉽게 보낼 수 있습니다.

Cmdlet에서 반환 되는 기존.NET Framework 개체가 자주 스크립트 개발자나 사용자에 필요한 일부 중요 하거나 편리한 멤버가 없습니다. 이러한 누락 된 멤버는 표시 및 파이프라인에 개체를 올바르게 전달할 수 있도록 올바른 멤버 이름을 만들기 위해 특히 중요할 수 있습니다. 이러한 필수 멤버를 문서화 하는 사용자 지정 Types.ps1xml 파일을 만듭니다. 이 파일을 만들면 다음 명명 규칙을 권장 합니다. *< Your_Product_Name >* 합니다. Types.ps1xml 합니다.

예를 들어, 추가할 수 있습니다를 `Mode` 스크립트 속성을 합니다 [System.IO.Fileinfo](/dotnet/api/System.IO.FileInfo) 파일의 속성을 보다 명확 하 게 표시 하는 형식입니다. 또한 추가할 수 있습니다는 `Count` 별칭 속성을 합니다 [System.Array](/dotnet/api/System.Array) 는 속성 이름의 일관 된 사용을 허용 하는 형식 (대신 `Length`).

##### <a name="implement-the-icomparable-interface"></a>IComparable 인터페이스를 구현 합니다.

구현 된 [System.Icomparable](/dotnet/api/System.IComparable) 모든 출력 개체에 대 한 인터페이스입니다. 이렇게 하면 출력 개체를를 쉽게 정렬 및 분석에 대 한 다양 한 cmdlet에 파이프할 수 있습니다.

##### <a name="update-display-information"></a>정보를 표시 하는 업데이트

개체에 대 한 표시는 예상된 결과 제공 하지 않으면, 사용자 지정 만들기  *\<YourProductName >* 합니다. 해당 개체에 대 한 Format.ps1xml 파일입니다.

### <a name="support-well-defined-pipeline-input-sc02"></a>잘 정의 된 파이프라인 입력 (SC02)를 지원 합니다.

#### <a name="implement-for-the-middle-of-a-pipeline"></a>파이프라인의 중간에 대 한 구현

파이프라인의 중간에서 호출할 수는 가정 하 고 cmdlet을 구현 (즉, 다른 cmdlet은 해당 입력을 생성 또는 해당 출력을 사용). 예를 들어는 생각할 수 있습니다는 `Get-Process` cmdlet, 데이터를 생성 하기 때문에 으로만 사용 되며 파이프라인의 첫 번째 cmdlet. 그러나이 cmdlet을 파이프라인의 중간에 대 한 디자인 되었으므로이 cmdlet에서는 이전 cmdlet 또는 데이터 검색 프로세스를 지정 하는 파이프라인입니다.

#### <a name="support-input-from-the-pipeline"></a>파이프라인의 입력 지원

각 매개 변수를 cmdlet에 대 한 설정에서 파이프라인의 입력을 지 원하는 하나 이상의 매개 변수가 포함 됩니다. 파이프라인 입력에 대 한 지원 데이터 나 결과 cmdlet에 직접 전달 하 고 올바른 매개 변수 집합으로 보낼 개체를 검색할 수가 있습니다.

경우 매개 변수는 파이프라인의 입력을 허용 합니다 **매개 변수** 특성 포함를 `ValueFromPipeline` 키워드를는 `ValueFromPipelineByPropertyName` 키워드 특성 또는 두 키워드를 선언 합니다. 지지도 설정 하는 경우 매개 변수에서 매개 변수를 `ValueFromPipeline` 또는 `ValueFromPipelineByPropertyName` 키워드, cmdlet 맥락 배치할 수 없습니다 후 다른 cmdlet 파이프라인 입력을 무시 합니다.

#### <a name="support-the-processrecord-method"></a>ProcessRecord 메서드를 지원 합니다.

파이프라인 이전 cmdlet에서 모든 레코드를 허용 하려면 cmdlet 구현 해야 합니다 [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드. Windows PowerShell이이 메서드를 호출을 여러 번 번 cmdlet로 전송 되는 모든 레코드에 대 한 합니다.

### <a name="write-single-records-to-the-pipeline-sc03"></a>파이프라인 (SC03)에 단일 레코드 기록

Cmdlet은 개체를 작성 해야 cmdlet 개체를 반환 하는 경우 즉시 생성 됩니다. Cmdlet은 결합 된 배열로 버퍼링 하기 위해 이러한을 보관 하지 말아야 합니다. 입력으로 개체를 수신 하는 cmdlet을 처리 하 고, 표시 또는 처리 지연 시간 없이 출력 개체를 표시 됩니다. Cmdlet 출력을 생성 하는 개체를 한 번에 하나씩 호출 해야 합니다 [System.Management.Automation.Cmdlet.Writeobject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 메서드. (예를 들어, 기본 API 반환 하므로 출력 개체의 배열) 일괄 처리에서 출력 개체를 생성 하는 cmdlet을 호출 해야 합니다 [System.Managemet.Automation.Cmdlet.Writeobject](/dotnet/api/System.Managemet.Automation.Cmdlet.WriteObject) 의 두 번째 매개 변수를 사용 하 여 메서드 설정 `true`입니다.

### <a name="make-cmdlets-case-insensitive-and-case-preserving-sc04"></a>Cmdlet을 대/소문자 확인 대소 문자가 구분 (SC04) 및

기본적으로 자체 Windows PowerShell은 대/소문자입니다. 그러나 많은 기존 시스템을 사용 하 여 처리 하기 때문에 Windows PowerShell은 작업 및 호환성의 편의 위해 대/소문자를 유지 합니다. 즉, 문자를 대문자로 제공 하면 Windows PowerShell에에서 유지 대문자입니다. 제대로 작동 하려면 시스템에 대 한 cmdlet이이 규칙에 따라 해야 합니다. 가능한 경우 대/소문자 구분 방식으로 작동 해야 합니다. 하지만 명령에서 나중에 또는 파이프라인에서 발생 하는 cmdlet에 대 한 원래 대/소문자는 유지 해야 합니다.

## <a name="see-also"></a>참고 항목

[필요한 개발 지침](./required-development-guidelines.md)

[자문 개발 지침](./advisory-development-guidelines.md)

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
