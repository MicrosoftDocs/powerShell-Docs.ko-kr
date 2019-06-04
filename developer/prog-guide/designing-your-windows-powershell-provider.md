---
title: Windows PowerShell 공급자 디자인 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide], designing
ms.assetid: 11d20319-cc40-4227-b810-4af33372b182
caps.latest.revision: 10
ms.openlocfilehash: 711a85e9b2eade7b9095d7560f53610e709e380a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081821"
---
# <a name="designing-your-windows-powershell-provider"></a>Windows PowerShell 공급자 설계

귀하의 제품이 나 구성 하려는 사용자를 탐색 하거나 이동할 데이터베이스와 같은 저장 된 데이터 집합을 노출 하는 경우에 Windows PowerShell 공급자를 구현 해야 합니다. 또한 다단계 컨테이너가 없는 경우에 컨테이너를 제공 하는 제품, Windows PowerShell 공급자를 구현 하는 것이 수 있습니다. 예를 들어, 다음 cmdlet 동사 복사, 이동, 이름 바꾸기, 새로운 또는 Remove 어떤지에 제품 또는 구성 데이터에 대 한 작업으로 Windows PowerShell 컨테이너 공급자를 구현 하는 것이 좋습니다.

## <a name="windows-powershell-paths-identify-your-provider"></a>Windows PowerShell 경로 공급자를 식별합니다.

Windows PowerShell 경로 사용 하 여 적절 한 Windows PowerShell 공급자에 액세스 하는 Windows PowerShell 런타임입니다. Cmdlet 이러한 경로 중 하나를 지정 하는 경우 런타임에서 연결 된 데이터 저장소에 액세스 하는 데는 공급자입니다. 이러한 경로 드라이브의 정규화 된 경로, 공급자의 정규화 된 경로, 공급자 직접 경로 및 공급자-내부 경로 포함 합니다. 각 Windows PowerShell 공급자는 이러한 경로 중 하나 이상을 지원 해야 합니다.

Windows PowerShell 경로 대 한 자세한 내용은 Windows PowerShell 작동 방식을 참조 하세요.

### <a name="defining-a-drive-qualified-path"></a>드라이브의 정규화 된 경로 정의합니다.

사용자가 실제 드라이브에 있는 데이터에 액세스할 수 있도록 Windows PowerShell 공급자에는 드라이브의 정규화 된 경로 지원 해야 합니다. 이 경로 드라이브 이름 뒤에 콜론 (:), 예를 들어 mydrive:\abc\bar 사용 하 여 시작 합니다.

### <a name="defining-a-provider-qualified-path"></a>공급자의 정규화 된 경로 정의합니다.

초기화 하 고 공급자 초기화를 취소 하도록 Windows PowerShell 런타임에 허용 하려면 Windows PowerShell 공급자는 공급자의 정규화 된 경로 지원 해야 합니다. 예를 들어 FileSystem::\\\uncshare\abc\bar는 Windows PowerShell에서 제공한 파일 시스템 공급자에 대 한 공급자의 정규화 된 경로입니다.

### <a name="defining-a-provider-direct-path"></a>직접 공급자 경로 정의합니다.

Windows PowerShell 공급자에 대 한 원격 액세스를 허용 하려면 현재 위치에 대 한 Windows PowerShell 공급자에 직접 전달 하도록 공급자 직접 경로 지원 해야 합니다. Windows PowerShell 레지스트리 공급자가 사용할 수 예를 들어 \\공급자 직접 경로로 \server\regkeypath 합니다.

### <a name="defining-a-provider-internal-path"></a>내부 공급자 경로 정의합니다.

공급자 cmdlet이 Windows PowerShell이 아닌 Api (응용 프로그래밍 인터페이스)를 사용 하 여 데이터 액세스를 허용 하려면 Windows PowerShell 공급자는 공급자-내부 경로 지원 해야 합니다. 후이 경로 표시 합니다 "::" 공급자의 정규화 된 경로에 있습니다. 예를 들어 filesystem Windows PowerShell 공급자 공급자-내부 경로 \\\uncshare\abc\bar 합니다.

## <a name="changing-stored-data"></a>저장 된 데이터를 변경합니다.

내부 데이터 저장소를 수정 하는 메서드를 재정의할 때 항상 호출 합니다 [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) 에서 변경 된 항목의 최신 버전을 사용 하 여 메서드 메서드입니다. 공급자 인프라 항목 개체를 사용자-PassThru 매개 변수를 지정 하는 경우 같은 파이프라인으로 전달 해야 하는지 여부를 결정 합니다. 최신 항목을 검색 하는 비용이 많이 드는 작업 (성능 관점에서 보면) 하는 경우 실제로 결과 항목을 작성 해야 하는 경우 결정 Context.PassThru 속성을 테스트할 수 있습니다.

## <a name="choose-a-base-class-for-your-provider"></a>공급자에 대 한 기본 클래스를 선택 합니다.

Windows PowerShell에는 여러 고유한 Windows PowerShell 공급자를 구현 하는 데 사용할 수 있는 기본 클래스를 제공 합니다. 공급자를 디자인할 때 요구 사항에 가장 적합 한이 섹션에 설명 된 기본 클래스를 선택 합니다.

각 Windows PowerShell 공급자 기본 클래스는 cmdlet 집합을 사용할 수 있습니다. 이 섹션에서는 cmdlet을 설명 하지만 해당 매개 변수를 설명 하지 않습니다.

세션 상태를 사용 하는 Windows PowerShell 런타임에 여러 위치 cmdlet를 사용할 수 있게 특정 Windows PowerShell 공급자와 같은 합니다 `Get-Location`, `Set-Location`를 `Pop-Location`, 및 `Push-Location` cmdlet. 사용할 수는 `Get-Help` cmdlet은 이러한 위치 cmdlet에 대 한 정보를 가져오려고 합니다.

### <a name="cmdletprovider-base-class"></a>CmdletProvider 기본 클래스

합니다 [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) 클래스는 기본 Windows PowerShell 공급자를 정의 합니다. 이 클래스는 공급자 선언을 지원 하 고 다양 한 속성 및 모든 Windows PowerShell 공급자에 사용할 수 있는 방법을 제공 합니다. 클래스에서 호출 되는 `Get-PSProvider` 세션에 대 한 모든 사용 가능한 공급자를 나열 하는 cmdlet입니다. 세션 상태에 따라 제공 되는이 cmdlet의 구현입니다.

> [!NOTE]
> Windows PowerShell 공급자는 모든 Windows PowerShell 언어 범위에 사용할 수 있습니다.

### <a name="drivecmdletprovider-base-class"></a>DriveCmdletProvider 기본 클래스

합니다 [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 클래스, 새 드라이브를 추가 하 고, 기존 드라이브를 제거 하 고, 기본 드라이브 초기화에 대 한 작업을 지 원하는 Windows PowerShell 드라이브 공급자를 정의 합니다. 예를 들어, Windows PowerShell에서 제공 되는 파일 시스템 공급자 드라이브와 같은 하드 드라이브와 CD/DVD 장치 드라이브 탑재 되는 모든 볼륨을 초기화 합니다.

이 클래스에서 파생 된 [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) 기본 클래스입니다. 다음 표에서이 클래스에 의해 노출 cmdlet을 나열 합니다. 표에 제공 된 것 외에도 `Get-PSDrive` cmdlet (세션 상태에 따라 노출 됨)는 사용 가능한 드라이브를 검색 하는 데 사용 되는 관련된 cmdlet.

|Cmdlet|정의|
|------------|----------------|
|`New-PSDrive`|세션에 대해 새 드라이브를 만들고 드라이브 정보를 스트리밍합니다.|
|`Remove-PSDrive`|세션에서 드라이브를 제거합니다.|

### <a name="itemcmdletprovider-base-class"></a>ItemCmdletProvider 기본 클래스

합니다 [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 클래스는 데이터 저장소의 개별 항목에 대 한 작업을 수행 하 여 Windows PowerShell 항목 공급자를 정의 하 고 모든 컨테이너를 가정 하지는 않습니다 또는 탐색 기능입니다. 이 클래스에서 파생 된 [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 기본 클래스입니다. 다음 표에서이 클래스에 의해 노출 cmdlet을 나열 합니다.

|Cmdlet|정의|
|------------|----------------|
|`Clear-Item`|지정된 된 위치에 항목의 현재 내용을 지우고 공급자가 지정한 "지우기" 값으로 바꿉니다. 경우가 아니면이 cmdlet은 파이프라인을 통해 출력 개체를 통과 하지 못하면 해당 `PassThru` 매개 변수를 지정 합니다.|
|`Get-Item`|지정된 된 위치에서 항목을 검색 하 고 결과 개체를 스트리밍합니다.|
|`Invoke-Item`|지정된 된 경로에 있는 항목에 대 한 기본 작업을 호출합니다.|
|`Set-Item`|표시 된 값을 사용 하 여 지정된 된 위치에 항목을 설정합니다. 경우가 아니면이 cmdlet은 파이프라인을 통해 출력 개체를 통과 하지 못하면 해당 `PassThru` 매개 변수를 지정 합니다.|
|`Resolve-Path`|Windows PowerShell 경로 및 스트림 경로 정보에 대 한 와일드 카드를 확인합니다.|
|`Test-Path`|지정된 된 경로 대 한 테스트 하 고 반환 `true` 존재 하는 경우 및 `false` 그렇지 않은 경우. 이 cmdlet을 지원 하도록 구현 된 `IsContainer` 에 대 한 매개 변수를 [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) 메서드.|

### <a name="containercmdletprovider-base-class"></a>ContainerCmdletProvider 기본 클래스

합니다 [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 클래스 사용자에 게 데이터 저장소 항목에 대 한 컨테이너를 노출 하는 Windows PowerShell 컨테이너 공급자를 정의 합니다. 하나의 컨테이너 (중첩 된 컨테이너 없음) 항목을 사용 하 여 필요한 경우에 Windows PowerShell 컨테이너 공급자를 사용할 수 있는지 알아야 합니다. 중첩 된 컨테이너의 경우 Windows PowerShell 탐색 공급자를 구현 해야 합니다.

이 클래스에서 파생 된 [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 기본 클래스입니다. 다음 표에서이 클래스에서 구현 하는 cmdlet을 정의 합니다.

|Cmdlet|정의|
|------------|----------------|
|`Copy-Item`|한 위치에서 다른 항목을 복사 합니다. 경우가 아니면이 cmdlet은 파이프라인을 통해 출력 개체를 통과 하지 못하면 해당 `PassThru` 매개 변수를 지정 합니다.|
|`Get-Childitem`|지정 된 위치의 자식 항목을 검색 하 고 개체로 스트리밍합니다.|
|`New-Item`|지정된 된 위치에 새 항목을 만들고 결과 개체를 스트림 합니다.|
|`Remove-Item`|지정된 된 위치에서 항목을 제거합니다.|
|`Rename-Item`|지정 된 위치에 있는 항목을 이름을 바꿉니다. 경우가 아니면이 cmdlet은 파이프라인을 통해 출력 개체를 통과 하지 못하면 해당 `PassThru` 매개 변수를 지정 합니다.|

### <a name="navigationcmdletprovider-base-class"></a>NavigationCmdletProvider 기본 클래스

합니다 [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 클래스 둘 이상의 컨테이너를 사용 하는 항목에 대 한 작업을 수행 하는 Windows PowerShell 탐색 공급자를 정의 합니다. 이 클래스에서 파생 된 [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 기본 클래스입니다. 다음 표에서이 클래스에 의해 노출 되는 cmdlet을 나열 합니다.

|Cmdlet|정의|
|------------|----------------|
|경로 결합|두 개의 경로 경로 간의 공급자별 구분 기호를 사용 하 여 단일 경로 결합 합니다. 이 cmdlet은 문자열을 스트리밍합니다.|
|`Move-Item`|지정된 된 위치에 항목을 이동합니다. 경우가 아니면이 cmdlet은 파이프라인을 통해 출력 개체를 통과 하지 못하면 해당 `PassThru` 매개 변수를 지정 합니다.|

관련된 cmdlet은 Windows PowerShell에서 제공한 기본 구문 분석 경로 cmdlet. 이 cmdlet을 지원 하기 위해 Windows PowerShell 경로 구문 분석에 사용할 수 있습니다는 `Parent` 매개 변수입니다. 부모 경로 문자열을 스트리밍합니다.

## <a name="select-provider-interfaces-to-support"></a>지원 공급자 인터페이스를 선택 합니다.

Windows PowerShell 기본 클래스 중 하나에서 파생을 하는 것 외에도 Windows PowerShell 공급자는 하나 이상의 다음 공급자 인터페이스에서 파생 하 여 다른 기능을 지원할 수 있습니다. 이 섹션에서는 이러한 인터페이스 및 각에서 지 원하는 cmdlet을 정의 합니다. 인터페이스를 지 원하는 cmdlet에 대 한 매개 변수를 설명 하지는 않습니다. Cmdlet 매개 변수 정보를 사용 하 여 온라인 사용할 수는 `Get-Command` 고 `Get-Help` cmdlet.

### <a name="icontentcmdletprovider"></a>IContentCmdletProvider

합니다 [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 인터페이스는 데이터 항목의 내용에 작업을 수행 하는 콘텐츠 공급자를 정의 합니다. 다음 표에서이 인터페이스에서 노출 된 cmdlet을 나열 합니다.

|Cmdlet|정의|
|------------|----------------|
|`Add-Content`|지정된 된 항목의 내용에 표시 된 값 길이 추가합니다. 경우가 아니면이 cmdlet은 파이프라인을 통해 출력 개체를 통과 하지 못하면 해당 `PassThru` 매개 변수를 지정 합니다.|
|`Clear-Content`|값 "지우기"를 지정된 된 항목의 콘텐츠를 설정합니다. 경우가 아니면이 cmdlet은 파이프라인을 통해 출력 개체를 통과 하지 못하면 해당 `PassThru` 매개 변수를 지정 합니다.|
|`Get-Content`|지정된 된 항목의 콘텐츠를 검색 하 고 결과 개체를 스트리밍합니다.|
|`Set-Content`|지정된 된 항목에 대 한 기존 콘텐츠를 대체합니다. 경우가 아니면이 cmdlet은 파이프라인을 통해 출력 개체를 통과 하지 못하면 해당 `PassThru` 매개 변수를 지정 합니다.|

### <a name="ipropertycmdletprovider"></a>IPropertyCmdletProvider

합니다 [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) 인터페이스 데이터 저장소에서 항목의 속성에 대 한 작업을 수행 하는 속성의 Windows PowerShell 공급자를 정의 합니다. 다음 표에서이 인터페이스에서 노출 된 cmdlet을 나열 합니다.

> [!NOTE]
> `Path` 이러한 cmdlet에 매개 변수 속성을 식별 하는 대신 항목에 대 한 경로 나타냅니다.

|Cmdlet|정의|
|------------|----------------|
|`Clear-ItemProperty`|값 "지우기"를 지정된 된 항목의 속성을 설정 합니다. 경우가 아니면이 cmdlet은 파이프라인을 통해 출력 개체를 통과 하지 못하면 해당 `PassThru` 매개 변수를 지정 합니다.|
|`Get-ItemProperty`|지정된 된 항목의 속성을 검색 하 고 결과 개체를 스트리밍합니다.|
|`Set-ItemProperty`|표시 된 값을 사용 하 여 지정된 된 항목의 속성을 설정 합니다. 경우가 아니면이 cmdlet은 파이프라인을 통해 출력 개체를 통과 하지 못하면 해당 `PassThru` 매개 변수를 지정 합니다.|

### <a name="idynamicpropertycmdletprovider"></a>IDynamicPropertyCmdletProvider

합니다 [System.Management.Automation.Provider.Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) 에서 파생 된 인터페이스 [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider), 정의 지원 되는 해당 cmdlet에 대 한 동적 매개 변수를 지정 하는 공급자입니다. 이 유형의 공급자는 새 속성 작업을 예를 들어 런타임에 속성을 정의할 수 있는 작업을 처리 합니다. 이러한 작업 항목 속성을 정적으로 정의 하지 가능 하지 않습니다. 다음 표에서이 인터페이스에서 노출 된 cmdlet을 나열 합니다.

|Cmdlet|정의|
|------------|----------------|
|`Copy-ItemProperty`|다른 항목에 지정된 된 항목에서 속성을 복사합니다. 경우가 아니면이 cmdlet은 파이프라인을 통해 출력 개체를 통과 하지 못하면 해당 `PassThru` 매개 변수를 지정 합니다.|
|`Move-ItemProperty`|지정된 된 항목에서 속성을 다른 항목으로 이동합니다. 경우가 아니면이 cmdlet은 파이프라인을 통해 출력 개체를 통과 하지 못하면 해당 `PassThru` 매개 변수를 지정 합니다.|
|`New-ItemProperty`|지정된 된 항목에 속성을 생성 하 고 결과 개체를 스트리밍합니다.|
|`Remove-ItemProperty`|지정된 된 항목에 대 한 속성을 제거합니다.|
|`Rename-ItemProperty`|지정된 된 항목의 속성을 이름을 바꿉니다. 경우가 아니면이 cmdlet은 파이프라인을 통해 출력 개체를 통과 하지 못하면 해당 `PassThru` 매개 변수를 지정 합니다.|

### <a name="isecuritydescriptorcmdletprovider"></a>ISecurityDescriptorCmdletProvider

합니다 [System.Management.Automation.Provider.Isecuritydescriptorcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ISecurityDescriptorCmdletProvider) 인터페이스 공급자에 보안 설명자 기능을 추가 합니다. 이 인터페이스에서에서 가져오기 및 설정 항목에 대 한 보안 설명자 정보가 데이터 저장소에 있습니다. 다음 표에서이 인터페이스에서 노출 된 cmdlet을 나열 합니다.

|Cmdlet|정의|
|------------|----------------|
|`Get-Acl`|예를 들어 운영 체제 리소스를 보호 하는 데 보안 설명자, 파일 또는 개체의 일부인는 액세스 제어 목록 (ACL)에 포함 된 정보를 검색 합니다.|
|`Set-Acl`|ACL에 대 한 정보를 설정합니다. 인스턴스의 형태로 것 [System.Security.Accesscontrol.Objectsecurity](/dotnet/api/System.Security.AccessControl.ObjectSecurity) 지정된 된 경로에 지정 된 항목의 합니다. Windows PowerShell 공급자의 보안 정보 설정을 지 원하는 경우이 cmdlet 레지스트리 또는 다른 공급자 항목을 파일, 키 및 하위 키에 대 한 정보를 설정할 수 있습니다.|

## <a name="see-also"></a>참고 항목

[Windows PowerShell 공급자 만들기](./how-to-create-a-windows-powershell-provider.md)

[Windows PowerShell의 작동 원리](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Windows PowerShell SDK](../windows-powershell-reference.md)