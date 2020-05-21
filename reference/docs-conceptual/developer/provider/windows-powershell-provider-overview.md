---
title: Windows PowerShell 공급자 개요 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82244fbd-07b9-47f3-805c-3fb90ebbf58a
caps.latest.revision: 13
ms.openlocfilehash: 9f1b94e722e59e707a26547949c661b5098d29e0
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560953"
---
# <a name="windows-powershell-provider-overview"></a>Windows PowerShell 공급자 개요

Windows PowerShell 공급자를 사용 하면 모든 데이터 저장소가 탑재 된 드라이브인 것 처럼 파일 시스템 처럼 노출 될 수 있습니다. 예를 들어 기본 제공 레지스트리 공급자를 사용 하 여 컴퓨터 드라이브를 탐색 하는 것 처럼 레지스트리를 탐색할 수 있습니다 `c` . 공급자는 `Item` `Get-Item` `Set-Item` 파일 시스템을 탐색할 때 파일 및 디렉터리가 처리 되는 것 처럼 데이터 저장소의 데이터를 처리할 수 있도록 cmdlet (예:, 등)을 재정의할 수도 있습니다. 공급자 및 드라이브 및 Windows PowerShell의 기본 제공 공급자에 대 한 자세한 내용은 [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers)를 참조 하세요.

## <a name="providers-and-drives"></a>공급자 및 드라이브

공급자는 데이터 저장소에 액세스 하 고, 탐색 하 고, 편집 하는 데 사용 되는 논리를 정의 하는 반면, 드라이브는 공급자가 정의한 형식의 데이터 저장소 또는 데이터 저장소의 일부에 대 한 특정 진입점을 지정 합니다. 예를 들어 레지스트리 공급자를 사용 하 여 레지스트리의 hive와 키에 액세스할 수 있으며 HKLM 및 HKCU 드라이브는 레지스트리 내에서 해당 하이브를 지정 합니다. HKLM 및 HKCU 드라이브는 모두 레지스트리 공급자를 사용 합니다.

공급자를 작성할 때 공급자를 사용할 수 있을 때 자동으로 생성 되는 기본 드라이브 드라이브를 지정할 수 있습니다. 또한 메서드를 정의 하 여 해당 공급자를 사용 하는 새 드라이브를 만듭니다.

## <a name="type-of-providers"></a>공급자 유형

각각 서로 다른 수준의 기능을 제공 하는 여러 유형의 공급자가 있습니다. 공급자는 [SessionStateCategory](/dotnet/api/system.management.automation.sessionstatecategory?view=pscore-6.2.0) **cmdletprovider** 클래스의 하위 항목 중 하나에서 파생 되는 클래스로 구현 됩니다. 다양 한 공급자 유형에 대 한 자세한 내용은 [공급자 유형](./provider-types.md)을 참조 하세요.

## <a name="provider-cmdlets"></a>공급자 cmdlet

공급자는 cmdlet에 해당 하는 메서드를 구현 하 여 해당 공급자의 드라이브에서 사용 되는 경우 해당 cmdlet에 대 한 사용자 지정 동작을 만들 수 있습니다. 공급자 유형에 따라 다양 한 cmdlet 집합을 사용할 수 있습니다. 공급자에서 사용자 지정에 사용할 수 있는 cmdlet의 전체 목록은 [공급자 cmdlet](./provider-cmdlets.md)을 참조 하세요.

## <a name="provider-paths"></a>공급자 경로

사용자는 파일 시스템과 같은 공급자 드라이브를 탐색 합니다. 이로 인해 경로 구문이 파일 시스템 탐색에 사용 되는 경로에 해당 하는 것으로 간주 됩니다. 사용자는 공급자 cmdlet을 실행할 때 액세스할 항목에 대 한 경로를 지정 합니다. 지정 된 경로는 여러 가지 방법으로 해석할 수 있습니다. 공급자는 다음 경로 유형을 하나 이상 지원 해야 합니다.

### <a name="drive-qualified-paths"></a>드라이브 정규화 된 경로

드라이브 정규화 된 경로는 항목 이름, 항목이 있는 컨테이너 및 하위 컨테이너, 항목에 액세스 하는 데 사용할 Windows PowerShell 드라이브의 조합입니다. (드라이브는 데이터 저장소에 액세스 하는 데 사용 되는 공급자에 의해 정의 됩니다. 이 경로는 드라이브 이름 뒤에 콜론 (:)으로 시작 합니다. 예: `get-childitem C:`

### <a name="provider-qualified-paths"></a>공급자 정규화 경로

Windows PowerShell 엔진이 공급자를 초기화 하 고 초기화 하지 못하게 하려면 공급자는 공급자의 정규화 된 경로를 지원 해야 합니다. 예를 들어 사용자는 다음과 같은 공급자 한정 경로를 정의 하기 때문에 FileSystem 공급자를 초기화 하 고 초기화 취소할 수 있습니다 `FileSystem::\\uncshare\abc\bar` .

### <a name="provider-direct-paths"></a>공급자-직접 경로

Windows PowerShell 공급자에 대 한 원격 액세스를 허용 하려면 현재 위치에 대 한 Windows PowerShell 공급자에 직접 전달 하는 공급자 직접 경로를 지원 해야 합니다. 예를 들어 Windows PowerShell 공급자는 공급자 직접 경로로를 사용할 수 있습니다 `\\server\regkeypath` .

### <a name="provider-internal-paths"></a>공급자-내부 경로

공급자 cmdlet이 비 Windows PowerShell Api (응용 프로그래밍 인터페이스)를 사용 하 여 데이터에 액세스할 수 있도록 하려면 Windows PowerShell 공급자가 공급자 내부 경로를 지원 해야 합니다. 이 경로는 공급자 정규화 경로의 "::" 뒤에 표시 됩니다. 예를 들어 filesystem Windows PowerShell 공급자에 대 한 공급자 내부 경로는 `\\uncshare\abc\bar` 입니다.

## <a name="overriding-cmdlet-parameters"></a>Cmdlet 매개 변수 재정의

공급자에 따라 특정 cmdlet의 동작을 재정의할 수 있습니다. 재정의할 수 있는 매개 변수 목록 및 공급자 클래스에서 재정의 하는 방법에 대해서는 [provider cmdlet 매개 변수](./provider-cmdlet-parameters.md) 를 참조 하세요.

## <a name="dynamic-parameters"></a>동적 매개 변수

공급자는 사용자가 cmdlet의 정적 매개 변수 중 하나에 대해 특정 값을 지정할 때 공급자 cmdlet에 추가 되는 동적 매개 변수를 정의할 수 있습니다. 공급자는 동적 매개 변수 메서드를 하나 이상 구현 하 여이를 수행 합니다. 동적 매개 변수를 추가 하는 데 사용할 수 있는 cmdlet 매개 변수 목록 및 해당 매개 변수를 구현 하는 데 사용 되는 메서드는 [Provider cmdlet 동적 매개 변수](./provider-cmdlet-dynamic-parameters.md)를 참조 하세요.

## <a name="provider-capabilities"></a>공급자 기능

[System.object](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 는 공급자가 지원할 수 있는 많은 기능을 정의 합니다. 여기에는 와일드 카드, 필터 항목 및 지원 트랜잭션을 사용 하는 기능이 포함 됩니다. 공급자에 대 한 기능을 지정 하려면 [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) `OR` 공급자 클래스에 대 한 [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) 특성의 [Cmdletproviderattribute *](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities) 속성 (특성의 두 번째 매개 변수)으로 논리 작업과 함께 사용 되는 system.object의 값 목록을 추가 합니다 (특성의 두 번째 매개 변수를 사용 하는 방법) .입니다. 예를 들어 다음 특성은 공급자가 [system.object](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities?view=pscore-6.2.0) 를 지원 하는지 여부를 지정 하 고, **Shouldprocess** 및 [system.object](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities?view=pscore-6.2.0) 의 **트랜잭션** 기능을 지원 합니다.

```csharp
[CmdletProvider(RegistryProvider.ProviderName, ProviderCapabilities.ShouldProcess | ProviderCapabilities.Transactions)]

```

## <a name="provider-cmdlet-help"></a>공급자 cmdlet 도움말

공급자를 작성할 때 지원 되는 공급자 cmdlet에 대 한 고유한 도움말을 구현할 수 있습니다. 여기에는 동적 매개 변수 사용에 따라 공급자 cmdlet이 다르게 작동 하는 경우에 대 한 도움말 항목의 각 공급자 cmdlet 또는 여러 버전에 대 한 단일 도움말 항목이 포함 됩니다. 공급자 cmdlet에 대 한 도움말을 지원 하려면 공급자가 [Icmdletprovidersupportshelp](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp) 인터페이스를 구현 해야 합니다.

Windows PowerShell 엔진은 [Icmdletprovidersupportshelp. Gethelpmaml *](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp.GetHelpMaml) 메서드를 호출 하 여 공급자 cmdlet에 대 한 도움말 항목을 표시 합니다. 엔진은 사용자가 cmdlet을 실행할 때 지정한 cmdlet의 이름과 `Get-Help` 사용자의 현재 경로를 제공 합니다. 현재 경로는 공급자가 다른 드라이브에 대해 동일한 공급자 cmdlet의 다른 버전을 구현 하는 경우에 필요 합니다. 메서드는 cmdlet 도움말의 XML이 포함 된 문자열을 반환 해야 합니다.

도움말 파일의 콘텐츠는 PSMAML XML을 사용 하 여 작성 됩니다. 이는 독립 실행형 cmdlet에 대 한 도움말 콘텐츠를 작성 하는 데 사용 되는 XML 스키마와 동일 합니다. 사용자 지정 cmdlet 도움말의 콘텐츠를 요소의 공급자에 대 한 도움말 파일에 추가 합니다 `CmdletHelpPaths` . 다음 예에서는 `command` 단일 공급자 cmdlet에 대 한 요소를 보여 주고 공급자의 공급자 cmdlet 이름을 지정 하는 방법을 보여 줍니다. 에서는 앱 스토어의 앱, 웹 응용 프로그램 및 회사 내부에서 직접 작성한 앱 등

```xml
<CmdletHelpPaths>
  <command:command>
    <command:details>
      <command:name>ProviderCmdletName</command:name>
      <command:verb>Verb</command:verb>
      <command:noun>Noun</command:noun>
    <command:details>
  </command:command>
<CmdletHelpPath>
```

## <a name="see-also"></a>참고 항목

[Windows PowerShell 공급자 기능](./provider-types.md)

[공급자 Cmdlet](./provider-cmdlets.md)

[Windows PowerShell 공급자 작성](./writing-a-windows-powershell-provider.md)
