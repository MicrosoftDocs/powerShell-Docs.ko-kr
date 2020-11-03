---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-webserviceproxy?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WebServiceProxy
ms.openlocfilehash: aea656bc8ad4416673a7abb7d32a58d45dd3cc4f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214601"
---
# <span data-ttu-id="d9031-103">New-WebServiceProxy</span><span class="sxs-lookup"><span data-stu-id="d9031-103">New-WebServiceProxy</span></span>

## <span data-ttu-id="d9031-104">개요</span><span class="sxs-lookup"><span data-stu-id="d9031-104">SYNOPSIS</span></span>
<span data-ttu-id="d9031-105">PowerShell에서 웹 서비스를 사용 하 고 관리할 수 있는 웹 서비스 프록시 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-105">Creates a Web service proxy object that lets you use and manage the Web service in PowerShell.</span></span>

## <span data-ttu-id="d9031-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d9031-106">SYNTAX</span></span>

### <span data-ttu-id="d9031-107">NoCredentials (기본값)</span><span class="sxs-lookup"><span data-stu-id="d9031-107">NoCredentials (Default)</span></span>

```
New-WebServiceProxy [-Uri] <Uri> [[-Class] <String>] [[-Namespace] <String>] [<CommonParameters>]
```

### <span data-ttu-id="d9031-108">자격 증명</span><span class="sxs-lookup"><span data-stu-id="d9031-108">Credential</span></span>

```
New-WebServiceProxy [-Uri] <Uri> [[-Class] <String>] [[-Namespace] <String>] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="d9031-109">UseDefaultCredential</span><span class="sxs-lookup"><span data-stu-id="d9031-109">UseDefaultCredential</span></span>

```
New-WebServiceProxy [-Uri] <Uri> [[-Class] <String>] [[-Namespace] <String>] [-UseDefaultCredential]
 [<CommonParameters>]
```

## <span data-ttu-id="d9031-110">설명</span><span class="sxs-lookup"><span data-stu-id="d9031-110">DESCRIPTION</span></span>

<span data-ttu-id="d9031-111">`New-WebServiceProxy`Cmdlet을 사용 하면 PowerShell에서 웹 서비스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-111">The `New-WebServiceProxy` cmdlet lets you use a Web service in PowerShell.</span></span> <span data-ttu-id="d9031-112">Cmdlet은 웹 서비스에 연결 하 고 PowerShell에서 웹 서비스 프록시 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-112">The cmdlet connects to a Web service and creates a Web service proxy object in PowerShell.</span></span> <span data-ttu-id="d9031-113">프록시 개체를 사용하여 웹 서비스를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-113">You can use the proxy object to manage the Web service.</span></span>

<span data-ttu-id="d9031-114">웹 서비스는 네트워크, 특히 인터넷을 통해 데이터를 교환 하는 XML 기반 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-114">A Web service is an XML-based program that exchanges data over a network, especially over the Internet.</span></span> <span data-ttu-id="d9031-115">Microsoft .NET Framework는 웹 서비스를 .NET Framework 개체로 나타내는 웹 서비스 프록시 개체를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-115">The Microsoft .NET Framework provides Web service proxy objects that represent the Web service as a .NET Framework object.</span></span>

## <span data-ttu-id="d9031-116">예제</span><span class="sxs-lookup"><span data-stu-id="d9031-116">EXAMPLES</span></span>

### <span data-ttu-id="d9031-117">예제 1: 웹 서비스에 대 한 프록시 만들기</span><span class="sxs-lookup"><span data-stu-id="d9031-117">Example 1: Create a proxy for a Web service</span></span>

<span data-ttu-id="d9031-118">이 예제에서는 Windows PowerShell에서 계산기 웹 서비스의 .NET Framework 프록시를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-118">This example creates a .NET Framework proxy of the calculator Web service in Windows PowerShell.</span></span>

```powershell
$calc = New-WebServiceProxy -Uri "http://www.dneonline.com/calculator.asmx?wsdl"
```

### <span data-ttu-id="d9031-119">예제 2: 웹 서비스에 대 한 프록시를 만들고 네임 스페이스 및 클래스 지정</span><span class="sxs-lookup"><span data-stu-id="d9031-119">Example 2: Create a proxy for a Web service and specify namespace and class</span></span>

<span data-ttu-id="d9031-120">이 예제에서는 cmdlet을 사용 하 여 `New-WebServiceProxy` 계산기 웹 서비스의 .NET Framework 프록시를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-120">This example uses the `New-WebServiceProxy` cmdlet to create a .NET Framework proxy of the calculator Web service.</span></span>

```powershell
$URI = "http://www.dneonline.com/calculator.asmx?wsdl"
$calc = New-WebServiceProxy -Uri $URI -Namespace "WSProxy" -Class "Calculator"
```

<span data-ttu-id="d9031-121">이 명령은 **uri** 매개 변수를 사용 하 여 uri를 지정 하 고, **네임 스페이스** 및 **클래스** 매개 변수를 사용 하 여 개체의 네임 스페이스 및 클래스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-121">The command uses the **Uri** parameter to specify the URI and the **Namespace** and **Class** parameters to specify the namespace and class of the object.</span></span>

### <span data-ttu-id="d9031-122">예제 3: 웹 서비스 프록시의 표시 메서드</span><span class="sxs-lookup"><span data-stu-id="d9031-122">Example 3: Display methods of a Web service proxy</span></span>

```powershell
$calc | Get-Member -MemberType method
```

```Output
   TypeName: WSProxy.Calculator

Name                      MemberType Definition
----                      ---------- ----------
Abort                     Method     void Abort()
Add                       Method     int Add(int intA, int intB)
AddAsync                  Method     void AddAsync(int intA, int intB), void AddAsync(int intA,
BeginAdd                  Method     System.IAsyncResult BeginAdd(int intA, int intB, System.Asy
BeginDivide               Method     System.IAsyncResult BeginDivide(int intA, int intB, System.
BeginMultiply             Method     System.IAsyncResult BeginMultiply(int intA, int intB, Syste
BeginSubtract             Method     System.IAsyncResult BeginSubtract(int intA, int intB, Syste
CancelAsync               Method     void CancelAsync(System.Object userState)
CreateObjRef              Method     System.Runtime.Remoting.ObjRef CreateObjRef(type requestedT
Discover                  Method     void Discover()
Dispose                   Method     void Dispose(), void IDisposable.Dispose()
Divide                    Method     int Divide(int intA, int intB)
DivideAsync               Method     void DivideAsync(int intA, int intB), void DivideAsync(int
EndAdd                    Method     int EndAdd(System.IAsyncResult asyncResult)
EndDivide                 Method     int EndDivide(System.IAsyncResult asyncResult)
EndMultiply               Method     int EndMultiply(System.IAsyncResult asyncResult)
EndSubtract               Method     int EndSubtract(System.IAsyncResult asyncResult)
Equals                    Method     bool Equals(System.Object obj)
GetHashCode               Method     int GetHashCode()
GetLifetimeService        Method     System.Object GetLifetimeService()
GetType                   Method     type GetType()
InitializeLifetimeService Method     System.Object InitializeLifetimeService()
Multiply                  Method     int Multiply(int intA, int intB)
MultiplyAsync             Method     void MultiplyAsync(int intA, int intB), void MultiplyAsync(
Subtract                  Method     int Subtract(int intA, int intB)
SubtractAsync             Method     void SubtractAsync(int intA, int intB), void SubtractAsync(
ToString                  Method     string ToString()
```

<span data-ttu-id="d9031-123">이 예제에서는 cmdlet을 사용 하 여 `Get-Member` 웹 서비스 프록시 개체의 메서드를 변수에 표시 `$calc` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-123">This example uses the `Get-Member` cmdlet to display the methods of the Web service proxy object in the `$calc` variable.</span></span> <span data-ttu-id="d9031-124">다음 예제에서 이러한 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-124">We uses these methods in the following example.</span></span>

<span data-ttu-id="d9031-125">프록시 개체 WebServiceProxy의 **TypeName** 은 이전 예제에서 지정 된 네임 스페이스 및 클래스 이름을 반영 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-125">Notice that the **TypeName** of the proxy object, WebServiceProxy, reflects the namespace and class names that were specified in the previous example.</span></span>

### <span data-ttu-id="d9031-126">예제 4: 웹 서비스 프록시 사용</span><span class="sxs-lookup"><span data-stu-id="d9031-126">Example 4: Use a Web service proxy</span></span>

```powershell
PS> $calc.Multiply(6,7)
42
```

<span data-ttu-id="d9031-127">이 예에서는 변수에 저장 된 웹 서비스 프록시를 사용 `$calc` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-127">This example uses the Web service proxy stored in the `$calc` variable.</span></span> <span data-ttu-id="d9031-128">이 명령은 프록시의 **곱하기** 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-128">The command uses the **Multiply** method of the proxy.</span></span>

## <span data-ttu-id="d9031-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d9031-129">PARAMETERS</span></span>

### <span data-ttu-id="d9031-130">-클래스</span><span class="sxs-lookup"><span data-stu-id="d9031-130">-Class</span></span>

<span data-ttu-id="d9031-131">cmdlet이 웹 서비스에 대해 만드는 프록시 클래스의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-131">Specifies a name for the proxy class that the cmdlet creates for the Web service.</span></span> <span data-ttu-id="d9031-132">이 매개 변수 값은 **네임 스페이스** 매개 변수와 함께 사용 되어 클래스의 정규화 된 이름을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-132">The value of this parameter is used together with the **Namespace** parameter to provide a fully qualified name for the class.</span></span> <span data-ttu-id="d9031-133">기본값은 URI (Uniform Resource Identifier)에서 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-133">The default value is generated from the Uniform Resource Identifier (URI).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: FileName, FN

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d9031-134">-Credential</span><span class="sxs-lookup"><span data-stu-id="d9031-134">-Credential</span></span>

<span data-ttu-id="d9031-135">이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-135">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="d9031-136">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-136">The default is the current user.</span></span> <span data-ttu-id="d9031-137">**UseDefaultCredential** 매개 변수 대신 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-137">This is an alternative to using the **UseDefaultCredential** parameter.</span></span>

<span data-ttu-id="d9031-138">User01 또는 Domain01\User01과 같은 사용자 이름을 입력 하거나, cmdlet에 의해 생성 된 것과 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="d9031-138">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="d9031-139">사용자 이름을 입력 하는 경우이 cmdlet은 암호를 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-139">If you type a user name, this cmdlet prompts you for a password.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Credential
Aliases: Cred

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d9031-140">-Namespace</span><span class="sxs-lookup"><span data-stu-id="d9031-140">-Namespace</span></span>

<span data-ttu-id="d9031-141">새 클래스의 네임스페이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-141">Specifies a namespace for the new class.</span></span>

<span data-ttu-id="d9031-142">이 매개 변수 값은 클래스 매개 변수의 값과 함께 사용 되어 **클래스의** 정규화 된 이름을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-142">The value of this parameter is used together with the value of the **Class** parameter to generate a fully qualified name for the class.</span></span> <span data-ttu-id="d9031-143">기본값은 **Microsoft. PowerShell. NewWebserviceProxy입니다. AutogeneratedTypes** 와 URI에서 생성 되는 형식을 더한 값입니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-143">The default value is **Microsoft.PowerShell.Commands.NewWebserviceProxy.AutogeneratedTypes** plus a type that is generated from the URI.</span></span>

<span data-ttu-id="d9031-144">동일한 이름을 가진 여러 웹 서비스에 액세스할 수 있도록 **Namespace** 매개 변수의 값을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-144">You can set the value of the **Namespace** parameter so that you can access multiple Web services that have the same name.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: NS

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d9031-145">-Uri</span><span class="sxs-lookup"><span data-stu-id="d9031-145">-Uri</span></span>

<span data-ttu-id="d9031-146">웹 서비스의 URI를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-146">Specifies the URI of the Web service.</span></span> <span data-ttu-id="d9031-147">서비스 설명이 포함 된 파일의 경로 및 파일 이름 또는 URI를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-147">Enter a URI or the path and filename of a file that contains a service description.</span></span>

<span data-ttu-id="d9031-148">URI는 `.asmx` 서비스 설명을 반환 하는 페이지 또는 페이지를 반환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-148">The URI must return an `.asmx` page or to a page that returns a service description.</span></span> <span data-ttu-id="d9031-149">ASP.NET를 사용 하 여 만든 웹 서비스에 대 한 서비스 설명을 반환 하려면 "?를 추가 합니다. WSDL "에서 웹 서비스의 URL (예:)을 사용할 수 `http://www.contoso.com/MyWebService.asmx?WSDL` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-149">To return a service description of a Web service that was created using ASP.NET, append "?WSDL" to the URL of the Web service (for example, `http://www.contoso.com/MyWebService.asmx?WSDL`).</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: WL, WSDL, Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d9031-150">-UseDefaultCredential</span><span class="sxs-lookup"><span data-stu-id="d9031-150">-UseDefaultCredential</span></span>

<span data-ttu-id="d9031-151">이 cmdlet이 기본 자격 증명을 사용 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-151">Indicates that this cmdlet uses the default credential.</span></span> <span data-ttu-id="d9031-152">이 cmdlet은 결과 프록시 개체의 **UseDefaultCredential** 속성을 True로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-152">This cmdlet sets the **UseDefaultCredential** property in the resulting proxy object to True.</span></span> <span data-ttu-id="d9031-153">**Credential** 매개 변수를 사용 하는 대신 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-153">This is an alternative to using the **Credential** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseDefaultCredential
Aliases: UDC

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d9031-154">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d9031-154">CommonParameters</span></span>

<span data-ttu-id="d9031-155">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d9031-155">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d9031-156">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d9031-156">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d9031-157">입력</span><span class="sxs-lookup"><span data-stu-id="d9031-157">INPUTS</span></span>

### <span data-ttu-id="d9031-158">없음</span><span class="sxs-lookup"><span data-stu-id="d9031-158">None</span></span>

<span data-ttu-id="d9031-159">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-159">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="d9031-160">출력</span><span class="sxs-lookup"><span data-stu-id="d9031-160">OUTPUTS</span></span>

### <span data-ttu-id="d9031-161">웹 서비스 프록시 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-161">A Web service proxy object</span></span>

<span data-ttu-id="d9031-162">이 cmdlet은 웹 서비스 프록시 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-162">This cmdlet returns a Web service proxy object.</span></span> <span data-ttu-id="d9031-163">개체의 네임스페이스 및 클래스는 명령의 매개 변수에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-163">The namespace and class of the object are determined by the parameters of the command.</span></span> <span data-ttu-id="d9031-164">기본값은 입력 URI에서 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-164">The default is generated from the input URI.</span></span>

## <span data-ttu-id="d9031-165">참고</span><span class="sxs-lookup"><span data-stu-id="d9031-165">NOTES</span></span>

<span data-ttu-id="d9031-166">`New-WebServiceProxy`**시스템 .net. WebClient** 클래스를 사용 하 여 지정 된 웹 서비스를 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9031-166">`New-WebServiceProxy` uses the **System.Net.WebClient** class to load the specified Web service.</span></span>

## <span data-ttu-id="d9031-167">관련 링크</span><span class="sxs-lookup"><span data-stu-id="d9031-167">RELATED LINKS</span></span>

[<span data-ttu-id="d9031-168">New-Service</span><span class="sxs-lookup"><span data-stu-id="d9031-168">New-Service</span></span>](New-Service.md)
