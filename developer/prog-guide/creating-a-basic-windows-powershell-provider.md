---
title: 기본 Windows PowerShell 공급자 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- base provider [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], base provider
ms.assetid: 11eeea41-15c8-47ad-9016-0f4b72573305
caps.latest.revision: 7
ms.openlocfilehash: 19cc3817016d96e1412a5f3506e9d694ba55b48d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861769"
---
# <a name="creating-a-basic-windows-powershell-provider"></a>기본 Windows PowerShell 공급자 만들기

이 항목은 Windows PowerShell 공급자를 만드는 방법을 학습 하기 위한 시작 지점입니다. 여기에 설명 된 기본 공급자를 시작 및 중지를 공급자에 대 한 메서드를 제공 하 고이 공급자는 데이터 저장소에 액세스 하려면 또는 가져오기 또는 데이터 저장소에서 데이터를 설정 하는 수단을 제공 하지 않습니다., 하지만에 필요한 기본 기능을 제공지 않습니다. 모든 공급자입니다.

이전에 설명 된 기본 공급자를 설명한 것 처럼 여기 시작 및 중지 공급자에 대 한 메서드를 구현 합니다. Windows PowerShell 런타임을 초기화 하 고 공급자를 초기화 합니다. 이러한 메서드를 호출 합니다.

> [!NOTE]
> Windows PowerShell에서 제공 되는 AccessDBSampleProvider01.cs 파일에서이 공급자의 샘플을 찾을 수 있습니다.

이 항목의 섹션은 다음과 같습니다.

- [Windows PowerShell 공급자 클래스를 정의합니다.](#Defining-the-Windows-PowerShell-Provider-Class)

- [공급자 관련 상태 정보를 정의합니다.](#Defining-Provider-Specific-State-Information)

- [공급자를 초기화합니다.](#Initializing-the-Provider)

- [동적 매개 변수를 시작 합니다.](#Start-Dynamic-Parameters)

- [공급자 초기화 취소](#Uninitializing-the-Provider)

- [코드 샘플](#Code-Sample)

- [Windows PowerShell 공급자 테스트](#Testing-the-Windows-PowerShell-Provider)

## <a name="defining-the-windows-powershell-provider-class"></a>Windows PowerShell 공급자 클래스를 정의합니다.

Windows PowerShell 공급자를 만드는 첫 번째 단계는 해당.NET 클래스를 정의 하는 것입니다. 이 기본 공급자 라는 클래스를 정의 `AccessDBProvider` 에서 파생 되는 [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) 기본 클래스입니다.

공급자 클래스를 배치 하는 것이 좋습니다는 `Providers` xxx 예를 들어 API 네임 스페이스의 네임 스페이스입니다. PowerShell.Providers 합니다. 이 공급자가 사용 하 여 `Microsoft.Samples.PowerShell.Provider` 네임 스페이스에 있는 모든 Windows PowerShell 공급자 샘플을 실행 합니다.

> [!NOTE]
> Windows PowerShell 공급자에 대 한 클래스 해야 명시적으로 공용으로 표시 되어야 합니다. 공용으로 표시 되지 않은 클래스는 기본적으로 내부 및 Windows PowerShell 런타임에 의해 찾을 수 없습니다.

이 기본 공급자에 대 한 클래스 정의 다음과 같습니다.

[!code-csharp[AccessDBProviderSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L23-L24 "AccessDBProviderSample01.cs")]

클래스 정의 직전 선언 해야 합니다 [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) [CmdletProvider()] 구문 사용 하 여 특성입니다.

필요한 경우 추가 클래스를 선언 하려면 키워드 특성을 설정할 수 있습니다. 다음에 유의 합니다 [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) 여기에 선언 된 특성에는 두 매개 변수가 포함 됩니다. 첫 번째 특성 매개 변수는 사용자가 나중에 수정할 수 있는 공급자에 대 한 기본 이름을 지정 합니다. 두 번째 매개 변수는 명령 처리 하는 동안 공급자가 Windows PowerShell 런타임에 노출 하는 Windows PowerShell 정의 기능을 지정 합니다. 공급자 기능에 대 한 가능한 값은 정의한 합니다 [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거형입니다. 기본 공급자 이기 때문에 없는 기능을 지원 합니다.

> [!NOTE]
> Windows PowerShell 공급자의 정규화 된 이름을 어셈블리 이름 및 공급자를 등록 하면 Windows PowerShell에서 결정 하는 다른 특성을 포함 합니다.

## <a name="defining-provider-specific-state-information"></a>공급자 관련 상태 정보를 정의합니다.

합니다 [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) 기본 클래스와 모든 파생된 클래스는 상태 비저장으로 간주 되므로 Windows PowerShell 런타임에 필요한 만큼만 공급자 인스턴스를 만듭니다. 따라서 공급자에 게 완전 한 제어 및 상태 유지 관리 공급자 관련 데이터에 필요한 경우 클래스에서 파생 되어야 합니다는 [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) 클래스입니다. 파생된 클래스는 Windows PowerShell 런타임에 호출 하는 경우 공급자 특정 데이터에 액세스할 수 있도록 상태를 유지 하는 데 필요한 멤버를 정의 해야 합니다 [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) 공급자를 초기화 하는 방법입니다.

Windows PowerShell 공급자는 연결 기반 상태를 유지할 수도 수 있습니다. 연결 상태를 유지 하는 방법에 대 한 자세한 내용은 참조 하세요. [PowerShell 드라이브 공급자 만들기](./creating-a-windows-powershell-drive-provider.md)합니다.

## <a name="initializing-the-provider"></a>공급자를 초기화합니다.

Windows PowerShell 런타임 호출 공급자를 초기화 합니다 [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) Windows PowerShell이 시작 될 때 메서드. 공급자 단순히 반환 하는이 메서드의 기본 구현은 사용 하는 대부분의 경우는 [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) 공급자를 설명 하는 개체입니다. 그러나 추가 초기화 정보를 추가 하려는 경우 구현 해야 사용자 고유의 [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) 합니다 의수정된된버전을반환하는메서드[ System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) 공급자에 전달 되는 개체입니다. 일반적으로이 메서드는 제공 된 반환할지 [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) 개체 또는 수정 된 전달할 [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) 개체 다른 초기화 정보를 포함합니다.

이 기본 공급자는이 메서드를 재정의 하지 않습니다. 그러나 다음 코드는이 메서드의 기본 구현을 보여 줍니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStart](Msh_samplesaccessdbprov01#accessdbprov01ProviderStart)]  -->

에 설명 된 대로 공급자의 공급자별 정보 상태를 유지 관리할 수 있습니다 [정의 공급자별 데이터 상태](#Defining-Provider-Specific-State-Information)합니다. 이 경우 구현 재정의 해야 합니다 [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) 파생된 클래스의 인스턴스를 반환 하는 방법입니다.

## <a name="start-dynamic-parameters"></a>동적 매개 변수를 시작 합니다.

공급자 구현 된 [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) 메서드 추가 매개 변수가 필요 합니다. 이 경우 공급자를 재정의 해야 합니다 [System.Management.Automation.Provider.Cmdletprovider.Startdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.StartDynamicParameters) 메서드와 반환 된 속성 및 필드를 구문 분석 하는 개체 특성 비슷합니다는 cmdlet 클래스 또는 [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체입니다.

이 기본 공급자는이 메서드를 재정의 하지 않습니다. 그러나 다음 코드는이 메서드의 기본 구현을 보여 줍니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters](Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters)]  -->

## <a name="uninitializing-the-provider"></a>공급자 초기화 취소

Windows PowerShell 공급자를 사용 하는 리소스를 확보 하기 위해 공급자에 구현 해야 자체 [System.Management.Automation.Provider.Cmdletprovider.Stop*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Stop) 메서드. 이 메서드는 세션을 종료할 때 공급자 초기화를 취소 하려면 Windows PowerShell 런타임에 의해 호출 됩니다.

이 기본 공급자는이 메서드를 재정의 하지 않습니다. 그러나 다음 코드는이 메서드의 기본 구현을 보여 줍니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStop](Msh_samplesaccessdbprov01#accessdbprov01ProviderStop)]  -->

## <a name="code-sample"></a>코드 예제

전체 샘플 코드를 보려면 [AccessDbProviderSample01 코드 샘플](./accessdbprovidersample01-code-sample.md)합니다.

## <a name="testing-the-windows-powershell-provider"></a>Windows PowerShell 공급자 테스트

Windows PowerShell을 사용 하 여 Windows PowerShell 공급자가 등록 되 면 명령줄에서 지원 되는 cmdlet을 실행 하 여 테스트할 수 있습니다. 이 기본 공급자에 대 한 새 셸을 실행 하 고 사용 된 `Get-PSProvider` cmdlet 공급자 목록을 가져와 AccessDb 공급자 있는지 확인 합니다.

```powershell
Get-PSProvider
```

다음과 같은 출력이 나타납니다.

```output
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

[Windows PowerShell 공급자를 디자인합니다.](./designing-your-windows-powershell-provider.md)