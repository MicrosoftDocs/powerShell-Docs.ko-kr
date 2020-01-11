---
title: Windows PowerShell 탐색 공급자 만들기
ms.date: 09/13/2016
ms.topic: article
ms.assetid: 8bd3224d-ca6f-4640-9464-cb4d9f4e13b1
ms.openlocfilehash: 96a9167019c047bb9c6e56362b2c1110ece553dd
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870696"
---
# <a name="creating-a-windows-powershell-navigation-provider"></a>Windows PowerShell 탐색 공급자 만들기

이 항목에서는 데이터 저장소를 탐색할 수 있는 Windows PowerShell 탐색 공급자를 만드는 방법에 대해 설명 합니다. 이 유형의 공급자는 재귀 명령, 중첩 된 컨테이너 및 상대 경로를 지원 합니다.

> [!NOTE]
> Windows Vista 및 .NET Framework C# 3.0 런타임 구성 요소에 대 한 Microsoft Windows 소프트웨어 개발 키트를 사용 하 여이 공급자에 대 한 원본 파일 (AccessDBSampleProvider05.cs)을 다운로드할 수 있습니다. 다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/scripting/developer/installing-the-windows-powershell-sdk)을 참조 하세요.
> 다운로드 된 원본 파일은 **\<PowerShell Samples >** 디렉터리에서 사용할 수 있습니다. 다른 Windows PowerShell 공급자 구현에 대 한 자세한 내용은 [Windows Powershell 공급자 디자인](./designing-your-windows-powershell-provider.md)을 참조 하세요.

여기에 설명 된 공급자를 사용 하면 사용자가 데이터베이스의 데이터 테이블로 이동할 수 있도록 Access 데이터베이스를 드라이브로 처리할 수 있습니다. 사용자 고유의 탐색 공급자를 만들 때 탐색에 필요한 드라이브 한정 경로를 설정 하 고, 상대 경로를 정규화 하 고, 데이터 저장소의 항목을 이동 하 고, 자식 이름을 가져오는 메서드와 항목의 부모 경로를 가져오고, 테스트 하는 메서드를 구현할 수 있습니다. 항목이 컨테이너 인지 여부를 식별 합니다.

> [!CAUTION]
> 이 설계에서는 이름이 ID가 인 필드가 있는 데이터베이스를 가정 하 고 해당 필드의 형식은가 중 정수 라는 것을 알고 있어야 합니다.

## <a name="define-the-windows-powershell-provider"></a>Windows PowerShell 공급자 정의

Windows PowerShell 탐색 공급자는 [system.object](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 클래스에서 파생 되는 .net 클래스를 만들어야 합니다. 이 섹션에서 설명 하는 탐색 공급자에 대 한 클래스 정의는 다음과 같습니다.

[!code-csharp[AccessDBProviderSample05.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L31-L32
"AccessDBProviderSample05.cs")]

이 공급자에서 [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) 특성에는 두 개의 매개 변수가 포함 되어 있습니다. 첫 번째 매개 변수는 Windows PowerShell에서 사용 되는 공급자에 대 한 친숙 한 이름을 지정 합니다. 두 번째 매개 변수는 명령을 처리 하는 동안 공급자가 Windows PowerShell 런타임에 노출 하는 Windows PowerShell 특정 기능을 지정 합니다. 이 공급자의 경우 추가 되는 Windows PowerShell 관련 기능이 없습니다.

## <a name="defining-base-functionality"></a>기본 기능 정의

[PS 공급자 디자인](./designing-your-windows-powershell-provider.md)에 설명 된 대로 다른 공급자 기능을 제공 하는 다른 여러 클래스에서 [파생 됩니다.](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 따라서 Windows PowerShell 탐색 공급자는 해당 클래스에서 제공 하는 기능을 모두 정의 해야 합니다.

세션 관련 초기화 정보를 추가 하 고 공급자가 사용 하는 리소스를 해제 하는 기능을 구현 하려면 [기본 PS 공급자 만들기](./creating-a-basic-windows-powershell-provider.md)를 참조 하세요. 그러나 여기에 설명 된 공급자를 비롯 한 대부분의 공급자는 Windows PowerShell에서 제공 하는이 기능의 기본 구현을 사용할 수 있습니다.

Windows PowerShell 드라이브를 통해 데이터 저장소에 대 한 액세스 권한을 얻으려면 [system.object](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 의 메서드를 구현 해야 합니다... 이러한 메서드를 구현 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 드라이브 공급자 만들기](./creating-a-windows-powershell-drive-provider.md)를 참조 하세요.

항목 가져오기, 설정 및 지우기와 같은 데이터 저장소의 항목을 조작 하려면 공급자는 [system.object](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 에서 제공 하는 메서드를 구현 해야 합니다. 이러한 메서드를 구현 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 항목 공급자 만들기](./creating-a-windows-powershell-item-provider.md)를 참조 하세요.

항목을 만들고, 복사 하 고, 이름을 바꾸고, 제거 하는 메서드 뿐만 아니라 자식 항목 또는 데이터 저장소의 이름을 가져오려면 [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 기본 클래스에서 제공 하는 메서드를 구현 해야 합니다. 이러한 메서드를 구현 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 컨테이너 공급자 만들기](./creating-a-windows-powershell-container-provider.md)를 참조 하세요.

## <a name="creating-a-windows-powershell-path"></a>Windows PowerShell 경로 만들기

Windows PowerShell 탐색 공급자는 공급자 내부 Windows PowerShell 경로를 사용 하 여 데이터 저장소의 항목을 탐색 합니다. 공급자 내부 경로를 만들려면 공급자가 Combine 경로 [*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) 메서드를 구현 하 여 Combine path cmdlet의 호출을 지원 해야 합니다. 이 메서드는 부모 및 자식 경로 사이에 공급자별 경로 구분 기호를 사용 하 여 부모 및 자식 경로를 공급자 내부 경로로 결합 합니다.

기본 구현에서는 경로 구분 기호로 "/" 또는 "\\" 인 경로를 사용 하 고, 경로 구분 기호를 "\\"로 정규화 하 고, 부모 및 자식 경로 부분을 두 요소 사이의 구분 기호와 결합 한 다음 조합 된 경로를 포함 하는 문자열을 반환 합니다.

이 탐색 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는 System.object의 기본 구현입니다. [Makecmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) 메서드를 제공 합니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermakepath](Msh_samplestestcmdlets#testprovidermakepath)]  -->

#### <a name="things-to-remember-about-implementing-makepath"></a>MakePath 구현에 대해 기억할 사항

다음 조건은 System.object의 구현에 적용 될 수 있습니다. [Makecmdletprovider *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath):

- [System.object](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) 의 구현에서는 공급자 네임 스페이스의 올바른 정규화 된 경로로 경로의 유효성을 검사 하면 안 됩니다 .이 메서드를 구현 해야 합니다. 각 매개 변수는 경로의 일부만 나타낼 수 있고 결합 된 부분은 정규화 된 경로를 생성 하지 않을 수 있습니다. 예를 들어 filesystem 공급자에 대 한 windows\system32 매개 변수는 "" `parent`에서 ""를 수신 하 고 filesystem 공급자에 대 한 매개 변수에서 "`child` abc"를 [받을 수 있습니다](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) . 메서드는 "\\" 구분 기호를 사용 하 여 이러한 값을 조인 하 고 정규화 된 파일 시스템 경로가 아닌 "windows\system32\abc.dll"를 반환 합니다.

  > [!IMPORTANT]
  > System.object에 대 한 호출에 제공 된 경로 부분입니다 [. makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) 는 공급자 네임 스페이스에 허용 되지 않는 문자를 포함할 수 있습니다. 이러한 문자는 와일드 카드 확장에 사용 되며,이 메서드를 구현 하면 이러한 문자를 제거 하면 안 됩니다.

## <a name="retrieving-the-parent-path"></a>부모 경로를 검색 하는 중

Windows PowerShell 탐색 공급자는 표시 된 전체 또는 부분 공급자별 경로의 부모 파트를 검색 하는 [Getparentpath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) 메서드를 구현 합니다. 메서드는 경로의 자식 부분을 제거 하 고 부모 경로 부분을 반환 합니다. `root` 매개 변수는 드라이브의 루트에 대 한 정규화 된 경로를 지정 합니다. 탑재 된 드라이브가 검색 작업에 사용 되 고 있지 않으면이 매개 변수는 null 이거나 비어 있을 수 있습니다. 루트가 지정 된 경우 메서드는 루트와 동일한 트리의 컨테이너에 대 한 경로를 반환 해야 합니다.

샘플 탐색 공급자는이 메서드를 재정의 하지 않지만 기본 구현을 사용 합니다.
"/" 및 "\\"를 모두 경로 구분 기호로 사용 하는 경로를 허용 합니다. 먼저 "\\" 구분 기호를 포함 하도록 경로를 정규화 한 다음 마지막 "\\"에서 부모 경로를 분할 하 고 부모 경로를 반환 합니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetparentpath](Msh_samplestestcmdlets#testprovidergetparentpath)]  -->

#### <a name="to-remember-about-implementing-getparentpath"></a>GetParentPath 구현에 대 한 자세한 내용은

[Getparentpath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) 메서드를 구현 하는 경우 공급자 네임 스페이스에 대 한 경로 구분 기호에서 경로를 어휘 단위로 분할 해야 합니다. 예를 들어 파일 시스템 공급자는이 메서드를 사용 하 여 마지막 "\\"을 검색 하 고 구분 기호 왼쪽에 있는 모든 항목을 반환 합니다.

## <a name="retrieve-the-child-path-name"></a>자식 경로 이름 검색

탐색 공급자는 표시 된 전체 또는 부분 공급자별 경로에 있는 항목의 자식에 대 한 이름 (리프 요소)을 검색 하는 [Getchildname *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) 메서드를 구현 합니다.

샘플 탐색 공급자는이 메서드를 재정의 하지 않습니다. 기본 구현은 다음과 같습니다. "/" 및 "\\"를 모두 경로 구분 기호로 사용 하는 경로를 허용 합니다. 먼저 "\\" 구분 기호를 포함 하도록 경로를 정규화 한 다음 마지막 "\\"에서 부모 경로를 분할 하 고 자식 경로 부분의 이름을 반환 합니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildname](Msh_samplestestcmdlets#testprovidergetchildname)]  -->

#### <a name="things-to-remember-about-implementing-getchildname"></a>GetChildName 구현에 대해 기억할 사항

[Getchildname *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) 메서드를 구현 하면 경로 구분 기호에서 경로를 어휘 적으로 분할 해야 합니다. 제공 된 경로에 경로 구분 기호가 포함 되어 있지 않으면이 메서드는 수정 되지 않은 경로를 반환 해야 합니다.

> [!IMPORTANT]
> 이 메서드에 대 한 호출에 제공 된 경로에 공급자 네임 스페이스에 잘못 된 문자가 포함 되어 있을 수 있습니다. 이러한 문자는 와일드 카드 확장 또는 정규식 일치에 사용 될 수 있으며,이 메서드를 구현 하면 이러한 문자를 제거 하면 안 됩니다.

## <a name="determining-if-an-item-is-a-container"></a>항목이 컨테이너 인지 확인

탐색 공급자는 지정 된 경로가 컨테이너를 표시 하는지 확인 하기 위해 [Isitemcontainer *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) 메서드를 구현할 수 있습니다. 경로가 컨테이너를 나타내면 true를 반환 하 고 그렇지 않으면 false를 반환 합니다. 사용자는 제공 된 경로에 대해 `Test-Path` cmdlet을 사용 하려면이 메서드가 필요 합니다.

다음 코드는 샘플 탐색 공급자의 [Isitemcontainer *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) 구현을 보여 줍니다 .이 예제에서는 메서드는 지정 된 경로가 올바른지 그리고 테이블이 있는지 확인 하 고 경로가 컨테이너를 나타내는 경우 true를 반환 합니다.

[!code-csharp[AccessDBProviderSample05.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L847-L872 "AccessDBProviderSample05.cs")]

#### <a name="things-to-remember-about-implementing-isitemcontainer"></a>IsItemContainer 구현에 대해 기억할 사항

탐색 공급자 .NET 클래스가 ExpandWildcards, Filter, Include 또는 Exclude의 공급자 기능을 [system.object](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거에서 선언할 수 있습니다. 이 경우에는 전달 된 경로가 요구 사항을 충족 하는지 확인 하기 위해 [Isitemcontainer *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) 를 구현 해야 합니다. 이 작업을 수행 하려면 메서드가 적절 한 속성 (예: [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) )에 액세스 해야 합니다.

## <a name="moving-an-item"></a>항목 이동

`Move-Item` cmdlet을 지원 하기 위해 탐색 공급자는 [Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 메서드를 구현 합니다. 이 메서드는 `path` 매개 변수로 지정 된 항목을 `destination` 매개 변수에 제공 된 경로의 컨테이너로 이동 합니다.

샘플 탐색 공급자는 [Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 메서드를 재정의 하지 않습니다 .이 메서드는 다음은 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitem](Msh_samplestestcmdlets#testprovidermoveitem)]  -->

#### <a name="things-to-remember-about-implementing-moveitem"></a>MoveItem 구현에 대해 기억할 사항

탐색 공급자 .NET 클래스가 ExpandWildcards, Filter, Include 또는 Exclude의 공급자 기능을 [system.object](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거에서 선언할 수 있습니다. 이 경우 [Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 를 구현 하면 전달 된 경로가 요구 사항을 충족 하는지 확인 해야 합니다. 이렇게 하려면 메서드가 적절 한 속성 (예: **Cmdletprovider. Exclude** 속성)에 액세스 해야 합니다.

기본적으로이 메서드의 재정의는 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 를 `true`로 설정 하지 않으면 기존 개체를 통해 개체를 이동 하면 안 됩니다. 예를 들어 c:\temp\abc.txt [*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 속성이 `true`로 설정 되어 있지 않으면 파일 시스템 공급자는 기존 c:\bar.txt 파일을 통해를 복사 하지 않습니다. `destination` 매개 변수에 지정 된 경로가 있고 컨테이너인 경우에는 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 를 지정 하지 않아도 됩니다.... 이 경우 [Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 는 `path` 매개 변수로 표시 된 항목을 `destination` 매개 변수로 표시 되는 컨테이너로 이동 해야 합니다 (자식 항목).

[Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 메서드를 구현 하는 경우에는 데이터 저장소를 변경 하기 전에 해당 반환 값을 확인 [하 고 해당 반환 값을 확인](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 하는 것이 좋습니다. 이 메서드는 시스템 상태가 변경 될 때 (예: 파일 삭제) 작업 실행을 확인 하는 데 사용 됩니다.
Windows PowerShell 런타임이 사용자에 게 표시 되는 항목을 확인 하는 데 필요한 명령줄 설정이 나 기본 설정 변수를 고려 하 여 사용자에 게 변경할 리소스의 [이름을 보냅니다.](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)

[System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)에 대한 호출이 끝나면 [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 메서드는 [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 메서드를 `true`호출해야 합니다. 이 메서드는 사용자에 게 작업을 계속 해야 하는 경우 사용자에 게 메시지를 보내 사용자에 게 피드백을 보냅니다. 공급자는 System.object를 호출 해야 합니다 [. shouldcontinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 잠재적으로 위험한 시스템 수정에 대 한 추가 검사로 계속 합니다.

## <a name="attaching-dynamic-parameters-to-the-move-item-cmdlet"></a>동적 매개 변수를 Move Item Cmdlet에 연결

경우에 따라 `Move-Item` cmdlet에는 런타임에 동적으로 제공 되는 추가 매개 변수가 필요 합니다. 이러한 동적 매개 변수를 제공 하기 위해 탐색 공급자는 지정 된 경로의 항목에서 필수 매개 변수 값을 가져오고 cmdlet 클래스 또는 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체와 유사한 구문 분석 특성을 가진 속성 및 필드가 있는 개체를 반환 하기 위해 system.web. c a g. c a n [g](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) .

이 탐색 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는 System.object의 기본 구현입니다. [Moveitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters](Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters)]  -->

## <a name="normalizing-a-relative-path"></a>상대 경로 정규화

탐색 공급자는 [Normalizerelativepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) 메서드를 구현 하 여 `path` 매개 변수에 표시 된 정규화 된 경로를 `basePath` 매개 변수로 지정 된 경로를 기준으로 정규화 합니다. 메서드는 정규화 된 경로에 대 한 문자열 표현을 반환 합니다. `path` 매개 변수가 존재 하지 않는 경로를 지정 하는 경우 오류를 기록 합니다.

샘플 탐색 공급자는이 메서드를 재정의 하지 않습니다. 다음은 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernormalizepath](Msh_samplestestcmdlets#testprovidernormalizepath)]  -->

#### <a name="things-to-remember-about-implementing-normalizerelativepath"></a>NormalizeRelativePath 구현에 대해 기억할 사항

[Normalizerelativepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) 의 구현은 `path` 매개 변수를 구문 분석 해야 하지만, 순수 구문 분석을 사용 하지 않아도 됩니다. 경로를 사용 하 여 데이터 저장소의 경로 정보를 조회 하 고 대/소문자 구분 및 표준화 된 경로 구문과 일치 하는 경로를 생성 하도록이 메서드를 설계 하는 것이 좋습니다.

## <a name="code-sample"></a>코드 예제

전체 샘플 코드는 [AccessDbProviderSample05 코드 샘플](./accessdbprovidersample05-code-sample.md)을 참조 하세요.

## <a name="defining-object-types-and-formatting"></a>개체 형식 및 서식 정의

공급자는 기존 개체에 멤버를 추가 하거나 새 개체를 정의할 수 있습니다. 자세한 내용은[개체 형식 확장 및 서식 지정](/previous-versions/ms714665(v=vs.85))을 참조 하세요.

## <a name="building-the-windows-powershell-provider"></a>Windows PowerShell 공급자 빌드

자세한 내용은 [cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions/ms714644(v=vs.85))을 참조 하세요.

## <a name="testing-the-windows-powershell-provider"></a>Windows PowerShell 공급자 테스트

Windows powershell 공급자를 Windows PowerShell에 등록 한 경우에는 파생에서 사용할 수 있는 cmdlet을 포함 하 여 명령줄에서 지원 되는 cmdlet을 실행 하 여 테스트할 수 있습니다. 이 예제에서는 샘플 탐색 공급자를 테스트 합니다.

1. 새 셸을 실행 하 고 `Set-Location` cmdlet을 사용 하 여 Access 데이터베이스를 나타내는 경로를 설정 합니다.

   ```powershell
   Set-Location mydb:
   ```

2. 이제 `Get-Childitem` cmdlet을 실행 하 여 사용 가능한 데이터베이스 테이블인 데이터베이스 항목 목록을 검색 합니다. 각 테이블에 대해이 cmdlet은 테이블 행의 수도 검색 합니다.

   ```powershell
   Get-ChildItem | Format-Table rowcount,name -AutoSize
   ```

   ```Output
   RowCount   Name
   --------   ----
        180   MSysAccessObjects
          0   MSysACEs
          1   MSysCmdbars
          0   MSysIMEXColumns
          0   MSysIMEXSpecs
          0   MSysObjects
          0   MSysQueries
          7   MSysRelationships
          8   Categories
         91   Customers
          9   Employees
       2155   Order Details
        830   Orders
         77   Products
          3   Shippers
         29   Suppliers
   ```

3. `Set-Location` cmdlet을 다시 사용 하 여 Employees 데이터 테이블의 위치를 설정 합니다.

   ```powershell
   Set-Location Employees
   ```

4. 이제 `Get-Location` cmdlet을 사용 하 여 Employees 테이블에 대 한 경로를 검색 해 보겠습니다.

   ```powershell
   Get-Location
   ```

   ```Output
   Path
   ----
   mydb:\Employees
   ```

5. 이제 `Format-Table` cmdlet에 파이프 된 `Get-Childitem` cmdlet을 사용 합니다. 이 cmdlet 집합은 Employees 데이터 테이블 (테이블 행)에 대 한 항목을 검색 합니다. `Format-Table` cmdlet에 지정 된 대로 형식이 지정 됩니다.

   ```powershell
   Get-ChildItem | Format-Table rownumber,psiscontainer,data -AutoSize
   ```

   ```Output
   RowNumber   PSIsContainer   Data
   ---------   --------------   ----
   0           False            System.Data.DataRow
   1           False            System.Data.DataRow
   2           False            System.Data.DataRow
   3           False            System.Data.DataRow
   4           False            System.Data.DataRow
   5           False            System.Data.DataRow
   6           False            System.Data.DataRow
   7           False            System.Data.DataRow
   8           False            System.Data.DataRow
   ```

6. 이제 `Get-Item` cmdlet을 실행 하 여 Employees 데이터 테이블의 행 0에 대 한 항목을 검색할 수 있습니다.

   ```powershell
   Get-Item 0
   ```

   ```Output
   PSPath        : AccessDB::C:\PS\Northwind.mdb\Employees\0
   PSParentPath  : AccessDB::C:\PS\Northwind.mdb\Employees
   PSChildName   : 0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data           : System.Data.DataRow
   RowNumber      : 0
   ```

7. `Get-Item` cmdlet을 다시 사용 하 여 0 행의 항목에 대 한 직원 데이터를 검색 합니다.

   ```powershell
   (Get-Item 0).data
   ```

   ```Output
   EmployeeID      : 1
   LastName        : Davis
   FirstName       : Sara
   Title           : Sales Representative
   TitleOfCourtesy : Ms.
   BirthDate       : 12/8/1968 12:00:00 AM
   HireDate        : 5/1/1992 12:00:00 AM
   Address         : 4567 Main Street
                     Apt. 2A
   City            : Buffalo
   Region          : NY
   PostalCode      : 98052
   Country         : USA
   HomePhone       : (206) 555-9857
   Extension       : 5467
   Photo           : EmpID1.bmp
   Notes           : Education includes a BA in psychology from
                     Colorado State University. She also completed "The
                     Art of the Cold Call."  Nancy is a member of
                     Toastmasters International.
   ReportsTo       : 2
   ```

## <a name="see-also"></a>참고 항목

[Windows PowerShell 공급자 만들기](./how-to-create-a-windows-powershell-provider.md)

[Windows PowerShell 공급자 디자인](./designing-your-windows-powershell-provider.md)

[개체 형식 및 서식 확장](/previous-versions/ms714665(v=vs.85))

[컨테이너 Windows PowerShell 공급자 구현](./creating-a-windows-powershell-container-provider.md)

[Cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions/ms714644(v=vs.85))

[Windows PowerShell 프로그래머 가이드](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
