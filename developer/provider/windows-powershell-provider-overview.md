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
ms.openlocfilehash: 0d4addc0a064873701ae15c204dbd335f3374ab7
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795626"
---
# <a name="windows-powershell-provider-overview"></a>Windows PowerShell 공급자 개요

Windows PowerShell 공급자를 통해 모든 데이터 저장소를 탑재 된 드라이브 것 처럼 파일 시스템과 마찬가지로 노출 될 수 있습니다. 예를 들어, 기본 제공 레지스트리 공급자 있습니다 탐색할 때와 같은 레지스트리를 탐색 하는 `c` 컴퓨터의 드라이브. 공급자를 재정의할 수도 있습니다는 `Item` cmdlet (예를 들어 `Get-Item`, `Set-Item`등) 파일과 같은 데이터 저장소의 데이터를 처리할 수 있습니다 하 고 디렉터리를 파일 시스템을 탐색 하면 처리 됩니다. 공급자 및 드라이브를 Windows PowerShell에서 기본 제공 공급자에 대 한 자세한 내용은 참조 하세요. [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers)합니다.

## <a name="providers-and-drives"></a>공급자 및 드라이브

공급자를 액세스, 탐색 및 드라이브 공급자에 의해 정의 된 형식의 데이터 저장소 (또는 데이터 저장소의 일부)는 특정 항목 위치를 지정 하는 동안 데이터 저장소를 편집 하는 데 사용 되는 논리를 정의 합니다. 예를 들어 레지스트리 공급자를 사용 하면 하이브와 레지스트리에 키를 액세스할 수 있습니다 하 고 드라이브 HKLM 및 HKCU 레지스트리 내 해당 하이브를 지정 합니다. HKLM 및 HKCU 드라이브 레지스트리 공급자를 사용합니다.

공급자를 작성할 때 기본 드라이브 드라이브 공급자가 사용할 수 있는 때 자동으로 생성 되는 지정할 수 있습니다. 해당 공급자를 사용 하는 새 드라이브를 만드는 메서드를 정의할 수도 있습니다.

## <a name="type-of-providers"></a>공급자의 형식

여러 유형의 다른 수준의 기능을 제공 하는 각 공급자 있습니다. 공급자의 하위 항목 중 하나에서 파생 되는 클래스로 구현 되는 [System.Management.Automation.Sessionstatecategory.Cmdletprovider](/dotnet/api/System.Management.Automation.SessionStateCategory.CmdletProvider) 클래스입니다. 다양 한 유형의 공급자에 대 한 정보를 참조 하세요 [공급자 유형을](./provider-types.md)합니다.

## <a name="provider-cmdlets"></a>공급자 cmdlet

공급자는 공급자에 대 한 드라이브에서 사용 하는 경우 이러한 cmdlet에 대 한 사용자 지정 동작 만들기 cmdlet에 해당 하는 메서드를 구현할 수 있습니다. 공급자의 형식에 따라 cmdlet의 다른 집합을 사용할 수 있습니다. 사용자 지정 공급자에서 사용할 수 있는 cmdlet의 전체 목록은 참조 하세요 [공급자 cmdlet](./provider-cmdlets.md)합니다.

## <a name="provider-paths"></a>공급자 경로

사용자가 같은 파일 시스템 공급자 드라이브를 이동합니다. 이 인해 파일 시스템 탐색에 사용 되는 경로에 해당 하는 경로 구문의 기대 합니다. 사용자가 공급자 cmdlet을 실행 하는 경우 이러한 항목에 액세스할 수에 대 한 경로 지정 합니다. 지정 된 경로 여러 가지 방법으로 해석할 수 있습니다. 공급자는 다음 경로 형식 중 하나 이상을 지원 해야 합니다.

### <a name="drive-qualified-paths"></a>드라이브의 정규화 된 경로

드라이브의 정규화 된 경로 항목 이름, 컨테이너 및 항목의 위치를 가리키는, 하위 컨테이너 항목이 액세스 될 Windows PowerShell 드라이브의 조합입니다. (드라이브는 데이터 저장소에 액세스 하는 데 사용 되는 공급자에 의해 정의 됩니다. 이 경로 드라이브 이름 뒤에 콜론 (:)를 사용 하 여 시작 합니다. 예를 들면 다음과 같습니다. `get-childitem C:`

### <a name="provider-qualified-paths"></a>공급자의 정규화 된 경로

초기화 하 고 공급자를 초기화 하는 Windows PowerShell 엔진을 허용 하려면 공급자는 공급자의 정규화 된 경로 지원 해야 합니다. 사용자 수 초기화 하 고 다음 공급자의 정규화 된 경로 정의 하기 때문에 파일 시스템 공급자를 초기화 하는 예를 들어: `FileSystem::\\uncshare\abc\bar`합니다.

### <a name="provider-direct-paths"></a>공급자 직접 경로

Windows PowerShell 공급자에 대 한 원격 액세스를 허용 하려면 현재 위치에 대 한 Windows PowerShell 공급자에 직접 전달 하도록 공급자 직접 경로 지원 해야 합니다. Windows PowerShell 레지스트리 공급자가 사용할 수 예를 들어 `\\server\regkeypath` 공급자 직접 경로로 합니다.

### <a name="provider-internal-paths"></a>내부 공급자 경로

공급자 cmdlet이 Windows PowerShell이 아닌 Api (응용 프로그래밍 인터페이스)를 사용 하 여 데이터 액세스를 허용 하려면 Windows PowerShell 공급자는 공급자-내부 경로 지원 해야 합니다. 후이 경로 표시 합니다 "::" 공급자의 정규화 된 경로에 있습니다. 예를 들어 filesystem Windows PowerShell 공급자 공급자-내부 경로 `\\uncshare\abc\bar`합니다.

## <a name="overriding-cmdlet-parameters"></a>Cmdlet 매개 변수를 재정의합니다.

공급자가 일부 공급자 특정 cmdlet의 동작을 재정의할 수 있습니다. 재정의할 수 있는 매개 변수 목록을 공급자 클래스에서 재정의 하는 방법에 대 한 참조 [공급자 cmdlet 매개 변수](./provider-cmdlet-parameters.md)

## <a name="dynamic-parameters"></a>동적 매개 변수

공급자는 cmdlet의 정적 매개 변수 중 하나에 대 한 특정 값을 지정할 때 공급자 cmdlet에 추가 되는 동적 매개 변수를 정의할 수 있습니다. 공급자는 하나 이상의 동적 매개 변수 메서드를 구현 하 여이 수행 합니다. 동적 매개 변수 및 구현 하는 데 사용 된 메서드를 추가 하는 cmdlet 매개 변수 목록을 참조 하세요 [공급자 cmdlet 동적 매개 변수](./provider-cmdlet-dynamic-parameters.md)합니다.

## <a name="provider-capabilities"></a>공급자 기능

합니다 [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거형은 다양 한 공급자에서 지원할 수 있는 기능을 정의 합니다. 여기에 트랜잭션을 지원 사용 하 여 와일드 카드, 항목을 필터링 하는 기능이 포함 됩니다. 기능 공급자를 지정 하려면 값의 목록을 추가 합니다 [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 논리 결합 열거형 `OR` 작업으로는 [ System.Management.Automation.Provider.Cmdletproviderattribute.Providercapabilities*](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities) 는 두 번째 매개 변수인 특성의 속성을 [System.Management.Automation.Provider.Cmdletproviderattribute ](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) 공급자 클래스에 대 한 특성입니다. 공급자를 지원 한다는 다음 특성을 지정 하는 예를 들어 합니다 [System.Management.Automation.Provider.Providercapabilities.Shouldprocess](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities.ShouldProcess) 고 [ System.Management.Automation.Provider.Providercapabilities.Transactions](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities.Transactions) 기능입니다.

```csharp
[CmdletProvider(RegistryProvider.ProviderName, ProviderCapabilities.ShouldProcess | ProviderCapabilities.Transactions)]

```

## <a name="provider-cmdlet-help"></a>공급자 cmdlet 도움말

공급자를 작성할 때 지 공급자 cmdlet에 대 한 도움말을 직접 구현할 수 있습니다. 각 공급자 cmdlet 또는 동적 매개 변수 사용에 따라 다르게 경우 공급자 cmdlet의 작동에 대 한 도움말 항목의 여러 버전에 대 한 단일 도움말 항목을 포함 합니다. 공급자 cmdlet 관련 도움말을 지원 하려면 공급자를 구현 해야 합니다 [System.Management.Automation.Provider.Icmdletprovidersupportshelp](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp) 인터페이스입니다.

Windows PowerShell 엔진 호출을 [System.Management.Automation.Provider.Icmdletprovidersupportshelp.Gethelpmaml*](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp.GetHelpMaml) 공급자 cmdlet에 대 한 도움말 항목을 표시 하는 방법입니다. 엔진이 실행 하는 경우 사용자 지정 cmdlet의 이름을 제공 합니다 `Get-Help` cmdlet 및 사용자의 현재 경로입니다. 공급자는 서로 다른 드라이브에 대 한 동일한 공급자 cmdlet의 다른 버전을 구현 하는 경우 현재 경로가 필요 합니다. 메서드는 cmdlet 도움말에 대 한 XML이 포함 된 문자열을 반환 해야 합니다.

도움말 파일에 대 한 콘텐츠 PSMAML XML을 사용 하 여 기록 됩니다. 독립 실행형 cmdlet에 대 한 도움말 콘텐츠를 작성에 사용 되는 동일한 XML 스키마입니다. 사용자 지정 cmdlet 도움말 파일을 공급자에 대 한 도움말에 대 한 콘텐츠를 추가 합니다. 아래는 `CmdletHelpPaths` 요소입니다. 다음 예제와 `command` 요소에 대 한 단일 공급자 cmdlet 공급자 cmdlet의 이름을 지정 하는 방법을 보여 줍니다는 공급자입니다. 지원

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