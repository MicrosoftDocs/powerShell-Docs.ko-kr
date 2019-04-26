---
title: 와일드 카드 식 별칭을 추가 하 고 Cmdlet 매개 변수를 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: db664e589f625855b5a33a02c522d6b238ad2810
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075259"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a>Cmdlet 매개 변수에 별칭, 와일드카드 확장 및 도움말 추가

이 섹션에서는 와일드 카드 식 별칭을 추가 하는 방법을 설명 하 고 도움말 메시지 중지 Proc cmdlet의 매개 변수를 (에서 설명한 [시스템을 수정 하는 Cmdlet를 만들](./creating-a-cmdlet-that-modifies-the-system.md)).

이 중지 Proc cmdlet Get-proc cmdlet을 사용 하 여 검색 되는 프로세스를 중지 하려고 합니다. (에서 설명한 [첫 번째 Cmdlet 만들기](./creating-a-cmdlet-without-parameters.md)).

이 섹션의에서 항목에서는 다음과 같습니다.

- [Cmdlet을 정의합니다.](#Defining-the-Cmdlet)

- [시스템 수정에 대 한 매개 변수를 정의합니다.](#Defining-Parameters-for-System-Modification)

- [매개 변수 별칭을 정의합니다.](#Defining-a-Parameter-Alias)

- [매개 변수에 대 한 도움말 작성](#Creating-Help-for-Parameters)

- [입력 처리 메서드를 재정의 합니다.](#Overriding-an-Input-Processing-Method)

- [와일드 카드 확장 지원](#Supporting-Wildcard-Expansion)

- [코드 샘플](#Defining-a-Parameter-Alias)

- [개체 유형 정의 및 서식 지정](#Define-Object-Types-and-Formatting)

- [Cmdlet은 빌드](#Building-the-Cmdlet)

- [테스트 Cmdlet](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a>Cmdlet을 정의합니다.

Cmdlet 만드는 첫 번째 단계는 항상 cmdlet 이름과 cmdlet을 구현 하는.NET 클래스를 선언 합니다. 시스템을 변경 하는 cmdlet를 작성 하는 때문에 적절 하 게 명명 해야 합니다. 이 cmdlet은 시스템 프로세스를 중지, 정의한 동사 "Stop"을 사용 합니다 [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) 클래스를 "Proc" 프로세스를 나타내려면 명사를 사용 하 여 합니다. 승인 된 cmdlet 동사에 대 한 자세한 내용은 참조 하세요. [Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md)합니다.

다음 코드는이 중지 Proc cmdlet에 대 한 클래스 정의입니다.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>시스템 수정에 대 한 매개 변수를 정의합니다.

Cmdlet는 지원 시스템 수정 및 사용자 피드백 매개 변수를 정의 해야 합니다. Cmdlet을 정의 해야는 `Name` 매개 변수 또는 해당 cmdlet은 식별자의 일종으로 시스템을 수정할 수 있도록 합니다. 또한, cmdlet 정의 해야 합니다 `Force` 및 `PassThru` 매개 변수입니다. 이러한 매개 변수에 대 한 자세한 내용은 참조 하세요. [시스템을 수정 하는 Cmdlet를 만들](./creating-a-cmdlet-that-modifies-the-system.md)합니다.

## <a name="defining-a-parameter-alias"></a>매개 변수 별칭을 정의합니다.

대체 이름 또는 cmdlet 매개 변수에 대해 잘 정의 된 문자 1 또는 2 자의 짧은 이름을 매개 변수 별칭을 수 있습니다. 두 경우 모두 명령줄에서 사용자 입력을 단순화 하기 위해 별칭을 사용 하 여 목표가입니다. Windows PowerShell을 통해 매개 변수 별칭을 지원 합니다 [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) 의 선언 구문은 [Alias()]를 사용 하는 특성입니다.

다음 코드를 별칭은 추가 하는 방법을 보여 줍니다는 `Name` 매개 변수입니다.

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
[Alias("ProcessName")]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

사용 하는 것 외에도 합니다 [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) 특성에는 Windows PowerShell 런타임에 수행 부분 이름에 일치 하는 별칭 없음 지정 된 경우에 합니다. 예를 들어 cmdlet에는 `FileName` 매개 변수 이며로 시작 하는 유일한 매개 변수인 `F`, 사용자가 입력할 수 `Filename`, `Filenam`, `File`, `Fi`, 또는 `F` 여전히 인식 하 고는 항목으로는 `FileName` 매개 변수입니다.

## <a name="creating-help-for-parameters"></a>매개 변수에 대 한 도움말 작성

Windows PowerShell을 사용 하면 cmdlet 매개 변수에 대 한 도움말을 만들 수 있습니다. 시스템 수정 및 사용자 피드백에 사용 되는 매개 변수에 대해이 작업을 수행 합니다. 도움말을 지원 하려면 각 매개 변수에 대해 설정할 수 있습니다 합니다 `HelpMessage` 특성의 키워드를 [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) 특성 선언 합니다. 이 키워드는 매개 변수를 사용 하 여 도움이 필요 하면 사용자에 게 표시할 텍스트를 정의 합니다. 설정할 수도 있습니다는 `HelpMessageBaseName` 키워드를 사용 하는 메시지에 사용할 리소스의 기본 이름입니다. 이 키워드를 사용 하도록 설정한 경우 설정 해야 합니다 `HelpMessageResourceId` 리소스 식별자를 지정 하는 키워드입니다.

이 중지 Proc cmdlet에서 다음 코드를 정의 합니다 `HelpMessage` 특성에 대 한 키워드는 `Name` 매개 변수입니다.

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
```

## <a name="overriding-an-input-processing-method"></a>입력 처리 메서드를 재정의 합니다.

Cmdlet는 입력 처리 메서드를 재정의 해야, 가장 일반적인 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)합니다. 시스템을 수정할 때 cmdlet을 호출 해야 합니다 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 하 고 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 사용자를 허용 하는 방법 변경 되기 전에 피드백을 제공 합니다. 이러한 방법에 대 한 자세한 내용은 참조 하세요. [시스템을 수정 하는 Cmdlet를 만들](./creating-a-cmdlet-that-modifies-the-system.md)합니다.

## <a name="supporting-wildcard-expansion"></a>와일드 카드 확장 지원

여러 개체의 선택에 허용 하려면 cmdlet에 사용할 수는 [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) 하 고 [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) 제공 하는 클래스 입력 매개 변수에 대 한 와일드 카드 확장 지원 합니다. 와일드 카드 패턴의 예는 lsa * \*.txt 및 [a-c]\*합니다. 패턴을 그대로 사용 해야 하는 문자를 포함 하는 경우에 이스케이프 문자로 역따옴표 (')를 사용 합니다.

파일 이름과 경로 와일드 카드 확장은 cmdlet을 여러 개체의 선택이 필요한 경우 지원에 대 한 경로 입력을 허용 하도록 할 수는 있는 일반적인 시나리오의 예입니다. 현재 폴더에 있는 모든 파일을 보려면 사용자가 있는 파일 시스템의 일반적인 사례 이며

드물게만 사용자 지정된 와일드 카드 패턴 일치 하는 구현을 해야 합니다. 이 경우 cmdlet 전체 POSIX 1003.2, 와일드 카드 확장에 대 한 3.13 사양 또는 다음 단순화 된 하위 집합을 지원 해야 합니다.

- **물음표 (?)입니다.** 지정된 된 위치에 문자를 찾습니다.

- **별표 (\*).** 지정된 된 위치에서 시작 하는 0 개 이상의 문자와 일치 합니다.

- **대괄호 ()를 엽니다.** 문자 또는 문자 범위를 포함할 수 있는 패턴 대괄호 식을 소개 합니다. 범위가 필요한 경우 하이픈 (-) 범위를 나타내기 위해 사용 됩니다.

- **닫는 대괄호 (]).** 대괄호 식 패턴을 종료합니다.

- **백 견적 이스케이프 문자 (').** 다음 문자가 문자 그대로 해석 되도록 나타냅니다. 프로그래밍 방식으로 지정) (아닌 명령줄에서 백 따옴표 문자를 지정할 때 백 따옴표 이스케이프 문자를 지정 해야 합니다 두 번에 유의 합니다.

> [!NOTE]
> 와일드 카드 패턴에 대 한 자세한 내용은 참조 하세요. [Cmdlet 매개 변수에서 와일드 카드를 지 원하는](./supporting-wildcard-characters-in-cmdlet-parameters.md)합니다.

다음 코드에서는 와일드 카드 옵션을 설정 하 고 확인 하는 데 사용 되는 와일드 카드 패턴을 정의 하는 방법을 보여 줍니다.는 `Name` 이 cmdlet에 대 한 매개 변수입니다.

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

다음 코드는 프로세스 이름에 정의 된 와일드 카드 패턴 일치 하는지 여부를 테스트 하는 방법을 보여 줍니다. 이 경우 프로세스 이름 패턴 일치 하지 않는 경우 cmdlet에서 계속 다음 프로세스 이름을 가져오려면 알 수 있습니다.

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a>코드 예제

전체 C# 코드 샘플을 참조 하십시오 [StopProcessSample03 샘플](./stopprocesssample03-sample.md)합니다.

## <a name="define-object-types-and-formatting"></a>개체 유형 및 서식을 정의합니다

Windows PowerShell.Net 개체를 사용 하 여 cmdlet 간에 정보를 전달 합니다. 따라서 cmdlet는 고유한 형식을 정의 해야 합니다. 또는 cmdlet을 다른 cmdlet에서 제공 하는 기존 형식을 확장 해야 할 수 있습니다. 새 형식 정의 또는 기존 형식을 확장 하는 방법에 대 한 자세한 내용은 참조 하세요. [확장 개체 형식 및 서식](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)합니다.

## <a name="building-the-cmdlet"></a>Cmdlet은 빌드

Cmdlet를 구현한 후 등록 해야 Windows PowerShell을 사용 하 여 Windows PowerShell 스냅인을 통해. Cmdlet을 등록 하는 방법에 대 한 자세한 내용은 참조 하세요. [등록 Cmdlet, 공급자 및 응용 프로그램을 호스트 하는 방법을](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)합니다.

## <a name="testing-the-cmdlet"></a>테스트 Cmdlet

Windows PowerShell cmdlet에 등록 하는 경우 명령줄에서 실행 하 여 테스트할 수 있습니다. 샘플 프로시저 중지 cmdlet를 테스트해 보겠습니다. 명령줄에서 cmdlet을 사용 하는 방법에 대 한 자세한 내용은 참조는 [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)합니다.

- Windows PowerShell을 시작 및 중지 프로시저의 ProcessName 별칭을 사용 하는 프로세스를 중지 하는 데는 `Name` 매개 변수입니다.

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

다음과 같은 출력이 표시 됩니다.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- 명령줄에서 다음 항목을 확인 합니다. Name 매개 변수는 필수 이므로에 대 한 메시지가 표시 됩니다. 입력 "?" 매개 변수를 사용 하 여 연결 된 도움말 텍스트를 표시 합니다.

    ```powershell
    PS> stop-proc
    ```

다음과 같은 출력이 표시 됩니다.

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- 와일드 카드 패턴과 일치 하는 모든 프로세스를 중지 하려면 다음 항목을 확인 하 고 있습니다. "* 참고\*"입니다. 메시지가 표시 되는 패턴과 일치 하는 각 프로세스를 중지 하기 전에 합니다.

    ```powershell
    PS> stop-proc -Name *note*
    ```

다음과 같은 출력이 표시 됩니다.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

다음과 같은 출력이 표시 됩니다.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

다음과 같은 출력이 표시 됩니다.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>참고 항목

[시스템을 수정 하는 Cmdlet 만들기](./creating-a-cmdlet-that-modifies-the-system.md)

[Windows PowerShell Cmdlet을 만드는 방법](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[확장 개체 형식 및 서식 지정](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Cmdlet, 공급자, 등록 및 응용 프로그램을 호스트 하는 방법](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Cmdlet 매개 변수에서 와일드 카드 지원](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
