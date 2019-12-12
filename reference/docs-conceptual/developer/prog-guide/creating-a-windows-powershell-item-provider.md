---
title: Windows PowerShell 항목 공급자 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- item providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], item provider
ms.assetid: a5a304ce-fc99-4a5b-a779-de7d85e031fe
caps.latest.revision: 6
ms.openlocfilehash: ad42b8de867f468e832380ab6a22a39b6d27d3c6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417494"
---
# <a name="creating-a-windows-powershell-item-provider"></a>Windows PowerShell 항목 공급자 만들기

이 항목에서는 데이터 저장소의 데이터를 조작할 수 있는 Windows PowerShell 공급자를 만드는 방법에 대해 설명 합니다. 이 항목에서는 저장소에 있는 데이터 요소를 데이터 저장소의 "항목" 이라고 합니다. 결과적으로, 저장소의 데이터를 조작할 수 있는 공급자를 Windows PowerShell 항목 공급자 라고 합니다.

> [!NOTE]
> Windows Vista 및 .NET Framework C# 3.0 런타임 구성 요소에 대 한 Microsoft Windows 소프트웨어 개발 키트를 사용 하 여이 공급자에 대 한 원본 파일 (AccessDBSampleProvider03.cs)을 다운로드할 수 있습니다. 다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/scripting/developer/installing-the-windows-powershell-sdk)을 참조 하세요.
>
> 다운로드 된 원본 파일은 **\<PowerShell Samples >** 디렉터리에서 사용할 수 있습니다.
>
> 다른 Windows PowerShell 공급자 구현에 대 한 자세한 내용은 [Windows Powershell 공급자 디자인](./designing-your-windows-powershell-provider.md)을 참조 하세요.

이 항목에서 설명 하는 Windows PowerShell 항목 공급자는 Access 데이터베이스에서 데이터 항목을 가져옵니다. 이 경우 "항목"은 Access 데이터베이스의 테이블 또는 테이블의 행입니다.

## <a name="defining-the-windows-powershell-item-provider-class"></a>Windows PowerShell 항목 공급자 클래스 정의

Windows PowerShell 항목 공급자는 [system.object](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 클래스에서 파생 되는 .net 클래스를 정의 해야 합니다. 다음은이 섹션에서 설명 하는 항목 공급자에 대 한 클래스 정의입니다.

[!code-csharp[AccessDBProviderSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L34-L36 "AccessDBProviderSample03.cs")]

이 클래스 정의에서 [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) 특성에는 두 개의 매개 변수가 포함 되어 있습니다. 첫 번째 매개 변수는 Windows PowerShell에서 사용 되는 공급자에 대 한 친숙 한 이름을 지정 합니다. 두 번째 매개 변수는 명령을 처리 하는 동안 공급자가 Windows PowerShell 런타임에 노출 하는 Windows PowerShell 특정 기능을 지정 합니다. 이 공급자의 경우 추가 된 Windows PowerShell 관련 기능이 없습니다.

## <a name="defining-base-functionality"></a>기본 기능 정의

[Windows PowerShell 공급자 디자인](./designing-your-windows-powershell-provider.md)에 [설명 된 대로](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 다른 공급자 기능을 제공 하는 다른 여러 클래스에서 파생 됩니다. 따라서 Windows PowerShell 항목 공급자는 해당 클래스에서 제공 하는 기능을 모두 정의 해야 합니다.

세션 관련 초기화 정보를 추가 하 고 공급자가 사용 하는 리소스를 해제 하기 위한 기능을 구현 하는 방법에 대 한 자세한 내용은 [기본 Windows PowerShell 공급자 만들기](./creating-a-basic-windows-powershell-provider.md)를 참조 하세요. 그러나 여기에 설명 된 공급자를 비롯 한 대부분의 공급자는 Windows PowerShell에서 제공 하는이 기능의 기본 구현을 사용할 수 있습니다.

Windows PowerShell 항목 공급자는 저장소의 항목을 조작 하기 전에 데이터 저장소에 액세스 하는 데 사용 되는 [system.object](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 의 메서드를 구현 해야 합니다. 이 클래스를 구현 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 드라이브 공급자 만들기](./creating-a-windows-powershell-drive-provider.md)를 참조 하세요.

## <a name="checking-for-path-validity"></a>경로 유효성 검사

Windows powershell 런타임은 데이터 항목을 찾을 때 windows [powershell이 작동 하는 방법](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)의 "PSPath 개념" 단원에 정의 된 대로 공급자에 대 한 windows powershell 경로를 furnishes 합니다. Windows PowerShell 항목 공급자는 System.object를 구현 하 여 전달 된 경로의 구문 및 의미 체계 유효성을 확인 해야 합니다. [isvalidpath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) 메서드. 경로가 올바르면이 메서드는 `true`을 반환 하 고, 그렇지 않으면 `false` 합니다. 이 메서드의 구현에서는 경로에 항목이 있는지 확인 하지 않아야 합니다. 단, 경로가 구문적 이며 의미 체계가 올바른지 확인 해야 합니다.

이 공급자에 대 한 다음은이 공급자에 대 한 [system.object](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) 의 구현입니다. 이 구현은 NormalizePath helper 메서드를 호출 하 여 경로의 모든 구분 기호를 균일 한 것으로 변환 합니다.

[!code-csharp[AccessDBProviderSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L274-L298 "AccessDBProviderSample03.cs")]

## <a name="determining-if-an-item-exists"></a>항목이 있는지 확인

경로를 확인 한 후 Windows PowerShell 런타임에서 해당 경로에 데이터 항목이 있는지 확인 해야 합니다. 이러한 유형의 쿼리를 지원 하기 위해 Windows PowerShell 항목 공급자는 System.object를 구현 합니다. [Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) 메서드. 이 메서드는 지정 된 경로에서 항목을 찾은 `true`을 반환 하 고 그렇지 않으면 `false` (기본값)를 반환 합니다.

이 공급자에 대 한 다음은이 공급자에 대 한 [system.object](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) 의 구현입니다. 이 메서드는 PathIsDrive, ChunkPath 및 GetTable helper 메서드를 호출 하 고 공급자 정의 DatabaseTableInfo 개체를 사용 합니다.

[!code-csharp[AccessDBProviderSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L229-L267 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-itemexists"></a>ItemExists 구현에 대해 기억할 사항

다음 조건은 System.object의 구현에 적용 될 수 있습니다. [Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists):

- 공급자 클래스를 정의 하는 경우 Windows PowerShell 항목 공급자는 ExpandWildcards, Filter, Include 또는 Exclude의 공급자 기능을 [system.object](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거형에서 선언할 수 있습니다. 이러한 경우에는 [system.object](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) 의 구현이 메서드에 전달 된 경로가 지정 된 기능에 대 한 요구 사항을 충족 하는지 확인 하는 것이 좋습니다. 이 작업을 수행 하려면 메서드가 적절 한 속성 (예: System.object)에 액세스 해야 합니다. [*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 및 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .... n a m.

- 이 메서드의 구현은 항목이 사용자에 게 표시 될 수 있도록 하는 항목에 대 한 모든 형태의 액세스를 처리 해야 합니다. 예를 들어, 사용자가 파일 시스템 공급자 (Windows PowerShell에서 제공)를 통해 파일에 대 한 쓰기 권한을가지고 있지만 읽기 액세스 권한이 없는 경우 파일은 여전히 존재 하며,이 경우에는 System.object를 반환 합니다 [. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) 를 반환 합니다`true`. 구현에서 부모 항목을 확인 하 여 자식 항목을 열거할 수 있는지 여부를 확인 해야 할 수 있습니다.

## <a name="attaching-dynamic-parameters-to-the-test-path-cmdlet"></a>동적 매개 변수를 테스트 경로 Cmdlet에 연결

경우에 따라 [system.object](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) 를 호출 하는 `Test-Path` cmdlet에는 런타임에 동적으로 지정 되는 추가 매개 변수가 필요 합니다. 이러한 동적 매개 변수를 제공 하려면 Windows PowerShell 항목 공급자가 [Itemexistsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) 메서드를 구현 해야 합니다. 이 메서드는 지정된 경로에서 항목에 대한 동적 매개 변수를 검색하고 cmdlet 클래스 또는 [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 유사한 구문 분석 특성이 있는 속성 및 필드가 있는 개체를 반환합니다. Windows PowerShell 런타임은 반환 된 개체를 사용 하 여 `Test-Path` cmdlet에 매개 변수를 추가 합니다.

이 Windows PowerShell 항목 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는이 메서드의 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovideritemexistdynamicparameters](Msh_samplestestcmdlets#testprovideritemexistdynamicparameters)]  -->

## <a name="retrieving-an-item"></a>항목 검색

항목을 검색 하려면 Windows PowerShell 항목 공급자가 `Get-Item` cmdlet의 호출을 지원 하기 위해 [Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 메서드를 재정의 해야 합니다. 이 메서드는 System.object를 사용 하 여 항목을 씁니다. [Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) 메서드를 사용 합니다.

이 공급자에 대 한 [Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 메서드는 다음과 같이 구현 되어 있습니다. 이 메서드는 GetTable 및 GetRow 도우미 메서드를 사용 하 여 Access 데이터베이스의 테이블 또는 데이터 테이블의 행에 있는 항목을 검색 합니다.

[!code-csharp[AccessDBProviderSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L132-L163 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-getitem"></a>GetItem 구현에 대해 기억할 사항

다음과 같은 조건이 [Getitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)의 구현에 적용 될 수 있습니다...

- 공급자 클래스를 정의 하는 경우 Windows PowerShell 항목 공급자는 ExpandWildcards, Filter, Include 또는 Exclude의 공급자 기능을 [system.object](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거형에서 선언할 수 있습니다. 이러한 경우에는 [Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 를 구현 하 여 메서드에 전달 된 경로가 해당 요구 사항을 충족 하는지 확인 해야 합니다. 이 작업을 수행 하려면 메서드가 적절 한 속성 (예: System.object)에 액세스 해야 합니다. [*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 및 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .... n a m.

- 기본적으로이 메서드를 재정의 하면 일반적으로 사용자에 게 표시 되는 개체를 검색 하면 안 [됩니다 .이 속성을](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) `true`로 설정 하지 않으면 일반적으로 사용자에 게 표시 되지 않습니다. 예를 들어 파일 시스템 공급자에 대 한 [Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 메서드는 숨겨진 파일 또는 시스템 파일에 [대해 system.object를 호출 하기](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) 전에 [system.object를](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 확인 하 고, 그렇지 않은 경우에는 system.object * 속성을 확인 하는 데 사용할 수 있습니다.

## <a name="attaching-dynamic-parameters-to-the-get-item-cmdlet"></a>동적 매개 변수를 Get Item Cmdlet에 연결

경우에 따라 `Get-Item` cmdlet에는 런타임에 동적으로 지정 되는 추가 매개 변수가 필요 합니다. 이러한 동적 매개 변수를 제공 하려면 Windows PowerShell 항목 공급자가 [system.web. Itemcmdletprovider *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) 메서드를 구현 해야 합니다. 이 메서드는 지정된 경로에서 항목에 대한 동적 매개 변수를 검색하고 cmdlet 클래스 또는 [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 유사한 구문 분석 특성이 있는 속성 및 필드가 있는 개체를 반환합니다. Windows PowerShell 런타임은 반환 된 개체를 사용 하 여 `Get-Item` cmdlet에 매개 변수를 추가 합니다.

이 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는이 메서드의 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetitemdynamicparameters](Msh_samplestestcmdlets#testprovidergetitemdynamicparameters)]  -->

## <a name="setting-an-item"></a>항목 설정

항목을 설정 하려면 Windows PowerShell 항목 공급자가 `Set-Item` cmdlet의 호출을 지원 하도록 [Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 메서드를 재정의 해야 합니다. 이 메서드는 지정 된 경로에 있는 항목의 값을 설정 합니다.

이 공급자는 [Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 메서드에 대 한 재정의를 제공 하지 않습니다 (예를 들어). 그러나 다음은이 메서드의 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitem](Msh_samplestestcmdlets#testprovidersetitem)]  -->

#### <a name="things-to-remember-about-implementing-setitem"></a>SetItem 구현에 대해 기억할 사항

다음 조건은 Setitem의 구현에 적용 될 수 있습니다... i n [g](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem).

- 공급자 클래스를 정의 하는 경우 Windows PowerShell 항목 공급자는 ExpandWildcards, Filter, Include 또는 Exclude의 공급자 기능을 [system.object](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거형에서 선언할 수 있습니다. 이러한 경우에는 [Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 를 구현 하 여 메서드에 전달 된 경로가 해당 요구 사항을 충족 하는지 확인 해야 합니다. 이 작업을 수행 하려면 메서드가 적절 한 속성 (예: System.object)에 액세스 해야 합니다. [*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 및 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .... n a m.

- 기본적으로이 메서드의 재정의는 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 가 `true`로 설정 되어 있지 않으면 사용자에 게 숨겨진 개체를 설정 하거나 쓰지 않아야 합니다. 경로가 숨겨진 항목을 나타내는 경우 [WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) 메서드에 오류를 전송 해야 하며, 그렇지 않은 경우에는 `false`로 설정 합니다 [.](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 이 경우에는를 지정 합니다.

- [Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 메서드를 구현 하는 경우에는 데이터 저장소를 변경 하기 전에 해당 반환 값을 확인 [하 고 해당](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 반환 값이 있는지 확인 해야 합니다. 이 메서드는 데이터 저장소가 변경 될 때 (예: 파일 삭제) 작업 실행을 확인 하는 데 사용 됩니다. [System.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 메서드는 사용자에 게 변경할 리소스의 이름을 보냅니다. Windows PowerShell 런타임은 어떤 명령줄 설정이 나 표시 되어야 하는 기본 설정 변수를 고려 하 여 사용자에 게 변경할 수 있습니다.

  [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)에 대한 호출이 끝나면 [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 메서드는 [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 메서드를 `true`호출해야 한다. 이 메서드는 사용자에 게 작업을 계속 해야 하는지 여부를 확인 하기 위해 사용자에 게 메시지를 보냅니다. System.object를 호출 하면 잠재적으로 위험한 시스템 수정에 대 한 추가 검사를 수행할 수 있습니다 [.](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)

## <a name="retrieving-dynamic-parameters-for-setitem"></a>SetItem에 대 한 동적 매개 변수 검색

경우에 따라 `Set-Item` cmdlet에는 런타임에 동적으로 지정 되는 추가 매개 변수가 필요 합니다. 이러한 동적 매개 변수를 제공 하려면 Windows PowerShell 항목 공급자가 System.object를 구현 해야 합니다. [Setitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) 메서드. 이 메서드는 지정된 경로에서 항목에 대한 동적 매개 변수를 검색하고 cmdlet 클래스 또는 [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 유사한 구문 분석 특성이 있는 속성 및 필드가 있는 개체를 반환합니다. Windows PowerShell 런타임은 반환 된 개체를 사용 하 여 `Set-Item` cmdlet에 매개 변수를 추가 합니다.

이 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는이 메서드의 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitemdynamicparameters](Msh_samplestestcmdlets#testprovidersetitemdynamicparameters)]  -->

## <a name="clearing-an-item"></a>항목 지우기

항목을 제거 하기 위해 Windows PowerShell 항목 공급자는 `Clear-Item` cmdlet의 호출을 지원 하기 위해 [system.object](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) 를 구현 합니다. 이 메서드는 지정 된 경로에서 데이터 항목을 지웁니다.

이 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는이 메서드의 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitem](Msh_samplestestcmdlets#testproviderclearitem)]  -->

#### <a name="things-to-remember-about-implementing-clearitem"></a>ClearItem 구현에 대해 기억할 사항

다음 조건은 System.web. Itemcmdletprovider의 구현에 적용 될 수 있습니다 [. Clearitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem):

- 공급자 클래스를 정의 하는 경우 Windows PowerShell 항목 공급자는 ExpandWildcards, Filter, Include 또는 Exclude의 공급자 기능을 [system.object](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거형에서 선언할 수 있습니다. 이러한 경우에는 [system.object](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) 를 구현 하 여 메서드에 전달 된 경로가 해당 요구 사항을 충족 하는지 확인 해야 합니다. 이 작업을 수행 하려면 메서드가 적절 한 속성 (예: System.object)에 액세스 해야 합니다. [*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 및 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .... n a m.

- 기본적으로이 메서드의 재정의는 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 가 `true`로 설정 되어 있지 않으면 사용자에 게 숨겨진 개체를 설정 하거나 쓰지 않아야 합니다. 경로가 사용자에 게 표시 되지 않는 항목을 나타내는 경우 [WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) 메서드에 오류를 전송 해야 합니다 .이 경우에는이 고, 그렇지 않으면 [*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 가 `false`로 설정 됩니다.

- [Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 메서드를 구현 하는 경우에는 데이터 저장소를 변경 하기 전에 해당 반환 값을 확인 [하 고 해당](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 반환 값이 있는지 확인 해야 합니다. 이 메서드는 데이터 저장소가 변경 될 때 (예: 파일 삭제) 작업 실행을 확인 하는 데 사용 됩니다. [System.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 는 Windows PowerShell 런타임을 사용 하 여 사용자에 게 변경할 리소스의 이름을 보내고, 표시 되는 항목을 결정 하는 데 필요한 명령줄 설정 또는 기본 변수를 처리 합니다.

  [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)에 대한 호출이 끝나면 [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 메서드는 [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 메서드를 `true`호출해야 한다. 이 메서드는 사용자에 게 작업을 계속 해야 하는지 여부를 확인 하기 위해 사용자에 게 메시지를 보냅니다. System.object를 호출 하면 잠재적으로 위험한 시스템 수정에 대 한 추가 검사를 수행할 수 있습니다 [.](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)

## <a name="retrieve-dynamic-parameters-for-clearitem"></a>ClearItem에 대 한 동적 매개 변수 검색

경우에 따라 `Clear-Item` cmdlet에는 런타임에 동적으로 지정 되는 추가 매개 변수가 필요 합니다. 이러한 동적 매개 변수를 제공 하려면 Windows PowerShell 항목 공급자가 [system.web. Itemcmdletdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) 메서드를 구현 해야 합니다. 이 메서드는 지정된 경로에서 항목에 대한 동적 매개 변수를 검색하고 cmdlet 클래스 또는 [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 유사한 구문 분석 특성이 있는 속성 및 필드가 있는 개체를 반환합니다. Windows PowerShell 런타임은 반환 된 개체를 사용 하 여 `Clear-Item` cmdlet에 매개 변수를 추가 합니다.

이 항목 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는이 메서드의 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitemdynamicparameters](Msh_samplestestcmdlets#testproviderclearitemdynamicparameters)]  -->

## <a name="performing-a-default-action-for-an-item"></a>항목에 대 한 기본 작업 수행

Windows PowerShell 항목 공급자는 [Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) 메서드를 구현 하 여 공급자가 지정 된 경로에 있는 항목에 대 한 기본 작업을 수행할 수 있도록 하는 `Invoke-Item` cmdlet의 호출을 지원할 수 있습니다. 예를 들어 FileSystem 공급자는이 메서드를 사용 하 여 특정 항목에 대해 ShellExecute를 호출할 수 있습니다.

이 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는이 메서드의 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultaction](Msh_samplestestcmdlets#testproviderinvokedefaultaction)]  -->

#### <a name="things-to-remember-about-implementing-invokedefaultaction"></a>InvokeDefaultAction 구현에 대해 기억할 사항

다음과 같은 조건이 [Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)의 구현에 적용 될 수 있습니다...

- 공급자 클래스를 정의 하는 경우 Windows PowerShell 항목 공급자는 ExpandWildcards, Filter, Include 또는 Exclude의 공급자 기능을 [system.object](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거형에서 선언할 수 있습니다. 이러한 경우에는 [Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) 를 구현 하 여 메서드에 전달 된 경로가 해당 요구 사항을 충족 하는지 확인 해야 합니다. 이 작업을 수행 하려면 메서드가 적절 한 속성 (예: System.object)에 액세스 해야 합니다. [*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 및 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .... n a m.

- 기본적으로이 메서드의 재정의는 사용자가 숨겨진 개체를 설정 하거나 쓰지 않아야 합니다 .이 경우에는 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 를 `true`으로 설정 해야 합니다. 경로가 사용자에 게 표시 되지 않는 항목을 나타내는 경우 [WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) 메서드에 오류를 전송 해야 합니다 .이 경우에는이 고, 그렇지 않으면 [*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 가 `false`로 설정 됩니다.

## <a name="retrieve-dynamic-parameters-for-invokedefaultaction"></a>InvokeDefaultAction에 대 한 동적 매개 변수 검색

경우에 따라 `Invoke-Item` cmdlet에는 런타임에 동적으로 지정 되는 추가 매개 변수가 필요 합니다. 이러한 동적 매개 변수를 제공 하려면 Windows PowerShell 항목 공급자가 [Invokedefaultactiondynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) 메서드를 구현 해야 합니다. 이 메서드는 지정된 경로에서 항목에 대한 동적 매개 변수를 검색하고 cmdlet 클래스 또는 [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 유사한 구문 분석 특성이 있는 속성 및 필드가 있는 개체를 반환합니다. Windows PowerShell 런타임은 반환 된 개체를 사용 하 여 `Invoke-Item` cmdlet에 동적 매개 변수를 추가 합니다.

이 항목 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는이 메서드의 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters](Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters)]  -->

## <a name="implementing-helper-methods-and-classes"></a>도우미 메서드 및 클래스 구현

이 항목 공급자는 Windows PowerShell에 정의 된 공용 재정의 메서드에서 사용 하는 몇 가지 도우미 메서드 및 클래스를 구현 합니다. 이러한 도우미 메서드 및 클래스에 대 한 코드는 [코드 샘플](#code-sample) 섹션에 나와 있습니다.

### <a name="normalizepath-method"></a>NormalizePath 메서드

이 항목 공급자는 NormalizePath 도우미 메서드를 구현 하 여 경로의 형식이 일치 하는지 확인 합니다. 지정 된 형식에서 백슬래시 (\\)를 구분 기호로 사용 합니다.

### <a name="pathisdrive-method"></a>PathIsDrive 메서드

이 항목 공급자는 PathIsDrive 도우미 메서드를 구현 하 여 지정 된 경로가 실제로 드라이브 이름 인지 여부를 확인 합니다.

### <a name="chunkpath-method"></a>ChunkPath 메서드

이 항목 공급자는 지정 된 경로를 구분 하는 청크 경로 도우미 메서드를 구현 하 여 공급자가 개별 요소를 식별할 수 있도록 합니다. Path 요소로 구성 된 배열을 반환 합니다.

### <a name="gettable-method"></a>GetTable 메서드

이 항목 공급자는 호출에 지정 된 테이블에 대 한 정보를 나타내는 DatabaseTableInfo 개체를 반환 하는 GetTables 도우미 메서드를 구현 합니다.

### <a name="getrow-method"></a>GetRow 메서드

이 항목 공급자에 대 한 [Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 메서드는 GetRows 도우미 메서드를 호출 합니다. 이 도우미 메서드는 테이블의 지정 된 행에 대 한 정보를 나타내는 DatabaseRowInfo 개체를 검색 합니다.

### <a name="databasetableinfo-class"></a>DatabaseTableInfo 클래스

이 항목 공급자는 데이터베이스의 데이터 테이블에 있는 정보 컬렉션을 나타내는 DatabaseTableInfo 클래스를 정의 합니다. 이 클래스는 [system.io.directoryinfo](/dotnet/api/System.IO.DirectoryInfo) 클래스와 유사 합니다.

샘플 항목 공급자는 데이터베이스의 테이블을 정의 하는 테이블 정보 개체의 컬렉션을 반환 하는 DatabaseTableInfo 메서드를 정의 합니다. 이 메서드는 try/catch 블록을 포함 하 여 모든 데이터베이스 오류가 항목이 없는 행으로 표시 되도록 합니다.

### <a name="databaserowinfo-class"></a>DatabaseRowInfo 클래스

이 항목 공급자는 데이터베이스 테이블의 행을 나타내는 DatabaseRowInfo helper 클래스를 정의 합니다. 이 클래스는 [system.object](/dotnet/api/System.IO.FileInfo) 클래스와 유사 합니다.

샘플 공급자는 지정 된 테이블에 대 한 행 정보 개체의 컬렉션을 반환 하는 DatabaseRowInfo 메서드를 정의 합니다. 이 메서드에는 예외를 트래핑 하는 try/catch 블록이 포함 됩니다. 오류가 발생 하면 행 정보가 나타나지 않습니다.

## <a name="code-sample"></a>코드 예제

전체 샘플 코드는 [AccessDbProviderSample03 코드 샘플](./accessdbprovidersample03-code-sample.md)을 참조 하세요.

## <a name="defining-object-types-and-formatting"></a>개체 형식 및 서식 정의

공급자를 작성할 때 기존 개체에 멤버를 추가 하거나 새 개체를 정의 해야 할 수 있습니다. 완료 되 면 Windows PowerShell에서 개체의 멤버와 개체 표시 방법을 정의 하는 서식 파일을 식별 하는 데 사용할 수 있는 형식 파일을 만듭니다. 에 대 한 자세한 내용은 [개체 형식 확장 및 서식 지정](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)을 참조 하세요.

## <a name="building-the-windows-powershell-provider"></a>Windows PowerShell 공급자 빌드

[Cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법을](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)참조 하세요.

## <a name="testing-the-windows-powershell-provider"></a>Windows PowerShell 공급자 테스트

Windows powershell을 사용 하 여이 Windows PowerShell 항목 공급자를 등록 한 경우에는 공급자의 기본 및 드라이브 기능만 테스트할 수 있습니다. 항목 조작을 테스트 하려면 [컨테이너 Windows PowerShell 공급자 구현](./creating-a-windows-powershell-container-provider.md)에 설명 된 컨테이너 기능을 구현 해야 합니다.

## <a name="see-also"></a>참고 항목

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell 프로그래머 가이드](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell 공급자 만들기](./how-to-create-a-windows-powershell-provider.md)

[Windows PowerShell 공급자 디자인](./designing-your-windows-powershell-provider.md)

[개체 형식 및 서식 확장](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Windows PowerShell 작동 방법](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[컨테이너 Windows PowerShell 공급자 만들기](./creating-a-windows-powershell-container-provider.md)

[드라이브 만들기 Windows PowerShell 공급자](./creating-a-windows-powershell-drive-provider.md)

[Cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)
