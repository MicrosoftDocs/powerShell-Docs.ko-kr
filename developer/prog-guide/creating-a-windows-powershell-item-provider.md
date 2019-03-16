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
ms.openlocfilehash: f2c9e10f0dc392399cf062500b7f28b3d1c07f6e
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055124"
---
# <a name="creating-a-windows-powershell-item-provider"></a>Windows PowerShell 항목 공급자 만들기

이 항목에서는 데이터 저장소에 데이터를 조작할 수 있는 Windows PowerShell 공급자를 만드는 방법을 설명 합니다. 이 항목에서는 저장소에 있는 데이터 요소의 저장할 데이터의 "항목" 이라고 합니다. 결과적으로 저장소에서 데이터를 조작할 수 있는 공급자는 Windows PowerShell 항목 공급자 하 라고 합니다.

> [!NOTE]
> 다운로드할 수 있습니다는 C# Microsoft Windows 소프트웨어 개발 키트에 대 한 Windows Vista 및.NET Framework 3.0 런타임 구성 요소를 사용 하 여이 공급자에 대 한 원본 파일 (AccessDBSampleProvider03.cs). 다운로드 지침에 대해서 [Windows PowerShell 설치 및 Windows PowerShell SDK를 다운로드 하는 방법을](/powershell/developer/installing-the-windows-powershell-sdk)합니다.
>
> 다운로드 한 소스 파일에서 사용할 수는  **\<PowerShell 샘플 >** 디렉터리입니다.
>
> 다른 Windows PowerShell 공급자 구현에 대 한 자세한 내용은 참조 하십시오 [Your Windows PowerShell 공급자 디자인](./designing-your-windows-powershell-provider.md)합니다.

이 항목에서 설명 하는 Windows PowerShell 항목 공급자는 Access 데이터베이스에서 데이터 항목을 가져옵니다. 이 경우 "항목"은 Access 데이터베이스에서 테이블 또는 테이블의 행입니다.

다음은이 항목의 섹션을 포함합니다. Windows PowerShell 항목 공급자 작성에 익숙한 경우 표시 되는 순서 대로 다음이 섹션을 참조 합니다. 그러나 Windows PowerShell 항목 공급자 작성에 익숙한 경우 다음과 같이 해야 하는 정보에 직접 이동 합니다.

- [Windows PowerShell 항목 공급자 클래스를 정의합니다.](#Defining-the-Windows-PowerShell-Item-Provider-Class)

- [기본 기능 정의](#Defining-Base-Functionality)

- [경로 유효성 검사](#Checking-for-Path-Validity)

- [항목의 존재 여부 확인](#Determining-if-an-Item-Exists)

- [동적 매개 변수를 연결 합니다 `Test-Path` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Test-Path-Cmdlet)

- [항목 검색](#Retrieving-an-Item)

- [동적 매개 변수를 연결 합니다 `Get-Item` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-Item-Cmdlet)

- [항목 설정](#Setting-an-Item)

- [동적 매개 변수를 연결 합니다 `Set-Item` Cmdlet](#Retrieving-Dynamic-Parameters-for-SetItem)

- [항목 지우기](#Clearing-an-Item)

- [동적 연결 매개 변수를 지우려면 Clear-item Cmdlet](#Retrieve-Dynamic-Parameters-for-ClearItem)

- [항목에 대 한 기본 작업 수행](#Performing-a-Default-Action-for-an-Item)

- [InvokeDefaultAction 동적 매개 변수 검색](#Retrieve-Dynamic-Parameters-for-InvokeDefaultAction)

- [도우미 메서드 및 클래스를 구현합니다.](#Implementing-Helper-Methods-and-Classes)

- [코드 샘플](#Code-Sample)

- [개체 유형 정의 및 서식 지정](#Defining-Object-Types-and-Formatting)

- [Windows PowerShell 공급자 작성](#Building-the-Windows-PowerShell-provider)

- [Windows PowerShell 공급자 테스트](#Testing-the-Windows-PowerShell-provider)

## <a name="defining-the-windows-powershell-item-provider-class"></a>Windows PowerShell 항목 공급자 클래스를 정의합니다.

Windows PowerShell 항목 공급자에서 파생 되는.NET 클래스를 정의 해야 합니다 [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 기본 클래스입니다. 다음은이 섹션에 설명 된 항목 공급자에 대 한 클래스 정의 합니다.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L34-L36 "AccessDBProviderSample03.cs")]

이 클래스를 정의 하는 합니다 [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) 특성에는 두 개의 매개 변수가 포함 됩니다. 첫 번째 매개 변수는 Windows PowerShell에서 사용 되는 공급자에 대 한 알기 쉬운 이름을 지정 합니다. 두 번째 매개 변수는 명령 처리 하는 동안 공급자가 Windows PowerShell 런타임에 노출 하는 Windows PowerShell 특정 기능을 지정 합니다. 이 공급자에 대 한 추가 Windows PowerShell 특정 기능이 없으며 있습니다.

## <a name="defining-base-functionality"></a>기본 기능 정의

에 설명 된 대로 [디자인 해당 Windows PowerShell 공급자](./designing-your-windows-powershell-provider.md)서 [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 다른 제공 하는 다른 여러 클래스에서 파생 되는 클래스 공급자 기능입니다. Windows PowerShell 항목 공급자, 따라서 정의 해야 모든 해당 클래스에서 제공 하는 기능.

특정 세션 초기화 정보를 추가 하 고 공급자가 사용 되는 리소스를 해제 하기 위해 기능을 구현 하는 방법에 대 한 자세한 내용은 참조 하세요. [는 기본 Windows PowerShell 공급자를 만들어](./creating-a-basic-windows-powershell-provider.md)합니다. 그러나 여기에 설명 된 공급자를 비롯 한 대부분의 공급자를 Windows PowerShell에서 제공 하는이 기능의 기본 구현을 사용할 수 있습니다.

Windows PowerShell 항목 공급자는 저장소의 항목을 조작할 수 있습니다, 전에의 메서드를 구현 해야 합니다 [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 기본 데이터 저장소에 액세스 하는 클래스입니다. 이 클래스를 구현 하는 방법에 대 한 자세한 내용은 참조 하십시오 [Windows PowerShell 드라이브 공급자 만들기](./creating-a-windows-powershell-drive-provider.md)합니다.

## <a name="checking-for-path-validity"></a>경로 유효성 검사

"PSPath 개념" 섹션에 정의 된 대로 Windows PowerShell 런타임에 공급자에 게는 Windows PowerShell 경로 제공 데이터 항목을 찾아보면 [Windows PowerShell 작동 방식](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)합니다. Windows PowerShell 항목 공급자를 구현 하 여 전달 된 경로의 구문 및 의미 체계 유효성을 확인 해야 합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) 메서드. 이 메서드는 반환 `true` 경로 유효한 경우 및 `false` 그렇지 않은 경우. 되며이 메서드의 구현만 경로에 있는 항목 경로 구문상의 존재 여부를 확인 하지 말라고 인식 의미 체계가 잘못 되었습니다.

여기의 구현은 합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) 이 공급자에 대 한 메서드. 이 구현은 균일 한 단일 경로에 모든 구분 기호를 변환할 NormalizePath 도우미 메서드를 호출 하는 참고 합니다.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L274-L298 "AccessDBProviderSample03.cs")]

## <a name="determining-if-an-item-exists"></a>항목의 존재 여부 확인

경로 확인 한 후 Windows PowerShell 런타임에 데이터 항목이 해당 경로에 있는지 확인 해야 합니다. 이러한 유형의 쿼리를 지원 하려면 Windows PowerShell 항목 공급자를 구현 합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) 메서드. 이 메서드가 반환 `true` 지정된 된 경로에 항목이 및 `false` (기본값) 그렇지 않은 경우.

여기의 구현은 합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) 이 공급자에 대 한 메서드. 이 메서드가 PathIsDrive, ChunkPath, 및 GetTable 도우미 메서드를 호출 하 고 공급자를 사용 하 여 DatabaseTableInfo 개체를 정의 합니다.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L229-L267 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-itemexists"></a>ItemExists를 구현 하는 방법에 대 한 고려해 야 할 사항

다음과의 구현에 적용 될 수 있습니다 [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists):

- 공급자 클래스를 정의 하는 경우 Windows PowerShell 항목 공급자에서 ExpandWildcards, 필터, 포함 또는 제외의 공급자 기능을 선언할 수 있습니다는 [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)열거형입니다. 이러한 경우의 구현에는 [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) 메서드는 메서드에 전달 된 경로 지정 된 기능의 요구를 충족 하는지 확인 해야 합니다. 이 작업을 수행 하는 메서드 액세스 해야 적절 한 속성을 예를 들어, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 고 [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) 속성입니다.

- 이 메서드의 구현은 모든 형태의 사용자에 게 표시 되는 항목을 만들 수 있는 항목에 대 한 액세스를 처리 해야 합니다. 예를 들어, 사용자에 대 한 쓰기 액세스는 FileSystem 공급자 (Windows PowerShell에서 제공)를 통해 읽기 액세스할 수는 없습니다 파일로 파일이 여전히 존재 하는지와 [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) 반환 `true`합니다. 구현 자식 항목을 열거할 수 있습니다 하는 경우를 확인 하려면 부모 항목을 확인 해야 합니다.

## <a name="attaching-dynamic-parameters-to-the-test-path-cmdlet"></a>Test-path Cmdlet에 연결 하는 동적 매개 변수

경우에 따라 합니다 `Test-Path` 를 호출 하는 cmdlet [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) 런타임에 동적으로 지정 된 추가 매개 변수가 필요 합니다. Windows PowerShell 항목 공급자를 구현 해야 이러한 동적 매개 변수를 제공 합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) 메서드. 이 메서드는 지정 된 경로에 있는 항목에 대 한 동적 매개 변수를 검색 하 고 속성 및 cmdlet 클래스와 유사한 특성을 구문 분석 된 필드에 있는 개체를 반환 또는 [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체입니다. Windows PowerShell 런타임에 반환 되는 개체를 사용 하 여 매개 변수를 추가 하 여 `Test-Path` cmdlet.

이 Windows PowerShell 항목 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는이 메서드의 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovideritemexistdynamicparameters](Msh_samplestestcmdlets#testprovideritemexistdynamicparameters)]  -->

## <a name="retrieving-an-item"></a>항목 검색

항목을 검색 하려면 Windows PowerShell 항목 공급자를 재정의 해야 합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 메서드 호출에서 지원 하기는 `Get-Item` cmdlet. 이 메서드를 사용 하 여 항목 기록 합니다 [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) 메서드.

여기의 구현은 합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 이 공급자에 대 한 메서드. 이 메서드가 GetTable 및 GetRow 도우미 메서드를 사용 하 여 Access 데이터베이스에서 테이블 또는 데이터 테이블의 행 수 있는 항목을 검색 하는 참고 합니다.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L132-L163 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-getitem"></a>GetItem를 구현 하는 방법에 대 한 고려해 야 할 사항

다음과의 구현에 적용 될 수 있습니다 [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem):

- 공급자 클래스를 정의 하는 경우 Windows PowerShell 항목 공급자에서 ExpandWildcards, 필터, 포함 또는 제외의 공급자 기능을 선언할 수 있습니다는 [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)열거형입니다. 이러한 경우 구현의 [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 메서드에 전달 된 경로 이러한 요구 사항을 충족 하는지 확인 해야 합니다. 이 작업을 수행 하는 메서드 액세스 해야 적절 한 속성을 예를 들어, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 고 [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) 속성입니다.

- 기본적으로이 메서드는 재정의 하지 않는 한 일반적으로 사용자 로부터 숨겨진 개체 검색 하지 않아야 합니다 [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 속성이 `true`합니다. 예를 들어 합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) FileSystem 공급자 확인에 대 한 메서드는 [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 호출 하려고 시도 하기 전에 속성 [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) 에 숨겨진 또는 시스템 파일입니다.

## <a name="attaching-dynamic-parameters-to-the-get-item-cmdlet"></a>Get-item Cmdlet에 연결 하는 동적 매개 변수

경우에 따라는 `Get-Item` cmdlet에는 런타임에 동적으로 지정 된 추가 매개 변수가 필요 합니다. Windows PowerShell 항목 공급자를 구현 해야 이러한 동적 매개 변수를 제공 합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) 메서드. 이 메서드는 지정 된 경로에 있는 항목에 대 한 동적 매개 변수를 검색 하 고 속성 및 cmdlet 클래스와 유사한 특성을 구문 분석 된 필드에 있는 개체를 반환 또는 [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체입니다. Windows PowerShell 런타임에 반환 되는 개체를 사용 하 여 매개 변수를 추가 하 여 `Get-Item` cmdlet.

이 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는이 메서드의 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetitemdynamicparameters](Msh_samplestestcmdlets#testprovidergetitemdynamicparameters)]  -->

## <a name="setting-an-item"></a>항목 설정

항목을 설정 하려면 Windows PowerShell 항목 공급자를 재정의 해야 합니다는 [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 메서드 호출에서 지원 하기는 `Set-Item` cmdlet. 이 메서드는 지정된 된 경로에 있는 항목의 값을 설정합니다.

이 공급자에 대 한 재정의 제공 하지 않습니다 합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 메서드. 그러나 다음은이 메서드의 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitem](Msh_samplestestcmdlets#testprovidersetitem)]  -->

#### <a name="things-to-remember-about-implementing-setitem"></a>SetItem를 구현 하는 방법에 대 한 고려해 야 할 사항

다음과의 구현에 적용 될 수 있습니다 [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem):

- 공급자 클래스를 정의 하는 경우 Windows PowerShell 항목 공급자에서 ExpandWildcards, 필터, 포함 또는 제외의 공급자 기능을 선언할 수 있습니다는 [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)열거형입니다. 이러한 경우 구현의 [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 메서드에 전달 된 경로 이러한 요구 사항을 충족 하는지 확인 해야 합니다. 이 작업을 수행 하는 메서드 액세스 해야 적절 한 속성을 예를 들어, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 고 [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) 속성입니다.

- 기본적으로이 메서드는 재정의 해야 또는 설정 하지 않는 한 사용자 로부터 숨겨진 개체를 쓸 합니다 [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 속성이 `true`합니다. 오류를 보내야 합니다 [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) 경로는 숨겨진된 항목을 나타내는 경우 메서드 및 [ System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 로 설정 된 `false`합니다.

- 구현 된 [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 메서드를 호출 해야 [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)데이터 저장소로 변경 하기 전에 해당 반환 값을 확인 합니다. 이 메서드는 데이터 저장소에, 예를 들어 파일을 삭제 하는 변경 될 때 작업의 실행을 확인 하려면 사용 됩니다. 합니다 [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 메서드를 사용 하 여 명령줄 설정을 고려 하는 Windows PowerShell 런타임에 사용자에 게 변경할지 리소스의 이름을 전송 또는 표시할 내용을 결정 하는 데 기본 설정 변수입니다.

  호출한 후 [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 반환 `true`는 [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)메서드를 호출 해야 합니다 [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 메서드. 이 메서드는 작업을 계속 진행 해야 하는 경우를 확인 하는 피드백을 허용 하도록 사용자에 게 메시지를 보냅니다. 에 대 한 호출 [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 잠재적으로 위험한 시스템 수정에 대 한 추가 검사를 허용 합니다.

## <a name="retrieving-dynamic-parameters-for-setitem"></a>SetItem 동적 매개 변수 검색

경우에 따라는 `Set-Item` cmdlet에는 런타임에 동적으로 지정 된 추가 매개 변수가 필요 합니다. Windows PowerShell 항목 공급자를 구현 해야 이러한 동적 매개 변수를 제공 합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) 메서드. 이 메서드는 지정 된 경로에 있는 항목에 대 한 동적 매개 변수를 검색 하 고 속성 및 cmdlet 클래스와 유사한 특성을 구문 분석 된 필드에 있는 개체를 반환 또는 [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체입니다. Windows PowerShell 런타임에 반환 되는 개체를 사용 하 여 매개 변수를 추가 하 여 `Set-Item` cmdlet.

이 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는이 메서드의 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitemdynamicparameters](Msh_samplestestcmdlets#testprovidersetitemdynamicparameters)]  -->

## <a name="clearing-an-item"></a>항목 지우기

Windows PowerShell 항목 공급자를 구현 하는 항목을 지우려면 합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) 메서드 호출에서 지원 하기는 `Clear-Item` cmdlet. 이 메서드는 지정된 된 경로에 있는 데이터 항목을 지웁니다.

이 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는이 메서드의 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitem](Msh_samplestestcmdlets#testproviderclearitem)]  -->

#### <a name="things-to-remember-about-implementing-clearitem"></a>ClearItem를 구현 하는 방법에 대 한 고려해 야 할 사항

다음과의 구현에 적용 될 수 있습니다 [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem):

- 공급자 클래스를 정의 하는 경우 Windows PowerShell 항목 공급자에서 ExpandWildcards, 필터, 포함 또는 제외의 공급자 기능을 선언할 수 있습니다는 [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)열거형입니다. 이러한 경우 구현의 [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) 메서드에 전달 된 경로 이러한 요구 사항을 충족 하는지 확인 해야 합니다. 이 작업을 수행 하는 메서드 액세스 해야 적절 한 속성을 예를 들어, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 고 [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) 속성입니다.

- 기본적으로이 메서드는 재정의 해야 또는 설정 하지 않는 한 사용자 로부터 숨겨진 개체를 쓸 합니다 [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 속성이 `true`합니다. 오류를 보내야 합니다 [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) 경로 사용자 로부터 숨겨진 항목을 나타내는 경우 메서드 및 [ System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 로 설정 된 `false`합니다.

- 구현 된 [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 메서드를 호출 해야 [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)데이터 저장소로 변경 하기 전에 해당 반환 값을 확인 합니다. 이 메서드는 데이터 저장소에, 예를 들어 파일을 삭제 하는 변경 될 때 작업의 실행을 확인 하려면 사용 됩니다. 합니다 [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 메서드를 Windows PowerShell 런타임에 사용자에 게 변경 하 고 명령줄 설정이 나 기본 설정 처리 리소스의 이름을 전송 표시할 내용을 결정 하는 변수입니다.

  호출한 후 [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 반환 `true`는 [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)메서드를 호출 해야 합니다 [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 메서드. 이 메서드는 작업을 계속 진행 해야 하는 경우를 확인 하는 피드백을 허용 하도록 사용자에 게 메시지를 보냅니다. 에 대 한 호출 [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 잠재적으로 위험한 시스템 수정에 대 한 추가 검사를 허용 합니다.

## <a name="retrieve-dynamic-parameters-for-clearitem"></a>ClearItem에 대 한 동적 매개 변수를 검색 합니다.

경우에 따라는 `Clear-Item` cmdlet에는 런타임에 동적으로 지정 된 추가 매개 변수가 필요 합니다. Windows PowerShell 항목 공급자를 구현 해야 이러한 동적 매개 변수를 제공 합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) 메서드. 이 메서드는 지정 된 경로에 있는 항목에 대 한 동적 매개 변수를 검색 하 고 속성 및 cmdlet 클래스와 유사한 특성을 구문 분석 된 필드에 있는 개체를 반환 또는 [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체입니다. Windows PowerShell 런타임에 반환 되는 개체를 사용 하 여 매개 변수를 추가 하 여 `Clear-Item` cmdlet.

이 항목 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는이 메서드의 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitemdynamicparameters](Msh_samplestestcmdlets#testproviderclearitemdynamicparameters)]  -->

## <a name="performing-a-default-action-for-an-item"></a>항목에 대 한 기본 작업 수행

Windows PowerShell 항목 공급자를 구현할 수는 [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) 메서드 호출에서 지원 하기는 `Invoke-Item` 공급자를 허용 하는 cmdlet를 지정된 된 경로에 있는 항목에 대 한 기본 작업을 수행 합니다. 예를 들어, 파일 시스템 공급자 특정 항목은 ShellExecute를 호출 하려면이 메서드를 사용할 수 있습니다.

이 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는이 메서드의 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultaction](Msh_samplestestcmdlets#testproviderinvokedefaultaction)]  -->

#### <a name="things-to-remember-about-implementing-invokedefaultaction"></a>InvokeDefaultAction를 구현 하는 방법에 대 한 고려해 야 할 사항

다음과의 구현에 적용 될 수 있습니다 [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction):

- 공급자 클래스를 정의 하는 경우 Windows PowerShell 항목 공급자에서 ExpandWildcards, 필터, 포함 또는 제외의 공급자 기능을 선언할 수 있습니다는 [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)열거형입니다. 이러한 경우 구현의 [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) 메서드에 전달 된 경로 이러한 요구 사항을 충족 하는지 확인 해야 합니다. 이 작업을 수행 하는 메서드 액세스 해야 적절 한 속성을 예를 들어, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 고 [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) 속성입니다.

- 기본적으로이 메서드는 재정의 해야 설정 하지 않거나 해야만 사용자 로부터 숨길 개체를 작성 합니다 [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 속성이 `true`합니다. 오류를 보내야 합니다 [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) 경로 사용자 로부터 숨겨진 항목을 나타내는 경우 메서드 및 [ System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 로 설정 된 `false`합니다.

## <a name="retrieve-dynamic-parameters-for-invokedefaultaction"></a>InvokeDefaultAction에 대 한 동적 매개 변수를 검색 합니다.

경우에 따라는 `Invoke-Item` cmdlet에는 런타임에 동적으로 지정 된 추가 매개 변수가 필요 합니다. Windows PowerShell 항목 공급자를 구현 해야 이러한 동적 매개 변수를 제공 합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) 메서드. 이 메서드는 지정 된 경로에 있는 항목에 대 한 동적 매개 변수를 검색 하 고 속성 및 cmdlet 클래스와 유사한 특성을 구문 분석 된 필드에 있는 개체를 반환 또는 [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체입니다. Windows PowerShell 런타임에 반환 되는 개체를 사용 하 여 동적 매개 변수를 추가 하 여 `Invoke-Item` cmdlet.

이 항목 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는이 메서드의 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters](Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters)]  -->

## <a name="implementing-helper-methods-and-classes"></a>도우미 메서드 및 클래스를 구현합니다.

이 항목 공급자는 몇 가지 도우미 메서드를 구현 하 고 공개적으로 사용 되는 클래스가 Windows PowerShell에서 정의 된 메서드를 재정의 합니다. 이러한 도우미 메서드 및 클래스에 대 한 코드에 표시 되는 [코드 샘플](#Code-Sample) 섹션입니다.

### <a name="normalizepath-method"></a>NormalizePath 메서드

이 항목 공급자 경로 일관 된 형식을 갖도록 NormalizePath 도우미 메서드를 구현 합니다. 백슬래시를 사용 하는 지정 된 형식 (\\)을 구분 기호로 사용 합니다.

### <a name="pathisdrive-method"></a>PathIsDrive 메서드

이 항목 공급자 드라이브 이름을 실제로 지정된 된 경로 인지 확인 하려면 PathIsDrive 도우미 메서드를 구현 합니다.

### <a name="chunkpath-method"></a>ChunkPath 메서드

이 항목 공급자를 분할 하 여 지정된 된 경로 공급자는 해당 개별 요소를 식별할 수 있도록 하는 ChunkPath 도우미 메서드를 구현 합니다. 경로 요소를 구성 된 배열을 반환 합니다.

### <a name="gettable-method"></a>GetTable 메서드

이 항목 공급자 호출에서 지정 된 테이블에 대 한 정보를 나타내는 DatabaseTableInfo 개체를 반환 하는 GetTables 도우미 메서드를 구현 합니다.

### <a name="getrow-method"></a>GetRow 메서드

합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 이 항목 공급자의 메서드에 GetRows 도우미 메서드를 호출 합니다. 이 도우미 메서드는 테이블의 지정된 된 행에 대 한 정보를 나타내는 DatabaseRowInfo 개체를 검색 합니다.

### <a name="databasetableinfo-class"></a>DatabaseTableInfo 클래스

이 항목 공급자 데이터베이스에 데이터 테이블의 정보의 컬렉션을 나타내는 DatabaseTableInfo 클래스를 정의 합니다. 이 클래스는 비슷합니다는 [System.IO.Directoryinfo](/dotnet/api/System.IO.DirectoryInfo) 클래스입니다.

샘플 항목 공급자 데이터베이스에 테이블을 정의 하는 테이블 정보 개체의 컬렉션을 반환 하는 DatabaseTableInfo.GetTables 메서드를 정의 합니다. 이 메서드는 0 개 항목이 행으로 모든 데이터베이스 오류 표시 되도록 try/catch 블록을 포함 합니다.

### <a name="databaserowinfo-class"></a>DatabaseRowInfo 클래스

이 항목 공급자는 데이터베이스의 테이블에 행을 나타내는 DatabaseRowInfo 도우미 클래스를 정의 합니다. 이 클래스는 비슷합니다는 [System.IO.FileInfo](/dotnet/api/System.IO.FileInfo) 클래스입니다.

샘플 공급자는 지정한 테이블의 행 정보 개체의 컬렉션을 반환 하려면 DatabaseRowInfo.GetRows 메서드를 정의 합니다. 이 메서드는 예외를 트래핑 하는 try/catch 블록을 포함 합니다. 행 정보 없음 오류가 발생 합니다.

## <a name="code-sample"></a>코드 예제

전체 샘플 코드를 보려면 [AccessDbProviderSample03 코드 샘플](./accessdbprovidersample03-code-sample.md)합니다.

## <a name="defining-object-types-and-formatting"></a>개체 유형 정의 및 서식 지정

공급자를 작성할 때 기존 개체에 멤버를 추가 하거나 새 개체를 정의 해야 할 수도 있습니다. 완료 되 면 Windows PowerShell 개체의 멤버를 식별 하는 데 사용할 수 있는 형식 파일 및 개체 표시 되는 방식을 정의 하는 서식 파일을 만듭니다. 에 대 한 자세한 내용은 참조 하세요. [확장 개체 형식 및 서식](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)합니다.

## <a name="building-the-windows-powershell-provider"></a>Windows PowerShell 공급자 작성

참조 [Cmdlet, 공급자, 등록 및 응용 프로그램을 호스트 하는 방법을](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)합니다.

## <a name="testing-the-windows-powershell-provider"></a>Windows PowerShell 공급자 테스트

Windows PowerShell을 사용 하 여이 Windows PowerShell 항목 공급자가 등록 하는 경우만 기본 테스트를 드라이브 공급자의 기능입니다. 항목의 조작을 테스트 하려면 또한에 설명 된 컨테이너 기능을 구현 해야 [Windows PowerShell 컨테이너 공급자 구현](./creating-a-windows-powershell-container-provider.md)합니다.

## <a name="see-also"></a>참고 항목

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell 프로그래머 가이드](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell 공급자 만들기](./how-to-create-a-windows-powershell-provider.md)

[디자인 Your Windows PowerShell 공급자](./designing-your-windows-powershell-provider.md)

[확장 개체 형식 및 서식 지정](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Windows PowerShell의 작동 원리](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Windows PowerShell 컨테이너 공급자 만들기](./creating-a-windows-powershell-container-provider.md)

[Windows PowerShell 드라이브 공급자 만들기](./creating-a-windows-powershell-drive-provider.md)

[Cmdlet, 공급자, 등록 및 응용 프로그램을 호스트 하는 방법](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)