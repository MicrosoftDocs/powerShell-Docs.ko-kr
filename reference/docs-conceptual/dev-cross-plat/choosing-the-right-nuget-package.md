---
title: .NET 프로젝트에 적합한 PowerShell NuGet 패키지 선택
description: 각 PowerShell 릴리스로 게시된 실행 파일 패키지와 함께 PowerShell 팀은 NuGet에서 사용할 수 있는 여러 패키지도 유지 관리합니다. 해당 패키지는 .NET의 API 플랫폼으로 PowerShell을 대상으로 지정할 수 있습니다.
ms.date: 06/25/2020
ms.custom: rjmholt
ms.openlocfilehash: 39369ed872faa76ad2c41d813da5e0a98cf1c078
ms.sourcegitcommit: d0461273abb6db099c5e784ef00f57fd551be4a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85795322"
---
# <a name="choosing-the-right-powershell-nuget-package-for-your-net-project"></a>.NET 프로젝트에 적합한 PowerShell NuGet 패키지 선택

각 PowerShell 릴리스로 게시된 `pwsh` 실행 파일 패키지와 함께 PowerShell 팀은 [NuGet][]에서 사용할 수 있는 여러 패키지도 유지 관리합니다. 해당 패키지는 .NET의 API 플랫폼으로 PowerShell을 대상으로 지정할 수 있습니다.

API를 제공하고 자체(이진 모듈)을 구현하는 .NET 라이브러리를 로드해야 하는 .NET 애플리케이션으로, PowerShell은 NuGet 패키지 형식으로 사용할 수 있어야 합니다.

현재 PowerShell API 노출 영역의 일부 표시를 제공하는 여러 NuGet 패키지가 있습니다. 특정 프로젝트에서 사용할 패키지가 무엇인지 항상 분명한 것은 아닙니다. 이 문서에서는 PowerShell 대상 .NET 프로젝트의 몇 가지 일반적인 시나리오와 함께 PowerShell 기반 .NET 프로젝트의 대상으로 지정할 적합한 NuGet 패키지를 선택하는 방법을 중점적으로 다룹니다.

## <a name="hosting-vs-referencing"></a>호스팅 및 참조 비교

일부 .NET 프로젝트는 기존 PowerShell 런타임에 로드되는 코드(예: `pwsh`, `powershell.exe`, PowerShell 통합 콘솔 또는 ISE)를 작성하려고 하지만 다른 프로젝트는 자체 애플리케이션에서 PowerShell을 실행하려고 합니다.

- **참조**는 프로젝트(일반적으로 모듈)가 PowerShell로 로드되어야 하는 경우에 해당합니다.
  프로젝트와 상호 작용하려면 PowerShell이 제공하는 API에 대해 프로젝트를 컴파일해야 하지만, PowerShell 구현은 프로젝트를 로드하는 PowerShell 프로세스에서 제공됩니다. 참조를 위해 프로젝트는 [참조 어셈블리][] 또는 실제 런타임 어셈블리를 컴파일 대상으로 사용할 수 있지만, 관련 어셈블리를 빌드와 함께 게시하지 않도록 해야 합니다.
- 프로젝트는 일반적으로 PowerShell을 실행해야 하는 독립 실행형 애플리케이션이기 때문에 **호스팅**은 프로젝트에 자체 PowerShell 구현이 필요한 경우입니다. 이 경우 순수 참조 어셈블리를 사용할 수 없습니다. 대신, 구체적인 PowerShell 구현에 종속되어야 합니다. 구체적인 PowerShell 구현을 사용해야 하므로 호스팅을 위해 특정 버전의 PowerShell을 선택해야 하며, 단일 호스트 애플리케이션은 PowerShell 버전을 다중 대상으로 지정할 수 없습니다.

### <a name="publishing-projects-that-target-powershell-as-a-reference"></a>PowerShell을 대상으로 하는 프로젝트를 참조로 게시

> [!NOTE]
> 이 문서에서는 `dotnet publish` 실행을 나타내는 **게시**라는 용어를 사용하며, 해당 작업은 특정 런타임에 배포할 수 있는 모든 관련 종속성과 함께 .NET 라이브러리를 디렉터리에 배치합니다.

컴파일 참조 대상으로 사용되는 프로젝트 종속성 게시를 방지하기 위해 [PrivateAssets 특성][]을 설정하는 것이 좋습니다.

```xml
<PackageReference Include="PowerShellStandard.Library" Version="5.1.0.0" PrivateAssets="all" />
```

해당 작업을 기억하지 못하고 참조 어셈블리를 대상으로 사용하면 실제 구현 대신 참조 어셈블리의 기본 구현을 사용하는 것에 관련된 문제가 발생할 수 있습니다. 참조 어셈블리는 종종 단순히 `null`을 반환하여 구현 API를 모방하므로 해당 문제는 `NullReferenceException` 형식으로 나타날 수 있습니다.

## <a name="key-kinds-of-powershell-targeting-net-projects"></a>PowerShell 대상 .NET 프로젝트의 키 종류

모든 .NET 라이브러리나 애플리케이션은 PowerShell을 포함할 수 있지만 PowerShell API를 사용하는 몇 가지 일반적인 시나리오가 있습니다.

- **PowerShell 이진 모듈 구현**

  PowerShell 이진 모듈은 각각 cmdlet 또는 공급자를 공개하기 위해 [PSCmdlet][] 또는 [CmdletProvider][] 형식과 같은 PowerShell API를 구현해야 하는 PowerShell에서 로드하는 .NET 라이브러리입니다. 모듈은 로드되기 때문에 빌드에 게시하지 않고 PowerShell에 대한 참조에 대해 컴파일하려고 합니다. 또한 일반적으로 모듈은 이상적으로 디스크 공간, 복잡성 또는 반복 구현의 오버헤드를 최소화하여 여러 PowerShell 버전 및 플랫폼을 지원하려고 합니다. 모듈에 관한 자세한 내용은 [about_Modules][]를 참조하세요.

- **PowerShell 호스트 구현**

  PowerShell 호스트는 PowerShell 런타임의 상호 작용 계층을 제공합니다. 해당 호스트는 [PSHost][]가 PowerShell에 대한 새로운 사용자 인터페이스로 구현되는 특정 ‘호스팅’ 형식입니다. 예를 들어 PowerShell ConsoleHost는 PowerShell 실행 파일의 터미널 사용자 인터페이스를 제공하는 반면, PowerShell 편집기 서비스 호스트와 ISE 호스트는 둘 다 PowerShell에 관련된 편집기 통합형 부분 그래픽 사용자 인터페이스를 제공합니다. 호스트를 기존 PowerShell 프로세스에 로드할 수 있지만 호스트 구현이 PowerShell 엔진을 재배포하는 독립 실행형 PowerShell 구현으로 작동하는 것이 훨씬 더 일반적입니다.

- **다른 .NET 애플리케이션에서 PowerShell 호출**

  모든 애플리케이션과 마찬가지로 PowerShell은 하위 프로세스로 호출하여 워크로드를 실행할 수 있습니다. 그러나 .NET 애플리케이션은 PowerShell In Process를 호출하여 호출 애플리케이션 내에서 사용할 전체 .NET 개체를 가져올 수도 있습니다. 이는 애플리케이션이 내부 사용을 위해 자체 PowerShell 구현을 저장하는 더 일반적인 ‘호스팅’ 형식입니다. 해당 호스트의 예로는 머신 상태를 관리하기 위해 PowerShell을 실행하는 서비스 또는 디먼이나 클라우드 배포 관리 같은 작업을 수행하기 위해 요청 시 PowerShell을 실행하는 웹 애플리케이션이 있습니다.

- **.NET의 PowerShell 모듈 단위 테스트**

  PowerShell에 기능을 공개하도록 디자인된 모듈 및 기타 라이브러리는 기본적으로 PowerShell에서 테스트해야 하지만([Pester][] 권장) .NET에서 PowerShell 모듈용으로 작성된 API를 단위 테스트해야 하는 경우도 있습니다. 해당 상황에는 다양한 PowerShell 버전을 대상으로 지정하려는 모듈 코드가 포함되지만 테스트 시에는 구체적인 특정 구현에서 해당 코드를 실행해야 합니다.

## <a name="powershell-nuget-packages-at-a-glance"></a>PowerShell NuGet 패키지 한눈에 보기

이 문서에서는 PowerShell API를 공개하는 다음 NuGet 패키지를 설명합니다.

- [PowerShellStandard.Library][] - 여러 PowerShell 런타임에서 로드할 수 있는 단일 어셈블리를 빌드하는 데 사용되는 참조 어셈블리입니다.
- [Microsoft.PowerShell.SDK][] - 전체 PowerShell SDK를 대상으로 지정하고 다시 호스트하는 방법입니다.
- [System.Management.Automation][] 패키지 - 최소한의 호스티드 구현 및 버전별 대상 지정 시나리오에 유용할 수 있는 핵심 PowerShell 런타임 및 엔진 구현입니다.
- **Windows PowerShell 참조 어셈블리** - Windows PowerShell(PowerShell 버전 5.1 이하)을 대상으로 지정하고 효과적으로 다시 호스트하는 방법입니다.

> [!NOTE]
> [PowerShell NuGet][] 패키지는 .NET 라이브러리 패키지가 아니지만 대신 PowerShell dotnet 전역 도구 구현을 제공합니다. 해당 패키지는 실행 파일만 제공하므로 프로젝트에서 사용하지 않아야 합니다.

## <a name="powershellstandardlibrary"></a>PowerShellStandard.Library

PowerShell Standard 라이브러리는 PowerShell 버전 7, 6 및 5.1의 API 교집합을 캡처하는 참조 어셈블리입니다. .NET 코드를 컴파일할 컴파일 시간이 검사된 API 표면을 제공하므로 .NET 프로젝트가 존재하지 않는 API를 호출할 위험 없이 PowerShell 버전 7, 6 및 5.1을 대상으로 지정할 수 있습니다.

PowerShell Standard는 PowerShell 모듈을 작성하거나 PowerShell 프로세스로 로드한 후에만 실행되는 다른 코드를 작성하는 데 사용됩니다. PowerShell Standard는 참조 어셈블리이기 때문에 구현 자체를 포함하지 않으므로 독립 실행형 애플리케이션을 위한 기능을 제공하지 않습니다.

### <a name="using-powershell-standard-with-different-net-runtimes"></a>다른 .NET 런타임에서 PowerShell Standard 사용

PowerShell Standard는 .NET Framework 및 .NET Core에서 공유하는 일반적인 노출 영역을 제공하도록 디자인된 외관 런타임인 [.NET Standard 2.0][] 대상 런타임을 대상으로 합니다. 이렇게 하면 단일 런타임을 대상으로 지정하여 여러 PowerShell 버전에서 작동하는 단일 어셈블리를 생성할 수 있지만 다음과 같은 결과가 나타납니다.

- 모듈 또는 라이브러리를 로드하는 PowerShell은 최소한 .NET 4.6.1을 실행해야 하며, .NET 4.6 및 .NET 4.5.2는 .NET Standard을 지원하지 않습니다. 최신 Windows PowerShell 버전이 최신 .NET Framework 버전을 의미하지는 않으며, Windows PowerShell 5.1은 .NET 4.5.2에서 실행할 수 있습니다.
- .NET Framework 4.7.1 이하를 실행하는 PowerShell을 사용하기 위해 netstandard.dll 및 기타 shim 어셈블리를 이전 .NET Framework 버전에 제공하려면 .NET 4.6.1 [NETStandard.Library][] 구현이 필요합니다.

PowerShell 6 이상은 .NET Framework 4.6.1 이상에서 .NET Core로 형식 전달을 위한 자체 shim 어셈블리를 제공합니다. 즉, 모듈에서 .NET Core에 있는 API만 사용하는 한, 모듈이 .NET Framework 4.6.1(`net461` 런타임 대상)용으로 빌드된 경우 PowerShell 6 이상에서 모듈을 로드하여 실행할 수 있습니다.

즉, 단일 게시된 DLL로 여러 PowerShell 버전을 대상으로 지정하는 데 PowerShell Standard를 사용하는 이진 모듈에는 두 가지 옵션이 있습니다.

1. `net461` 대상 런타임용으로 빌드된 어셈블리 게시. 여기에는 다음이 포함됩니다.
   - `net461` 런타임을 위한 프로젝트 게시
   - 또한 빌드 출력을 사용하지 않고 `netstandard2.0` 런타임에 대해 컴파일하여 사용되는 모든 API가 .NET Core에도 포함되도록 함

1. `netstandard2.0` 대상 런타임을 위한 어셈블리 빌드 게시. 여기에는 다음이 필요합니다.
   - `netstandard2.0` 런타임을 위한 프로젝트 게시
   - .NET Framework에서 수정된 어셈블리가 형식으로 전달되도록 NETStandard.Library의 `net461` 종속성을 사용하고 프로젝트 어셈블리의 게시 위치에 복사

이전 .NET Framework 버전을 대상으로 하는 PowerShell 모듈 또는 라이브러리를 빌드하려면 여러 .NET 런타임을 대상으로 지정하는 것이 좋을 수 있습니다. 이렇게 하면 각 대상 런타임을 위한 어셈블리가 게시되며 모듈 로드 시간에 올바른 어셈블리를 로드해야 합니다(예: 루트 모듈로 작은 psm1 사용).

### <a name="testing-powershell-standard-projects-in-net"></a>.NET에서 PowerShell Standard 프로젝트 테스트

xUnit 같은 .NET 테스트 러너에서 모듈을 테스트하는 경우 컴파일 시간 검사는 한계가 있을 수 있습니다. 관련 PowerShell 플랫폼에서 모듈을 테스트해야 합니다.

.NET의 PowerShell Standard에서 빌드된 API를 테스트하려면 .NET Core(원하는 PowerShell 버전과 일치하도록 설정된 버전 포함)를 사용하여 테스트 종속성으로 `Microsoft.Powershell.SDK`를 추가하고 .NET Framework를 사용하여 적절한 Windows PowerShell 참조 어셈블리를 추가해야 합니다.

PowerShell Standard 및 해당 항목을 사용하여 여러 PowerShell 버전에서 작동하는 이진 모듈을 작성하는 방법에 관한 자세한 내용은 [이 블로그 게시물][]을 참조하세요. 또한 GitHub에서 [PowerShell Standard 리포지토리][]를 참조하세요.

## <a name="microsoftpowershellsdk"></a>Microsoft.PowerShell.SDK

`Microsoft.PowerShell.SDK`는 PowerShell SDK의 모든 구성 요소를 단일 NuGet 패키지로 함께 가져오는 메타 패키지입니다. 자체 포함 .NET 애플리케이션은 외부 PowerShell 설치 또는 라이브러리에 의존하지 않고 Microsoft.PowerShell.SDK를 사용하여 임의 PowerShell 기능을 실행할 수 있습니다.

> [!NOTE]
> PowerShell SDK는 PowerShell을 구성하고 PowerShell을 사용한 .NET 개발에 사용할 수 있는 모든 구성 요소 패키지를 나타냅니다.

지정된 `Microsoft.Powershell.SDK` 버전에는 동일한 PowerShell 애플리케이션 버전의 구체적인 구현이 포함되며, 버전 7.0에는 PowerShell 7.0 구현이 포함되며 해당 버전에서 실행하는 명령이나 스크립트는 대체로 PowerShell 7.0에서 실행하는 것처럼 동작합니다.

SDK에서 PowerShell 명령을 실행하는 것은 완전히는 아니지만 일반적으로 `pwsh`에서 실행하는 것과 동일합니다. 예를 들어 [Start-Job][]은 현재 제공되는 `pwsh` 실행 파일을 사용하므로 기본적으로 `Microsoft.Powershell.SDK`에서 작동하지 않습니다.

.NET 애플리케이션에서 `Microsoft.Powershell.SDK`를 대상으로 지정하면 `System.Management.Automation`, `Microsoft.PowerShell.Management` 및 기타 모듈 어셈블리와 같은 PowerShell의 모든 구현 어셈블리와 통합할 수 있습니다.

`Microsoft.Powershell.SDK`를 대상으로 하는 애플리케이션 게시에는 모든 해당 어셈블리 및 PowerShell에 필요한 모든 종속성이 포함됩니다. 또한 `Microsoft.PowerShell.*` 모듈의 모듈 매니페스트 및 [Add-Type][]에 필요한 `ref` 디렉터리와 같이 PowerShell이 해당 빌드에서 필요한 다른 자산이 포함됩니다.

`Microsoft.Powershell.SDK` 완결성의 경우 다음에 가장 적합합니다.

- PowerShell 호스트의 구현
- PowerShell 참조 어셈블리를 대상으로 하는 라이브러리의 xUnit 테스트
- .NET 애플리케이션에서 PowerShell In Process 호출

`Microsoft.PowerShell.SDK`는 .NET 프로젝트를 모듈로 사용하거나 PowerShell을 통해 로드해야 하지만 특정 버전의 PowerShell에 있는 API만 사용하는 경우 참조 대상으로 사용될 수도 있습니다. 특정 버전의 `Microsoft.PowerShell.SDK`에 대해 게시된 어셈블리는 해당 버전의 PowerShell에서만 안전하게 로드 및 사용할 수 있습니다. 특정 API가 포함된 여러 PowerShell 버전을 대상으로 지정하려면 각각 자체 버전의 `Microsoft.Powershell.SDK`를 대상으로 하는 여러 빌드가 필요합니다.

> [!NOTE]
> PowerShell SDK는 PowerShell 버전 6 이상에서만 사용할 수 있습니다. Windows PowerShell에서 동일한 기능을 제공하려면 아래에 설명된 Windows PowerShell 참조 어셈블리를 사용합니다.

## <a name="systemmanagementautomation"></a>System.Management.Automation

`System.Management.Automation` 패키지는 PowerShell SDK의 핵심입니다. 주로 `Microsoft.Powershell.SDK`가 가져올 자산으로 NuGet에 있습니다. 그러나 더 작은 호스팅 시나리오 및 버전 대상 모듈용 패키지로 직접 사용할 수도 있습니다.

특히 다음과 같은 경우 `System.Management.Automation` 패키지를 PowerShell 기능의 공급자로 사용하는 것이 좋습니다.

- PowerShell 파서, AST 및 AST 방문자 API(예: PowerShell의 정적 분석용)와 같은 PowerShell 언어 기능을 `System.Management.Automation.Language` 네임스페이스에서 사용하는 것만 고려합니다.
- `Microsoft.PowerShell.Core` 모듈에서 특정 명령만 실행하려고 하며 [CreateDefault2][] 팩터리 메서드를 사용하여 만든 세션 상태에서 실행할 수 있습니다.

또한 `System.Management.Automation`은 다음과 같은 경우에 유용한 참조 어셈블리입니다.

- 특정 PowerShell 버전에만 있는 API를 대상으로 지정하려는 경우
- `System.Management.Automation` 어셈블리 외부에서 발생하는 형식을 사용하지 않으려는 경우(예: `Microsoft.PowerShell.*` 모듈의 cmdlet을 통해 내보낸 형식).

## <a name="windows-powershell-reference-assemblies"></a>Windows PowerShell 참조 어셈블리

PowerShell 버전 5.1 이하(Windows PowerShell)의 경우 Windows PowerShell 구현이 Windows에 포함되므로 PowerShell 구현을 제공하는 SDK가 없습니다.

대신, Windows PowerShell 참조 어셈블리는 참조 대상 및 Windows PowerShell을 다시 호스트하는 방법을 둘 다 제공하여 PowerShell SDK가 버전 6 이상에서 작동하는 것과 동일하게 작동합니다.

버전별로 구분되는 것이 아니라 Windows PowerShell 참조 어셈블리에는 각 Windows PowerShell 버전에 해당하는 다른 패키지가 포함됩니다.

- [PowerShell 5.1](https://www.nuget.org/packages/Microsoft.PowerShell.5.ReferenceAssemblies/)
- [PowerShell 4](https://www.nuget.org/packages/Microsoft.PowerShell.4.ReferenceAssemblies/)
- [PowerShell 3](https://www.nuget.org/packages/Microsoft.PowerShell.3.ReferenceAssemblies/)

Windows PowerShell 참조 어셈블리를 사용하는 방법에 관한 정보는 [Windows PowerShell SDK][]에서 찾을 수 있습니다.

## <a name="real-world-examples-using-these-nuget-packages"></a>해당 NuGet 패키지를 사용하는 실제 예제

다양한 PowerShell 도구 프로젝트는 요구 사항에 따라 다양한 PowerShell NuGet 패키지를 대상으로 합니다. 여기에 몇 가지 주목할 만한 예가 나와 있습니다.

### <a name="psreadline"></a>PSReadLine

[PSReadLine][] - PowerShell의 풍부한 콘솔 환경을 많이 제공하고, 특정 PowerShell 버전이 아닌 종속성으로 PowerShell Standard를 대상으로 지정하고, [csproj][]에서 `net461` .NET 런타임을 대상으로 하는 PowerShell 모듈입니다.

PowerShell 6 이상은 .NET Framework의 `mscorlib.dll`에 대한 바인딩을 관련 .NET Core 어셈블리로 리디렉션하여 `net461` 런타임을 대상으로 하는 DLL이 로드될 때 “바로 작동”하도록 허용하는 자체 shim 어셈블리를 제공합니다.

PowerShell Standard는 사용되는 API만 PowerShell 5.1 및 PowerShell 6 이상에서 둘 다 제공되도록 하지만 모듈이 단일 어셈블리에만 함께 제공될 수 있도록 하므로 이렇게 하면 PSReadLine의 모듈 레이아웃 및 전송이 크게 간소화됩니다.

.NET 4.6.1 대상의 경우 .NET 4.5.2 및 .NET 4.6에서 실행되는 Windows PowerShell이 지원되지 않는다는 의미가 아닙니다.

### <a name="powershell-editor-services"></a>PowerShell Editor Services

PSES([PowerShell Editor Services][])는 [Visual Studio Code][]용 [PowerShell 확장][]의 백 엔드이며, 실제로 PowerShell 실행 파일을 통해 로드된 후 해당 프로세스를 인수하여 언어 서비스 프로토콜 및 디버그 어댑터 기능을 제공하면서 내부에 PowerShell을 다시 호스트하는 PowerShell 모듈 형식입니다.

PSES는 `netcoreapp2.1`이 PowerShell 6 이상을 대상으로 지정하고(PowerShell 7의 `netcoreapp3.1` 런타임이 이전 버전과 호환되기 때문) `net461`이 Windows PowerShell 5.1을 대상으로 지정하도록 구체적인 구현 대상을 제공하지만, `netstandard2.0` 및 PowerShell Standard를 대상으로 하는 두 번째 어셈블리에서 대부분의 논리를 포함합니다. 이를 통해 .NET Core 및 .NET Framework 플랫폼에 필요한 종속성을 가져올 수 있지만 균일 추상화를 기반으로 대부분의 코드베이스를 단순화할 수 있습니다.

PowerShell Standard에 대해 빌드되기 때문에 PSES를 제대로 테스트하려면 PowerShell의 런타임 구현이 필요합니다. 해당 작업을 수행하기 위해 [PSES의 xUnit][] 테스트는 `Microsoft.PowerShell.SDK` 및 `Microsoft.PowerShell.5.ReferenceAssemblies`를 가져와서 테스트 환경에서 PowerShell 구현을 제공합니다.

PSReadLine과 마찬가지로 PSES는 .NET 4.6 이하를 지원할 수 없지만 더 낮은 .NET Framework 런타임에서 크래쉬를 일으킬 수 있는 모든 API를 호출하기 전에 런타임에 [검사를 수행][]합니다.

### <a name="psscriptanalyzer"></a>PSScriptAnalyzer

PowerShell의 linter인 [PSScriptAnalyzer][]는 특정 버전의 PowerShell에만 도입된 구문 요소를 대상으로 지정해야 합니다. [AstVisitor2][]를 구현하여 해당 구문 요소를 인식하기 때문에 PowerShellStandard를 사용할 수 없으며 최신 PowerShell 구문을 위한 AST 방문자 메서드도 구현할 수 없습니다.

대신, PSScriptAnalyzer는 빌드 구성으로 [각 PowerShell 버전을 대상으로 지정][]하며 각 버전에 대해 별도 DLL을 생성합니다. 이렇게 하면 빌드 크기 및 복잡성이 증가하지만 다음이 가능합니다.

- 버전별 API 대상 지정
- 기본적으로 런타임 비용 없이 버전별 기능 구현
- .NET Framework 4.5.2까지 전체 Windows PowerShell 지원

## <a name="summary"></a>요약

이 문서에서는 PowerShell을 사용하는 .NET 프로젝트를 구현할 때 대상에서 사용할 수 있는 NuGet 패키지 및 각 패키지를 사용할 수 있는 이유를 나열하고 설명했습니다.

요약으로 건너뛴 경우 몇 가지 광범위한 권장 사항은 다음과 같습니다.

- PowerShell **모듈**은 다양한 PowerShell 버전에 공통된 API만 필요한 경우 PowerShell Standard에 대해 컴파일해야 합니다.
- 내부적으로 PowerShell을 실행해야 하는 PowerShell **호스트 및 애플리케이션**은 PowerShell 6 이상의 경우 PowerShell SDK를, Windows PowerShell의 경우 관련 Windows PowerShell 참조 어셈블리를 대상으로 지정해야 합니다.
- **버전별 API**가 필요한 PowerShell 모듈은 필요한 PowerShell 버전에 해당하는 PowerShell SDK 또는 Windows PowerShell 참조 어셈블리를 참조 어셈블리로 사용하여(PowerShell 종속성을 게시하는 것이 아님) 대상으로 지정해야 합니다.

<!--link references -->

[.NET Standard 2.0]: /dotnet/standard/net-standard
[about_Modules]: /powershell/module/microsoft.powershell.core/about/about_modules
[Add-Type]: /powershell/module/microsoft.powershell.utility/add-type
[AstVisitor2]: /dotnet/api/system.management.automation.language.astvisitor2
[CmdletProvider]: /dotnet/api/system.management.automation.provider.cmdletprovider
[CreateDefault2]: /dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2
[csproj]: https://github.com/PowerShell/PSReadLine/blob/master/PSReadLine/PSReadLine.csproj
[Microsoft.PowerShell.SDK]: https://www.nuget.org/packages/Microsoft.PowerShell.SDK/
[NETStandard.Library]: https://www.nuget.org/packages/NETStandard.Library/
[NuGet]: https://www.nuget.org/
[검사 수행]: https://github.com/PowerShell/PowerShellEditorServices/blob/8c500ee1752201d3c1cc2e5d90f1a2af3b1eb15d/src/PowerShellEditorServices.Hosting/EditorServicesLoader.cs#L231-L251
[Pester]: https://github.com/Pester/Pester
[PowerShell Editor Services]: https://github.com/PowerShell/PowerShellEditorServices/
[PowerShell 확장]: https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell
[PowerShell NuGet]: https://www.nuget.org/packages/PowerShell/
[PowerShell Standard 리포지토리]: https://github.com/PowerShell/PowerShellStandard
[PowerShellStandard.Library]: https://www.nuget.org/packages/PowerShellStandard.Library/
[PSCmdlet]: /dotnet/api/system.management.automation.pscmdlet
[PSES의 xUnit]: https://github.com/PowerShell/PowerShellEditorServices/blob/8c500ee1752201d3c1cc2e5d90f1a2af3b1eb15d/test/PowerShellEditorServices.Test/PowerShellEditorServices.Test.csproj#L15-L20
[PSHost]: /dotnet/api/system.management.automation.host.pshost
[PrivateAssets 특성]: /dotnet/core/tools/csproj#packagereference
[PSReadLine]: https://github.com/PowerShell/PSReadLine
[PSScriptAnalyzer]: https://github.com/powershell/psscriptanalyzer
[참조 어셈블리]: https://github.com/dotnet/standard/blob/master/docs/history/evolution-of-design-time-assemblies.md#definitions
[Start-Job]: /powershell/module/microsoft.powershell.core/start-job
[System.Management.Automation]: https://www.nuget.org/packages/System.Management.Automation/
[각 PowerShell 버전을 대상으로 지정]: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/Engine/Engine.csproj
[이 블로그 게시물]: https://devblogs.microsoft.com/powershell/powershell-standard-library-build-single-module-that-works-across-windows-powershell-and-powershell-core/
[Visual Studio Code]: https://code.visualstudio.com/
[Windows PowerShell SDK]: /powershell/scripting/developer/windows-powershell
