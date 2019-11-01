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
ms.openlocfilehash: 2e864da581915c1e42518914476dcc8e8eb08395
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360512"
---
# <a name="creating-a-windows-powershell-content-provider"></a>Windows PowerShell 콘텐츠 공급자 만들기

이 항목에서는 사용자가 데이터 저장소에 있는 항목의 내용을 조작할 수 있도록 하는 Windows PowerShell 공급자를 만드는 방법에 대해 설명 합니다. 결과적으로 항목의 내용을 조작할 수 있는 공급자를 Windows PowerShell 콘텐츠 공급자 라고 합니다.

> [!NOTE]
> Windows Vista 및 .NET Framework C# 3.0 런타임 구성 요소에 대 한 Microsoft Windows 소프트웨어 개발 키트를 사용 하 여이 공급자에 대 한 원본 파일 (AccessDBSampleProvider06.cs)을 다운로드할 수 있습니다. 다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/developer/installing-the-windows-powershell-sdk)을 참조 하세요.
>
> 다운로드 된 원본 파일은 **\<PowerShell Samples >** 디렉터리에서 사용할 수 있습니다.
>
> 다른 Windows PowerShell 공급자 구현에 대 한 자세한 내용은 [Windows Powershell 공급자 디자인](./designing-your-windows-powershell-provider.md)을 참조 하세요.

## <a name="define-the-windows-powershell-content-provider-class"></a>Windows PowerShell 콘텐츠 공급자 클래스 정의

Windows PowerShell 콘텐츠 공급자는 [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 인터페이스를 지 원하는 .net 클래스를 만들어야 합니다. 이 섹션에서 설명 하는 항목 공급자에 대 한 클래스 정의는 다음과 같습니다.

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L32-L33 "AccessDBProviderSample06.cs")]

이 클래스 정의에서 [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) 특성에는 두 개의 매개 변수가 포함 되어 있습니다. 첫 번째 매개 변수는 Windows PowerShell에서 사용 되는 공급자에 대 한 친숙 한 이름을 지정 합니다. 두 번째 매개 변수는 명령을 처리 하는 동안 공급자가 Windows PowerShell 런타임에 노출 하는 Windows PowerShell 특정 기능을 지정 합니다. 이 공급자의 경우 추가 된 Windows PowerShell 관련 기능이 없습니다.

## <a name="define-functionality-of-base-class"></a>기본 클래스의 기능 정의

[Windows PowerShell 공급자 디자인](./designing-your-windows-powershell-provider.md)에 설명 된 대로, 다른 공급자 기능을 제공 하는 다른 여러 클래스에서 [파생 된 다른](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 클래스에서 파생 됩니다. 따라서 Windows PowerShell 콘텐츠 공급자는 일반적으로 해당 클래스에서 제공 하는 모든 기능을 정의 합니다.

세션 관련 초기화 정보를 추가 하 고 공급자가 사용 하는 리소스를 해제 하기 위한 기능을 구현 하는 방법에 대 한 자세한 내용은 [기본 Windows PowerShell 공급자 만들기](./creating-a-basic-windows-powershell-provider.md)를 참조 하세요. 그러나 여기에 설명 된 공급자를 비롯 한 대부분의 공급자는 Windows PowerShell에서 제공 하는이 기능의 기본 구현을 사용할 수 있습니다.

데이터 저장소에 액세스 하려면 공급자는 [system.object](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 의 메서드를 구현 해야 합니다 (예를 들어). 이러한 메서드를 구현 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 드라이브 공급자 만들기](./creating-a-windows-powershell-drive-provider.md)를 참조 하세요.

항목 가져오기, 설정 및 지우기와 같은 데이터 저장소의 항목을 조작 하려면 공급자는 [system.object](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 에서 제공 하는 메서드를 구현 해야 합니다. 이러한 메서드를 구현 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 항목 공급자 만들기](./creating-a-windows-powershell-item-provider.md)를 참조 하세요.

다중 계층 데이터 저장소에서 작업 하려면 공급자가 [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 기본 클래스에서 제공 하는 메서드를 구현 해야 합니다. 이러한 메서드를 구현 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 컨테이너 공급자 만들기](./creating-a-windows-powershell-container-provider.md)를 참조 하세요.

재귀 명령, 중첩 된 컨테이너 및 상대 경로를 지원 하려면 공급자가 [system.object](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 를 구현 해야 합니다. 또한이 Windows PowerShell 콘텐츠 공급자는 [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 인터페이스를 [system.object](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 에 연결할 수 있으며,이에 대 한 기본 클래스는 다음과 같이 제공 됩니다. 따라서는 해당 클래스에서 제공 하는 메서드를 구현 해야 합니다. 자세한 내용은 이러한 메서드 구현을 참조 하세요. [탐색 Windows PowerShell 공급자 구현](./creating-a-windows-powershell-navigation-provider.md)을 참조 하세요.

## <a name="implementing-a-content-reader"></a>콘텐츠 판독기 구현

항목에서 콘텐츠를 읽으려면 공급자가 [Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader)에서 파생 되는 콘텐츠 판독기 클래스를 구현 해야 합니다. 이 공급자에 대 한 콘텐츠 판독기를 사용 하면 데이터 테이블의 행 내용에 액세스할 수 있습니다. 콘텐츠 판독기 클래스는 표시 된 행에서 데이터를 검색 하 고 해당 데이터를 나타내는 목록, 콘텐츠 판독기를 이동 하는 **Seek** 메서드, 콘텐츠 판독기를 닫는 **Close** 메서드 및를 **반환 하는 읽기 메서드를 정의 합니다. Dispose** 메서드입니다.

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2115-L2241 "AccessDBProviderSample06.cs")]

## <a name="implementing-a-content-writer"></a>콘텐츠 작성기 구현

항목에 콘텐츠를 쓰려면 공급자가 [Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter)에서 파생 된 콘텐츠 작성기 클래스를 구현 해야 합니다. 콘텐츠 작성기 클래스는 지정 된 행 내용을 쓰는 **Write** 메서드, 콘텐츠 작성기를 이동 하는 **Seek** 메서드, 콘텐츠 작성기를 닫는 **Close** 메서드 및 **Dispose** 메서드를 정의 합니다.

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2250-L2394 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-reader"></a>콘텐츠 판독기를 검색 하는 중

항목에서 콘텐츠를 가져오기 위해 공급자는 `Get-Content` cmdlet을 지원 하기 위해 [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) 을 구현 해야 합니다. 이 메서드는 지정 된 경로에 있는 항목에 대 한 콘텐츠 판독기를 반환 합니다. 그러면 판독기 개체를 열어 콘텐츠를 읽을 수 있습니다.

다음은이 공급자에 대 한이 메서드에 대 한 [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) 의 구현입니다.

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

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1829-L1846 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentreader"></a>GetContentReader 구현에 대해 기억할 사항

다음 조건은 Icontentcmdletprovider의 구현에 적용 될 수 있습니다. [*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)입니다.

- 공급자 클래스를 정의 하는 경우 Windows PowerShell 콘텐츠 공급자가 ExpandWildcards, Filter, Include 또는 Exclude의 공급자 기능을 [system.object](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거형에서 선언할 수 있습니다. 이러한 경우 [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) 를 구현 하면 메서드에 전달 된 경로가 지정 된 기능의 요구 사항을 충족 하는지 확인 해야 합니다 (예를 들어). 이 작업을 수행 하려면 메서드가 적절 한 속성 (예: System.object)에 액세스 해야 합니다. [*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 및 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .... n a m.

- 기본적으로이 메서드의 재정의는 사용자에 게 표시 되는 개체에 대 한 판독기를 검색 해서는 안 됩니다 .이 경우에는 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 를 `true`으로 설정 해야 합니다. 경로가 사용자 및 시스템에서 숨겨진 항목을 나타내는 경우에는 오류를 작성 해야 합니다 [. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 는 `false`로 설정 됩니다.

## <a name="attaching-dynamic-parameters-to-the-get-content-cmdlet"></a>Get Content Cmdlet에 동적 매개 변수 연결

@No__t_0 cmdlet에는 런타임에 동적으로 지정 되는 추가 매개 변수가 필요할 수 있습니다. 이러한 동적 매개 변수를 제공 하려면 Windows PowerShell 콘텐츠 공급자가 Icontentcmdletprovider. [Getcontentreaderdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) 메서드를 구현 해야 합니다. 이 메서드는 지정 된 경로에서 항목에 대 한 동적 매개 변수를 검색 하 고 cmdlet 클래스 또는 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 유사한 구문 분석 특성이 있는 속성 및 필드가 있는 개체를 반환 합니다. 개체가. Windows PowerShell 런타임은 반환 된 개체를 사용 하 여 cmdlet에 매개 변수를 추가 합니다.

이 Windows PowerShell 컨테이너 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는이 메서드의 기본 구현입니다.

```csharp
public object GetContentReaderDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1853-L1856 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-writer"></a>콘텐츠 기록기를 검색 하는 중

항목에 콘텐츠를 쓰려면 공급자가 `Set-Content` 및 `Add-Content` cmdlet을 지원 하기 위해 [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) 을 구현 해야 합니다 (). 이 메서드는 지정 된 경로에 있는 항목에 대 한 콘텐츠 작성기를 반환 합니다.

다음은이 메서드에 대 한 [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) 의 구현입니다 (예를 들어,

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

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1863-L1880 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentwriter"></a>GetContentWriter 구현에 대해 기억할 사항

다음 조건은 Icontentcmdletprovider의 구현에 적용 될 수 있습니다. [Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter):

- 공급자 클래스를 정의 하는 경우 Windows PowerShell 콘텐츠 공급자가 ExpandWildcards, Filter, Include 또는 Exclude의 공급자 기능을 [system.object](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거형에서 선언할 수 있습니다. 이러한 경우 [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) 메서드를 구현 하 여 메서드에 전달 된 경로가 지정 된 기능의 요구 사항을 충족 하는지 확인 해야 합니다 (예). 이 작업을 수행 하려면 메서드가 적절 한 속성 (예: System.object)에 액세스 해야 합니다. [*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 및 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .... n a m.

- 기본적으로이 메서드의 재정의는 사용자에 게 표시 되는 개체에 대 한 기록기를 검색 해서는 안 됩니다 .이 경우에는 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 를 `true`으로 설정 해야 합니다. 경로가 사용자 및 시스템에서 숨겨진 항목을 나타내는 경우에는 오류를 작성 해야 합니다 [. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 는 `false`로 설정 됩니다.

## <a name="attaching-dynamic-parameters-to-the-add-content-and-set-content-cmdlets"></a>동적 매개 변수를 추가 내용 및 집합 내용 Cmdlet에 연결

@No__t_0 및 `Set-Content` cmdlet에는 런타임에 추가 된 추가 동적 매개 변수가 필요할 수 있습니다. 이러한 동적 매개 변수를 제공 하려면 Windows PowerShell 콘텐츠 공급자가 이러한 매개 변수를 처리 하는 [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) 을 구현 해야 합니다. 이 메서드는 지정 된 경로에서 항목에 대 한 동적 매개 변수를 검색 하 고 cmdlet 클래스 또는 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 유사한 구문 분석 특성이 있는 속성 및 필드가 있는 개체를 반환 합니다. 개체가. Windows PowerShell 런타임은 반환 된 개체를 사용 하 여 cmdlet에 매개 변수를 추가 합니다.

이 Windows PowerShell 컨테이너 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는이 메서드의 기본 구현입니다.

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1887-L1890 "AccessDBProviderSample06.cs")]

## <a name="clearing-content"></a>콘텐츠 지우기

콘텐츠 공급자는 `Clear-Content` cmdlet을 지 원하는 [Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 메서드를 구현 합니다. 이 메서드는 지정 된 경로에 있는 항목의 내용을 제거 하지만 항목은 그대로 유지 합니다.

이 공급자에 대 한 [Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 메서드의 구현은 다음과 같습니다.

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1775-L1812 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-clearcontent"></a>ClearContent 구현에 대해 기억할 사항

다음 조건은 Icontentcmdletprovider의 구현에 적용 될 수 있습니다. [Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent):

- 공급자 클래스를 정의 하는 경우 Windows PowerShell 콘텐츠 공급자가 ExpandWildcards, Filter, Include 또는 Exclude의 공급자 기능을 [system.object](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거형에서 선언할 수 있습니다. 이러한 경우 [Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 메서드를 구현 하면 메서드에 전달 된 경로가 지정 된 기능의 요구 사항을 충족 하는지 확인 해야 합니다. 이 작업을 수행 하려면 메서드가 적절 한 속성 (예: System.object)에 액세스 해야 합니다. [*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 및 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .... n a m.

- 기본적으로이 메서드를 재정의 하면 사용자에 게 표시 되는 개체의 콘텐츠를 지워야 합니다 .이 경우에는 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 를 `true`으로 설정 해야 합니다. 경로가 사용자 및 시스템에서 숨겨진 항목을 나타내는 경우에는 오류를 작성 해야 합니다 [. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 는 `false`로 설정 됩니다.

- [Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 메서드를 구현 하면 해당 반환 값을 확인 [하 고 해당](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 반환 값이 있는지 확인 해야 합니다. 데이터 저장소를 변경 하기 전에 이 메서드는 콘텐츠 지우기와 같은 데이터 저장소가 변경 될 때 작업 실행을 확인 하는 데 사용 됩니다. Windows PowerShell 런타임에서 명령줄 설정이 나 기본 설정 변수를 처리 하 여 사용자에 게 변경할 리소스의 이름을 보냅니다 [...](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) n a m. 표시할 항목을 결정 합니다.

  [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)에 대한 호출이 `true`이면 [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 메서드는 잠재적으로 위험한 시스템 수정에 대한 추가 확인으로 [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 메서드를 호출해야 합니다. 이 메서드는 사용자에 게 작업을 계속 해야 하는지 여부를 확인 하기 위해 사용자에 게 메시지를 보냅니다. System.object를 호출 하면 잠재적으로 위험한 시스템 수정에 대 한 추가 검사를 수행할 수 있습니다 [.](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)

## <a name="attaching-dynamic-parameters-to-the-clear-content-cmdlet"></a>동적 매개 변수를 Clear Content Cmdlet에 연결

@No__t_0 cmdlet에는 런타임에 추가 되는 추가 동적 매개 변수가 필요할 수 있습니다. 이러한 동적 매개 변수를 제공 하려면 Windows PowerShell 콘텐츠 공급자가 이러한 매개 변수를 처리 하는 [Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) 을 구현 해야 합니다. 이 메서드는 지정 된 경로에서 항목에 대 한 매개 변수를 검색 합니다. 이 메서드는 지정 된 경로에서 항목에 대 한 동적 매개 변수를 검색 하 고 cmdlet 클래스 또는 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 유사한 구문 분석 특성이 있는 속성 및 필드가 있는 개체를 반환 합니다. 개체가. Windows PowerShell 런타임은 반환 된 개체를 사용 하 여 cmdlet에 매개 변수를 추가 합니다.

이 Windows PowerShell 컨테이너 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는이 메서드의 기본 구현입니다.

```csharp
public object ClearContentDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1819-L1822 "AccessDBProviderSample06.cs")]

## <a name="code-sample"></a>코드 예제

전체 샘플 코드는 [AccessDbProviderSample06 코드 샘플](./accessdbprovidersample06-code-sample.md)을 참조 하세요.

## <a name="defining-object-types-and-formatting"></a>개체 형식 및 서식 정의

공급자를 작성할 때 기존 개체에 멤버를 추가 하거나 새 개체를 정의 해야 할 수 있습니다. 이 작업이 완료 되 면 Windows PowerShell에서 개체의 멤버와 개체 표시 방법을 정의 하는 서식 파일을 식별 하는 데 사용할 수 있는 형식 파일을 만들어야 합니다. 자세한 내용은 [개체 형식 확장 및 서식 지정](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)을 참조 하세요.

## <a name="building-the-windows-powershell-provider"></a>Windows PowerShell 공급자 빌드

[Cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법을](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)참조 하세요.

## <a name="testing-the-windows-powershell-provider"></a>Windows PowerShell 공급자 테스트

Windows powershell 공급자를 Windows PowerShell에 등록 한 경우 명령줄에서 지원 되는 cmdlet을 실행 하 여 테스트할 수 있습니다. 예를 들어 샘플 콘텐츠 공급자를 테스트 합니다.

@No__t_0 cmdlet을 사용 하 여 `Path` 매개 변수로 지정 된 경로에서 데이터베이스 테이블의 지정 된 항목 내용을 검색할 수 있습니다. @No__t_0 매개 변수는 정의 된 콘텐츠 판독기에서 읽을 항목 수를 지정 합니다 (기본값 1). 다음 명령 항목을 사용 하 여 cmdlet은 테이블에서 두 개의 행 (항목)을 검색 하 고 해당 내용을 표시 합니다. 다음 예제 출력에서는 가상의 Access 데이터베이스를 사용 합니다.

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

## <a name="see-also"></a>관련 항목

[Windows PowerShell 공급자 만들기](./how-to-create-a-windows-powershell-provider.md)

[Windows PowerShell 공급자 디자인](./designing-your-windows-powershell-provider.md)

[개체 형식 및 서식 확장](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[탐색 Windows PowerShell 공급자 구현](./creating-a-windows-powershell-navigation-provider.md)

[Cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell 프로그래머 가이드](./windows-powershell-programmer-s-guide.md)
