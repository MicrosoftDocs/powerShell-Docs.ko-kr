---
ms.date: 05/22/2020
keywords: powershell,cmdlet
title: PowerShell이란?
description: 이 문서에서는 PowerShell 스크립팅 환경 및 해당 기능을 소개합니다.
ms.openlocfilehash: 91fc580af9a3adf43a24c40b4aaf3f1843882705
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500779"
---
# <a name="what-is-powershell"></a>PowerShell이란?

PowerShell은 명령줄 셸 및 스크립팅 언어로 구성된 플랫폼 간 작업 자동화 및 구성 관리 프레임워크입니다. 텍스트를 받아들이고 반환하는 대부분의 셸과는 달리 PowerShell은 .NET CLR(공용 언어 런타임)을 기반으로 하여 .NET 개체를 받아들이고 반환합니다. 이러한 근본적인 변화는 자동화를 위한 완전히 새로운 도구와 방법을 제공합니다.

<!-- removing images until we can get replacements
:::row:::
   :::column span="":::
      Windows
      [![PowerShell on Windows](media/overview/windows-desktop-660.gif)](media/overview/windows-desktop.gif#lightbox)
      [Install on Windows](install/installing-powershell-core-on-windows.md)
   :::column-end:::
   :::column span="":::
      Linux
      [![PowerShell on Linux](media/overview/linux-desktop-660.gif)](media/overview/linux-desktop.gif#lightbox)
      [Install on Linux](install/installing-powershell-core-on-linux.md)
   :::column-end:::
   :::column span="":::
      macOS
      [![PowerShell on macOS](media/overview/macos-desktop-660.gif)](media/overview/macos-desktop.gif#lightbox)
      [Install on macOS](install/installing-powershell-core-on-macos.md)
   :::column-end:::
:::row-end:::
-->

## <a name="output-is-object-based"></a>개체 기반의 출력

기존 명령줄 인터페이스와 달리 PowerShell cmdlet은 개체를 처리하도록 디자인되어 있습니다.
개체는 화면에 표시되는 문자열 이상의 의미를 갖는 구조화된 정보입니다. 명령 출력에는 필요할 때 사용할 수 있는 추가 정보가 항상 포함됩니다.

이전에 텍스트 처리 도구를 사용하여 데이터를 처리한 경우 PowerShell에서는 이러한 도구가 다르게 동작한다는 것을 알게 될 것입니다. 대부분의 경우 텍스트 처리 도구를 사용하여 특정 정보를 추출할 필요가 없습니다. 표준 PowerShell 개체 구문을 사용하여 데이터 부분에 직접 액세스할 수 있습니다.

## <a name="the-command-family-is-extensible"></a>확장 가능한 명령 패밀리

`cmd.exe`와 같은 인터페이스에서는 기본 제공 명령 세트를 직접 확장할 수 없습니다. `cmd.exe`에서 실행되는 외부 명령줄 도구를 만들 수 있습니다. 하지만 이러한 외부 도구에는 도움말 통합과 같은 서비스가 없습니다. `cmd.exe`는 이러한 외부 도구가 유효한 명령이라는 사실을 자동으로 알지 못합니다.

PowerShell의 명령을 _cmdlets_ 라고 합니다. 각 cmdlet을 개별적으로 사용할 수 있지만, 조합하여 복잡한 작업을 수행할 때 그 능력이 실현됩니다. 많은 셸과 마찬가지로, PowerShell을 통해 컴퓨터의 파일 시스템에 액세스할 수 있습니다. PowerShell ‘공급자’를 통해 레지스트리 및 인증서 스토리지와 같은 다른 데이터 스토리지를 파일 시스템처럼 쉽게 액세스할 수 있습니다.

컴파일된 코드 또는 스크립트를 사용하여 사용자 고유의 cmdlet 및 함수 모듈을 만들 수 있습니다. 모듈은 셸에 cmdlet 및 공급자를 추가할 수 있습니다. 또한 PowerShell은 UNIX 셸 스크립트 및 `cmd.exe` 배치 파일과 유사한 스크립트를 지원합니다.

## <a name="support-for-command-aliases"></a>명령 별칭 지원

PowerShell은 대체 이름으로 명령을 참조하도록 별칭을 지원합니다. 별칭은 다른 셸을 사용해 본 경험이 있는 사용자가 이미 알고 있는 일반적인 명령 이름을 PowerShell의 유사한 작업에 사용할 수 있도록 해줍니다.

별칭은 새 이름을 다른 명령과 연결합니다. 예를 들어 PowerShell에는 출력 창을 지우는 `Clear-Host`라는 내부 함수가 있습니다. 명령 프롬프트에서 `cls` 또는 `clear` 별칭을 입력할 수 있습니다. PowerShell은 이러한 별칭을 해석하고 `Clear-Host` 함수를 실행합니다.

이 기능은 사용자가 PowerShell을 익히는 데 도움이 됩니다. 첫째, 대부분의 `cmd.exe` 및 Unix 사용자는 이름으로 이미 알고 있는 대규모 명령 모음을 보유하게 됩니다. PowerShell의 해당 명령이 동일한 결과를 생성하지 않을 수 있습니다. 그러나 결과는 사용자가 PowerShell 명령 이름을 모르는 상태로 사용해도 될만큼 충분히 유사합니다. “머슬 메모리”는 새 명령 셸을 학습할 때 겪게 되는 또 다른 어려움입니다. 수년 동안 `cmd.exe`를 사용해왔다면 화면을 지우기 위해 반사적으로 `cls` 명령을 입력할 수 있을 것입니다. `Clear-Host`에 대한 별칭이 없으면, 오류 메시지가 수신되고 출력을 지우기 위해 어떻게 해야 할지 알 수 없을 것입니다.

## <a name="powershell-handles-console-input-and-display"></a>Powershell로 콘솔 입력 및 표시 처리

사용자가 명령을 입력하면 PowerShell은 항상 이 명령줄 입력을 직접 처리합니다. 또한 PowerShell은 화면에 표시되는 출력의 형식을 지정합니다. 이러한 차이점은 각 cmdlet에 대해 필요한 작업을 줄여주므로 중요합니다. 또한 사용자가 항상 어떤 cmdlet으로도 동일한 방식으로 작업할 수 있도록 합니다. 따라서 cmdlet 개발자는 명령줄 인수를 구문 분석하거나 출력 형식을 지정하기 위해 코드를 작성할 필요가 없습니다.

이전의 명령줄 도구는 도움말을 요청하고 표시하는 자체 구성을 갖습니다. 일부 명령줄 도구는 `/?`을 사용하여 도움말 표시를 트리거합니다. 다른 경우에는 `-?`, `/H` 또는 심지어 `//`를 사용합니다. 또한 일부 명령줄 도구는 콘솔 화면 대신 GUI 창에 도움말을 표시합니다. 사용자가 잘못된 매개 변수를 사용할 경우 이러한 도구는 사용자의 입력 내용을 무시하고 자동으로 작업을 실행할 수 있습니다.
PowerShell은 명령줄을 자동으로 구문 분석하고 처리하므로 `-?` 매개 변수는 항상 “이 명령에 대한 도움말 표시”를 의미합니다.

> [!NOTE]
> PowerShell에서 그래픽 애플리케이션을 실행하면 해당 애플리케이션의 창이 열립니다.
> PowerShell은 사용자가 제공하는 명령줄 입력이나 콘솔 창에 반환되는 애플리케이션 출력을 처리할 때만 개입합니다. 애플리케이션이 내부적으로 작업을 수행하는 방식에는 영향을 주지 않습니다.

## <a name="powershell-has-a-pipeline"></a>PowerShell에는 파이프라인이 있음

파이프라인은 명령줄 인터페이스에 사용되는 가장 중요한 개념이라고 할 수 있습니다. 적절히 사용하는 경우 파이프라인은 복잡한 명령을 사용할 필요를 줄여주고, 작업 흐름을 보다 쉽게 확인할 수 있도록 합니다. 파이프라인의 각 명령은 출력을 항목별로 다음 명령에 전달합니다. 따라서 명령이 한 번에 둘 이상의 항목을 처리할 필요가 없습니다. 그 결과 리소스 사용량이 줄어들고 출력이 바로 표시됩니다.

파이프라인에 사용되는 표기법은 다른 셸에 사용되는 표기법과 비슷합니다. 얼핏 보면 파이프라인이 PowerShell과 어떻게 다른지 명확하지 않을 수 있습니다. 화면에 텍스트가 표시되어 있는 경우에도 PowerShell은 명령 사이에 있는 텍스트가 아닌 개체를 파이프합니다.

예를 들어 `Out-Host` cmdlet을 사용하여 다른 명령의 출력을 페이지 단위로 표시하면 다음과 같이 일반 텍스트가 페이지 단위로 나뉘어져 화면에 표시된 것처럼 보입니다.

```powershell
Get-ChildItem | Out-Host -Paging
```

```Output
    Directory: /mnt/c/Git/PS-Docs/PowerShell-Docs/reference/7.0/Microsoft.PowerShell.Core

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d----          05/22/2020    08:30                About
-----          05/20/2020    14:36           9044 Add-History.md
-----          05/20/2020    14:36          12227 Clear-History.md
-----          05/20/2020    14:36           3566 Clear-Host.md
-----          05/20/2020    14:36          29087 Connect-PSSession.md
-----          05/20/2020    14:36           5705 Debug-Job.md
-----          05/20/2020    14:36           3515 Disable-ExperimentalFeature.md
-----          05/20/2020    14:36          25531 Disable-PSRemoting.md
-----          05/20/2020    14:36           7852 Disable-PSSessionConfiguration.md
-----          05/20/2020    14:36          25355 Disconnect-PSSession.md
-----          05/20/2020    14:36           3491 Enable-ExperimentalFeature.md
-----          05/20/2020    14:36          13310 Enable-PSRemoting.md
-----          05/20/2020    14:36           8401 Enable-PSSessionConfiguration.md
-----          05/20/2020    14:36           9531 Enter-PSHostProcess.md
...
<SPACE> next page; <CR> next line; Q quit
```

페이징을 사용하면 전체 페이지를 표시할 준비가 되면 처리가 `Out-Host` cmdlet으로 전송되므로 역시 CPU 사용률을 줄이는 데 효과가 있습니다. 파이프라인의 앞에 나오는 cmdlet은 출력의 다음 페이지를 사용할 수 있게 될 때까지 실행을 일시 중지합니다.

### <a name="objects-in-the-pipeline"></a>파이프라인의 개체

PowerShell에서 cmdlet을 실행하면 개체를 콘솔 창에 텍스트로 표시해야 하므로 텍스트 출력이 표시됩니다. 텍스트 출력에 출력되는 개체의 모든 속성이 표시되지는 않을 수 있습니다.

예를 들어 `Get-Location` cmdlet을 고려해보세요. 텍스트 출력은 `Get-Location`에서 반환된 개체의 완전한 표현이 아니라 정보의 요약입니다. 화면에 표시되는 데이터에 서식을 지정하는 프로세스에 따라 출력의 제목이 추가됩니다.

```powershell
Get-Location
```

```Output
Path
----
C:\
```

출력을 `Get-Member` cmdlet으로 파이프하면 `Get-Location`에서 반환된 개체에 대한 정보가 표시됩니다.

```powershell
Get-Location | Get-Member
```

```Output
   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Equals       Method     bool Equals(System.Object obj)
GetHashCode  Method     int GetHashCode()
GetType      Method     type GetType()
ToString     Method     string ToString()
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   string Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {get;}
ProviderPath Property   string ProviderPath {get;}
```

`Get-Location`는 현재 경로 및 기타 정보를 포함하는 **PathInfo** 개체를 반환합니다.

## <a name="built-in-help-system"></a>기본 제공 도움말 시스템

Unix `man` 페이지와 비슷하게 PowerShell에는 PowerShell 개념과 명령 구문을 설명하는 자세한 도움말 문서가 포함되어 있습니다. [Get-Help][] cmdlet을 사용하여 명령 프롬프트에서 이러한 도움말 문서를 표시하거나 PowerShell 온라인 설명서에서 이러한 문서의 가장 최근 업데이트 버전을 볼 수 있습니다.

## <a name="next-steps"></a>다음 단계

PowerShell에 대한 자세한 내용은 이 사이트의 **PowerShell 학습** 섹션을 참조하세요.

<!-- link references -->

[Get-Help]: /powershell/module/microsoft.powershell.core/Get-Help
