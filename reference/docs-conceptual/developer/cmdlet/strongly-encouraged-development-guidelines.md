---
title: 권장 되는 개발 지침 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 02488fea557b42ed30ea5cfde177b3efe0b3f559
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787821"
---
# <a name="strongly-encouraged-development-guidelines"></a>적극 권장되는 개발 지침

이 섹션에서는 cmdlet을 작성할 때 따라야 하는 지침을 설명 합니다. Cmdlet을 디자인 하기 위한 지침과 cmdlet 코드를 작성 하기 위한 지침으로 구분 됩니다. 이러한 지침은 모든 시나리오에 적용 되지 않을 수 있습니다. 그러나 이러한 지침이 적용 되는 경우 이러한 지침을 따르지 않으면 사용자가 cmdlet을 사용 하는 경우 사용자에 게 좋지 않은 경험이 있을 수 있습니다.

## <a name="design-guidelines"></a>디자인 지침

- [Cmdlet 이름에 특정 명사 사용 (SD01)](./strongly-encouraged-development-guidelines.md#use-a-specific-noun-for-a-cmdlet-name-sd01)

- [Cmdlet 이름으로 파스칼식 대/소문자 사용 (SD02)](./strongly-encouraged-development-guidelines.md#use-pascal-case-for-cmdlet-names-sd02)

- [매개 변수 디자인 지침 (SD03)](./strongly-encouraged-development-guidelines.md#parameter-design-guidelines-sd03)

- [사용자에 게 피드백 제공 (SD04)](./strongly-encouraged-development-guidelines.md#provide-feedback-to-the-user-sd04)

- [Cmdlet 도움말 파일 만들기 (SD05)](./strongly-encouraged-development-guidelines.md#create-a-cmdlet-help-file-sd05)

## <a name="code-guidelines"></a>코드 지침

- [매개 변수 코딩 (SC01)](./strongly-encouraged-development-guidelines.md#coding-parameters-sc01)

- [잘 정의 된 파이프라인 입력 지원 (SC02)](./strongly-encouraged-development-guidelines.md#support-well-defined-pipeline-input-sc02)

- [파이프라인에 단일 레코드 쓰기 (SC03)](./strongly-encouraged-development-guidelines.md#write-single-records-to-the-pipeline-sc03)

- [Cmdlet에서 대/소문자를 구분 하지 않고 대/소문자를 유지 합니다 (SC04).](./strongly-encouraged-development-guidelines.md#make-cmdlets-case-insensitive-and-case-preserving-sc04)

## <a name="design-guidelines"></a>디자인 지침

Cmdlet을 사용 하 여 cmdlet 및 기타 cmdlet을 사용 하는 것과 일관 된 사용자 환경을 보장 하기 위해 cmdlet을 디자인할 때는 다음 지침을 따라야 합니다. 상황에 적용 되는 디자인 지침을 찾았으면 유사한 지침에 대 한 코드 지침을 확인 해야 합니다.

### <a name="use-a-specific-noun-for-a-cmdlet-name-sd01"></a>Cmdlet 이름에 특정 명사 사용 (SD01)

Cmdlet 이름에 사용 되는 명사는 사용자가 cmdlet을 검색할 수 있도록 매우 구체적 이어야 합니다. "Server"와 같은 일반적인 명사를 제품 이름의 축약 된 버전으로 접두사로 붙입니다. 예를 들어 명사가 Microsoft SQL Server의 인스턴스를 실행 하는 서버를 참조 하는 경우 "SQLServer"와 같은 명사를 사용 합니다. 사용자는 특정 명사와 승인 된 동사의 짧은 목록을 조합 하 여 cmdlet 이름 간의 중복을 방지 하면서 기능을 신속 하 게 검색 하 고 예측할 수 있습니다.

사용자 환경을 개선 하기 위해 cmdlet 이름에 대해 선택 하는 명사는 단 수 여야 합니다. 예를 들어, `Get-Process` **Get 프로세스**대신 이름을 사용 합니다. Cmdlet이 둘 이상의 항목에 대해 작동할 가능성이 있는 경우에도 모든 cmdlet 이름에 대해이 규칙을 따르는 것이 가장 좋습니다.

### <a name="use-pascal-case-for-cmdlet-names-sd02"></a>Cmdlet 이름으로 파스칼식 대/소문자 사용 (SD02)

매개 변수 이름으로 파스칼식 대/소문자를 사용 합니다. 즉, 동사에서 첫 글자를 대문자로 사용 하 고 모든 용어를 명사에 사용 합니다. 예: "`Clear-ItemProperty`".

### <a name="parameter-design-guidelines-sd03"></a>매개 변수 디자인 지침 (SD03)

Cmdlet에는 작동 해야 하는 데이터를 수신 하는 매개 변수와 작업의 특징을 결정 하는 데 사용 되는 정보를 나타내는 매개 변수가 필요 합니다. 예를 들어 cmdlet은 `Name` 파이프라인에서 데이터를 수신 하는 매개 변수를 가질 수 있으며 cmdlet은이 cmdlet을 통해 `Force` 작업을 강제로 수행할 수 있음을 나타내는 매개 변수를 가질 수 있습니다. Cmdlet에서 정의할 수 있는 매개 변수의 수에는 제한이 없습니다.

#### <a name="use-standard-parameter-names"></a>표준 매개 변수 이름 사용

사용자가 특정 매개 변수의 의미를 빠르게 확인할 수 있도록 cmdlet은 표준 매개 변수 이름을 사용 해야 합니다. 보다 구체적인 이름이 필요한 경우 표준 매개 변수 이름을 사용 하 고 별칭으로 더 구체적인 이름을 지정 합니다. 예를 들어 cmdlet에는 `Get-Service` 제네릭 이름 ( `Name` )과 보다 구체적인 별칭 ()이 있는 매개 변수가 있습니다 `ServiceName` . 두 용어는 모두 매개 변수를 지정 하는 데 사용할 수 있습니다.

매개 변수 이름 및 해당 데이터 형식에 대 한 자세한 내용은 [Cmdlet 매개 변수 이름 및 기능 지침](./standard-cmdlet-parameter-names-and-types.md)을 참조 하세요.

#### <a name="use-singular-parameter-names"></a>단일 매개 변수 이름 사용

값이 단일 요소인 매개 변수에는 복수 이름을 사용 하지 마십시오. 여기에는 사용자가 요소를 하나만 포함 하는 배열 또는 목록을 제공할 수 있으므로 배열이 나 목록을 사용 하는 매개 변수가 포함 됩니다.

복수형 매개 변수 이름은 매개 변수의 값이 항상 다중 요소 값인 경우에만 사용 해야 합니다. 이러한 경우, cmdlet은 여러 요소가 제공 되었는지 확인 하 고, 여러 요소를 제공 하지 않으면 cmdlet이 사용자에 게 경고를 표시 해야 합니다.

#### <a name="use-pascal-case-for-parameter-names"></a>매개 변수 이름으로 파스칼식 대/소문자 사용

매개 변수 이름으로 파스칼식 대/소문자를 사용 합니다. 즉, 매개 변수 이름에서 각 단어의 첫 글자를 대문자로 바꿉니다 (이름의 첫 문자 포함). 예를 들어 매개 변수 이름은 `ErrorAction` 올바른 대문자 표시를 사용 합니다. 다음 매개 변수 이름에는 잘못 된 대/소문자가 사용 됩니다.

- `errorAction`

- `erroraction`

#### <a name="parameters-that-take-a-list-of-options"></a>옵션 목록을 사용 하는 매개 변수

옵션 집합에서 값을 선택할 수 있는 매개 변수를 만드는 방법에는 두 가지가 있습니다.

- 유효한 값을 지정 하는 열거형 형식 (또는 기존 열거형 형식 사용)을 정의 합니다. 그런 다음 열거형 형식을 사용 하 여 해당 형식의 매개 변수를 만듭니다.

- **ValidateSet** 특성을 매개 변수 선언에 추가 합니다. 이 특성에 대 한 자세한 내용은 [ValidateSet Attribute 선언](./validateset-attribute-declaration.md)을 참조 하세요.

#### <a name="use-standard-types-for-parameters"></a>매개 변수에 표준 형식 사용

다른 cmdlet과의 일관성을 보장 하려면 가능한 경우 매개 변수에 표준 형식을 사용 합니다. 다른 매개 변수에 사용 해야 하는 형식에 대 한 자세한 내용은 [표준 Cmdlet 매개 변수 이름 및 형식](./standard-cmdlet-parameter-names-and-types.md)을 참조 하세요. 이 항목에서는 "활동 매개 변수"와 같은 표준 매개 변수 그룹의 이름 및 .NET Framework 유형을 설명 하는 여러 항목에 대 한 링크를 제공 합니다.

#### <a name="use-strongly-typed-net-framework-types"></a>강력한 형식의 .NET Framework 형식 사용

매개 변수를 .NET Framework 형식으로 정의 하 여 더 나은 매개 변수 유효성 검사를 제공 해야 합니다. 예를 들어 값 집합에서 하나의 값으로 제한 되는 매개 변수는 열거형 형식으로 정의 되어야 합니다. URI (Uniform Resource Identifier) 값을 지원 하려면 매개 변수를 [system.uri](/dotnet/api/System.Uri) 형식으로 정의 합니다. 자유 형식 텍스트 속성에 대 한 기본 문자열 매개 변수를 사용 하지 않습니다.

#### <a name="use-consistent-parameter-types"></a>일관 된 매개 변수 형식 사용

동일한 매개 변수를 여러 cmdlet에서 사용 하는 경우 항상 동일한 매개 변수 형식을 사용 합니다.  예를 들어 `Process` 매개 변수가 하나의 cmdlet에 [System.Int16](/dotnet/api/System.Int16) 대 한 system.string 형식인 경우 `Process` 다른 cmdlet에 대 한 매개 변수를 [system.object](/dotnet/api/System.UInt16) 형식으로 만들지 마십시오.

#### <a name="parameters-that-take-true-and-false"></a>True 및 False를 사용 하는 매개 변수

매개 변수가 및만 사용 `true` 하 `false` 는 경우 매개 변수를 [system.object](/dotnet/api/System.Management.Automation.SwitchParameter)형식으로 정의 합니다. 스위치 매개 변수는 명령에 지정 된 대로 처리 됩니다 `true` . 매개 변수가 명령에 포함 되지 않은 경우 Windows PowerShell은 매개 변수 값을로 간주 합니다 `false` . 부울 매개 변수를 정의 하지 마십시오.

매개 변수가 3 개의 값을 구분 해야 하는 경우 ($true, $false 및 "지정 되지 않음") Nullable 형식의 매개 변수를 정의 \<bool> 합니다.  세 번째 "지정 되지 않음" 값은 일반적으로 cmdlet이 개체의 부울 속성을 수정할 수 있는 경우에 발생 합니다. 이 경우 "지정 하지 않음"은 속성의 현재 값을 변경 하지 않음을 의미 합니다.

#### <a name="support-arrays-for-parameters"></a>매개 변수에 대 한 지원 배열

사용자는 여러 인수에 대해 동일한 작업을 수행 해야 하는 경우가 많습니다. 이러한 사용자의 경우 cmdlet은 사용자가 인수를 매개 변수에 Windows PowerShell 변수로 전달할 수 있도록 배열을 매개 변수 입력으로 허용 해야 합니다. 예를 들어, [Get Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet은 검색할 프로세스의 이름을 식별 하는 문자열에 대해 배열을 사용 합니다.

#### <a name="support-the-passthru-parameter"></a>PassThru 매개 변수 지원

기본적으로 [Stop Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet과 같이 시스템을 수정 하는 많은 cmdlet은 개체의 "싱크" 역할을 하며 결과를 반환 하지 않습니다. 이러한 cmdlet `PassThru` 은 매개 변수를 구현 하 여 cmdlet이 강제로 개체를 반환 하도록 해야 합니다. `PassThru`매개 변수가 지정 된 경우 cmdlet은 [WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 메서드를 호출 하 여 개체를 반환 합니다. 예를 들어 다음 명령은 Calc 프로세스를 중지 하 고 결과 프로세스를 파이프라인으로 전달 합니다.

```powershell
Stop-Process calc -passthru
```

대부분의 경우 Add, Set 및 New cmdlet은 매개 변수를 지원 해야 합니다 `PassThru` .

#### <a name="support-parameter-sets"></a>매개 변수 집합 지원

Cmdlet은 단일 용도를 달성 하기 위한 것입니다. 그러나 작업 또는 작업 대상을 설명 하는 방법에는 여러 가지가 있습니다. 예를 들어 프로세스는 이름, 식별자 또는 프로세스 개체로 식별할 수 있습니다. Cmdlet은 해당 대상의 모든 적절 한 표현을 지원 해야 합니다. 일반적으로 cmdlet은 함께 작동 하는 매개 변수 집합 (매개 변수 집합 이라고 함)을 지정 하 여이 요구 사항을 충족 합니다. 단일 매개 변수는 원하는 수의 매개 변수 집합에 속할 수 있습니다. 매개 변수 집합에 대 한 자세한 내용은 [Cmdlet 매개 변수 집합](./cmdlet-parameter-sets.md)을 참조 하세요.

매개 변수 집합을 지정 하는 경우 집합의 매개 변수를 ValueFromPipeline로 설정 합니다. **매개 변수** 특성을 선언 하는 방법에 대 한 자세한 내용은 [parameterattribute 선언](./parameter-attribute-declaration.md)을 참조 하세요.

매개 변수 집합을 사용 하는 경우 기본 매개 변수 집합은 **Cmdlet** 특성에 의해 정의 됩니다. 기본 매개 변수 집합은 대화형 Windows PowerShell 세션에서 사용 될 가능성이 가장 높은 매개 변수를 포함 해야 합니다. **Cmdlet** 특성을 선언 하는 방법에 대 한 자세한 내용은 [cmdletattribute 선언](./cmdlet-attribute-declaration.md)을 참조 하세요.

### <a name="provide-feedback-to-the-user-sd04"></a>사용자에 게 피드백 제공 (SD04)

이 섹션의 지침을 사용 하 여 사용자에 게 피드백을 제공 합니다. 이 피드백을 통해 사용자는 시스템에서 발생 하는 상황을 인식 하 고 관리 관련 결정을 더 높일 수 있습니다.

Windows PowerShell 런타임을 사용 하면 사용자가 `Write` 기본 설정 변수를 설정 하 여 메서드에 대 한 각 호출의 출력을 처리 하는 방법을 지정할 수 있습니다. 사용자는 시스템에서 정보를 표시 해야 하는지 여부를 결정 하는 변수와, 추가 작업을 수행 하기 전에 시스템에서 사용자를 쿼리해야 하는지 여부를 결정 하는 변수를 포함 하 여 몇 가지 기본 설정 변수를 설정할 수 있습니다.

#### <a name="support-the-writewarning-writeverbose-and-writedebug-methods"></a>WriteWarning, Writewarning 및 Writewarning 메서드를 지원 합니다.

Cmdlet에서 의도 하지 않은 결과가 발생할 수 있는 작업을 수행 하려고 할 때에는 cmdlet이 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) 를 호출 해야 합니다. 예를 들어 cmdlet이 읽기 전용 파일을 덮어쓰려고 하는 경우이 메서드를 호출 해야 합니다.

Cmdlet은 사용자가 cmdlet이 수행 하는 작업에 대 한 세부 정보가 필요한 경우에는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) 를 호출 해야 합니다. 예를 들어 cmdlet이 cmdlet이 수행 하는 작업에 대 한 추가 정보가 필요할 수 있는 시나리오가 있는 경우 cmdlet은이 정보를 호출 해야 합니다.

개발자 또는 기술 지원 엔지니어가 cmdlet 작업의 손상 원인을 이해 해야 하는 경우 cmdlet은 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) 를 호출 해야 합니다. 매개 변수가 두 정보 집합을 모두 제공 하기 때문에 cmdlet이 동일한 코드에서 System.object를 호출 하는 것과 동일한 코드에서 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) 를 호출할 필요가 [없습니다.](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) `Debug`

#### <a name="support-writeprogress-for-operations-that-take-a-long-time"></a>시간이 오래 걸리는 작업의 WriteProgress 지원

완료 하는 데 시간이 오래 걸리고 백그라운드에서 실행할 수 없는 Cmdlet 작업은 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) 를 주기적으로 호출 하 여 진행률 보고를 지원 해야 합니다.

#### <a name="use-the-host-interfaces"></a>호스트 인터페이스 사용

경우에 따라 cmdlet은 사용자와 직접 통신 해야 하며,이는 여러 가지 Write 또는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet) 가 지 원하는 메서드를 사용 하는 대신 사용자와 직접 통신 해야 합니다. 이 경우 cmdlet은 [PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) 클래스에서 파생 되 고 [PSCmdlet *](/dotnet/api/System.Management.Automation.PSCmdlet.Host) 속성을 사용 해야 합니다 (예를 들어). 이 속성은 PromptForChoice, Prompt 및 WriteLine/ReadLine 유형을 포함 하 여 서로 다른 수준의 통신 유형을 지원 합니다. 또한 가장 구체적인 수준에서 개별 키를 읽고 쓰고 버퍼를 처리 하는 방법도 제공 합니다.

Cmdlet이 GUI (그래픽 사용자 인터페이스)를 생성 하도록 특별히 디자인 되지 않은 경우 [PSCmdlet *](/dotnet/api/System.Management.Automation.PSCmdlet.Host) 속성을 사용 하 여 호스트를 우회 해서는 안 됩니다. GUI를 생성 하도록 설계 된 cmdlet의 예는 [Out-GridView](/powershell/module/Microsoft.PowerShell.Utility/Out-GridView) cmdlet입니다.

> [!NOTE]
> Cmdlet은 [System.web](/dotnet/api/System.Console) API를 사용 하면 안 됩니다.

### <a name="create-a-cmdlet-help-file-sd05"></a>Cmdlet 도움말 파일 만들기 (SD05)

각 cmdlet 어셈블리에 대해 cmdlet에 대 한 정보가 포함 된 Help.xml 파일을 만듭니다. 이 정보에는 cmdlet에 대 한 설명, cmdlet의 매개 변수에 대 한 설명, cmdlet의 사용 예 등이 포함 됩니다.

## <a name="code-guidelines"></a>코드 지침

Cmdlet 및 기타 cmdlet을 사용 하는 것과 일관 된 사용자 환경을 보장 하기 위해 cmdlet을 코딩 하는 경우 다음 지침을 따라야 합니다. 사용자의 상황에 적용 되는 코드 지침을 찾았으면 유사한 지침에 대 한 디자인 지침을 확인 해야 합니다.

### <a name="coding-parameters-sc01"></a>매개 변수 코딩 (SC01)

**매개 변수** 특성을 사용 하 여 데코레이팅된 cmdlet 클래스의 public 속성을 선언 하 여 매개 변수를 정의 합니다. 매개 변수는 cmdlet에 대해 파생 된 .NET Framework 클래스의 정적 멤버일 필요가 없습니다. **매개 변수** 특성을 선언 하는 방법에 대 한 자세한 내용은 [매개 변수 특성 선언](./parameter-attribute-declaration.md)을 참조 하세요.

#### <a name="support-windows-powershell-paths"></a>Windows PowerShell 경로 지원

Windows PowerShell 경로는 네임 스페이스에 대 한 액세스를 정규화 하는 메커니즘입니다. Cmdlet의 매개 변수에 Windows PowerShell 경로를 할당 하면 사용자는 특정 경로에 대 한 바로 가기 역할을 하는 사용자 지정 "드라이브"를 정의할 수 있습니다. 사용자가 이러한 드라이브를 지정 하는 경우 레지스트리의 데이터와 같은 저장 된 데이터를 일관 된 방식으로 사용할 수 있습니다.

사용자가 cmdlet에서 파일 또는 데이터 원본을 지정할 수 있도록 허용 하는 경우 [system.string](/dotnet/api/System.String)형식의 매개 변수를 정의 해야 합니다. 둘 이상의 드라이브가 지원 되는 경우 형식은 배열 이어야 합니다. 매개 변수의 이름은 `Path` 이며 별칭을 사용 합니다 `PSPath` . 또한 `Path` 매개 변수는 와일드 카드 문자를 지원 해야 합니다. 와일드 카드 문자를 지원 하지 않아도 되는 경우 `LiteralPath` 매개 변수를 정의 합니다.

Cmdlet에서 읽기 또는 쓰기 데이터를 파일로 사용 해야 하는 경우 cmdlet은 Windows PowerShell 경로 입력을 수락 해야 하며, cmdlet은 [Sessionstate](/dotnet/api/System.Management.Automation.SessionState.Path) 속성을 사용 하 여 windows powershell 경로를 파일 시스템에서 인식 하는 경로로 변환 해야 합니다. 특정 메커니즘에는 다음과 같은 메서드가 포함 됩니다.

- [PSCmdlet. GetResolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PSCmdlet.GetResolvedProviderPathFromPSPath)

- [PSCmdlet. GetUnresolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PSCmdlet.GetUnresolvedProviderPathFromPSPath)

- [GetResolvedProviderPathFromPSPath (영문)](/dotnet/api/System.Management.Automation.PathIntrinsics.GetResolvedProviderPathFromPSPath)

- [GetUnresolvedProviderPathFromPSPath (영문)](/dotnet/api/System.Management.Automation.PathIntrinsics.GetUnresolvedProviderPathFromPSPath)

Cmdlet에서 읽기 또는 쓰기 데이터를 파일 대신 문자열 집합만 사용 하는 경우 cmdlet은 공급자 콘텐츠 정보 ( `Content` 멤버)를 사용 하 여 읽고 써야 합니다. 이 정보는 [InvokeProvider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.InvokeProvider) 속성에서 가져온 것이 고, 이러한 메커니즘을 통해 다른 데이터 저장소에서 데이터 읽기 및 쓰기에 참여할 수 있습니다.

#### <a name="support-wildcard-characters"></a>와일드 카드 문자 지원

가능 하면 cmdlet은 와일드 카드 문자를 지원 해야 합니다. Cmdlet의 여러 위치에서 와일드 카드 문자를 지원 합니다. 특히 매개 변수가 개체 집합에서 하나의 개체를 식별 하는 문자열을 사용 하는 경우에는 특히 그렇습니다. 예를 들어 [Stopproc 자습서](./stopproc-tutorial.md) 의 샘플 **Stop proc** cmdlet은 `Name` 프로세스 이름을 나타내는 문자열을 처리 하는 매개 변수를 정의 합니다. 이 매개 변수는 사용자가 중지할 프로세스를 쉽게 지정할 수 있도록 와일드 카드 문자를 지원 합니다.

와일드 카드 문자 지원을 사용할 수 있는 경우 일반적으로 cmdlet 작업에서 배열을 생성 합니다. 경우에 따라 사용자가 한 번에 하나의 항목만 사용할 수 있기 때문에 배열을 지 원하는 것은 적절 하지 않습니다. 예를 들어, 사용자가 단일 위치만 설정 하므로 [집합 위치](/powershell/module/Microsoft.PowerShell.Management/Set-Location) cmdlet은 배열을 지원할 필요가 없습니다. 이 인스턴스에서 cmdlet은 여전히 와일드 카드 문자를 지원 하지만 단일 위치에 대해 해상도를 강제 적용 합니다.

와일드 카드 문자 패턴에 대 한 자세한 내용은 [Cmdlet 매개 변수에서 와일드 카드 문자 지원](./supporting-wildcard-characters-in-cmdlet-parameters.md)을 참조 하세요.

#### <a name="defining-objects"></a>개체 정의

이 섹션에는 cmdlet에 대 한 개체를 정의 하 고 기존 개체를 확장 하기 위한 지침이 포함 되어 있습니다.

##### <a name="define-standard-members"></a>표준 멤버 정의

표준 멤버를 정의 하 여 사용자 지정 Types.ps1xml 파일의 개체 유형을 확장 합니다 (Windows PowerShell Types.ps1xml 파일을 템플릿으로 사용). 표준 멤버는 이름이 PSStandardMembers 인 노드에 의해 정의 됩니다. 이러한 정의를 통해 다른 cmdlet 및 Windows PowerShell 런타임은 일관 된 방식으로 개체를 사용할 수 있습니다.

##### <a name="define-objectmembers-to-be-used-as-parameters"></a>매개 변수로 사용할 ObjectMembers 정의

Cmdlet에 대 한 개체를 디자인 하는 경우 해당 멤버가 해당 멤버를 사용 하는 cmdlet의 매개 변수에 직접 매핑되는지 확인 합니다. 이 매핑을 사용 하면 개체를 파이프라인으로 쉽게 보내고 하나의 cmdlet에서 다른 cmdlet으로 전달할 수 있습니다.

Cmdlet에서 반환 되는 기존 .NET Framework 개체에는 스크립트 개발자 또는 사용자에 게 필요한 몇 가지 중요 한 멤버나 편리한 멤버가 종종 있습니다. 이러한 누락 된 멤버는 개체를 파이프라인으로 올바르게 전달할 수 있도록 올바른 멤버 이름을 표시 하 고 만드는 데 특히 중요할 수 있습니다. 사용자 지정 Types.ps1xml 파일을 만들어 이러한 필수 멤버를 문서화 합니다. 이 파일을 만들 때 *<Your_Product_Name>*.Types.ps1xml 명명 규칙을 따르는 것이 좋습니다.

예를 들어, `Mode` 스크립트 속성을 [system.object](/dotnet/api/System.IO.FileInfo) 형식에 추가 하 여 파일의 특성을 보다 명확 하 게 표시할 수 있습니다. 또한 `Count` alias 속성을 system.string 형식에 추가 하 여 [System.Array](/dotnet/api/System.Array) 해당 속성 이름을 일관 되 게 사용할 수 있습니다 (대신 `Length` ).

##### <a name="implement-the-icomparable-interface"></a>IComparable 인터페이스 구현

모든 출력 개체에 대해 [system.object](/dotnet/api/System.IComparable) 인터페이스를 구현 합니다. 이렇게 하면 출력 개체를 다양 한 정렬 및 분석 cmdlet으로 쉽게 파이프 할 수 있습니다.

##### <a name="update-display-information"></a>표시 정보 업데이트

개체에 대 한 디스플레이가 예상 결과를 제공 하지 않는 경우 *\<YourProductName>* 해당 개체에 대 한 사용자 지정.Format.ps1xml 파일을 만듭니다.

### <a name="support-well-defined-pipeline-input-sc02"></a>잘 정의 된 파이프라인 입력 지원 (SC02)

#### <a name="implement-for-the-middle-of-a-pipeline"></a>파이프라인 중간에 대해를 구현 합니다.

파이프라인 중간에서 호출 될 것으로 가정 하는 cmdlet을 구현 합니다. 즉, 다른 cmdlet은 해당 입력을 생성 하거나 해당 출력을 사용 합니다. 예를 들어 `Get-Process` cmdlet이 데이터를 생성 하기 때문에 파이프라인의 첫 번째 cmdlet 으로만 사용 된다고 가정할 수 있습니다. 그러나이 cmdlet은 파이프라인 중간에 맞게 설계 되었으므로이 cmdlet은 파이프라인의 이전 cmdlet 또는 데이터에서 검색할 프로세스를 지정할 수 있도록 합니다.

#### <a name="support-input-from-the-pipeline"></a>파이프라인의 입력 지원

Cmdlet에 대해 설정 된 각 매개 변수에서 파이프라인의 입력을 지 원하는 매개 변수를 하나 이상 포함 합니다. 파이프라인 입력 지원을 통해 사용자는 데이터 나 개체를 검색 하 고, 올바른 매개 변수 집합으로 전송 하 고, 결과를 cmdlet에 직접 전달할 수 있습니다.

매개 **변수** 는 `ValueFromPipeline` `ValueFromPipelineByPropertyName` 해당 선언에 키워드, 키워드 특성 또는 두 키워드를 모두 포함 하는 경우 파이프라인의 입력을 허용 합니다. 매개 변수 집합의 매개 변수가 또는 키워드를 지원 하지 않는 경우 `ValueFromPipeline` `ValueFromPipelineByPropertyName` cmdlet은 파이프라인 입력을 무시 하기 때문에 다른 cmdlet 뒤에 의미를 가질 수 없습니다.

#### <a name="support-the-processrecord-method"></a>ProcessRecord 메서드 지원

파이프라인에서 위의 cmdlet의 모든 레코드를 수락 하려면 cmdlet이 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드를 구현 해야 합니다. Windows PowerShell은 cmdlet에 전송 된 모든 레코드에 대해이 메서드를 여러 번 호출 합니다.

### <a name="write-single-records-to-the-pipeline-sc03"></a>파이프라인에 단일 레코드 쓰기 (SC03)

Cmdlet에서 개체를 반환 하는 경우 cmdlet은 생성 되는 즉시 개체를 작성 해야 합니다. 이 cmdlet은 결합 된 배열로 버퍼링 하기 위해 해당 변수를 포함 해서는 안 됩니다. 그러면 개체를 입력으로 수신 하는 cmdlet이 출력 개체를 지연 없이 처리, 표시 또는 처리 하 고 표시할 수 있습니다. 한 번에 하나씩 출력 개체를 생성 하는 cmdlet은 [WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 메서드를 호출 해야 합니다. 출력 개체를 일괄 처리로 생성 하는 cmdlet (예: 기본 API가 출력 개체의 배열을 반환 하는 경우)은 두 번째 매개 변수를로 설정 하 여 [WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 메서드를 호출 해야 합니다 `true` .

### <a name="make-cmdlets-case-insensitive-and-case-preserving-sc04"></a>Cmdlet에서 대/소문자를 구분 하지 않고 대/소문자를 유지 합니다 (SC04).

기본적으로 Windows PowerShell 자체는 대/소문자를 구분 하지 않습니다. 그러나 많은 기존 시스템을 처리 하기 때문에 Windows PowerShell은 작업 및 호환성을 위해 대/소문자를 유지 합니다. 즉, 문자를 대문자로 제공 하는 경우 Windows PowerShell은 해당 문자를 대문자로 유지 합니다. 시스템이 제대로 작동 하려면 cmdlet이이 규칙을 따라야 합니다. 가능 하면 대/소문자를 구분 하지 않는 방식으로 작동 해야 합니다. 그러나 나중에 명령이 나 파이프라인에서 발생 하는 cmdlet에 대 한 원래 사례를 유지 해야 합니다.

## <a name="see-also"></a>참고 항목

[필수 개발 지침](./required-development-guidelines.md)

[권장되는 개발 지침](./advisory-development-guidelines.md)

[Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)](./writing-a-windows-powershell-cmdlet.md)
