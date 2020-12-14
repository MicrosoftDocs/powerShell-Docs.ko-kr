---
title: PowerShell 모듈 어셈블리 종속성 충돌 해결
description: C#에서 이진 PowerShell 모듈을 작성하는 경우 다른 패키지나 라이브러리에 대한 종속성을 사용하여 기능을 제공하는 것이 자연스럽습니다.
ms.date: 06/25/2020
ms.custom: rjmholt
ms.openlocfilehash: 93bb39bdd440c7f97c27aa81e68f68331569b69e
ms.sourcegitcommit: 2fc6ee49a70bda4c59135136bd5cc7782836a124
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94810405"
---
# <a name="resolving-powershell-module-assembly-dependency-conflicts"></a>PowerShell 모듈 어셈블리 종속성 충돌 해결

C#에서 이진 PowerShell 모듈을 작성하는 경우 다른 패키지나 라이브러리에 대한 종속성을 사용하여 기능을 제공하는 것이 자연스럽습니다. 코드를 재사용을 위해 다른 라이브러리에 대한 종속성을 사용하는 것이 좋습니다. PowerShell은 항상 어셈블리를 동일한 컨텍스트에 로드합니다. 이로 인해 모듈의 종속성이 이미 로드된 DLL과 충돌할 때 문제가 발생하며 동일한 PowerShell 세션에서 두 가지 관련이 없는 모듈을 사용하지 못할 수 있습니다.

해당 문제가 발생하면 다음과 같은 오류 메시지가 표시됩니다.

![어셈블리 로드 충돌 오류 메시지](./media/resolving-dependency-conflicts/moduleconflict.png)

이 문서에서는 PowerShell에서 종속성 충돌이 발생하는 방법 및 종속성 충돌 문제를 완화하는 방법을 살펴봅니다. 여기에는 모듈 작성자가 아니더라도 사용하는 모듈에서 발생하는 종속성 충돌에 도움이 될 수 있는 몇 가지 요령이 있습니다.

## <a name="why-do-dependency-conflicts-occur"></a>종속성 충돌이 발생하는 이유는 무엇인가요?

.NET에서는 동일한 어셈블리의 두 버전이 동일한 _어셈블리 로드 컨텍스트_ 에 로드될 때 종속성 충돌이 발생합니다. 해당 용어는 여러 .NET 플랫폼에서 조금씩 다른 의미로 사용되며 관련 내용은 [뒤에서](#powershell-and-net) 설명합니다. 해당 충돌은 버전이 지정된 종속성이 사용되는 모든 소프트웨어에서 발생하는 일반적인 문제입니다. 간단한 솔루션은 없고 많은 종속성 해결 프레임워크가 다양한 방법으로 문제를 해결하려고 시도하기 때문에 해당 상황을 “종속성 결함”이라고도 합니다.

충돌 문제는 프로젝트가 의도적이든 직접적이든 동일한 종속성의 두 가지 버전에 종속되지 않는다는 사실로 인해 심각해집니다. 대신, 프로젝트는 동일한 종속성의 각기 다른 버전이 필요한 두 개 이상의 종속성을 가집니다.

예를 들어 .NET 애플리케이션인 `DuckBuilder`가 해당 기능의 일부를 수행하는 두 가지 종속성을 제공하며 다음과 같이 표시된다고 가정하겠습니다.

![DuckBuilder의 두 종속성은 Newtonsoft.json의 서로 다른 버전을 사용합니다.](./media/resolving-dependency-conflicts/dep-conflict.jpg)

`Contoso.ZipTools` 및 `Fabrikam.FileHelpers`는 서로 다른 버전의 `Newtonsoft.Json`을 사용하므로 각 종속성이 로드되는 방식에 따라 종속성 충돌이 있을 수 있습니다.

### <a name="conflicting-with-powershells-dependencies"></a>PowerShell 종속성과 충돌

PowerShell 모듈 및 PowerShell 자체 종속성이 동일한 공유 컨텍스트에 로드되므로 PowerShell에서 종속성 충돌 문제가 커집니다. 즉, PowerShell 엔진과 로드된 모든 PowerShell 모듈에는 충돌하는 종속성이 없어야 합니다. 이에 관한 기존 예는 `Newtonsoft.Json`입니다.

![FictionalTools 모듈은 PowerShell보다 최신 버전의 Newtonsoft.json을 사용합니다.](./media/resolving-dependency-conflicts/engine-conflict.jpg)

이 예제에서 모듈 `FictionalTools`는 예제 PowerShell에 제공되는 `11.0.2`보다 최신 `Newtonsoft.Json` 버전인 `Newtonsoft.Json` 버전 `12.0.3`을 사용합니다.

> [!NOTE]
> 이는 예제이며 PowerShell 7에는 현재 `Newtonsoft.Json 12.0.3`이 함께 제공됩니다.

모듈은 최신 버전의 어셈블리를 사용하므로 PowerShell이 이미 로드한 버전을 허용하지 않습니다. 그러나 PowerShell이 이미 특정 버전의 어셈블리를 로드했으므로 모듈은 기존 로드 메커니즘을 사용하여 자체 버전을 로드할 수 없습니다.

### <a name="conflicting-with-another-modules-dependencies"></a>또 다른 모듈의 종속성과 충돌

PowerShell의 또 다른 일반적인 시나리오는 한 버전의 어셈블리를 사용하는 모듈이 로드된 다음, 다른 버전의 해당 어셈블리를 사용하는 또 다른 모듈이 나중에 로드되는 경우입니다.

해당 시나리오는 다음과 같이 표시됩니다.

![두 PowerShell 모듈에는 서로 다른 버전의 Microsoft.Extensions.Logging 종속성이 필요합니다.](./media/resolving-dependency-conflicts/mod-conflict.jpg)

이 경우 `FictionalTools` 모듈에는 `FilesystemManager` 모듈보다 최신 버전의 `Microsoft.Extensions.Logging`이 필요합니다.

해당 모듈이 종속성 어셈블리를 루트 모듈 어셈블리와 동일한 디렉터리에 배치하여 종속성을 로드한다고 가정해 보겠습니다. 이렇게 하면 .NET은 종속성을 이름으로 암시적으로 로드할 수 있습니다. PowerShell 7(.NET Core 3.1 기반)을 실행하는 경우 `FictionalTools`를 로드하고 실행한 다음, 문제 없이 `FilesystemManager`를 로드하고 실행할 수 있습니다. 그러나 새 세션에서 `FilesystemManager`를 로드하고 실행한 다음, `FictionalTools`를 로드하면 로드된 것보다 최신 버전의 `Microsoft.Extensions.Logging`이 필요하므로 `FictionalTools` 명령에서 `FileLoadException`이 발생합니다.
이름이 같은 어셈블리가 이미 로드되었으므로 `FictionalTools`는 필요한 버전을 로드할 수 없습니다.

## <a name="powershell-and-net"></a>PowerShell 및 .NET

PowerShell은 .NET 플랫폼에서 실행됩니다. NET은 기본적으로 어셈블리 종속성 확인 및 로드를 담당하므로 종속성 충돌을 이해하려면 여기에서 .NET이 작동하는 방식을 이해해야 합니다.

또한 여러 가지 버전의 PowerShell이 여러 가지 .NET 구현에서 실행된다는 사실도 인식해야 합니다. 일반적으로 PowerShell 5.1 이하는 .NET Framework에서 실행되지만 PowerShell 6 이상은 .NET Core에서 실행됩니다. .NET의 해당하는 두 가지 구현은 어셈블리를 서로 다르게 로드하고 처리합니다.
즉, 종속성 충돌 해결은 기본 .NET 플랫폼에 따라 달라질 수 있습니다.

### <a name="assembly-load-contexts"></a>어셈블리 로드 컨텍스트

.NET에서 어셈블리가 로드되는 런타임 네임스페이스인 ALC(‘어셈블리 로드 컨텍스트’) 입니다. 어셈블리 이름은 고유해야 합니다. 해당 개념을 사용하면 각 ALC에서 이름으로 어셈블리를 고유하게 확인할 수 있습니다.

### <a name="assembly-reference-loading-in-net"></a>.NET의 어셈블리 참조 로딩

어셈블리 로딩의 의미 체계는 .NET 구현(.NET Core 대비 .NET Framework) 및 특정 어셈블리를 로드하는 데 사용되는 .NET API에 따라 달라집니다. 여기서 자세히 설명하지 않지만 각 .NET 구현에서 .NET 어셈블리 로딩이 작동하는 방식을 자세히 살펴볼 수 있는 링크가 [추가 정보](#further-reading) 섹션에 있습니다.

이 문서에서는 다음 메커니즘을 참조합니다.

- 암시적 어셈블리 로드(실제로 `Assembly.Load(AssemblyName)`) - .NET이 .NET 코드의 정적 어셈블리 참조에서 이름으로 어셈블리를 암시적으로 로드하려고 시도하는 경우.
- `Assembly.LoadFrom()` - 로드된 DLL의 종속성을 확인하기 위한 처리기를 추가하는 플러그인 기반 로딩 API입니다. 해당 메서드는 원하는 방식으로 종속성을 확인할 수 없습니다.
- `Assembly.LoadFile()` - 요청된 어셈블리만 로드하고 종속성을 처리하지 않는 기본 로딩 API.

### <a name="differences-in-net-framework-vs-net-core"></a>.NET Framework 및 .NET Core의 차이점

해당 API가 작동하는 방식은 .NET Core와 .NET Framework 간에 약간 변경되었으므로 포함된 [링크](#further-reading)를 참조하는 것이 좋습니다. 중요한 점은, .NET Framework와 .NET Core 간에 어셈블리 로드 컨텍스트 및 기타 어셈블리 확인 메커니즘이 변경되었다는 것입니다.

특히 .NET Framework에는 다음 기능이 있습니다.

- 머신 전체의 어셈블리 확인을 위한 전역 어셈블리 캐시
- 어셈블리 격리를 위해 In Process 샌드박스에서 작동하며 경합할 serialization 계층을 제공하는 애플리케이션 도메인
- 각각 자체 동작을 포함하는 고정된 어셈블리 로드 컨텍스트 세트가 있는 제한된 어셈블리 로드 컨텍스트 모델([여기](/dotnet/framework/deployment/best-practices-for-assembly-loading)에서 자세히 설명함):
  - 기본적으로 어셈블리가 로드되는 기본 로드 컨텍스트
  - 런타임에 어셈블리를 수동으로 로드하기 위한 로드 시작 컨텍스트
  - 어셈블리를 실행하지 않고 메타데이터를 읽도록 어셈블리를 안전하게 로드하기 위한 리플렉션 전용 컨텍스트
  - `Assembly.LoadFile(string path)` 및 `Assembly.Load(byte[] asmBytes)`로 로드된 어셈블리가 있는 이해하기 힘든 void

.NET Core(및 .NET 5 이상)에서는 해당 복잡성이 보다 간단한 모델로 대체되었습니다.

- 전역 어셈블리 캐시 없음 애플리케이션이 모든 자체 종속성을 제공합니다. 이에 따라 애플리케이션에서 종속성 확인을 위한 외부 요소가 제거되어 종속성 확인의 재현 가능성이 높아집니다.
  플러그인 호스트로서 PowerShell은 모듈에서 해당 상황을 약간 복잡하게 만듭니다. `$PSHOME`에서 해당 종속성은 모든 모듈과 공유됩니다.
- 애플리케이션 도메인이 하나만 있고 새 항목을 만들 수 없음 애플리케이션 도메인 개념은 .NET Core에서 .NET 프로세스의 전역 상태로만 유지 관리됩니다.
- 확장 가능한 새 어셈블리 로드 컨텍스트 모델. 어셈블리 확인은 새 ALC에 배치하여 네임스페이스로 지정할 수 있습니다. .NET Core 프로세스는 모든 어셈블리가 로드되는 단일 기본 ALC로 시작됩니다. (`Assembly.LoadFile(string)` 및 `Assembly.Load(byte[])`를 사용하여 로드된 어셈블리 제외) 그러나 프로세스는 자체 로딩 논리를 사용하여 자체 사용자 지정 ALC를 만들고 정의할 수 있습니다. 어셈블리가 로드되면 해당 어셈블리가 로드되는 첫 번째 ALC는 해당 종속성을 확인해야 합니다. 이렇게 하면 강력한 .NET 플러그인 로딩 메커니즘을 구현할 수 있습니다.

두 가지 구현에서 모두 어셈블리는 지연 로드됩니다. 즉, 해당 형식이 필요한 메서드가 처음으로 실행될 때 로드됩니다.

예를 들어 서로 다른 시간에 종속성을 로드하는 동일한 코드의 두 가지 버전은 다음과 같습니다.

첫 번째 코드는 종속성 참조가 메서드 내에 어휘로 존재하기 때문에 항상 `Program.GetRange()`가 호출될 때 해당 종속성을 로드합니다.

```csharp
using Dependency.Library;

public static class Program
{
    public static List<int> GetRange(int limit)
    {
        var list = new List<int>();
        for (int i = 0; i < limit; i++)
        {
            if (i >= 20)
            {
                // Dependency.Library will be loaded when GetRange is run
                // because the dependency call occurs directly within the method
                DependencyApi.Use();
            }

            list.Add(i);
        }
        return list;
    }
}
```

두 번째는 메서드를 통한 내부 간접 참조이므로 `limit` 매개 변수가 20개 이상인 경우에만 해당 종속성을 로드합니다.

```csharp
using Dependency.Library;

public static class Program
{
    public static List<int> GetNumbers(int limit)
    {
        var list = new List<int>();
        for (int i = 0; i < limit; i++)
        {
            if (i >= 20)
            {
                // Dependency.Library is only referenced within
                // the UseDependencyApi() method,
                // so will only be loaded when limit >= 20
                UseDependencyApi();
            }

            list.Add(i);
        }
        return list;
    }

    private static void UseDependencyApi()
    {
        // Once UseDependencyApi() is called, Dependency.Library is loaded
        DependencyApi.Use();
    }
}
```

이는 메모리와 파일 시스템 I/O를 최소화하고 리소스를 보다 효율적으로 사용하기 때문에 좋은 사례입니다. 이로 인한 안타까운 부작용은 어셈블리를 로드하려고 하는 코드 경로에 도달할 때까지 어셈블리가 로드에 실패하는지 알 수 없다는 것입니다.

어셈블리 로드 충돌의 타이밍 조건을 만들 수도 있습니다. 동일한 프로그램의 두 부분이 동일한 어셈블리의 서로 다른 버전을 로드하려고 시도하면 로드되는 버전은 먼저 실행되는 코드 경로에 따라 결정됩니다.

PowerShell의 경우 이는 다음 요소가 어셈블리 로드 충돌에 영향을 줄 수 있음을 의미합니다.

- 먼저 로드된 모듈은 무엇인가요?
- 종속성 라이브러리를 사용하는 코드 경로가 실행되었나요?
- PowerShell이 시작 시 또는 특정 코드 경로에서만 충돌 종속성을 로드하나요?

## <a name="quick-fixes-and-their-limitations"></a>빠른 수정 및 제한 사항

일부 경우에는 모듈을 약간 조정하고 최소한의 작업으로 항목을 수정할 수 있습니다. 그러나 해당 솔루션은 신중하게 제공되는 것이 일반적입니다. 모듈에 적용될 수 있지만 모든 모듈에서 작동하지는 않습니다.

### <a name="change-your-dependency-version"></a>종속성 버전 변경

종속성 충돌을 방지하는 가장 간단한 방법은 종속성에 동의하는 것입니다. 해당 방법은 다음 경우에 가능할 수 있습니다.

- 충돌이 모듈의 직접 종속성에서 발생하며 버전을 제어합니다.
- 충돌이 간접 종속성에서 발생하지만 작업 가능한 간접 종속성 버전을 사용하도록 직접 종속성을 구성할 수 있습니다.
- 충돌 버전을 알고 있으며 변경하지 않고 해당 버전을 사용할 수 있습니다.

`Newtonsoft.Json` 패키지는 마지막 시나리오의 좋은 예입니다. 해당 패키지는 PowerShell 6 이상의 종속성이며 Windows PowerShell에서 사용되지 않습니다. 즉, 버전 지정 충돌을 해결하는 간단한 방법은 대상으로 지정하려는 PowerShell 버전에서 `Newtonsoft.Json`의 가장 낮은 버전을 대상으로 지정하는 것입니다.

예를 들어 PowerShell 6.2.6 및 PowerShell 7.0.2는 둘 다 현재 `Newtonsoft.Json` 버전 12.0.3을 사용합니다. 따라서 Windows PowerShell, PowerShell 6 및 PowerShell 7을 대상으로 하는 모듈을 만들려면 종속성으로 `Newtonsoft.Json 12.0.3`을 대상으로 지정하고 빌드된 모듈에 포함합니다. 모듈이 PowerShell 6 또는 7에 로드되면 PowerShell의 자체 `Newtonsoft.Json` 어셈블리가 이미 로드된 것입니다. 또한 모듈에 필요한 최소한의 버전이므로 확인이 성공합니다. Windows PowerShell에서 어셈블리는 아직 PowerShell에 존재하지 않습니다. 대신, 모듈 폴더에서 로드됩니다.

일반적으로 `Microsoft.PowerShell.Sdk` 또는 `System.Management.Automation` 같은 구체적인 PowerShell 패키지를 대상으로 지정하는 경우 NuGet은 필요한 적합한 종속성 버전을 확인할 수 있어야 합니다. 대상으로 여러 프레임워크 또는 `PowerShellStandard.Library`를 지정하도록 선택해야 하므로 Windows PowerShell 및 PowerShell 6 이상을 둘 다 대상으로 지정하는 것이 더 어려워집니다.

일반 종속성 버전으로 고정할 수 없는 경우는 다음과 같습니다.

- 충돌이 간접 종속성에서 발생하며 일반 버전을 사용하도록 구성할 수 있는 종속성이 없는 경우
- 다른 종속성 버전이 자주 변경될 수 있으므로 일반 버전의 정착이 단기 고정일 뿐인 경우

### <a name="add-an-assemblyresolve-event-handler-to-create-a-dynamic-binding-redirect"></a>AssemblyResolve 이벤트 처리기를 추가하여 동적 바인딩 리디렉션 만들기

경우에 따라 자체 종속성 버전을 변경하는 것이 불가능하거나 너무 어렵습니다. 또 다른 옵션은 `AssemblyResolve` 이벤트의 이벤트 처리기를 등록하여 동적 바인딩 리디렉션을 설정하는 것입니다.

정적 바인딩 리디렉션과 마찬가지로 요점은 종속성의 모든 소비자가 동일한 실제 어셈블리를 사용하도록 강제하는 것입니다. 종속성을 로드하는 호출을 가로채고 항상 원하는 버전으로 리디렉션합니다.

다음과 같이 표시됩니다.

```csharp
// Register the event handler as early as you can in your code.
// A good option is to use the IModuleAssemblyInitializer interface
// that PowerShell provides to run code early on when your module is loaded.

// This class will be instantiated on module import and the OnImport() method run.
// Make sure that:
//  - the class is public
//  - the class has a public, parameterless constructor
//  - the class implements IModuleAssemblyInitializer
public class MyModuleInitializer : IModuleAssemblyInitializer
{
    public void OnImport()
    {
        AppDomain.CurrentDomain.AssemblyResolve += DependencyResolution.ResolveNewtonsoftJson;
    }
}

// Clean up the event handler when the the module is removed
// to prevent memory leaks.
//
// Like IModuleAssemblyInitializer, IModuleAssemblyCleanup allows
// you to register code to run when a module is removed (with Remove-Module).
// Make sure it is also public with a public parameterless contructor
// and implements IModuleAssemblyCleanup.
public class MyModuleCleanup : IModuleAssemblyCleanup
{
    public void OnRemove()
    {
        AppDomain.CurrentDomain.AssemblyResolve -= DependencyResolution.ResolveNewtonsoftJson;
    }
}

internal static class DependencyResolution
{
    private static readonly string s_modulePath = Path.GetDirectoryName(
        Assembly.GetExecutingAssembly().Location);

    public static Assembly ResolveNewtonsoftJson(object sender, ResolveEventArgs args)
    {
        // Parse the assembly name
        var assemblyName = new AssemblyName(args.Name);

        // We only want to handle the dependency we care about.
        // In this example it's Newtonsoft.Json.
        if (!assemblyName.Name.Equals("Newtonsoft.Json"))
        {
            return null;
        }

        // Generally the version of the dependency you want to load is the higher one,
        // since it's the most likely to be compatible with all dependent assemblies.
        // The logic here assumes our module always has the version we want to load.
        // Also note the use of Assembly.LoadFrom() here rather than Assembly.LoadFile().
        return Assembly.LoadFrom(Path.Combine(s_modulePath, "Newtonsoft.Json.dll"));
    }
}
```

기술적으로 PowerShell 내에 스크립트 블록을 등록하여 `AssemblyResolve` 이벤트를 처리할 수 있지만 다음과 같은 경우가 있습니다.

- PowerShell이 처리할 수 없는 모든 스레드에서 `AssemblyResolve` 이벤트가 트리거될 수 있습니다.
- 이벤트가 적합한 스레드에서 처리되는 경우에도 PowerShell의 범위 지정 개념에 따라 외부에서 정의되는 변수를 사용하지 않도록 이벤트 처리기 스크립트 블록을 신중하게 작성해야 합니다.

일반 버전으로 리디렉션이 작동하지 않는 경우가 있습니다.

- 버전 간에 종속성에 관련된 호환성이 손상되는 변경이 있는 경우 또는 종속 코드가 리디렉션되는 버전에서 사용할 수 없는 기능을 사용하는 경우
- 모듈이 충돌 종속성 전에 로드되지 않은 경우 종속성이 로드된 후 `AssemblyResolve` 이벤트 처리기를 등록하면 처리기가 실행되지 않습니다. 또 다른 모듈과 종속성 충돌을 방지하려는 경우 다른 모듈이 먼저 로드될 수 있으므로 해당 상황에 문제가 될 수 있습니다.

### <a name="use-the-dependency-out-of-process"></a>out of process 종속성 사용

이 솔루션은 모듈 작성자보다 모듈 사용자를 위한 것입니다. 기존 종속성 충돌로 인해 작동하지 않는 모듈이 나타나는 경우 사용할 솔루션입니다.

동일한 어셈블리의 두 버전이 동일한 .NET 프로세스로 로드되기 때문에 종속성 충돌이 발생합니다. 간단한 솔루션은, 양쪽에서 해당 기능을 사용할 수 있다면 두 버전을 서로 다른 프로세스로 로드하는 것입니다.

PowerShell에서 해당 작업을 수행하는 방법에는 여러 가지가 있습니다.

- PowerShell을 하위 프로세스로 호출

  현재 프로세스에서 PowerShell 명령을 실행하는 간단한 방법은 명령 호출을 통해 직접 새 PowerShell 프로세스를 시작하는 것입니다.

  ```powershell
  pwsh -c 'Invoke-ConflictingCommand'
  ```

  여기서 주요 제한 사항은 결과를 재구성하는 것이 다른 옵션보다 더 까다롭고 오류가 발생하기 쉽다는 것입니다.

- PowerShell 작업 시스템

  PowerShell 작업 시스템은 새 PowerShell 프로세스에 명령을 전송하고 결과를 반환함으로써 명령을 out of process로 실행합니다.

  ```powershell
  $result = Start-Job { Invoke-ConflictingCommand } | Receive-Job -Wait
  ```

  이 경우 변수와 상태가 제대로 전달되었는지 확인해야 합니다.

  작은 명령을 실행하는 경우 작업 시스템이 약간 복잡할 수도 있습니다.

- PowerShell 원격 기능

  사용할 수 있는 경우 PowerShell 원격은 명령을 out of process로 실행하는 유용한 방법일 수 있습니다. 원격을 사용하여 새 프로세스에서 새 **PSSession** 을 만들고, PowerShell 원격을 통해 해당 명령을 호출한 다음, 충돌 종속성을 포함하는 다른 모듈에서 로컬로 결과를 사용할 수 있습니다.

  예제는 다음과 같이 표시될 수 있습니다.

  ```powershell
  # Create a local PowerShell session
  # where the module with conflicting assemblies will be loaded
  $s = New-PSSession

  # Import the module with the conflicting dependency via remoting,
  # exposing the commands locally
  Import-Module -PSSession $s -Name ConflictingModule

  # Run a command from the module with the conflicting dependencies
  Invoke-ConflictingCommand
  ```

- Windows PowerShell에 대한 암시적 원격

  PowerShell 7의 또 다른 옵션은 `Import-Module`에서 `-UseWindowsPowerShell` 플래그를 사용하는 것입니다. 이 방법으로 로컬 원격 세션을 통해 모듈을 Windows PowerShell로 가져옵니다.

  ```powershell
  Import-Module -Name ConflictingModule -UseWindowsPowerShell
  ```

  모듈이 작동하지 않거나 Windows PowerShell과 다르게 작동할 수도 있습니다.

#### <a name="when-out-of-process-invocation-should-not-be-used"></a>Out of Procss 호출을 사용하지 않아야 하는 경우

모듈 작성자로서 out of process 명령 호출은 모듈에 반영되기 어려우며 문제를 일으키는 에지 사례를 포함할 수 있습니다. 특히 원격 및 작업은 모듈이 작동해야 하는 일부 환경에서 사용하지 못할 수 있습니다. 그러나 구현을 out of process로 이동하고 PowerShell 모듈이 더 씬한 클라이언트가 되도록 허용하는 일반적인 원칙이 계속 적용될 수 있습니다.

모듈 사용자로서는 out of process 호출이 작동하지 않는 경우가 있습니다.

- 사용할 권한이 없거나 사용하도록 설정되지 않아 PowerShell 원격을 사용할 수 없는 경우
- 특정 .NET 형식이 출력에서 메서드 또는 다른 명령에 대한 입력으로 필요한 경우.
  PowerShell 원격을 통해 실행되는 명령은 강력한 형식의 .NET 개체가 아닌 역직렬화된 개체를 내보냅니다. 즉, 메서드 호출 및 강력한 형식의 API는 원격을 통해 가져온 명령의 출력에서 작동하지 않습니다.

## <a name="more-robust-solutions"></a>더 강력한 솔루션

이전 솔루션에는 모두 작동하지 않는 시나리오 및 모듈이 있습니다. 그러나 비교적 간단하게 제대로 구현할 수 있다는 장점도 있습니다. 다음 솔루션은 더 강력하지만, 제대로 구현하려면 더 많은 작업이 필요하며, 신중하게 작성되지 않을 경우 사소한 버그가 도입될 수 있습니다.

### <a name="loading-through-net-core-assembly-load-contexts"></a>.NET Core 어셈블리 로드 컨텍스트를 통해 로드

특히 동일한 어셈블리의 여러 버전을 동일한 런타임으로 로드해야 하는 필요성을 해결하기 위해 구현 가능한 API로서 ALC([어셈블리 로드 컨텍스트](/dotnet/api/system.runtime.loader.assemblyloadcontext))가 .NET Core 1.0에 도입되었습니다.

.NET Core 및 .NET 5 내에서 ALC는 어셈블리의 충돌 버전을 로드하는 문제에 대한 가장 강력한 솔루션을 제공합니다. 그러나 사용자 지정 ALC는 .NET Framework에서 사용할 수 없습니다. 즉, 해당 솔루션은 PowerShell 6 이상에서만 작동합니다.

현재 PowerShell에서 종속성 격리를 위해 ALC를 사용하는 가장 좋은 예는 PowerShell Editor Services, Visual Studio Code용 PowerShell 확장의 언어 서버에 있습니다. [ALC를 사용](https://github.com/PowerShell/PowerShellEditorServices/blob/master/src/PowerShellEditorServices.Hosting/Internal/PsesLoadContext.cs)하여 PowerShell Editor Services의 자체 종속성이 PowerShell 모듈의 종속성과 충돌하지 않도록 방지합니다.

ALC를 사용하여 모듈 종속성 격리를 구현하는 것은 개념적으로 어렵지만 최소한의 예제를 통해 작업할 예정입니다. PowerShell 7에서만 작동하도록 고안된 간단한 모듈이 있다고 가정해 보겠습니다.
원본 코드는 다음과 같이 구성됩니다.

```
+ AlcModule.psd1
+ src/
    + TestAlcModuleCommand.cs
    + AlcModule.csproj
```

cmdlet 구현은 다음과 같이 표시됩니다.

```csharp
using Shared.Dependency;

namespace AlcModule
{
    [Cmdlet(VerbsDiagnostic.Test, "AlcModule")]
    public class TestAlcModuleCommand : Cmdlet
    {
        protected override void EndProcessing()
        {
            // Here's where our dependency gets used
            Dependency.Use();
            // Something trivial to make our cmdlet do *something*
            WriteObject("done!");
        }
    }
}
```

(매우 단순화된) 매니페스트는 다음과 같이 표시됩니다.

```powershell
@{
    Author = 'Me'
    ModuleVersion = '0.0.1'
    RootModule = 'AlcModule.dll'
    CmdletsToExport = @('Test-AlcModule')
    PowerShellVersion = '7.0'
}
```

또한 `csproj`는 다음과 같이 표시됩니다.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Shared.Dependency" Version="1.0.0" />
    <PackageReference Include="Microsoft.PowerShell.Sdk" Version="7.0.1" PrivateAssets="all" />
  </ItemGroup>
</Project>
```

해당 모듈을 빌드할 때 생성된 출력의 레이아웃은 다음과 같습니다.

```
AlcModule/
  + AlcModule.psd1
  + AlcModule.dll
  + Shared.Dependency.dll
```

이 예제에서 문제는 가상 충돌 종속성인 `Shared.Dependency.dll` 어셈블리에 있습니다. 이는 모듈 특정 버전을 사용할 수 있도록 ALC 뒤에 배치해야 하는 종속성입니다.

다음과 같이 모듈을 다시 엔지니어링해야 합니다.

- 모듈 종속성은 PowerShell의 ALC가 아닌 사용자 지정 ALC에만 로드되므로 충돌이 발생하지 않습니다. 또한 프로젝트에 더 많은 종속성을 추가하면서 로딩이 계속 작동하도록 더 많은 코드를 지속적으로 추가하지 않으려고 합니다. 대신, 재사용 가능한 제네릭 종속성 확인 논리를 원합니다.
- 모듈 로드는 PowerShell에서 계속 정상적으로 작동합니다. PowerShell 모듈 시스템에 필요한 cmdlet 및 기타 형식은 PowerShell 자체 ALC 내에서 정의됩니다.

두 가지 요구 사항을 중재하려면 모듈을 다음과 같은 두 어셈블리로 분할해야 합니다.

- PowerShell의 모듈 시스템에서 모듈을 제대로 로드하는 데 필요한 모든 형식의 정의를 포함하는 cmdlet 어셈블리 `AlcModule.Cmdlets.dll`. 즉, `Cmdlet` 기본 클래스의 구현과 사용자 지정 ALC를 통해 `AlcModule.Engine.dll`을 적절히 로드하도록 `AssemblyLoadContext.Default.Resolving`의 이벤트 처리기를 설정하는 `IModuleAssemblyInitializer`를 구현하는 클래스의 구현을 모두 포함합니다. PowerShell 7은 다른 ALC에 로드된 어셈블리에 정의된 형식을 의도적으로 숨기므로 PowerShell에 공개적으로 공개되어야 하는 모든 형식도 여기에서 정의해야 합니다. 마지막으로, 사용자 지정 ALC 정의를 해당 어셈블리에서 정의해야 합니다. 그 외에도 해당 어셈블리에는 최대한 적은 코드가 있어야 합니다.
- 모듈의 실제 구현을 처리하는 엔진 어셈블리 `AlcModule.Engine.dll`.
  해당 어셈블리의 형식은 PowerShell ALC에서 사용할 수 있지만 처음에는 사용자 지정 ALC를 통해 로드됩니다. 해당 종속성은 사용자 지정 ALC에만 로드됩니다. 실제로 해당 종속성은 두 ALC 간에 ‘브리지’가 됩니다.

브리지 개념을 사용하는 새로운 어셈블리 상황은 다음과 같이 표시됩니다.

![두 ALC를 연결하는 AlcModule.Engine.dll을 나타내는 다이어그램](./media/resolving-dependency-conflicts/alc-diagram.jpg)

기본 ALC의 종속성 검색 논리가 사용자 지정 ALC로 로드되는 종속성을 확인하지 않도록 하려면 모듈의 해당하는 두 부분을 서로 다른 디렉터리로 분리해야 합니다. 새 모듈 레이아웃의 구조는 다음과 같습니다.

```
AlcModule/
  AlcModule.Cmdlets.dll
  AlcModule.psd1
  Dependencies/
  | + AlcModule.Engine.dll
  | + Shared.Dependency.dll
```

구현이 어떻게 변경되는지 확인하기 위해 `AlcModule.Engine.dll` 구현부터 시작하겠습니다.

```csharp
using Shared.Dependency;

namespace AlcModule.Engine
{
    public class AlcEngine
    {
        public static void Use()
        {
            Dependency.Use();
        }
    }
}
```

이는 종속성 `Shared.Dependency.dll`의 간단한 컨테이너이지만, 다른 어셈블리의 cmdlet이 PowerShell용으로 래핑하는 기능의 .NET API로 간주해야 합니다.

`AlcModule.Cmdlets.dll`의 cmdlet은 다음과 같이 표시됩니다.

```csharp
// Reference our module's Engine implementation here
using AlcModule.Engine;

namespace AlcModule.Cmdlets
{
    [Cmdlet(VerbsDiagnostic.Test, "AlcModule")]
    public class TestAlcModuleCommand : Cmdlet
    {
        protected override void EndProcessing()
        {
            AlcEngine.Use();
            WriteObject("done!");
        }
    }
}
```

이때 **AlcModule** 을 로드하고 `Test-AlcModule`을 실행하는 경우 기본 ALC가 `Alc.Engine.dll`을 로드하여 `EndProcessing()`을 실행하려고 시도하면 `FileNotFoundException`이 발생합니다. 해당 예외는 기본 ALC가 숨기려는 종속성을 찾을 수 없음을 의미하므로 정상입니다.

이제 `AlcModule.Engine.dll`을 확인하는 방법을 알 수 있도록 `AlcModule.Cmdlets.dll`에 코드를 추가해야 합니다. 먼저 모듈의 `Dependencies` 디렉터리에서 어셈블리를 확인할 사용자 지정 ALC를 정의해야 합니다.

```csharp
namespace AlcModule.Cmdlets
{
    internal class AlcModuleAssemblyLoadContext : AssemblyLoadContext
    {
        private readonly string _dependencyDirPath;

        public AlcModuleAssemblyLoadContext(string dependencyDirPath)
        {
            _dependencyDirPath = dependencyDirPath;
        }

        protected override Assembly Load(AssemblyName assemblyName)
        {
            // We do the simple logic here of
            // looking for an assembly of the given name
            // in the configured dependency directory
            string assemblyPath = Path.Combine(
                _dependencyDirPath,
                $"{assemblyName.Name}.dll");

            // The ALC must use inherited methods to load assemblies
            // Assembly.Load*() won't work here
            return LoadFromAssemblyPath(assemblyPath);
        }
    }
}
```

그런 다음, 사용자 지정 ALC를 기본 ALC의 `Resolving` 이벤트에 연결해야 합니다. 해당 이벤트는 애플리케이션 도메인에서 `AssemblyResolve` 이벤트의 ALC 버전입니다. 해당 이벤트는 `EndProcessing()`이 호출될 때 `AlcModule.Engine.dll`을 찾기 위해 실행됩니다.

```csharp
namespace AlcModule.Cmdlets
{
    public class AlcModuleResolveEventHandler : IModuleAssemblyInitializer, IModuleAssemblyCleanup
    {
        // Get the path of the dependency directory.
        // In this case we find it relative to the AlcModule.Cmdlets.dll location
        private static readonly string s_dependencyDirPath = Path.GetFullPath(
            Path.Combine(
                Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location),
                "Dependencies"));

        private static readonly AlcModuleAssemblyLoadContext s_dependencyAlc = new AlcModuleAssemblyLoadContext(s_dependencyDirPath);

        public void OnImport()
        {
            // Add the Resolving event handler here
            AssemblyLoadContext.Default.Resolving += ResolveAlcEngine;
        }

        public void OnRemove()
        {
          // Remove the Resolving event handler here
          AssemblyLoadContext.Default.Resolving -= ResolveAlcEngine;
        }

        private static Assembly ResolveAlcEngine(
            AssemblyLoadContext defaultAlc,
            AssemblyName assemblyToResolve)
        {
            // We only want to resolve the Alc.Engine.dll assembly here.
            // Because this will be loaded into the custom ALC,
            // all of *its* dependencies will be resolved
            // by the logic we defined for that ALC's implementation.
            //
            // Note that we are safe in our assumption that the name is enough
            // to distinguish our assembly here,
            // since it's unique to our module.
            // There should be no other AlcModule.Engine.dll on the system.
            if (!assemblyToResolve.Name.Equals("AlcModule.Engine"))
            {
                return null;
            }

            // Allow our ALC to handle the directory discovery concept
            //
            // This is where Alc.Engine.dll is loaded into our custom ALC
            // and then passed through into PowerShell's ALC,
            // becoming the bridge between both
            return s_dependencyAlc.LoadFromAssemblyName(assemblyToResolve);
        }
    }
}
```

새 구현에서는 모듈이 로드되고 `Test-AlcModule`이 실행될 때 발생하는 호출의 시퀀스를 살펴보겠습니다.

![사용자 지정 ALC를 사용하여 종속성을 로드하는 호출의 시퀀스 다이어그램](./media/resolving-dependency-conflicts/alc-sequence.png)

몇 가지 관심 지점은 다음과 같습니다.

- `IModuleAssemblyInitializer` 모듈은 `Resolving` 이벤트를 로드 및 설정할 때 먼저 실행됩니다.
- `Test-AlcModule`이 실행되고 해당 `EndProcessing()` 메서드가 호출될 때까지 종속성을 로드하지 않습니다.
- `EndProcessing()`이 호출되면 기본 ALC는 `AlcModule.Engine.dll`을 찾지 못하고 `Resolving` 이벤트를 실행합니다.
- 이벤트 처리기는 사용자 지정 ALC를 기본 ALC에 연결하고 `AlcModule.Engine.dll`만 로드합니다.
- `AlcModule.Engine.dll` 내에서 `AlcEngine.Use()`가 호출되면 사용자 지정 ALC는 다시 `Shared.Dependency.dll`을 확인하기 시작합니다. 특히 기본 ALC의 구성 요소와 충돌하지 않으므로 항상 ‘우리의’ `Shared.Dependency.dll`을 로드하며 `Dependencies` 디렉터리에만 표시됩니다.

구현을 어셈블하면 새 원본 코드 레이아웃이 다음과 같이 표시됩니다.

```
+ AlcModule.psd1
+ src/
  + AlcModule.Cmdlets/
  | + AlcModule.Cmdlets.csproj
  | + TestAlcModuleCommand.cs
  | + AlcModuleAssemblyLoadContext.cs
  | + AlcModuleInitializer.cs
  |
  + AlcModule.Engine/
  | + AlcModule.Engine.csproj
  | + AlcEngine.cs
```

AlcModule.Cmdlets.csproj는 다음과 같이 표시됩니다.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <ProjectReference Include="..\AlcModule.Engine\AlcModule.Engine.csproj" />
    <PackageReference Include="Microsoft.PowerShell.Sdk" Version="7.0.1" PrivateAssets="all" />
  </ItemGroup>
</Project>
```

AlcModule.Engine.csproj는 다음과 같이 표시됩니다.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Shared.Dependency" Version="1.0.0" />
  </ItemGroup>
</Project>
```

따라서 모듈을 빌드할 때 전략은 다음과 같습니다.

- `AlcModule.Engine` 빌드
- `AlcModule.Cmdlets` 빌드
- `AlcModule.Engine`의 모든 항목을 `Dependencies` 디렉터리로 복사하고 복사한 항목 기억
- `AlcModule.Engine`에 없는 `AlcModule.Cmdlets`의 모든 항목을 기본 모듈 디렉터리에 복사

여기서 모듈 레이아웃은 종속성 분리에 매우 중요하므로 원본 루트에서 사용할 빌드 스크립트는 다음과 같습니다.

```powershell
param(
    # The .NET build configuration
    [ValidateSet('Debug', 'Release')]
    [string]
    $Configuration = 'Debug'
)

# Convenient reusable constants
$mod = "AlcModule"
$netcore = "netcoreapp3.1"
$copyExtensions = @('.dll', '.pdb')

# Source code locations
$src = "$PSScriptRoot/src"
$engineSrc = "$src/$mod.Engine"
$cmdletsSrc = "$src/$mod.Cmdlets"

# Generated output locations
$outDir = "$PSScriptRoot/out/$mod"
$outDeps = "$outDir/Dependencies"

# Build AlcModule.Engine
Push-Location $engineSrc
dotnet publish -c $Configuration
Pop-Location

# Build AlcModule.Cmdlets
Push-Location $cmdletsSrc
dotnet publish -c $Configuration
Pop-Location

# Ensure out directory exists and is clean
Remove-Item -Path $outDir -Recurse -ErrorAction Ignore
New-Item -Path $outDir -ItemType Directory
New-Item -Path $outDeps -ItemType Directory

# Copy manifest
Copy-Item -Path "$PSScriptRoot/$mod.psd1"

# Copy each Engine asset and remember it
$deps = [System.Collections.Generic.Hashtable[string]]::new()
Get-ChildItem -Path "$engineSrc/bin/$Configuration/$netcore/publish/" |
    Where-Object { $_.Extension -in $copyExtensions } |
    ForEach-Object { [void]$deps.Add($_.Name); Copy-Item -Path $_.FullName -Destination $outDeps }

# Now copy each Cmdlets asset, not taking any found in Engine
Get-ChildItem -Path "$cmdletsSrc/bin/$Configuration/$netcore/publish/" |
    Where-Object { -not $deps.Contains($_.Name) -and $_.Extension -in $copyExtensions } |
    ForEach-Object { Copy-Item -Path $_.FullName -Destination $outDir }
```

마지막으로, 어셈블리 로드 컨텍스트를 사용하여 더 많은 종속성이 추가되면서 시간이 지남에 따라 강력하게 유지되는 모듈의 종속성을 격리하는 일반적인 방법이 있습니다.

자세한 예제는 관련 [GitHub 리포지토리](https://github.com/rjmholt/ModuleDependencyIsolationExample)를 참조하세요. 이 예제에서는 모듈을 마이그레이션하여 ALC를 사용하면서 .NET Framework에서 해당 모듈이 계속 작동하는 방법을 보여 줍니다. 또한 .NET Standard 및 PowerShell Standard를 사용하여 핵심 구현을 간소화하는 방법을 보여 줍니다.

### <a name="assembly-resolve-handler-for-side-by-side-loading-with-assemblyloadfile"></a>`Assembly.LoadFile()`을 사용하여 나란히 로드를 위한 어셈블리 확인 처리기

나란히 어셈블리 로딩을 수행하는 더 간단할 수 있는 또 다른 방법은 `Assembly.LoadFile()`에 `AssemblyResolve` 이벤트를 연결하는 것입니다. `Assembly.LoadFile()` 사용은 .NET Core 및 .NET Framework를 둘 다 구현하고 사용할 수 있는 가장 간단한 솔루션이라는 이점이 있습니다.

이를 제시하기 위해 동적 바인딩 리디렉션 예제 및 위 어셈블리 로드 컨텍스트 예제의 아이디어를 결합하는 구현의 간단한 예제를 살펴보겠습니다.

Trivial 명령 `Test-LoadFile [-Path] <path>`를 포함하는 **LoadFileModule** 모듈을 호출합니다. 해당 모듈은 `CsvHelper` 어셈블리(버전 15.0.5)에 대한 종속성을 사용합니다.

ALC 모듈과 마찬가지로 먼저 모듈을 두 부분으로 분할해야 합니다.

첫 번째 부분은 실제 구현인 `LoadFileModule.Engine`을 수행합니다.

```csharp
using CsvHelper;

namespace LoadFileModule.Engine
{
    public class Runner
    {
        public void Use(string path)
        {
            // Here's where we use the CsvHelper dependency
            using (var reader = new StreamReader(path))
            using (var csvReader = new CsvReader(reader, CultureInfo.InvariantCulture))
            {
                // Imagine we do something useful here...
            }
        }
    }
}
```

두 번째 부분은 PowerShell이 직접 로드하는 항목인 `LoadFileModule.Cmdlets`입니다. 종속성을 별도 디렉터리에 격리하는 ALC 모듈과 유사한 전략을 사용합니다. 그러나 이번에는 `LoadFileModule.Engine.dll`만이 아니라 확인 이벤트를 사용하여 모든 어셈블리를 로드합니다.

```csharp
using LoadFileModule.Engine;

namespace LoadFileModule.Cmdlets
{
    // Actual cmdlet definition
    [Cmdlet(VerbsDiagnostic.Test, "LoadFile")]
    public class TestLoadFileCommand : Cmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        protected override void EndProcessing()
        {
            // Here's where we use LoadFileModule.Engine
            new Runner().Use(Path);
        }
    }

    // This class controls our dependency resolution
    public class ModuleContextHandler : IModuleAssemblyInitializer, IModuleAssemblyCleanup
    {
        // We catalog our dependencies here to ensure we don't load anything else
        private static IReadOnlyDictionary<string, int> s_dependencies = new Dictionary<string, int>
        {
            { "CsvHelper", 15 },
        };

        // Set up the path to our dependency directory within the module
        private static string s_dependenciesDirPath = Path.GetFullPath(
            Path.Combine(
                Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location),
                "Dependencies"));

        // This makes sure we only try to resolve dependencies when the module is loaded
        private static bool s_engineLoaded = false;

        public void OnImport()
          {
            // Set up our event when the module is loaded
            AppDomain.CurrentDomain.AssemblyResolve += HandleResolveEvent;
        }

        public void OnRemove(PSModuleInfo psModuleInfo)
        {
            // Unset the event when the module is unloaded
            AppDomain.CurrentDomain.AssemblyResolve -= HandleResolveEvent;
        }

        private static Assembly HandleResolveEvent(object sender, ResolveEventArgs args)
        {
            var asmName = new AssemblyName(args.Name);

            // First we want to know if this is the top-level assembly
            if (asmName.Name.Equals("LoadFileModule.Engine"))
            {
                s_engineLoaded = true;
                return Assembly.LoadFile(Path.Combine(s_dependenciesDirPath, "Unrelated.Engine.dll"));
            }

            // Otherwise, if that assembly has been loaded, we must try to resolve its dependencies too
            if (s_engineLoaded
                && s_dependencies.TryGetValue(asmName.Name, out int requiredMajorVersion)
                && asmName.Version.Major == requiredMajorVersion)
            {
                string asmPath = Path.Combine(s_dependenciesDirPath, $"{asmName.Name}.dll");
                return Assembly.LoadFile(asmPath);
            }

            return null;
        }
    }
}
```

마지막으로, 모듈의 레이아웃도 ALC 모듈과 유사합니다.

```
LoadFileModule/
  + LoadFileModule.Cmdlets.dll
  + LoadFileModule.psd1
  + Dependencies/
  |  + LoadFileModule.Engine.dll
  |  + CsvHelper.dll
```

해당 구조가 준비되면 **LoadFileModule** 은 이제 **CsvHelper** 에 대한 종속성을 사용하여 다른 모듈과 함께 로드될 수 있습니다.

해당 처리기는 애플리케이션 도메인 전체에서 **모든** `AssemblyResolve` 이벤트에 적용되므로 다음과 같은 몇 가지 특정 디자인 항목을 선택해야 합니다.

- 이벤트가 다른 로딩을 방해할 수 있는 창을 좁히려면 `LoadFileModule.Engine.dll`이 로드된 후에만 일반 종속성 로딩 처리를 시작합니다.
- `LoadFileModule.Engine.dll`을 종속성 디렉터리에 푸시하면 PowerShell이 아닌 `LoadFile()` 호출을 통해 로드됩니다. 즉, 예를 들어 다른 `CsvHelper.dll`이 PowerShell에 로드된 경우에도 자체 종속성 로드는 항상 `AssemblyResolve` 이벤트를 발생시킵니다.
  이렇게 하면 올바른 종속성을 찾을 수 있습니다.
- 모듈의 특정 종속성만 해결 확인해야 하므로 종속성 이름 및 버전의 사전을 처리기로 코딩해야 합니다. 이 경우 `ResolveEventArgs.RequestingAssembly` 속성을 사용하여 `CsvHelper`가 모듈에서 요청되고 있는지 여부를 확인할 수 있습니다. 그러나 해당 내용은 `CsvHelper` 자체가 `AssemblyResolve` 이벤트를 발생시키는 경우와 같은 종속성의 종속성에는 적용되지 않습니다. `Dependencies` 디렉터리에 있는 어셈블리의 메타데이터에 요청된 어셈블리를 비교하는 등의 더 어려운 다른 방법으로 이 작업을 수행할 수 있습니다. 그러나 이 예제에서는 문제를 강조할 뿐 아니라 예제를 간소화하기 위해 해당 검사를 더 명시적으로 만들었습니다.

이는 `LoadFile()` 전략과 ALC 전략 간 주요 차이점입니다. `AssemblyResolve` 이벤트는 애플리케이션 도메인에서 모든 로드를 처리해야 하므로 종속성 확인이 다른 모듈에 관련되지 않도록 하는 것이 훨씬 더 어렵습니다. 그러나 .NET Framework에 ALC가 없으면 해당 옵션을 이해하는 것이 좋습니다.

### <a name="custom-application-domains"></a>사용자 지정 애플리케이션 도메인

어셈블리 격리의 가장 극단적인 최종 옵션은 사용자 지정 애플리케이션 도메인을 사용하는 것입니다.
애플리케이션 도메인은 .NET Framework에서만 사용할 수 있습니다. .NET 애플리케이션의 부분 간에 In Process 격리를 제공하는 데 사용됩니다. 용도 중 하나는 동일한 프로세스 내에서 어셈블리 로드를 서로 격리하는 것입니다.

그러나 애플리케이션 도메인은 serialization 경계입니다. 한 애플리케이션 도메인의 개체는 다른 애플리케이션 도메인의 개체에서 직접 참조하고 사용할 수 없습니다. `MarshalByRefObject`를 구현하여 해당 문제를 해결할 수 있습니다. 하지만 형식을 제어하지 않는 경우 일반적으로 종속성을 사용하는 경우처럼 여기에는 구현을 적용할 수 없습니다. 유일한 솔루션은 아키텍처를 크게 변경하는 것입니다. Serialization 경계는 성능에도 심각한 영향을 미칩니다.

애플리케이션 도메인에는 이런 심각한 제한 사항이 있고, 구현하기에 복잡하고, .NET Framework에서만 작동하기 때문에 여기서는 사용하는 방법의 예제는 제공하지 않습니다. 가능성으로 언급할 가치가 있지만 권장되지 않습니다.

사용자 지정 애플리케이션 도메인을 사용하려는 경우 다음 링크가 도움이 될 수 있습니다.

- [애플리케이션 도메인에 관한 개념 설명서](/dotnet/framework/app-domains/application-domains)
- [애플리케이션 도메인 사용 예제](/dotnet/framework/app-domains/use)

## <a name="solutions-for-dependency-conflicts-that-dont-work-for-powershell"></a>PowerShell에서 작동하지 않는 종속성 충돌의 솔루션

마지막으로, 유망해 보일 수 있지만 일반적으로 PowerShell에서 작동하지 않는 .NET 종속성 충돌을 .NET에서 조사할 때 나타나는 몇 가지 가능성을 처리합니다.

해당 솔루션에는 애플리케이션 및 가능한 경우 전체 머신을 제어하는 환경에 관한 배포 구성의 변경 내용이라는 일반적인 특징이 있습니다. 해당 솔루션은 웹 서버 및 서버 환경에 배포된 기타 애플리케이션과 같은 시나리오를 기반으로 합니다. 이 경우 환경은 애플리케이션을 호스트하는 데 사용되며 배포하는 사용자가 자유롭게 구성할 수 있습니다. 또한 대부분 .NET Framework를 기반으로 하는 경향이 있으므로 PowerShell 6 이상에서 작동하지 않습니다.

모듈이 전체 제어 권한이 있는 Windows PowerShell 5.1 환경에서만 사용되는 것을 알고 있으면 해당 솔루션 중 일부가 옵션일 수 있습니다. 그러나 일반적으로 **모듈은 이처럼 전역 머신 상태를 수정하면 안 됩니다**. 수정하는 경우 `powershell.exe`에서 문제를 일으키는 구성이 중단되거나 예기치 않게 모듈 실패를 일으키는 기타 종속 애플리케이션이 중단될 수 있습니다.

### <a name="static-binding-redirect-with-appconfig-to-force-using-the-same-dependency-version"></a>동일한 종속성 버전을 강제로 사용하기 위한 app.config를 통한 정적 바인딩 리디렉션

.NET Framework 애플리케이션은 `app.config` 파일을 활용하여 일부 애플리케이션 동작을 선언적으로 구성할 수 있습니다. 어셈블리 로딩을 특정 버전으로 리디렉션하도록 어셈블리 바인딩을 구성하는 `app.config` 항목을 작성할 수 있습니다.

PowerShell에서 해당 솔루션과 관련된 두 가지 문제는 다음과 같습니다.

- .NET Core는 `app.config`를 지원하지 않으므로 해당 솔루션은 `powershell.exe`에만 적용됩니다.
- `powershell.exe`는 `System32` 디렉터리에 있는 공유 애플리케이션입니다. 해당 모듈은 대부분의 시스템에서 관련 콘텐츠를 수정할 수 없을 것입니다. 수정할 수 있더라도 `app.config`를 수정하면 기존 구성이 중단되거나 다른 모듈의 로딩에 영향을 줄 수 있습니다.

### <a name="setting-codebase-with-appconfig"></a>app.config를 사용하여 `codebase` 설정

동일한 이유로 `app.config`에서 `codebase` 설정을 구성하려고 하면 PowerShell 모듈에서 작동하지 않습니다.

### <a name="installing-dependencies-to-the-global-assembly-cache-gac"></a>GAC(전역 어셈블리 캐시)에 종속성 설치

.NET Framework에서 종속성 버전 충돌을 해결하는 또 다른 방법은 GAC에서 다양한 버전을 나란히 로드할 수 있도록 GAC에 종속성을 설치하는 것입니다.

PowerShell 모듈의 경우 주요 문제는 다음과 같습니다.

- GAC는 .NET Framework에만 적용되므로 PowerShell 6 이상에서는 해당 방법이 도움이 되지 않습니다.
- GAC에 어셈블리를 설치하는 것은 전역 머신 상태를 수정하는 것이며 다른 애플리케이션 또는 다른 모듈에서 부작용을 일으킬 수 있습니다. 또한 모듈에 필요한 액세스 권한이 있는 경우에도 작업을 제대로 수행하기 어려울 수 있습니다. 작업이 잘못되면 다른 .NET 애플리케이션에서 머신 전체의 문제가 발생할 수 있습니다.

## <a name="further-reading"></a>추가 정보

.NET 어셈블리 버전 종속성 충돌에 관한 많은 자료를 참조할 수 있습니다. 몇 가지 좋은 출발점은 다음과 같습니다.

- [.NET: .NET의 어셈블리](/dotnet/standard/assembly/)
- [.NET Core: 관리형 어셈블리 로딩 알고리즘](/dotnet/core/dependency-loading/loading-managed)
- [.NET Core: System.Runtime.Loader.AssemblyLoadContext 이해](/dotnet/core/dependency-loading/understanding-assemblyloadcontext)
- [.NET Core: 나란히 어셈블리 로딩 솔루션에 관한 설명](https://github.com/dotnet/runtime/issues/13471)
- [.NET Framework: 어셈블리 버전 리디렉션](/dotnet/framework/configure-apps/redirect-assembly-versions)
- [.NET Framework: 어셈블리 로딩 모범 사례](/dotnet/framework/deployment/best-practices-for-assembly-loading)
- [.NET Framework: 런타임에서 어셈블리를 찾는 방법](/dotnet/framework/deployment/how-the-runtime-locates-assemblies)
- [.NET Framework: 어셈블리 로드 확인](/dotnet/standard/assembly/resolve-loads)
- [StackOverflow: 어셈블리 바인딩 리디렉션, 방법 및 이유](https://stackoverflow.com/questions/43365736/assembly-binding-redirect-how-and-why)
- [PowerShell: AssemblyLoadContexts 구현에 관한 설명](https://github.com/PowerShell/PowerShell/issues/11571)
- [PowerShell: `Assembly.LoadFile()`이 기본 AssemblyLoadContext에 로드되지 않음](https://github.com/PowerShell/PowerShell/issues/12052)
- [Rick Strahl: .NET 어셈블리 종속성이 로드되는 시기는 언제인가요?](https://weblog.west-wind.com/posts/2012/Nov/03/Back-to-Basics-When-does-a-NET-Assembly-Dependency-get-loaded)
- [Jon Skeet: .NET의 버전 지정 요약](https://codeblog.jonskeet.uk/2019/06/30/versioning-limitations-in-net/)
- [Nate McMaster: .NET Core 기본 형식에 관해 자세히 알아보기](https://natemcmaster.com/blog/2017/12/21/netcore-primitives/)
