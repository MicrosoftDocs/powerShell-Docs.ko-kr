---
title: Windows PowerShell 속성 공급자 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- property providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], property provider
ms.assetid: a6adca44-b94b-4103-9970-a9b414355e60
caps.latest.revision: 5
ms.openlocfilehash: 6ec0752a9ae06c5c2cdd1a1851caeeff52d8eb74
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081838"
---
# <a name="creating-a-windows-powershell-property-provider"></a>Windows PowerShell 속성 공급자 만들기

이 항목에서는 사용자가 데이터 저장소에 있는 항목의 속성을 조작할 수 있는 공급자를 만드는 방법을 설명 합니다. 결과적으로이 유형의 공급자는 Windows PowerShell 속성 공급자를 라고 합니다. 예를 들어 레지스트리 공급자 레지스트리 키 항목의 속성으로 Windows PowerShell 핸들 레지스트리 키 값으로 제공 합니다. 이 유형의 공급자를 추가 해야 합니다 [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) .NET 클래스의 구현에 대 한 인터페이스입니다.

> [!NOTE]
> Windows PowerShell에는 Windows PowerShell 공급자를 개발 하는 데 사용할 수 있는 템플릿 파일을 제공 합니다. TemplateProvider.cs 파일은 Microsoft Windows 소프트웨어 개발 키트에 대 한 Windows Vista 및.NET Framework 3.0 런타임 구성 요소에서 사용할 수 있습니다. 다운로드 지침에 대해서 [Windows PowerShell 설치 및 Windows PowerShell SDK를 다운로드 하는 방법을](/powershell/developer/installing-the-windows-powershell-sdk)합니다.
>
> 다운로드 한 템플릿에 사용할 수 있습니다 합니다  **\<PowerShell 샘플 >** 디렉터리입니다. 이 파일의 복사본을 확인 하 고 필요 하지 않은 모든 기능을 제거 하 여 새 Windows PowerShell 공급자를 만들기 위한 복사본을 사용 해야 합니다.
>
> 다른 Windows PowerShell 공급자 구현에 대 한 자세한 내용은 참조 하십시오 [Your Windows PowerShell 공급자 디자인](./designing-your-windows-powershell-provider.md)합니다.

> [!CAUTION]
> 속성 공급자의 메서드를 사용 하 여 모든 개체를 작성 해야 합니다 [System.Management.Automation.Provider.Cmdletprovider.Writepropertyobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WritePropertyObject) 메서드.

다음은이 항목의 섹션을 포함합니다. Windows PowerShell 속성 공급자 쓰기와 잘 모르는 경우이 표시 되는 순서에 따라이 정보를 읽습니다. 그러나 Windows PowerShell 속성 공급자 작성에 익숙한 경우 하세요로 직접 이동 해야 하는 정보.

- [Windows PowerShell 공급자를 정의합니다.](#Defining-the-Windows-PowerShell-provider)

- [기본 기능 정의](#Defining-Base-Functionality)

- [속성 검색](#Retrieving-Properties)

- [동적 매개 변수를 연결 합니다 `Get-ItemProperty` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-ItemProperty-Cmdlet)

- [속성 설정](#Setting-Properties)

- [동적 매개 변수를 연결 합니다 `Set-ItemProperty` Cmdlet](#Attaching-Dynamic-Parameters-for-the-Set-ItemProperty-Cmdlet)

- [속성의 선택을 취소](#Clearing-Properties)

- [동적 매개 변수를 연결 합니다 `Clear-ItemProperty` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Clear-ItemProperty-Cmdlet)

- [Windows PowerShell 공급자 작성](#Building-the-Windows-PowerShell-provider)

## <a name="defining-the-windows-powershell-provider"></a>Windows PowerShell 공급자를 정의합니다.

속성 공급자를 지 원하는.NET 클래스를 만들어야 합니다 [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) 인터페이스입니다. Windows PowerShell에서 제공 되는 TemplateProvider.cs 파일에서 기본 클래스 선언을 다음과 같습니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration](Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration)]  -->

## <a name="defining-base-functionality"></a>기본 기능 정의

합니다 [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) 인터페이스의 경우는 예외는 공급자 기본 클래스 중 하나에 연결할 수는 [ System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 클래스입니다. 사용 하는 기본 클래스에 필요한 기본 기능을 추가 합니다. 기본 클래스에 대 한 자세한 내용은 참조 하세요. [Your Windows PowerShell 공급자 디자인](./designing-your-windows-powershell-provider.md)합니다.

## <a name="retrieving-properties"></a>속성 검색

속성을 검색 하려면 공급자를 구현 해야 합니다 [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) 메서드 호출에서 지원 하기는 `Get-ItemProperty` cmdlet. 이 메서드는 지정된 된 공급자-내부 경로 (정규화 된)에 있는 항목의 속성을 검색 합니다.

`providerSpecificPickList` 매개 변수를 검색 하는 속성을 나타냅니다. 이 매개 변수가 `null` 또는 비어 있는 경우 메서드는 모든 속성을 검색 합니다. 또한 [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) 인스턴스에 씁니다를 [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) 나타내는 개체를 검색된 속성의 속성 모음입니다. 메서드는 아무 것도 반환 해야 합니다.

것이 좋습니다 구현의 [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) 선택 목록의 각 요소에 대 한 속성 이름의 와일드 카드 확장을 지원 합니다. 이 작업을 수행 하려면 사용 합니다 [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) 와일드 카드 패턴 일치를 수행 하는 클래스입니다.

기본 구현은 다음과 같습니다 [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) TemplateProvider.cs 파일 Windows PowerShell에서 제공 합니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty)]  -->

#### <a name="things-to-remember-about-implementing-getproperty"></a>GetProperty를 구현 하는 방법에 대 한 고려해 야 할 사항

다음과의 구현에 적용 될 수 있습니다 [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty):

- 공급자 클래스를 정의 하는 경우 Windows PowerShell 속성 공급자에서 ExpandWildcards, 필터, 포함 또는 제외의 공급자 기능을 선언할 수 있습니다는 [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거형입니다. 이러한 경우의 구현에는 [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) 메서드를 메서드에 전달 된 경로 지정 된 요구 사항을 충족 해야 합니다. 기능입니다. 이 작업을 수행 하는 메서드 액세스 해야 적절 한 속성을 예를 들어, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 고 [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) 속성입니다.

- 기본적으로이 메서드는 재정의 하지 않는 한 사용자 로부터 숨겨진 개체에 대 한 판독기를 검색 하지 않아야 합니다 [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 속성이 `true`합니다. 경로 사용자 로부터 숨겨진 항목을 나타내는 경우 오류를 작성 해야 하 고 [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 로 설정 된 `false`합니다.

## <a name="attaching-dynamic-parameters-to-the-get-itemproperty-cmdlet"></a>Get-itemproperty Cmdlet에 연결 하는 동적 매개 변수

`Get-ItemProperty` cmdlet 런타임에 동적으로 지정 된 추가 매개 변수가 필요 합니다. 이러한 동적 매개 변수를 제공 하려면 Windows PowerShell 속성 공급자를 구현 해야 합니다 [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) 메서드. 합니다 `path` 매개 변수를 정규화 된 공급자-내부 경로 나타냅니다 동안는 `providerSpecificPickList` 매개 변수는 명령줄에 입력 한 공급자별 속성을 지정 합니다. 이 매개 변수 수 `null` 이거나 속성 cmdlet으로 파이프 되는 경우 비어 있습니다. 이 메서드가 속성 및 필드는 cmdlet 클래스와 유사한 특성을 구문 분석 하는 개체를 반환 하는 예제의 경우 또는 [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체입니다. Windows PowerShell 런타임이 cmdlet에 매개 변수를 추가할 반환된 된 개체를 사용 합니다.

기본 구현은 다음과 같습니다 [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) TemplateProvider.cs 파일 Windows PowerShell에서 제공 합니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters)]  -->

## <a name="setting-properties"></a>속성 설정

속성을 설정 하려면 Windows PowerShell 속성 공급자를 구현 해야 합니다는 [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) 메서드 호출에서 지원 하기는 `Set-ItemProperty` cmdlet. 이 메서드는 지정된 된 경로에 항목의 하나 이상의 속성을 설정 하 고 필요에 따라 제공 된 속성을 덮어씁니다. [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) 도 씁니다. 인스턴스를 [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) 의 업데이트 된 속성 모음을 나타내는 개체 속성입니다.

기본 구현은 다음과 같습니다 [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) TemplateProvider.cs 파일 Windows PowerShell에서 제공 합니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty)]  -->

#### <a name="things-to-remember-about-implementing-set-itemproperty"></a>Set-itemproperty를 구현 하는 방법에 대 한 고려해 야 할 사항

다음과의 구현에 적용 될 수 있습니다 [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty):

- 공급자 클래스를 정의 하는 경우 Windows PowerShell 속성 공급자에서 ExpandWildcards, 필터, 포함 또는 제외의 공급자 기능을 선언할 수 있습니다는 [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거형입니다. 이러한 경우의 구현에는 [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) 메서드는 메서드에 전달 된 경로 지정 된 요구 사항을 충족 하는지 확인 해야 합니다 기능입니다. 이 작업을 수행 하는 메서드 액세스 해야 적절 한 속성을 예를 들어, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 고 [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) 속성입니다.

- 기본적으로이 메서드는 재정의 하지 않는 한 사용자 로부터 숨겨진 개체에 대 한 판독기를 검색 하지 않아야 합니다 [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 속성이 `true`합니다. 경로 사용자 로부터 숨겨진 항목을 나타내는 경우 오류를 작성 해야 하 고 [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 로 설정 된 `false`합니다.

- 구현 된 [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) 메서드를 호출 해야 [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 데이터 저장소로 변경 하기 전에 해당 반환 값을 확인 합니다. 이 메서드는 변경 될 때 시스템 상태를 예를 들어, 파일 이름 바꾸기 작업의 실행을 확인 하려면 사용 됩니다. [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) Windows PowerShell 런타임 및 명령줄 설정이 나 결정 하는 데 기본 설정 변수 처리를 사용 하 여 사용자에 게 변경 될 리소스의 이름을 전송 새로운 표시 되어야 합니다.

  호출한 후 [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 반환 `true`잠재적으로 위험한 시스템 수정 작업을 수행할 수 있는 경우는 [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) 메서드를 호출 해야 합니다 [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 메서드. 이 메서드는 작업을 계속할 수를 나타내는 추가 피드백을 허용 하도록 사용자에 게 확인 메시지를 보냅니다.

## <a name="attaching-dynamic-parameters-for-the-set-itemproperty-cmdlet"></a>Set-itemproperty Cmdlet에 대 한 동적 매개 변수 연결

`Set-ItemProperty` cmdlet 런타임에 동적으로 지정 된 추가 매개 변수가 필요 합니다. 이러한 동적 매개 변수를 제공 하려면 Windows PowerShell 속성 공급자를 구현 해야 합니다 [System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) 메서드. 속성 및 cmdlet 클래스와 유사한 특성을 구문 분석 된 필드에 있는 개체를 반환 하는이 메서드 또는 [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체입니다. `null` 없는 동적 매개 변수를 추가할 경우 값을 반환할 수 있습니다.

기본 구현은 다음과 같습니다 [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) TemplateProvider.cs 파일 Windows PowerShell에서 제공 합니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters)]  -->

## <a name="clearing-properties"></a>속성을 선택 취소

속성을 해제 하려면 Windows PowerShell 속성 공급자를 구현 해야 합니다는 [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) 메서드 호출에서 지원 하기는 `Clear-ItemProperty` cmdlet. 이 메서드는 지정된 된 경로에 있는 항목에 대 한 하나 이상의 속성을 설정 합니다.

기본 구현은 다음과 같습니다 [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) TemplateProvider.cs 파일 Windows PowerShell에서 제공 합니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty](Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty)]  -->

#### <a name="thing-to-remember-about-implementing-clearproperty"></a>ClearProperty를 구현 하는 방법에 대 한 기억해 야 할 사항

다음과의 구현에 적용 될 수 있습니다 [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty):

- 공급자 클래스를 정의 하는 경우 Windows PowerShell 속성 공급자에서 ExpandWildcards, 필터, 포함 또는 제외의 공급자 기능을 선언할 수 있습니다는 [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거형입니다. 이러한 경우의 구현에는 [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) 메서드를 메서드에 전달 된 경로 지정 된 요구 사항을 충족 해야 합니다. 기능입니다. 이 작업을 수행 하는 메서드 액세스 해야 적절 한 속성을 예를 들어, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 고 [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) 속성입니다.

- 기본적으로이 메서드는 재정의 하지 않는 한 사용자 로부터 숨겨진 개체에 대 한 판독기를 검색 하지 않아야 합니다 [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 속성이 `true`합니다. 경로 사용자 로부터 숨겨진 항목을 나타내는 경우 오류를 작성 해야 하 고 [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 로 설정 된 `false`합니다.

- 구현 된 [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) 메서드를 호출 해야 [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess ](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 데이터 저장소로 변경 하기 전에 해당 반환 값을 확인 합니다. 이 메서드는 콘텐츠를 지우는 등의 시스템 상태를 변경 되기 전에 작업의 실행을 확인 하려면 사용 됩니다. [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 명령줄 설정이 나 기본 설정 변수에서 고려 Windows PowerShell 런타임에 사용자에 게 변경 될 리소스의 이름을 전송 표시할 내용을 결정 합니다.

  호출한 후 [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 반환 `true`잠재적으로 위험한 시스템 수정 작업을 수행할 수 있는 경우는 [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) 메서드를 호출 해야 합니다 [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 메서드. 이 메서드는 잠재적으로 위험한 작업을 계속할 수를 나타내는 추가 피드백을 허용 하도록 사용자에 게 확인 메시지를 보냅니다.

## <a name="attaching-dynamic-parameters-to-the-clear-itemproperty-cmdlet"></a>Clear-itemproperty Cmdlet에 연결 하는 동적 매개 변수

`Clear-ItemProperty` cmdlet 런타임에 동적으로 지정 된 추가 매개 변수가 필요 합니다. 이러한 동적 매개 변수를 제공 하려면 Windows PowerShell 속성 공급자를 구현 해야 합니다 [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) 메서드. 속성 및 cmdlet 클래스와 유사한 특성을 구문 분석 된 필드에 있는 개체를 반환 하는이 메서드 또는 [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체입니다. `null` 없는 동적 매개 변수를 추가할 경우 값을 반환할 수 있습니다.

기본 구현은 다음과 같습니다 [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) TemplateProvider.cs 파일 Windows PowerShell에서 제공 합니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters)]  -->

## <a name="building-the-windows-powershell-provider"></a>Windows PowerShell 공급자 작성

참조 [Cmdlet, 공급자, 등록 및 응용 프로그램을 호스트 하는 방법을](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)합니다.

## <a name="see-also"></a>참고 항목

[Windows PowerShell 공급자](./designing-your-windows-powershell-provider.md)

[디자인 Your Windows PowerShell 공급자](./designing-your-windows-powershell-provider.md)

[확장 개체 형식 및 서식 지정](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Cmdlet, 공급자, 등록 및 응용 프로그램을 호스트 하는 방법](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)