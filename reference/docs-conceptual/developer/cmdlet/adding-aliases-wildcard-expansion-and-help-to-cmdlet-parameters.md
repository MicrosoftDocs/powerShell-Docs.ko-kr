---
title: 별칭, 와일드 카드 확장 및 Cmdlet 매개 변수에 대 한 도움말 추가 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 244c50c73972c2760e0029c7fa4f4b5764b066da
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774969"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a>Cmdlet 매개 변수에 별칭, 와일드카드 확장 및 도움말 추가

이 섹션에서는 진단, 와일드 카드 확장 및 도움말 메시지를 Stop Proc cmdlet의 매개 변수에 추가 하는 방법에 대해 설명 합니다 ( [시스템을 수정 하는 Cmdlet 만들기](./creating-a-cmdlet-that-modifies-the-system.md)참조).

이 Stop Proc cmdlet은 [첫 번째 Cmdlet 만들기](./creating-a-cmdlet-without-parameters.md)에 설명 된 것 처럼 Get-proc cmdlet을 사용 하 여 검색 된 프로세스를 중지 하려고 시도 합니다.

## <a name="defining-the-cmdlet"></a>Cmdlet 정의

Cmdlet을 만드는 첫 번째 단계는 항상 cmdlet의 이름을 지정 하 고 cmdlet을 구현 하는 .NET 클래스를 선언 하는 것입니다. 시스템을 변경 하는 cmdlet을 작성 하 고 있으므로 이름을 적절 하 게 지정 해야 합니다. 이 cmdlet은 시스템 프로세스를 중지 하므로 [Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) 클래스에 정의 된 동사 "Stop"을 사용 하 여 프로세스를 나타내는 명사 "Proc"를 사용 합니다. 승인 된 cmdlet 동사에 대 한 자세한 내용은 [Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md)을 참조 하세요.

다음 코드는이 Stop Proc cmdlet에 대 한 클래스 정의입니다.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>시스템 수정 매개 변수 정의

Cmdlet은 시스템 수정과 사용자 피드백을 지 원하는 매개 변수를 정의 해야 합니다. Cmdlet은 매개 변수를 정의 해야 합니다 `Name` . 이렇게 하면 cmdlet이 일종의 식별자로 시스템을 수정할 수 있습니다. 또한 cmdlet은 `Force` 및 매개 변수를 정의 해야 합니다 `PassThru` . 이러한 매개 변수에 대 한 자세한 내용은 [시스템을 수정 하는 Cmdlet 만들기](./creating-a-cmdlet-that-modifies-the-system.md)를 참조 하세요.

## <a name="defining-a-parameter-alias"></a>매개 변수 별칭 정의

매개 변수 별칭은 cmdlet 매개 변수에 대 한 대체 이름 또는 잘 정의 된 1 자 또는 2 자 짧은 이름일 수 있습니다. 두 경우 모두 별칭을 사용 하는 것은 명령줄에서 사용자 입력을 단순화 하는 것입니다. Windows PowerShell은 선언 구문 [Alias ()]를 사용 하는 [Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) 특성을 통해 매개 변수 별칭을 지원 합니다.

다음 코드는 매개 변수에 별칭을 추가 하는 방법을 보여 줍니다 `Name` .

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

[Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) 특성을 사용 하는 것 외에도 Windows PowerShell 런타임은 별칭이 지정 되지 않은 경우에도 부분 이름 일치를 수행 합니다. 예를 들어 cmdlet에 `FileName` 매개 변수가 있고로 시작 하는 유일한 매개 변수인 경우 `F` 사용자는,,, 또는를 입력 하 여 해당 `Filename` `Filenam` 항목을 `File` `Fi` `F` `FileName` 매개 변수로 계속 인식할 수 있습니다.

## <a name="creating-help-for-parameters"></a>매개 변수에 대 한 도움말 만들기

Windows PowerShell을 사용 하 여 cmdlet 매개 변수에 대 한 도움말을 만들 수 있습니다. 시스템 수정 및 사용자 의견에 사용 되는 매개 변수에 대해이 작업을 수행 합니다. 도움말을 지 원하는 각 매개 변수에 대해 `HelpMessage` [system.object](/dotnet/api/System.Management.Automation.ParameterAttribute) 특성 선언에서 attribute 키워드를 설정할 수 있습니다. 이 키워드는 매개 변수를 사용할 때 사용자에 게 표시 되는 텍스트를 정의 합니다. 또한 키워드를 설정 `HelpMessageBaseName` 하 여 메시지에 사용할 리소스의 기본 이름을 식별할 수 있습니다. 이 키워드를 설정 하는 경우 키워드를 설정 `HelpMessageResourceId` 하 여 리소스 식별자도 지정 해야 합니다.

이 Stop Proc cmdlet의 다음 코드는 `HelpMessage` 매개 변수에 대 한 attribute 키워드를 정의 합니다 `Name` .

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

## <a name="overriding-an-input-processing-method"></a>입력 처리 메서드 재정의

Cmdlet은 입력 처리 메서드를 재정의 해야 합니다. 대부분은 일반적으로 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)입니다. 시스템을 수정 하는 경우 cmdlet은 변경 전에 사용자에 게 피드백을 제공할 수 있도록 [system.web](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) .. n a m a. a m [a.](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 이러한 메서드에 대 한 자세한 내용은 시스템을 [수정 하는 Cmdlet 만들기](./creating-a-cmdlet-that-modifies-the-system.md)를 참조 하세요.

## <a name="supporting-wildcard-expansion"></a>와일드 카드 확장 지원

여러 개체를 선택할 수 있도록 cmdlet은 [Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) 및 [Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) 클래스를 사용 하 여 매개 변수 입력에 대 한 와일드 카드 확장 지원을 제공할 수 있습니다. 와일드 카드 패턴의 예로는 lsa *, \* .txt 및 [a-c]가 있습니다 \* . 패턴에 리터럴로 사용 해야 하는 문자가 포함 된 경우에는 백슬래시 문자 (')를 이스케이프 문자로 사용 합니다.

파일 및 경로 이름의 와일드 카드 확장은 여러 개체를 선택 해야 하는 경우 cmdlet이 경로 입력 지원을 허용 하려는 일반적인 시나리오의 예입니다. 일반적인 경우는 사용자가 현재 폴더에 있는 모든 파일을 확인 하려는 파일 시스템에 있습니다.

거의 사용자 지정 된 와일드 카드 패턴 일치 구현이 필요 합니다. 이 경우 cmdlet은 와일드 카드 확장 또는 다음 단순화 된 하위 집합에 대 한 전체 POSIX 1003.2, 3.13 사양을 지원 해야 합니다.

- **물음표 (?)를 표시 합니다.** 지정 된 위치에 있는 모든 문자를 찾습니다.

- **별표 ( \* ).** 지정 된 위치에서 시작 하 여 0 개 이상의 문자를 찾습니다.

- **여는 대괄호 ([).** 문자 또는 문자 범위를 포함할 수 있는 패턴 대괄호 식을 소개 합니다. 범위가 필요한 경우 범위를 나타내는 데 하이픈 (-)이 사용 됩니다.

- **닫는 대괄호 (])입니다.** 패턴 대괄호 식을 끝냅니다.

- **백슬래시 이스케이프 문자 (')입니다.** 는 다음 문자를 문자 그대로 사용 함을 나타냅니다. 명령줄에서 백슬래시 문자를 지정 하는 경우 (프로그래밍 방식으로 지정 하는 것과 반대), 백슬래시 이스케이프 문자를 두 번 지정 해야 합니다.

> [!NOTE]
> 와일드 카드 패턴에 대 한 자세한 내용은 [Cmdlet 매개 변수에서 와일드 카드 지원](./supporting-wildcard-characters-in-cmdlet-parameters.md)을 참조 하세요.

다음 코드에서는 와일드 카드 옵션을 설정 하 고 `Name` 이 cmdlet의 매개 변수를 확인 하는 데 사용 되는 와일드 카드 패턴을 정의 하는 방법을 보여 줍니다.

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

다음 코드에서는 프로세스 이름이 정의 된 와일드 카드 패턴과 일치 하는지 여부를 테스트 하는 방법을 보여 줍니다. 이 경우 프로세스 이름이 패턴과 일치 하지 않으면 cmdlet은 계속 해 서 다음 프로세스 이름을 가져옵니다.

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a>코드 예제

전체 c # 샘플 코드는 [StopProcessSample03 샘플](./stopprocesssample03-sample.md)을 참조 하세요.

## <a name="define-object-types-and-formatting"></a>개체 형식 및 서식 정의

Windows PowerShell은 .Net 개체를 사용 하 여 cmdlet 간에 정보를 전달 합니다. 따라서 cmdlet은 자체 형식을 정의 해야 할 수도 있고, 다른 cmdlet에서 제공 하는 기존 형식을 cmdlet에서 확장 해야 할 수도 있습니다. 새 형식을 정의 하거나 기존 형식을 확장 하는 방법에 대 한 자세한 내용은 [개체 형식 확장 및 서식 지정](/previous-versions//ms714665(v=vs.85))을 참조 하세요.

## <a name="building-the-cmdlet"></a>Cmdlet 빌드

Cmdlet을 구현한 후 Windows PowerShell 스냅인을 통해 Windows PowerShell에 등록 해야 합니다. Cmdlet을 등록 하는 방법에 대 한 자세한 내용은 [cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions//ms714644(v=vs.85))을 참조 하세요.

## <a name="testing-the-cmdlet"></a>Cmdlet 테스트

Windows PowerShell을 사용 하 여 cmdlet을 등록 한 경우 명령줄에서 실행 하 여 테스트할 수 있습니다. 샘플 중지-프로시저 cmdlet을 테스트해 보겠습니다. 명령줄에서 cmdlet을 사용 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 시작](/powershell/scripting/getting-started/getting-started-with-windows-powershell)을 참조 하세요.

- Windows PowerShell을 시작 하 고 ProcessName 별칭을 사용 하 여 매개 변수에 대 한 프로세스를 중지 하려면 Stop Proc를 사용 `Name` 합니다.

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

    다음 출력이 표시됩니다.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- 명령줄에 다음 항목을 만듭니다. Name 매개 변수는 필수 매개 변수 이므로 입력 하 라는 메시지가 표시 됩니다. "!?"를 입력 합니다. 매개 변수와 연결 된 도움말 텍스트를 표시 합니다.

    ```powershell
    PS> stop-proc
    ```

    다음 출력이 표시됩니다.

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- 이제 와일드 카드 패턴 "* note"와 일치 하는 모든 프로세스를 중지 하기 위해 다음 항목을 만듭니다 \* . 패턴과 일치 하는 각 프로세스를 중지 하기 전에 메시지가 표시 됩니다.

    ```powershell
    PS> stop-proc -Name *note*
    ```

    다음 출력이 표시됩니다.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

    다음 출력이 표시됩니다.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

    다음 출력이 표시됩니다.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>참고 항목

[시스템을 수정 하는 Cmdlet을 만듭니다.](./creating-a-cmdlet-that-modifies-the-system.md)

[Windows PowerShell Cmdlet을 만드는 방법](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[개체 형식 및 서식 확장](/previous-versions//ms714665(v=vs.85))

[Cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions//ms714644(v=vs.85))

[Cmdlet 매개 변수에 와일드 카드 지원](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
