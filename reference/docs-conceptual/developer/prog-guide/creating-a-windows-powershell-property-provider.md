---
title: Windows PowerShell 속성 공급자 만들기 | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- property providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], property provider
ms.openlocfilehash: e8ef92629fe036154cdd2f0facbe0cbe8add7533
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87778939"
---
# <a name="creating-a-windows-powershell-property-provider"></a>Windows PowerShell 속성 공급자 만들기

이 항목에서는 사용자가 데이터 저장소에 있는 항목의 속성을 조작할 수 있도록 하는 공급자를 만드는 방법에 대해 설명 합니다. 결과적으로이 유형의 공급자는 Windows PowerShell 속성 공급자 라고 합니다. 예를 들어 Windows PowerShell에서 제공 하는 레지스트리 공급자는 레지스트리 키 값을 레지스트리 키 항목의 속성으로 처리 합니다. 이 유형의 공급자는 .NET 클래스 구현에 [system.object](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) 를 추가 하 여 구현 해야 합니다.

> [!NOTE]
> Windows powershell은 Windows PowerShell 공급자를 개발 하는 데 사용할 수 있는 템플릿 파일을 제공 합니다. TemplateProvider.cs 파일은 Windows Vista 용 Microsoft Windows 소프트웨어 개발 키트 및 .NET Framework 3.0 런타임 구성 요소에서 사용할 수 있습니다. 다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/scripting/developer/installing-the-windows-powershell-sdk)을 참조 하세요.
> 다운로드 한 템플릿은 디렉터리에서 사용할 수 있습니다 **\<PowerShell Samples>** . 이 파일의 복사본을 만들고 복사본을 사용 하 여 새 Windows PowerShell 공급자를 만들어 필요 하지 않은 기능을 제거 해야 합니다. 다른 Windows PowerShell 공급자 구현에 대 한 자세한 내용은 [Windows Powershell 공급자 디자인](./designing-your-windows-powershell-provider.md)을 참조 하세요.

> [!CAUTION]
> 속성 공급자의 메서드는 System.object를 사용 하 여 개체를 작성 해야 합니다. [Writepropertyobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WritePropertyObject) 메서드.

## <a name="defining-the-windows-powershell-provider"></a>Windows PowerShell 공급자 정의

속성 공급자는 [system.object](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) 를 지 원하는 .net 클래스를 만들어야 합니다 .이 인터페이스는. 다음은 Windows PowerShell에서 제공 하는 TemplateProvider.cs 파일의 기본 클래스 선언입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration](Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration)]  -->

## <a name="defining-base-functionality"></a>기본 기능 정의

System.object [를](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) 공급자 기본 클래스 중 하나에 연결할 수 있습니다. 여기서는 system.object를 제외 하 고 [system.object](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 를 사용 하는 경우에는이 클래스를 사용 합니다. 사용 중인 기본 클래스에 필요한 기본 기능을 추가 합니다. 기본 클래스에 대 한 자세한 내용은 [Windows PowerShell 공급자 디자인](./designing-your-windows-powershell-provider.md)을 참조 하세요.

## <a name="retrieving-properties"></a>속성 검색

속성을 검색 하려면 공급자가 cmdlet의 호출을 지원 하기 위해 [system.web. i n i](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) o n * 메서드를 구현 해야 합니다. `Get-ItemProperty` 이 메서드는 지정 된 공급자 내부 경로 (정규화 된)에 있는 항목의 속성을 검색 합니다.

`providerSpecificPickList`매개 변수는 검색할 속성을 나타냅니다. 이 매개 변수가 `null` 이거나 비어 있는 경우 메서드는 모든 속성을 검색 해야 합니다. 또한,이 경우에는 검색 된 속성의 속성 모음을 나타내는 [system.web. PSObject](/dotnet/api/System.Management.Automation.PSObject) 개체의 [인스턴스를 작성](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) 하는 것이 좋습니다. 메서드는 아무것도 반환 하지 않아야 합니다.

선택 목록의 각 요소에 대 한 속성 이름의 와일드 카드 확장을 지원 하려면 [system.object](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) 를 구현 하는 것이 좋습니다. 이렇게 하려면 [Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) 클래스를 사용 하 여 와일드 카드 패턴 일치를 수행 합니다.

다음은 Windows PowerShell에서 제공 하는 TemplateProvider.cs [파일에서 제공](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) 하는 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty)]  -->

#### <a name="things-to-remember-about-implementing-getproperty"></a>GetProperty 구현에 대해 기억할 사항

다음 조건은 System.object의 구현에 적용 될 수 있습니다. [* * *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty):

- 공급자 클래스를 정의 하는 경우 Windows PowerShell 속성 공급자는 ExpandWildcards, Filter, Include 또는 Exclude의 공급자 기능을 [system.object](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거에서 선언할 수 있습니다. 이러한 경우에는 메서드에 전달 된 경로가 지정 된 기능의 요구 사항을 충족 하는지 확인 하는 데에는 [이 메서드를](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) 구현 해야 합니다. 이 작업을 수행 하려면 메서드가 적절 한 속성 (예: System.object)에 액세스 해야 합니다. [*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 및 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .... n a m.

- 기본적으로이 메서드의 재정의는 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 가로 설정 된 경우를 제외 하 고 사용자 로부터 숨겨진 개체에 대 한 판독기를 검색 하면 안 됩니다. `true` 경로가 사용자 및 시스템에서 숨겨진 항목을 나타내는 경우 오류를 작성 해야 합니다 [. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 는로 설정 됩니다. `false`

## <a name="attaching-dynamic-parameters-to-the-get-itemproperty-cmdlet"></a>동적 매개 변수를 Get-itemproperty Cmdlet에 연결

Cmdlet에는 `Get-ItemProperty` 런타임에 동적으로 지정 되는 추가 매개 변수가 필요할 수 있습니다. 이러한 동적 매개 변수를 제공 하려면 Windows PowerShell 속성 공급자가 System.object를 구현 해야 합니다. [Getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) 메서드. 매개 변수는 정규화 된 `path` 공급자 내부 경로를 나타내고 `providerSpecificPickList` 매개 변수는 명령줄에 입력 된 공급자별 속성을 지정 합니다. `null`속성이 cmdlet으로 파이프 되 면이 매개 변수가 이거나 비어 있을 수 있습니다. 이 경우이 메서드는 cmdlet 클래스 또는 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체와 유사한 구문 분석 특성이 있는 속성 및 필드가 있는 개체를 반환 합니다. Windows PowerShell 런타임은 반환 된 개체를 사용 하 여 cmdlet에 매개 변수를 추가 합니다.

다음은 Windows PowerShell에서 제공 하는 TemplateProvider.cs 파일에서 제공 하는 기본 구현인 [system.object](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) 의 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters)]  -->

## <a name="setting-properties"></a>속성 설정

속성을 설정 하려면 Windows PowerShell 속성 공급자가 cmdlet의 호출을 지원 하기 위해 [system.object](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) 를 구현 해야 합니다. `Set-ItemProperty` 이 메서드는 지정 된 경로에 있는 항목의 속성을 하나 이상 설정 하 고 필요한 경우 제공 된 속성을 덮어씁니다.
[System.object. Setproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) 는 업데이트 된 속성의 속성 모음을 나타내는 [system.object](/dotnet/api/System.Management.Automation.PSObject) 의 인스턴스를 작성 합니다. 또한이 개체는 업데이트 된 속성의 속성 모음을 나타냅니다.

다음은 Windows PowerShell에서 제공 하는 TemplateProvider.cs [파일에서 제공](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) 하는 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty)]  -->

#### <a name="things-to-remember-about-implementing-set-itemproperty"></a>Get-itemproperty 구현에 대해 기억할 사항

다음 조건은 System.object의 구현에 적용 될 수 있습니다. [Setproperty * *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty):

- 공급자 클래스를 정의 하는 경우 Windows PowerShell 속성 공급자는 ExpandWildcards, Filter, Include 또는 Exclude의 공급자 기능을 [system.object](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거에서 선언할 수 있습니다. 이러한 경우에는 [system.object](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) 를 구현 하 여 메서드에 전달 된 경로가 지정 된 기능의 요구 사항을 충족 하는지 확인 해야 합니다 .이 메서드를 구현 해야 합니다. 이 작업을 수행 하려면 메서드가 적절 한 속성 (예: System.object)에 액세스 해야 합니다. [*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 및 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .... n a m.

- 기본적으로이 메서드의 재정의는 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 가로 설정 된 경우를 제외 하 고 사용자 로부터 숨겨진 개체에 대 한 판독기를 검색 하면 안 됩니다. `true` 경로가 사용자 및 시스템에서 숨겨진 항목을 나타내는 경우 오류를 작성 해야 합니다 [. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 는로 설정 됩니다. `false`

- System.object 구현에서는 데이터 저장소를 변경 하기 전에 해당 반환 값을 확인 [하 고 해당 반환 값을 확인](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 하는 방법으로 구현 해야 합니다. ". [i](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) n d. 이 메서드는 시스템 상태가 변경 될 때 (예: 파일 이름 바꾸기) 작업 실행을 확인 하는 데 사용 됩니다.
  Windows PowerShell 런타임을 사용 하 여 사용자에 게 변경할 리소스의 [이름을 보내고,](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 표시 되는 항목을 결정 하는 데 필요한 명령줄 설정 또는 기본 변수를 처리 합니다.

  [System.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 를 호출 하 고 나면, 잠재적으로 위험할 수 있는 시스템을 수정할 수 있는 경우에는 system.object를 호출 해야 합니다. 즉,. n a m p. i n p. i n d. p a n `true` [*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) 메서드는 [system.object를](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 호출 해야 합니다. 이 메서드는 사용자에 게 확인 메시지를 보내 작업을 계속 해야 함을 나타내는 추가 피드백을 허용 합니다.

## <a name="attaching-dynamic-parameters-for-the-set-itemproperty-cmdlet"></a>Get-itemproperty Cmdlet에 대 한 동적 매개 변수 연결

Cmdlet에는 `Set-ItemProperty` 런타임에 동적으로 지정 되는 추가 매개 변수가 필요할 수 있습니다. 이러한 동적 매개 변수를 제공 하려면 Windows PowerShell 속성 공급자가 System.object를 구현 해야 합니다. [Setpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) 메서드. 이 메서드는 cmdlet 클래스 또는 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체와 유사한 구문 분석 특성이 있는 속성 및 필드가 있는 개체를 반환 합니다. `null`동적 매개 변수를 추가할 수 없는 경우 값을 반환할 수 있습니다.

다음은 Windows PowerShell에서 제공 하는 TemplateProvider.cs 파일에서 제공 하는 기본 구현인 [system.object](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) 의 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters)]  -->

## <a name="clearing-properties"></a>속성 지우기

속성을 지우려면 Windows PowerShell 속성 공급자가 cmdlet의 호출을 지원 하기 위해 System.object를 구현 해야 합니다 [. clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) 메서드. `Clear-ItemProperty` 이 메서드는 지정 된 경로에 있는 항목에 대 한 속성을 하나 이상 설정 합니다.

다음은 Windows PowerShell에서 제공 하는 TemplateProvider.cs 파일에서 제공 되는 기본 구현인 [system.object](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) 의 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty](Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty)]  -->

#### <a name="thing-to-remember-about-implementing-clearproperty"></a>ClearProperty 구현에 대해 기억해 야 할 사항

다음 조건은 System.object의 구현에 적용 될 수 있습니다. [Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty):.

- 공급자 클래스를 정의 하는 경우 Windows PowerShell 속성 공급자는 ExpandWildcards, Filter, Include 또는 Exclude의 공급자 기능을 [system.object](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거에서 선언할 수 있습니다. 이러한 경우에는 메서드에 전달 된 경로가 지정 된 기능의 요구 사항을 충족 하는지 확인 하는 데에는 [이 메서드를](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) 구현 해야 합니다. 이 작업을 수행 하려면 메서드가 적절 한 속성 (예: System.object)에 액세스 해야 합니다. [*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 및 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .... n a m.

- 기본적으로이 메서드의 재정의는 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 가로 설정 된 경우를 제외 하 고 사용자 로부터 숨겨진 개체에 대 한 판독기를 검색 하면 안 됩니다. `true` 경로가 사용자 및 시스템에서 숨겨진 항목을 나타내는 경우 오류를 작성 해야 합니다 [. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 는로 설정 됩니다. `false`

- [System.object](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) 구현에서는 데이터 저장소를 변경 하기 전에 해당 반환 값을 확인 [하 고 해당 반환 값을 확인](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 하는 것이 좋습니다.-... a n d. 이 메서드는 콘텐츠 지우기와 같은 시스템 상태를 변경 하기 전에 작업 실행을 확인 하는 데 사용 됩니다.
  Windows PowerShell 런타임이 사용자에 게 변경할 리소스의 [이름을 보내고,](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 표시 되는 항목을 결정 하는 데 사용 되는 모든 명령줄 설정이 나 기본 설정 변수를 고려 하 여 Windows PowerShell 런타임을 사용 합니다.

  System.object를 호출 하면 [ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 가 반환 `true` 되 고 잠재적으로 위험한 시스템을 수정할 수 있는 경우에는 system.object를 다시 만들 수 있습니다. [Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) 메서드는 system.object를 호출 해야 합니다. [shouldprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 메서드를 호출 해야 합니다. 이 메서드는 사용자에 게 확인 메시지를 보내 잠재적으로 위험한 작업을 계속 해야 함을 나타낼 수 있습니다.

## <a name="attaching-dynamic-parameters-to-the-clear-itemproperty-cmdlet"></a>Get-itemproperty Cmdlet에 동적 매개 변수 연결

Cmdlet에는 `Clear-ItemProperty` 런타임에 동적으로 지정 되는 추가 매개 변수가 필요할 수 있습니다. 이러한 동적 매개 변수를 제공 하기 위해 Windows PowerShell 속성 공급자는 System.object를 구현 해야 합니다. [Clearpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) 메서드. 이 메서드는 cmdlet 클래스 또는 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체와 유사한 구문 분석 특성이 있는 속성 및 필드가 있는 개체를 반환 합니다. `null`동적 매개 변수를 추가할 수 없는 경우 값을 반환할 수 있습니다.

다음은 Windows PowerShell에서 제공 하는 TemplateProvider.cs 파일에서 제공 하는 기본 구현인 [system.object](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) 의 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters)]  -->

## <a name="building-the-windows-powershell-provider"></a>Windows PowerShell 공급자 빌드

[Cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법을](https://msdn.microsoft.com/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)참조 하세요.

## <a name="see-also"></a>참고 항목

[Windows PowerShell 공급자](./designing-your-windows-powershell-provider.md)

[Windows PowerShell 공급자 디자인](./designing-your-windows-powershell-provider.md)

[개체 형식 및 서식 확장](https://msdn.microsoft.com/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](https://msdn.microsoft.com/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)
