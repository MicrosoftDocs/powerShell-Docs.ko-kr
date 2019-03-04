---
title: Windows PowerShell 탐색 공급자 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- navigation providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], navigation provider
ms.assetid: 8bd3224d-ca6f-4640-9464-cb4d9f4e13b1
caps.latest.revision: 5
ms.openlocfilehash: 066aa188d5d7dfde5af424a3bb8f15ff51c1e936
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856959"
---
# <a name="creating-a-windows-powershell-navigation-provider"></a>Windows PowerShell 탐색 공급자 만들기

이 항목에서는 데이터 저장소를 탐색할 수 있는 Windows PowerShell 탐색 공급자를 만드는 방법을 설명 합니다. 이 유형의 공급자는 재귀 명령, 중첩 된 컨테이너 및 상대 경로 지원합니다.

> [!NOTE]
> 다운로드할 수 있습니다는 C# Microsoft Windows 소프트웨어 개발 키트에 대 한 Windows Vista 및.NET Framework 3.0 런타임 구성 요소를 사용 하 여이 공급자에 대 한 원본 파일 (AccessDBSampleProvider05.cs). 다운로드 지침에 대해서 [Windows PowerShell 설치 및 Windows PowerShell SDK를 다운로드 하는 방법을](/powershell/developer/installing-the-windows-powershell-sdk)합니다.
> 다운로드할 수 있습니다는 C# Microsoft Windows 소프트웨어 개발 키트에 대 한 Windows Vista 및.NET Framework 3.0 런타임 구성 요소를 사용 하 여이 공급자에 대 한 원본 파일 (AccessDBSampleProvider05.cs). 다운로드 지침에 대해서 [Windows PowerShell 설치 및 Windows PowerShell SDK를 다운로드 하는 방법을](/powershell/developer/installing-the-windows-powershell-sdk)합니다.
>
> 다운로드 한 소스 파일에서 사용할 수는  **\<PowerShell 샘플 >** 디렉터리입니다.
>
> 다른 Windows PowerShell 공급자 구현에 대 한 자세한 내용은 참조 하십시오 [Your Windows PowerShell 공급자 디자인](./designing-your-windows-powershell-provider.md)합니다.

여기에 설명 된 공급자는 사용자 데이터베이스에 있는 데이터 테이블을 이동할 수 있도록 사용자 핸들 Access 데이터베이스 드라이브를 설정 합니다. 사용자 고유의 탐색 공급자를 만들 때 드라이브의 정규화 된 경로 탐색 하는 데 필요한 확인, 상대 경로 정규화, 자식 이름을 가져올 항목의 부모 경로 가져옵니다 하 고 테스트 하는 방법 뿐만 아니라 데이터 저장소의 항목을 이동할 수 있는 메서드를 구현할 수 있습니다. 항목이 컨테이너인 경우를 식별 합니다.

> [!CAUTION]
> 이 디자인 이름 ID 사용 하 여 필드가 있는 데이터베이스를 가정 하 고 필드의 형식이 LongInteger 알아야 합니다.

다음은이 항목에서 섹션을 포함 합니다. Windows PowerShell 탐색 공급자 작성에 익숙한 경우 나타나는 순서에 따라이 정보를 읽습니다. 그러나 Windows PowerShell 탐색 공급자 작성에 익숙한 경우 하세요로 직접 이동 해야 하는 정보.

- [PS 탐색 공급자 클래스를 정의합니다.](#Define-the-Windows-PowerShell-provider)

- [기본 기능 정의](#Defining-Base-Functionality)

- [PS 경로 만들기](#Creating-a-Windows-PowerShell-Path)

- [부모 경로 검색합니다.](#Retrieving-the-Parent-Path)

- [자식 경로 이름 검색](#Retrieve-the-Child-Path-Name)

- [항목 컨테이너 인지 확인 합니다.](#Determining-if-an-Item-is-a-Container)

- [항목 이동](#Moving-an-Item)

- [동적 매개 변수를 연결 합니다 `Move-Item` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Move-Item-Cmdlet)

- [상대 경로 정규화합니다.](#Normalizing-a-Relative-Path)

- [코드 샘플](#Code-Sample)

- [개체 유형 정의 및 서식 지정](#Defining-Object-Types-and-Formatting)

- [Windows PowerShell 공급자 작성](#Building-the-Windows-PowerShell-provider)

- [Windows PowerShell 공급자 테스트](#Testing-the-Windows-PowerShell-provider)

## <a name="define-the-windows-powershell-provider"></a>Windows PowerShell 공급자를 정의 합니다.

Windows PowerShell 탐색 공급자에서 파생 되는.NET 클래스를 만들어야 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 기본 클래스입니다. 이 섹션에 설명 된 탐색 공급자에 대 한 클래스 정의 다음과 같습니다.

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L31-L32 "AccessDBProviderSample05.cs")]

이 공급자는 [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) 특성에는 두 개의 매개 변수가 포함 됩니다. 첫 번째 매개 변수는 Windows PowerShell에서 사용 되는 공급자에 대 한 알기 쉬운 이름을 지정 합니다. 두 번째 매개 변수는 명령 처리 하는 동안 공급자가 Windows PowerShell 런타임에 노출 하는 Windows PowerShell 특정 기능을 지정 합니다. 이 공급자에 대 한 추가 되는 Windows PowerShell 특정 기능이 없으며 있습니다.

## <a name="defining-base-functionality"></a>기본 기능 정의

에 설명 된 대로 [디자인 해당 PS 공급자](./designing-your-windows-powershell-provider.md)서 [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 다른 공급자를 제공 하는 다른 여러 클래스에서 파생 되는 기본 클래스 기능입니다. Windows PowerShell 탐색 공급자, 따라서 정의 해야 모든 해당 클래스에서 제공 하는 기능.

특정 세션 초기화 정보를 추가 하 고 공급자가 사용 되는 리소스를 해제 하는 것에 대 한 기능을 구현 하려면 참조 [기본 PS 공급자 만들기](./creating-a-basic-windows-powershell-provider.md)합니다. 그러나 여기에 설명 된 공급자 등 대부분의 공급자 기본적으로 Windows PowerShell에서 제공 하는이 기능을 사용할 수 있습니다.

Windows PowerShell 드라이브를 통해 데이터 저장소에 액세스 하려면의 메서드를 구현 해야 합니다 [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 기본 클래스입니다. 이러한 메서드를 구현 하는 방법에 대 한 자세한 내용은 참조 하세요. [Windows PowerShell 드라이브 공급자 만들기](./creating-a-windows-powershell-drive-provider.md)합니다.

가져오기, 설정 및 지우기 항목을 같은 데이터 저장소의 항목을 조작 하는 공급자에서 제공 하는 메서드를 구현 해야 합니다는 [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 기본 클래스입니다. 이러한 메서드를 구현 하는 방법에 대 한 자세한 내용은 참조 하세요. [Windows PowerShell 항목 공급자 만들기](./creating-a-windows-powershell-item-provider.md)합니다.

자식 항목 또는 데이터 저장소 뿐만 아니라 만들기, 복사, 이름 바꾸기 및 항목을 제거 하는 메서드 이름을 제공한 메서드를 구현 해야 합니다 [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)기본 클래스입니다. 이러한 메서드를 구현 하는 방법에 대 한 자세한 내용은 참조 하세요. [Windows PowerShell 컨테이너 공급자 만들기](./creating-a-windows-powershell-container-provider.md)합니다.

## <a name="creating-a-windows-powershell-path"></a>Windows PowerShell 경로 만들기

Windows PowerShell 탐색 공급자에서는 공급자-내부 Windows PowerShell 경로 사용 하 여 데이터 저장소의 항목을 이동 합니다. 공급자 공급자-내부 경로 만들려면 구현 해야 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) 결합-Path cmdlet에서 지원 메서드를 호출 합니다. 이 메서드는 부모 및 자식 경로 간의 공급자별 경로 구분 기호를 사용 하 여 내부 공급자 경로로 부모와 자식 경로 결합 합니다.

기본 구현에서는 사용 하 여 경로 "/" 또는 "\\""를 경로 구분 기호 정규화 경로 구분 기호로\\", 둘 사이의 구분 기호를 사용 하 여 부모 및 자식 경로 부분을 결합 및 다음 포함 된 문자열을 반환 합니다 결합 된 경로입니다.

이 탐색 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는 기본 구현의 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) 메서드.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermakepath](Msh_samplestestcmdlets#testprovidermakepath)]  -->

#### <a name="things-to-remember-about-implementing-makepath"></a>MakePath를 구현 하는 방법에 대 한 고려해 야 할 사항

다음과의 구현에 적용 될 수 있습니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath):

- 구현의 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) 메서드 공급자 네임 스페이스에 잘못 된 정규화 된 경로와 경로 확인 하지 해야 합니다. 각 매개 변수에 경로 부분을 나타낼 수 있습니다 하는 결합 된 부분 정규화 된 경로 생성 하지 않습니다 주의 해야 합니다. 예를 들어 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) 파일 시스템 공급자에 대 한 메서드는에서 "windows\system32" 나타날는 `parent` 매개 변수와 "abc.dll"에 `child` 매개 변수입니다. 이러한 값을 조인 하는 메서드는 "\\" 구분 기호 및 반환 "windows\system32\abc.dll"에 정규화 된 파일 시스템 경로가 아닙니다.

  > [!IMPORTANT]
  > 호출에서 제공 하는 경로 파트 [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) 공급자 네임 스페이스에서 사용할 수 없는 문자가 포함 될 수 있습니다. 이러한 문자는 와일드 카드 확장에 대 한 대부분 사용 하 고이 메서드의 구현은 제거 하지 않아야 합니다.

## <a name="retrieving-the-parent-path"></a>부모 경로 검색합니다.

Windows PowerShell 탐색 공급자를 구현 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) 상위 파트의 지정 된 전체 또는 일부를 검색 하는 방법 공급자 관련 경로입니다. 메서드는 경로의 하위 파트를 제거 하 고 부모 경로 부분을 반환 합니다. `root` 매개 변수는 드라이브의 루트에 정규화 된 경로 지정 합니다. 이 매개 변수는 null 이거나 탑재 된 드라이브 검색 작업에 대 한 사용에 없는 경우 비어 있을 수 있습니다. 루트를 지정 하는 경우 메서드는 루트 동일한 트리에 있는 컨테이너에 경로 반환 해야 합니다.

샘플 탐색 공급자는이 메서드를 재정의 하지 않습니다 하지만 기본 구현을 사용 합니다. 함께 사용 하는 경로 받아들이는지 "/" 및 "\\" 경로 구분 기호로 합니다. 만 있는 경로 정규화 먼저 "\\" 구분 기호를 마지막으로 오프 부모 경로 분할 "\\" 부모 경로 반환 합니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetparentpath](Msh_samplestestcmdlets#testprovidergetparentpath)]  -->

#### <a name="to-remember-about-implementing-getparentpath"></a>GetParentPath를 구현 하는 방법에 대 한 기억 하기

구현 된 [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) 메서드는 공급자 네임 스페이스에 대 한 경로 구분 기호에 어휘 적으로 경로 분할 해야 합니다. 예를 들어, 파일 시스템 공급자가이 메서드를 사용 하 여 마지막 검색할 "\\" 구분 기호 왼쪽에 모든 항목을 반환 합니다.

## <a name="retrieve-the-child-path-name"></a>자식 경로 이름을 검색 합니다.

공급자가 구현 하 여 탐색 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) 표시 된 전체에 있는 항목의 자식 (리프 요소) 이름을 검색 하는 방법 또는 공급자별 경로 부분입니다.

샘플 탐색 공급자는이 메서드를 재정의 하지 않습니다. 기본 구현은 다음과 같습니다. 함께 사용 하는 경로 받아들이는지 "/" 및 "\\" 경로 구분 기호로 합니다. 만 있는 경로 정규화 먼저 "\\" 구분 기호를 마지막으로 오프 부모 경로 분할 "\\" 자식 요소의 이름을 경로 부분을 반환 합니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildname](Msh_samplestestcmdlets#testprovidergetchildname)]  -->

#### <a name="things-to-remember-about-implementing-getchildname"></a>GetChildName를 구현 하는 방법에 대 한 고려해 야 할 사항

구현 된 [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) 메서드는 경로 구분 기호에 어휘 적으로 경로 분할 해야 합니다. 제공된 된 경로의 경로 구분 기호를 포함 하는 경우 메서드는 수정 되지 않은 경로 반환 해야 합니다.

> [!IMPORTANT]
> 이 메서드에 대 한 호출에서 제공한 경로 공급자 네임 스페이스에서 유효 하지 않은 문자를 포함할 수 있습니다. 이러한 문자는 와일드 카드 확장 또는 정규식 일치에 사용 되는 가장 가능성이 높은 및이 메서드의 구현은 제거 하지 않아야 합니다.

## <a name="determining-if-an-item-is-a-container"></a>항목 컨테이너 인지 확인 합니다.

탐색 공급자를 구현할 수는 [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) 메서드를 지정된 된 경로 컨테이너를 가리키는지 확인 합니다. 경로 컨테이너 및 false 나타냅니다 그렇지 않은 경우 true를 반환 합니다. 사용자가이 메서드를 사용할 수는 `Test-Path` 제공 된 경로 대 한 cmdlet입니다.

다음 코드에서는 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) 샘플 탐색 공급자에서 구현 합니다. 메서드는 지정 된 경로가 올바른지와 테이블 존재 및 경로 컨테이너를 나타내면 true를 반환 하는 경우를 확인 합니다.

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L847-L872 "AccessDBProviderSample05.cs")]

#### <a name="things-to-remember-about-implementing-isitemcontainer"></a>IsItemContainer를 구현 하는 방법에 대 한 고려해 야 할 사항

.NET 클래스 탐색 공급자에서 ExpandWildcards, 필터, 포함 또는 제외의 공급자 기능을 선언할 수 있습니다 합니다 [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거형입니다. 이 예에서 구현의 [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) 전달 경로 요구 사항을 충족 하는지 확인 해야 합니다. 이 작업을 수행 하는 메서드 액세스 해야 적절 한 속성을 예를 들어, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 속성입니다.

## <a name="moving-an-item"></a>항목 이동

지 원하는 합니다 `Move-Item` cmdlet을 탐색 공급자 구현 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 메서드. 로 지정한 항목을 이동 하는이 메서드는 `path` 컨테이너에 제공 된 경로에 매개 변수는 `destination` 매개 변수입니다.

샘플 탐색 공급자를 재정의 하지 않습니다 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 메서드. 다음은 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitem](Msh_samplestestcmdlets#testprovidermoveitem)]  -->

#### <a name="things-to-remember-about-implementing-moveitem"></a>MoveItem를 구현 하는 방법에 대 한 고려해 야 할 사항

.NET 클래스 탐색 공급자에서 ExpandWildcards, 필터, 포함 또는 제외의 공급자 기능을 선언할 수 있습니다 합니다 [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거형입니다. 이 예에서 구현의 [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 전달 경로 요구 사항을 충족 하는지 확인 해야 합니다. 이 작업을 수행 하는 메서드 액세스 해야 적절 한 속성을 예를 들어, **CmdletProvider.Exclude** 속성입니다.

기본적으로이 메서드는 재정의 이동 하지 않아야 개체 기존 개체에 대해 경우가 아니면 합니다 [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 속성이 `true`합니다. 예를 들어, 파일 시스템 공급자는 복사 하지 c:\temp\abc.txt 기존 c:\bar.txt 파일 경우가 아니면 합니다 [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 속성이 `true`합니다. 경로에 지정 된 경우는 `destination` 매개 변수가 존재 하며 컨테이너에는 [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 속성이 필요 하지 않습니다. 이 경우 [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 가리키는 항목을 이동 해야 합니다 `path` 매개 변수는 컨테이너를 가리키는 `destination` 자식으로 매개 변수.

구현 된 [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 메서드를 호출 해야 [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 데이터 저장소로 변경 하기 전에 해당 반환 값을 확인 합니다. 이 메서드는 변경 될 때 시스템 상태를 예를 들어 파일을 삭제 하는 작업의 실행을 확인 하려면 사용 됩니다. [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 명령줄 설정이 나 기본 설정 변수에서 고려 Windows PowerShell 런타임에 사용자에 게 변경 될 리소스의 이름을 전송 사용자에 게 표시 되어야 할 사항을 확인 합니다.

호출한 후 [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 반환 `true`는 [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 메서드를 호출 해야 합니다 [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 메서드. 이 메서드는 작업을 계속 해야 하는 경우에 피드백을 허용 하도록 사용자에 게 메시지를 보냅니다. 공급자를 호출 해야 [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 잠재적으로 위험한 시스템 수정에 대 한 추가 검사 때문입니다.

## <a name="attaching-dynamic-parameters-to-the-move-item-cmdlet"></a>동적 연결 매개 변수를 Move-item Cmdlet

경우에 따라는 `Move-Item` cmdlet에는 런타임에 동적으로 제공 되는 추가 매개 변수가 필요 합니다. 이러한 동적 매개 변수를 제공 하려면 탐색 공급자를 구현 해야 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) 필수 매개 변수 값을 가져오는 방법 cmdlet 클래스와 유사한 특성에 속성과 필드를 구문 분석 하는 개체 돌아가 표시 된 경로에 있는 항목에서 또는 [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체입니다.

이 탐색 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는 기본 구현의 [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)합니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters](Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters)]  -->

## <a name="normalizing-a-relative-path"></a>상대 경로 정규화합니다.

공급자가 구현 하 여 탐색 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) 에 지정 된 정규화 된 경로 정규화 하는 메서드가 `path` 매개 변수 지정 된 경로 상대적인 것으로 `basePath` 매개 변수입니다. 메서드는 정규화 된 경로 문자열 표현을 반환 합니다. 경우에 오류를 기록 합니다 `path` 매개 변수가 존재 하지 않는 경로 지정 합니다.

샘플 탐색 공급자는이 메서드를 재정의 하지 않습니다. 다음은 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernormalizepath](Msh_samplestestcmdlets#testprovidernormalizepath)]  -->

#### <a name="things-to-remember-about-implementing-normalizerelativepath"></a>NormalizeRelativePath를 구현 하는 방법에 대 한 고려해 야 할 사항

구현의 [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) 구문 분석 되어야 합니다는 `path` 매개 변수 이지만 해당를 순수 하 게 구문 구문 분석을 사용 하지 않아도 됩니다. 디자인 데이터 저장소의 경로 정보를 조회 하는 경로 만들 경로 사용 하도록이 메서드는 대/소문자와 일치 하는 것이 좋습니다 하 경로 구문 표준화 합니다.

## <a name="code-sample"></a>코드 예제

전체 샘플 코드를 보려면 [AccessDbProviderSample05 코드 샘플](./accessdbprovidersample05-code-sample.md)합니다.

## <a name="defining-object-types-and-formatting"></a>개체 유형 정의 및 서식 지정

기존 개체에 멤버를 추가 하거나 새 개체를 정의 하는 공급자에 대 한 것 같습니다. 자세한 내용은[확장 개체 형식 및 서식](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)합니다.
기존 개체에 멤버를 추가 하거나 새 개체를 정의 하는 공급자에 대 한 것 같습니다. 자세한 내용은[확장 개체 형식 및 서식](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)합니다.

## <a name="building-the-windows-powershell-provider"></a>Windows PowerShell 공급자 작성

자세한 내용은 [등록 Cmdlet, 공급자 및 응용 프로그램을 호스트 하는 방법을](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)합니다.
자세한 내용은 [등록 Cmdlet, 공급자 및 응용 프로그램을 호스트 하는 방법을](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)합니다.

## <a name="testing-the-windows-powershell-provider"></a>Windows PowerShell 공급자 테스트

Windows PowerShell을 사용 하 여 Windows PowerShell 공급자가 등록 하는 경우에 파생에서 사용할 수 있는 cmdlet을 포함 하 여 명령줄에서 지원 되는 cmdlet을 실행 하 여 테스트할 수 있습니다. 이 예제에서는 샘플 탐색 공급자를 테스트 합니다.

1. 새 셸을 실행 하 고 사용 된 `Set-Location` Access 데이터베이스를 가리키는 경로 설정 하는 cmdlet입니다.

   ```powershell
   Set-Location mydb:
   ```

2. 이제 실행을 `Get-Childitem` cmdlet을 사용할 수 있는 데이터베이스 테이블에는 데이터베이스 항목의 목록을 검색 합니다. 각 테이블에 대해이 cmdlet도 테이블 행의 수를 검색합니다.

   ```powershell
   Get-ChildItem | Format-Table rowcount,name -AutoSize
   ```

   ```output
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

3. 사용 된 `Set-Location` 직원 데이터 테이블의 위치를 설정 하려면 다시 cmdlet.

   ```powershell
   Set-Location Employees
   ```

4. 이제 사용해 보겠습니다는 `Get-Location` Employees 테이블에 경로 검색 하는 cmdlet입니다.

   ```powershell
   Get-Location
   ```

   ```output
   Path
   ----
   mydb:\Employees
   ```

5. 이제 사용 합니다 `Get-Childitem` cmdlet으로 파이프 합니다 `Format-Table` cmdlet. Cmdlet이이 집합이 테이블 행에는 직원 데이터 테이블에 대 한 항목을 검색 합니다. 형식이 지정 될 지정 된 대로 `Format-Table` cmdlet.

   ```powershell
   Get-ChildItem | Format-Table rownumber,psiscontainer,data -AutoSize
   ```

   ```output
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

6. 이제 실행할 수 있습니다는 `Get-Item` 직원 데이터 테이블의 행 0에 대 한 항목을 검색 하기 위한 cmdlet입니다.

   ```powershell
   Get-Item 0
   ```

   ```output
   PSPath        : AccessDB::C:\PS\Northwind.mdb\Employees\0
   PSParentPath  : AccessDB::C:\PS\Northwind.mdb\Employees
   PSChildName   : 0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data           : System.Data.DataRow
   RowNumber      : 0
   ```

7. 사용 된 `Get-Item` 행 0에에서 있는 항목에 대 한 직원 데이터를 검색 하기 위한 다시 cmdlet.

   ```powershell
   (Get-Item 0).data
   ```

   ```output
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

[디자인 Your Windows PowerShell 공급자](./designing-your-windows-powershell-provider.md)

[확장 개체 형식 및 서식 지정](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[확장 개체 형식 및 서식 지정](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Windows PowerShell 컨테이너 공급자 구현](./creating-a-windows-powershell-container-provider.md)

[Cmdlet, 공급자, 등록 및 응용 프로그램을 호스트 하는 방법](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Cmdlet, 공급자, 등록 및 응용 프로그램을 호스트 하는 방법](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell 프로그래머 가이드](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)