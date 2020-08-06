---
title: 기본 Windows PowerShell 공급자 만들기 | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- base provider [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], base provider
ms.openlocfilehash: 16cadb6099bb4f315bacda4aea617b89f9af5626
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787226"
---
# <a name="creating-a-basic-windows-powershell-provider"></a>기본 Windows PowerShell 공급자 만들기

이 항목은 Windows PowerShell 공급자를 만드는 방법을 배우는 시작점입니다. 여기서 설명 하는 기본 공급자는 공급자를 시작 하 고 중지 하는 방법을 제공 합니다 .이 공급자는 데이터 저장소에 액세스 하거나 데이터 저장소의 데이터를 가져오거나 설정 하는 방법을 제공 하지 않지만 모든 공급자가 필요로 하는 기본 기능을 제공 합니다.

앞에서 설명한 대로 여기에 설명 된 기본 공급자는 공급자를 시작 및 중지 하기 위한 메서드를 구현 합니다. Windows PowerShell 런타임에서는 이러한 메서드를 호출 하 여 공급자를 초기화 하 고 초기화 합니다.

> [!NOTE]
> 이 공급자의 샘플은 Windows PowerShell에서 제공 하는 AccessDBSampleProvider01.cs 파일에서 찾을 수 있습니다.

## <a name="defining-the-windows-powershell-provider-class"></a>Windows PowerShell 공급자 클래스 정의

Windows PowerShell 공급자를 만드는 첫 번째 단계는 해당 .NET 클래스를 정의 하는 것입니다. 이 기본 공급자는 `AccessDBProvider` [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) 클래스에서 파생 되는 이라는 클래스를 정의 합니다.

`Providers`API 네임 스페이스 (예: xxx)의 네임 스페이스에 공급자 클래스를 추가 하는 것이 좋습니다. PowerShell. 공급자. 이 공급자는 `Microsoft.Samples.PowerShell.Provider` 모든 Windows PowerShell 공급자 샘플이 실행 되는 네임 스페이스를 사용 합니다.

> [!NOTE]
> Windows PowerShell 공급자에 대 한 클래스는 명시적으로 public으로 표시 되어야 합니다. Public으로 표시 되지 않은 클래스는 기본적으로 내부로 표시 되 고 Windows PowerShell 런타임에서 찾을 수 없습니다.

이 기본 공급자에 대 한 클래스 정의는 다음과 같습니다.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs" range="23-24":::

클래스 정의 바로 앞에 [CmdletProvider ()] 구문을 사용 하 여 [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) 특성을 선언 해야 합니다.

필요한 경우 특성 키워드를 설정 하 여 클래스를 추가로 선언할 수 있습니다. 여기에 선언 된 [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) 특성에는 두 개의 매개 변수가 포함 됩니다. 첫 번째 특성 매개 변수는 사용자가 나중에 수정할 수 있는 공급자의 기본 이름을 지정 합니다. 두 번째 매개 변수는 명령을 처리 하는 동안 공급자가 Windows PowerShell 런타임에 노출 하는 Windows PowerShell 정의 기능을 지정 합니다. 공급자 기능에 사용할 수 있는 값은 [system.web](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) .. x m m. 이 공급자는 기본 공급자 이므로 기능을 지원 하지 않습니다.

> [!NOTE]
> Windows PowerShell 공급자의 정규화 된 이름에는 공급자를 등록할 때 Windows PowerShell에서 결정 한 어셈블리 이름 및 기타 특성이 포함 됩니다.

## <a name="defining-provider-specific-state-information"></a>공급자별 상태 정보 정의

Windows PowerShell 런타임이 필요한 경우에만 공급자 인스턴스를 만들기 때문에 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) 및 모든 파생 클래스는 상태 비저장으로 간주 됩니다. 따라서 공급자에 게 공급자별 데이터에 대 한 모든 권한 및 상태 유지 관리가 필요한 경우 [Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) 클래스에서 클래스를 파생 해야 합니다. 파생 된 클래스는 상태를 유지 관리 하는 데 필요한 멤버를 정의 해야 합니다. 이렇게 하면 Windows PowerShell 런타임에서 공급자를 초기화할 때 공급자 특정 데이터에 액세스할 수 [있습니다.](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)

Windows PowerShell 공급자는 연결 기반 상태를 유지할 수도 있습니다. 연결 상태를 유지 관리 하는 방법에 대 한 자세한 내용은 [PowerShell 드라이브 공급자 만들기](./creating-a-windows-powershell-drive-provider.md)를 참조 하세요.

## <a name="initializing-the-provider"></a>공급자 초기화

Windows powershell이 시작 될 때 공급자를 초기화 하기 위해 Windows PowerShell 런타임에서는 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) 를 호출 합니다. 대부분의 경우 공급자는이 메서드의 기본 구현을 사용할 수 있습니다 .이 메서드는 공급자를 설명 하는 [Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) 개체를 반환 하기만 합니다. 그러나 추가 초기화 정보를 추가 하려는 경우에는 공급자에 전달 되는 [Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) 개체의 수정 된 버전을 반환 하는 고유한 [system.web](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) .. n a m a. i n a m. 일반적으로이 메서드는 전달 된 [Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) 개체 또는 다른 초기화 정보를 포함 하는 수정 된 [Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) 개체를 반환 해야 합니다.

이 기본 공급자는이 메서드를 재정의 하지 않습니다. 그러나 다음 코드는이 메서드의 기본 구현을 보여 줍니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStart](Msh_samplesaccessdbprov01#accessdbprov01ProviderStart)]  -->

공급자는 공급자별 [데이터 상태 정의](#defining-provider-specific-state-information)에 설명 된 대로 공급자별 정보의 상태를 유지할 수 있습니다. 이 경우, 구현에서 파생 클래스의 인스턴스를 반환 하려면 System.object를 재정의 하 여 다시 [시작](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) 해야 합니다.

## <a name="start-dynamic-parameters"></a>동적 매개 변수 시작

공급자를 구현 [하는 경우](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) 에는 추가 매개 변수가 필요할 수 있습니다. 이 경우 공급자는 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.StartDynamicParameters) 를 재정의 하 고 cmdlet 클래스 또는 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체와 유사한 구문 분석 특성을 가진 속성 및 필드가 있는 개체를 반환 해야 하는 경우를 반환 합니다.

이 기본 공급자는이 메서드를 재정의 하지 않습니다. 그러나 다음 코드는이 메서드의 기본 구현을 보여 줍니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters](Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters)]  -->

## <a name="uninitializing-the-provider"></a>공급자 초기화

Windows PowerShell 공급자가 사용 하는 리소스를 해제 하려면 공급자가 자체의 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Stop) 를 구현 해야 합니다. 이 메서드는 세션을 닫을 때 공급자의 초기화를 취소 하기 위해 Windows PowerShell 런타임에서 호출 됩니다.

이 기본 공급자는이 메서드를 재정의 하지 않습니다. 그러나 다음 코드는이 메서드의 기본 구현을 보여 줍니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStop](Msh_samplesaccessdbprov01#accessdbprov01ProviderStop)]  -->

## <a name="code-sample"></a>코드 예제

전체 샘플 코드는 [AccessDbProviderSample01 코드 샘플](./accessdbprovidersample01-code-sample.md)을 참조 하세요.

## <a name="testing-the-windows-powershell-provider"></a>Windows PowerShell 공급자 테스트

Windows powershell 공급자를 Windows PowerShell에 등록 한 후에는 명령줄에서 지원 되는 cmdlet을 실행 하 여 테스트할 수 있습니다. 이 기본 공급자의 경우 새 셸을 실행 하 고 cmdlet을 사용 `Get-PSProvider` 하 여 공급자 목록을 검색 하 고 AccessDb 공급자가 있는지 확인 합니다.

```powershell
Get-PSProvider
```

다음 출력이 표시됩니다.

```Output
Name                 Capabilities                  Drives
----                 ------------                  ------
AccessDb             None                          {}
Alias                ShouldProcess                 {Alias}
Environment          ShouldProcess                 {Env}
FileSystem           Filter, ShouldProcess         {C, Z}
Function             ShouldProcess                 {function}
Registry             ShouldProcess                 {HKLM, HKCU}
```

## <a name="see-also"></a>참고 항목

[Windows PowerShell 공급자 만들기](./how-to-create-a-windows-powershell-provider.md)

[Windows PowerShell 공급자 설계](./designing-your-windows-powershell-provider.md)
