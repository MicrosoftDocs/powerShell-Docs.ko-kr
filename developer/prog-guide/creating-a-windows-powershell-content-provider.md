---
title: Windows PowerShell 콘텐츠 공급자 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- content providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], content provider
ms.assetid: 3da88ff9-c4c7-4ace-aa24-0a29c8cfa060
caps.latest.revision: 6
ms.openlocfilehash: d7e237514b4db4bce3366836d3b6e0cd340bf107
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855015"
---
# <a name="creating-a-windows-powershell-content-provider"></a>Windows PowerShell 콘텐츠 공급자 만들기

이 항목에서는 데이터 저장소에 있는 항목의 내용을 조작할 수 있도록 해 주는 Windows PowerShell 공급자를 만드는 방법을 설명 합니다. 결과적으로 항목의 내용을 조작할 수 있는 공급자는 Windows PowerShell 콘텐츠 공급자로 하 라고 합니다.

> [!NOTE]
> 다운로드할 수 있습니다는 C# Microsoft Windows 소프트웨어 개발 키트에 대 한 Windows Vista 및.NET Framework 3.0 런타임 구성 요소를 사용 하 여이 공급자에 대 한 원본 파일 (AccessDBSampleProvider06.cs). 다운로드 지침에 대해서 [Windows PowerShell 설치 및 Windows PowerShell SDK를 다운로드 하는 방법을](/powershell/developer/installing-the-windows-powershell-sdk)합니다.
>
> 다운로드 한 소스 파일에서 사용할 수는  **\<PowerShell 샘플 >** 디렉터리입니다.
>
> 다른 Windows PowerShell 공급자 구현에 대 한 자세한 내용은 참조 하십시오 [Your Windows PowerShell 공급자 디자인](./designing-your-windows-powershell-provider.md)합니다.

## <a name="define-the-windows-powershell-content-provider-class"></a>Windows PowerShell 콘텐츠 공급자 클래스를 정의 합니다.

Windows PowerShell 콘텐츠 공급자를 지 원하는.NET 클래스를 만들어야 합니다 [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 인터페이스입니다. 이 섹션에 설명 된 항목 공급자에 대 한 클래스 정의 다음과 같습니다.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L32-L33 "AccessDBProviderSample06.cs")]

이 클래스를 정의 하는 합니다 [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) 특성에는 두 개의 매개 변수가 포함 됩니다. 첫 번째 매개 변수는 Windows PowerShell에서 사용 되는 공급자에 대 한 알기 쉬운 이름을 지정 합니다. 두 번째 매개 변수는 명령 처리 하는 동안 공급자가 Windows PowerShell 런타임에 노출 하는 Windows PowerShell 특정 기능을 지정 합니다. 이 공급자에 대 한 추가 Windows PowerShell 특정 기능이 없으며 있습니다.

## <a name="define-functionality-of-base-class"></a>기본 클래스의 기능 정의

에 설명 된 대로 [디자인 해당 Windows PowerShell 공급자](./designing-your-windows-powershell-provider.md)서 [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 제공 하는 다른 여러 클래스에서 파생 되는 클래스 다른 공급자 기능입니다. Windows PowerShell 콘텐츠 공급자, 따라서 일반적으로 모든 정의 해당 클래스에서 제공 하는 기능입니다.

특정 세션 초기화 정보를 추가 하 고 공급자가 사용 되는 리소스를 해제 하는 것에 대 한 기능을 구현 하는 방법에 대 한 자세한 내용은 참조 하세요. [는 기본 Windows PowerShell 공급자를 만들어](./creating-a-basic-windows-powershell-provider.md)합니다. 그러나 여기에 설명 된 공급자를 비롯 한 대부분의 공급자를 Windows PowerShell에서 제공 하는이 기능의 기본 구현을 사용할 수 있습니다.

데이터 저장소에 액세스 하려면 공급자의 메서드를 구현 해야 합니다 [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 기본 클래스입니다. 이러한 메서드를 구현 하는 방법에 대 한 자세한 내용은 참조 하세요. [Windows PowerShell 드라이브 공급자 만들기](./creating-a-windows-powershell-drive-provider.md)합니다.

가져오기, 설정 및 지우기 항목을 같은 데이터 저장소의 항목을 조작 하는 공급자에서 제공 하는 메서드를 구현 해야 합니다는 [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 기본 클래스입니다. 이러한 메서드를 구현 하는 방법에 대 한 자세한 내용은 참조 하세요. [Windows PowerShell 항목 공급자 만들기](./creating-a-windows-powershell-item-provider.md)합니다.

다중 계층 데이터 저장소에서 작업 하려면, 공급자에서 제공 하는 메서드를 구현 해야 합니다 [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 기본 클래스입니다. 이러한 메서드를 구현 하는 방법에 대 한 자세한 내용은 참조 하세요. [Windows PowerShell 컨테이너 공급자 만들기](./creating-a-windows-powershell-container-provider.md)합니다.

재귀적 명령, 중첩 된 컨테이너 및 상대 경로 지원 하려면 공급자를 구현 해야 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 기본 클래스입니다. 이 Windows PowerShell 콘텐츠 공급자의 연결 수 뿐만 [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 인터페이스는 [ System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 기본 클래스 및 해당 클래스에서 제공 하는 메서드를 구현 하므로 해야 합니다. 자세한 내용은 해당 메서드를 구현 참조 하십시오 [탐색 Windows PowerShell 공급자를 구현](./creating-a-windows-powershell-navigation-provider.md)합니다.

## <a name="implementing-a-content-reader"></a>콘텐츠 판독기 구현

항목에서 콘텐츠를 읽으려면 공급자에서 파생 되는 콘텐츠 판독기 클래스를 구현 해야 합니다 [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader)합니다. 이 공급자에 대 한 콘텐츠 판독기에는 데이터 테이블의 행의 내용에 액세스할 수 있습니다. 콘텐츠 판독기 클래스 정의 **읽기** 표시 된 행에서 데이터를 검색 하 고 해당 데이터를 나타내는 목록을 반환 하는 메서드를 **Seek** 콘텐츠 판독기를 이동 하는 메서드는  **닫기** 콘텐츠는 판독기가 닫히고 하는 메서드 및 **Dispose** 메서드.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2115-L2241 "AccessDBProviderSample06.cs")]

## <a name="implementing-a-content-writer"></a>콘텐츠 작성자를 구현합니다.

공급자를 항목에 콘텐츠를 쓸 콘텐츠를 구현 해야 작성기 클래스에서 파생 되며 [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter)합니다. 콘텐츠 작성기 클래스를 정의 **작성** 지정 된 행 콘텐츠를 기록 하는 메서드를 **Seek** 작성기에 해당 콘텐츠를 이동 하는 메서드를 **닫기** 닫는 메서드를 콘텐츠 작성자와 **Dispose** 메서드.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2250-L2394 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-reader"></a>콘텐츠 판독기를 검색합니다.

를 활용 하려면 콘텐츠 항목 공급자를 구현 해야 합니다 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) 지원 하기 위해는 `Get-Content` cmdlet. 이 메서드는 지정된 된 경로에 있는 항목에 대 한 콘텐츠 판독기를 반환 합니다. 판독기 개체는 다음 콘텐츠를 읽기 위해 열 수 있습니다.

여기의 구현인 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) 이 공급자에 대 한이 메서드에 대 한 합니다.

```csharp
public IContentReader GetContentReader(string path)
{
    string tableName;
    int rowNumber;

    PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

    if (type == PathType.Invalid)
    {
        ThrowTerminatingInvalidPathException(path);
    }
    else if (type == PathType.Row)
    {
        throw new InvalidOperationException("contents can be obtained only for tables");
    }

    return new AccessDBContentReader(path, this);
} // GetContentReader
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1829-L1846 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentreader"></a>GetContentReader를 구현 하는 방법에 대 한 고려해 야 할 사항

다음과의 구현에 적용 될 수 있습니다 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader):

- 공급자 클래스를 정의 하는 경우 Windows PowerShell 콘텐츠 공급자에서 ExpandWildcards, 필터, 포함 또는 제외의 공급자 기능을 선언할 수 있습니다는 [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)열거형입니다. 이러한 경우의 구현에는 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) 메서드는 메서드에 전달 된 경로 지정 된 요구 사항을 충족 하는지 확인 해야 합니다 기능입니다. 이 작업을 수행 하는 메서드 액세스 해야 적절 한 속성을 예를 들어, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 고 [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) 속성입니다.

- 기본적으로이 메서드는 재정의 하지 않는 한 사용자 로부터 숨겨진 개체에 대 한 판독기를 검색 하지 않아야 합니다 [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 속성이 `true`합니다. 경로 사용자 로부터 숨겨진 항목을 나타내는 경우 오류를 작성 해야 하 고 [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 로 설정 된 `false`합니다.

## <a name="attaching-dynamic-parameters-to-the-get-content-cmdlet"></a>Get-content Cmdlet에 연결 하는 동적 매개 변수

`Get-Content` cmdlet 런타임에 동적으로 지정 된 추가 매개 변수가 필요 합니다. 이러한 동적 매개 변수를 제공 하려면 Windows PowerShell 콘텐츠 공급자를 구현 해야 합니다 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) 메서드. 이 메서드는 지정 된 경로에 있는 항목에 대 한 동적 매개 변수를 검색 하 고 속성 및 cmdlet 클래스와 유사한 특성을 구문 분석 된 필드에 있는 개체를 반환 또는 [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체입니다. Windows PowerShell 런타임이 cmdlet에 매개 변수를 추가할 반환된 된 개체를 사용 합니다.

이 Windows PowerShell 컨테이너 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는이 메서드의 기본 구현입니다.

```csharp
public object GetContentReaderDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1853-L1856 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-writer"></a>콘텐츠 작성기를 검색합니다.

항목에 콘텐츠를 작성 하려면 공급자를 구현 해야 합니다 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) 지원 하기 위해는 `Set-Content` 및 `Add-Content` cmdlet. 이 메서드는 지정된 된 경로에 있는 항목에 대 한 콘텐츠 작성기를 반환 합니다.

여기의 구현인 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) 이 메서드에 대 한 합니다.

```csharp
public IContentWriter GetContentWriter(string path)
{
    string tableName;
    int rowNumber;

    PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

    if (type == PathType.Invalid)
    {
        ThrowTerminatingInvalidPathException(path);
    }
    else if (type == PathType.Row)
    {
        throw new InvalidOperationException("contents can be added only to tables");
    }

    return new AccessDBContentWriter(path, this);
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1863-L1880 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentwriter"></a>GetContentWriter를 구현 하는 방법에 대 한 고려해 야 할 사항

다음과의 구현에 적용 될 수 있습니다 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter):

- 공급자 클래스를 정의 하는 경우 Windows PowerShell 콘텐츠 공급자에서 ExpandWildcards, 필터, 포함 또는 제외의 공급자 기능을 선언할 수 있습니다는 [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)열거형입니다. 이러한 경우의 구현에는 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) 메서드는 메서드에 전달 된 경로 지정 된 요구 사항을 충족 하는지 확인 해야 합니다 기능입니다. 이 작업을 수행 하는 메서드 액세스 해야 적절 한 속성을 예를 들어, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 고 [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) 속성입니다.

- 기본적으로이 메서드는 재정의 하지 않는 한 사용자 로부터 숨겨진 개체에 대 한 작성기를 검색 하지 않아야 합니다 [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 속성이 `true`합니다. 경로 사용자 로부터 숨겨진 항목을 나타내는 경우 오류를 작성 해야 하 고 [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 로 설정 된 `false`합니다.

## <a name="attaching-dynamic-parameters-to-the-add-content-and-set-content-cmdlets"></a>동적 매개 변수를 Add-content 및 Set-content Cmdlet에 연결

합니다 `Add-Content` 및 `Set-Content` cmdlet 런타임에 추가 되는 추가 동적 매개 변수가 필요 합니다. 이러한 동적 매개 변수를 제공 하려면 Windows PowerShell 콘텐츠 공급자를 구현 해야 합니다 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) 이러한 처리 하는 방법 매개 변수입니다. 이 메서드는 지정 된 경로에 있는 항목에 대 한 동적 매개 변수를 검색 하 고 속성 및 cmdlet 클래스와 유사한 특성을 구문 분석 된 필드에 있는 개체를 반환 또는 [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체입니다. Windows PowerShell 런타임에 반환 되는 개체를 사용 하 여 cmdlet에 대 한 매개 변수를 추가 합니다.

이 Windows PowerShell 컨테이너 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는이 메서드의 기본 구현입니다.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1887-L1890 "AccessDBProviderSample06.cs")]

## <a name="clearing-content"></a>콘텐츠 지우기

콘텐츠 공급자가 구현 하는 [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 지 원하는 메서드를 `Clear-Content` cmdlet. 이 메서드는 지정된 된 경로에 있는 항목의 콘텐츠를 제거 하지만 항목을 그대로 둡니다.

여기의 구현은 합니다 [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 이 공급자에 대 한 메서드.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1775-L1812 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-clearcontent"></a>ClearContent를 구현 하는 방법에 대 한 고려해 야 할 사항

다음과의 구현에 적용 될 수 있습니다 [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent):

- 공급자 클래스를 정의 하는 경우 Windows PowerShell 콘텐츠 공급자에서 ExpandWildcards, 필터, 포함 또는 제외의 공급자 기능을 선언할 수 있습니다는 [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)열거형입니다. 이러한 경우의 구현에는 [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 메서드는 메서드에 전달 된 경로 지정 된 요구 사항을 충족 하는지 확인 해야 합니다 기능입니다. 이 작업을 수행 하는 메서드 액세스 해야 적절 한 속성을 예를 들어, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 고 [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) 속성입니다.

- 기본적으로이 메서드는 재정의 하지 않는 한 사용자 로부터 숨겨진 개체의 내용을 지우지 해야 합니다 [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 속성이 `true`합니다. 경로 사용자 로부터 숨겨진 항목을 나타내는 경우 오류를 작성 해야 하 고 [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 로 설정 된 `false`합니다.

- 구현 된 [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 메서드를 호출 해야 [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 데이터 저장소로 변경 하기 전에 해당 반환 값을 확인 합니다. 이 메서드는 콘텐츠 지우기와 같은 데이터 저장소에 변경 될 때 작업의 실행을 확인 하려면 사용 됩니다. 합니다 [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 메서드는 명령줄 설정이 나 기본 설정 처리 하는 Windows PowerShell 런타임에 사용자에 게 변경 될 리소스의 이름을 전송 합니다. 표시할 내용을 결정 하는 변수입니다.

  호출한 후 [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 반환 `true`는 [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 메서드를 호출 해야 합니다 [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 메서드. 이 메서드는 작업을 계속 진행 해야 하는 경우를 확인 하는 피드백을 허용 하도록 사용자에 게 메시지를 보냅니다. 에 대 한 호출 [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 잠재적으로 위험한 시스템 수정에 대 한 추가 검사를 허용 합니다.

## <a name="attaching-dynamic-parameters-to-the-clear-content-cmdlet"></a>Clear-content Cmdlet에 연결 하는 동적 매개 변수

`Clear-Content` cmdlet 런타임에 추가 되는 추가 동적 매개 변수가 필요 합니다. 이러한 동적 매개 변수를 제공 하려면 Windows PowerShell 콘텐츠 공급자를 구현 해야 합니다 [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) 이러한 처리 하는 방법 매개 변수입니다. 이 메서드는 지정 된 경로에 있는 항목에 대 한 매개 변수를 검색합니다. 이 메서드는 지정 된 경로에 있는 항목에 대 한 동적 매개 변수를 검색 하 고 속성 및 cmdlet 클래스와 유사한 특성을 구문 분석 된 필드에 있는 개체를 반환 또는 [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체입니다. Windows PowerShell 런타임이 cmdlet에 매개 변수를 추가할 반환된 된 개체를 사용 합니다.

이 Windows PowerShell 컨테이너 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는이 메서드의 기본 구현입니다.

```csharp
public object ClearContentDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1819-L1822 "AccessDBProviderSample06.cs")]

## <a name="code-sample"></a>코드 예제

전체 샘플 코드를 보려면 [AccessDbProviderSample06 코드 샘플](./accessdbprovidersample06-code-sample.md)합니다.

## <a name="defining-object-types-and-formatting"></a>개체 유형 정의 및 서식 지정

공급자를 작성할 때 기존 개체에 멤버를 추가 하거나 새 개체를 정의 해야 할 수도 있습니다. 이 완료 되 면 Windows PowerShell 개체의 멤버를 식별 하는 데 사용할 수 있는 형식 파일 및 개체 표시 되는 방식을 정의 하는 서식 파일을 만들어야 합니다. 자세한 내용은 [확장 개체 형식 및 서식](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)합니다.

## <a name="building-the-windows-powershell-provider"></a>Windows PowerShell 공급자 작성

참조 [Cmdlet, 공급자, 등록 및 응용 프로그램을 호스트 하는 방법을](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)합니다.

## <a name="testing-the-windows-powershell-provider"></a>Windows PowerShell 공급자 테스트

Windows PowerShell을 사용 하 여 Windows PowerShell 공급자가 등록 하는 경우 명령줄에서 지원 되는 cmdlet을 실행 하 여 테스트할 수 있습니다. 예를 들어 샘플 콘텐츠 공급자를 테스트 합니다.

사용 합니다 `Get-Content` cmdlet은 지정한 경로에 데이터베이스 테이블에서 지정 된 항목의 콘텐츠를 검색 하는 `Path` 매개 변수입니다. `ReadCount` 매개 변수 (기본값 1)를 읽는 데 사용할 콘텐츠 정의 판독기에 대 한 항목 수를 지정 합니다. 다음 명령은 항목을 사용 하 여 cmdlet 테이블에서 두 행 (항목)을 검색 하 고 해당 내용이 표시 됩니다. 다음 예제 출력에서는 가상의 Access 데이터베이스는 참고 합니다.

```powershell
Get-Content -Path mydb:\Customers -ReadCount 2
```

```output
ID        : 1
FirstName : Eric
LastName  : Gruber
Email     : ericgruber@fabrikam.com
Title     : President
Company   : Fabrikam
WorkPhone : (425) 555-0100
Address   : 4567 Main Street
City      : Buffalo
State     : NY
Zip       : 98052
Country   : USA
ID        : 2
FirstName : Eva
LastName  : Corets
Email     : evacorets@cohowinery.com
Title     : Sales Representative
Company   : Coho Winery
WorkPhone : (360) 555-0100
Address   : 8910 Main Street
City      : Cabmerlot
State     : WA
Zip       : 98089
Country   : USA
```

## <a name="see-also"></a>참고 항목

[Windows PowerShell 공급자 만들기](./how-to-create-a-windows-powershell-provider.md)

[디자인 Your Windows PowerShell 공급자](./designing-your-windows-powershell-provider.md)

[확장 개체 형식 및 서식 지정](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Windows PowerShell 탐색 공급자 구현](./creating-a-windows-powershell-navigation-provider.md)

[Cmdlet, 공급자, 등록 및 응용 프로그램을 호스트 하는 방법](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell 프로그래머 가이드](./windows-powershell-programmer-s-guide.md)
