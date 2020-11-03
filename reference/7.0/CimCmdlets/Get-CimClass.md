---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimclass?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimClass
ms.openlocfilehash: 2fd87935e2594a643327d2ae07fad112b1b9386f
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210033"
---
# <span data-ttu-id="07a9b-103">Get-CimClass</span><span class="sxs-lookup"><span data-stu-id="07a9b-103">Get-CimClass</span></span>

## <span data-ttu-id="07a9b-104">개요</span><span class="sxs-lookup"><span data-stu-id="07a9b-104">SYNOPSIS</span></span>
<span data-ttu-id="07a9b-105">특정 네임 스페이스에 있는 CIM 클래스의 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="07a9b-105">Gets a list of CIM classes in a specific namespace.</span></span>

## <span data-ttu-id="07a9b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="07a9b-106">SYNTAX</span></span>

### <span data-ttu-id="07a9b-107">ComputerSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="07a9b-107">ComputerSet (Default)</span></span>

```
Get-CimClass [[-ClassName] <String>] [[-Namespace] <String>] [-OperationTimeoutSec <UInt32>]
 [-ComputerName <String[]>] [-MethodName <String>] [-PropertyName <String>]
 [-QualifierName <String>] [<CommonParameters>]
```

### <span data-ttu-id="07a9b-108">SessionSet</span><span class="sxs-lookup"><span data-stu-id="07a9b-108">SessionSet</span></span>

```
Get-CimClass [[-ClassName] <String>] [[-Namespace] <String>] [-OperationTimeoutSec <UInt32>]
 -CimSession <CimSession[]> [-MethodName <String>] [-PropertyName <String>]
 [-QualifierName <String>] [<CommonParameters>]
```

## <span data-ttu-id="07a9b-109">설명</span><span class="sxs-lookup"><span data-stu-id="07a9b-109">DESCRIPTION</span></span>

<span data-ttu-id="07a9b-110">`Get-CimClass`Cmdlet은 특정 네임 스페이스에서 CIM 클래스 목록을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="07a9b-110">The `Get-CimClass` cmdlet retrieves a list of CIM classes in a specific namespace.</span></span> <span data-ttu-id="07a9b-111">제공 된 클래스 이름이 없으면 cmdlet은 네임 스페이스의 모든 클래스를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="07a9b-111">If there is no class name supplied, then the cmdlet returns all the classes in the namespace.</span></span> <span data-ttu-id="07a9b-112">Cim 인스턴스와 달리 cim 클래스는 검색 된 CIM 세션 또는 컴퓨터 이름을 포함 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="07a9b-112">Unlike a CIM instance, CIM classes do not contain the CIM session or computer name from which they are retrieved.</span></span>

## <span data-ttu-id="07a9b-113">예제</span><span class="sxs-lookup"><span data-stu-id="07a9b-113">EXAMPLES</span></span>

### <span data-ttu-id="07a9b-114">예제 1: 모든 클래스 정의 가져오기</span><span class="sxs-lookup"><span data-stu-id="07a9b-114">Example 1: Get all the class definitions</span></span>

<span data-ttu-id="07a9b-115">이 예제에서는 네임 스페이스 **root/cimv2** 의 모든 클래스 정의를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="07a9b-115">This example gets all the class definitions under the namespace **root/cimv2** .</span></span>

```powershell
Get-CimClass
```

### <span data-ttu-id="07a9b-116">예제 2: 특정 이름을 가진 클래스 가져오기</span><span class="sxs-lookup"><span data-stu-id="07a9b-116">Example 2: Get the classes with a specific name</span></span>

<span data-ttu-id="07a9b-117">이 예제에서는 이름에 word **디스크** 를 포함 하는 클래스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="07a9b-117">This example gets the classes that contain the word **disk** in their names.</span></span>

```powershell
Get-CimClass -ClassName *disk*
```

### <span data-ttu-id="07a9b-118">예 3: 특정 메서드 이름으로 클래스 가져오기</span><span class="sxs-lookup"><span data-stu-id="07a9b-118">Example 3: Get the classes with a specific method name</span></span>

<span data-ttu-id="07a9b-119">이 예제에서는 이름 **Win32** 로 시작 하 고 **Term** 로 시작 하는 메서드 이름이 있는 클래스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="07a9b-119">This example gets the classes that start with the name **Win32** and have a method name that starts with **Term** .</span></span>

```powershell
Get-CimClass -ClassName Win32* -MethodName Term*
```

### <span data-ttu-id="07a9b-120">예제 4: 특정 속성 이름을 사용 하 여 클래스 가져오기</span><span class="sxs-lookup"><span data-stu-id="07a9b-120">Example 4: Get the classes with a specific property name</span></span>

<span data-ttu-id="07a9b-121">이 예제에서는 **Win32** 이름으로 시작 하 고 **Handle** 이라는 속성을 포함 하는 클래스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="07a9b-121">This example gets the classes that start with the name **Win32** and have a property named **Handle** .</span></span>

```powershell
Get-CimClass -ClassName Win32* -PropertyName Handle
```

### <span data-ttu-id="07a9b-122">예 5: 특정 한정자 이름으로 클래스 가져오기</span><span class="sxs-lookup"><span data-stu-id="07a9b-122">Example 5: Get the classes with a specific qualifier name</span></span>

<span data-ttu-id="07a9b-123">이 예제에서는 **Win32** 이름으로 시작 하는 클래스를 가져오고, 이름에 word **디스크** 를 포함 하 고, 지정 된 한정자를 **연결** 합니다.</span><span class="sxs-lookup"><span data-stu-id="07a9b-123">This example gets the classes that start with the name **Win32** , contain the word **Disk** in their names and have the specified qualifier **Association** .</span></span>

```powershell
Get-CimClass -ClassName Win32*Disk* -QualifierName Association
```

### <span data-ttu-id="07a9b-124">예제 6: 특정 네임 스페이스에서 클래스 정의 가져오기</span><span class="sxs-lookup"><span data-stu-id="07a9b-124">Example 6: Get the class definitions from a specific namespace</span></span>

<span data-ttu-id="07a9b-125">이 예제에서는 지정 된 네임 스페이스 **root/standardCimv2** 에서 이름에 **Net** 이라는 단어가 포함 된 클래스 정의를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="07a9b-125">This example gets the class definitions that contain the word **Net** in their names from the specified namespace **root/standardCimv2** .</span></span>

```powershell
Get-CimClass -Namespace root/standardCimv2 -ClassName *Net*
```

### <span data-ttu-id="07a9b-126">예 7: 원격 서버에서 클래스 정의 가져오기</span><span class="sxs-lookup"><span data-stu-id="07a9b-126">Example 7: Get the class definitions from a remote server</span></span>

<span data-ttu-id="07a9b-127">이 예제에서는 지정 된 원격 서버 **Server01** 및 **Server02** 에서 이름에 word **디스크** 를 포함 하는 클래스 정의를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="07a9b-127">This example gets the class definitions that contain the word **disk** in their names from the specified remote servers **Server01** and **Server02** .</span></span>

```powershell
Get-CimClass -ClassName *disk* -ComputerName Server01, Server02
```

### <span data-ttu-id="07a9b-128">예 8: CIM 세션을 사용 하 여 클래스 가져오기</span><span class="sxs-lookup"><span data-stu-id="07a9b-128">Example 8: Get the classes by using a CIM session</span></span>

```powershell
$s = New-CimSession -ComputerName Server01, Server02
Get-CimClass -ClassName *disk* -CimSession $s
```

<span data-ttu-id="07a9b-129">이 명령 집합은 여러 컴퓨터를 포함 하는 세션을 만들고 `$s` cmdlet을 사용 하 여 변수에 저장 한 `New-CimSession` 다음 cmdlet을 사용 하 여 클래스를 가져옵니다 `Get-CimClass` .</span><span class="sxs-lookup"><span data-stu-id="07a9b-129">This set of commands creates a session with multiple computers and stores it into a variable `$s` using the `New-CimSession` cmdlet, and then gets the classes using the `Get-CimClass` cmdlet.</span></span>

## <span data-ttu-id="07a9b-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="07a9b-130">PARAMETERS</span></span>

### <span data-ttu-id="07a9b-131">-CimSession</span><span class="sxs-lookup"><span data-stu-id="07a9b-131">-CimSession</span></span>

<span data-ttu-id="07a9b-132">원격 세션에서 또는 원격 컴퓨터에서 cmdlet을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="07a9b-132">Runs the cmdlet in a remote session or on a remote computer.</span></span> <span data-ttu-id="07a9b-133">컴퓨터 이름 또는 세션 개체 (예: 또는 cmdlet의 출력)를 입력 `New-CimSession` 합니다 `Get-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="07a9b-133">Enter a computer name or a session object, such as the output of a `New-CimSession` or `Get-CimSession` cmdlet.</span></span> <span data-ttu-id="07a9b-134">기본값은 로컬 컴퓨터의 현재 세션입니다.</span><span class="sxs-lookup"><span data-stu-id="07a9b-134">The default is the current session on the local computer.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: SessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="07a9b-135">-ClassName</span><span class="sxs-lookup"><span data-stu-id="07a9b-135">-ClassName</span></span>

<span data-ttu-id="07a9b-136">작업을 수행할 CIM 클래스의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="07a9b-136">Specifies the name of the CIM class for which to perform the operation.</span></span> <span data-ttu-id="07a9b-137">PowerShell은 클래스 이름 목록을 제공 하기 위해 로컬 WMI 서버에서 클래스 목록을 가져오기 때문에 탭 완성 기능을 사용 하 여 클래스 목록을 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a9b-137">You can use tab completion to browse the list of classes, because PowerShell gets a list of classes from the local WMI server to provide a list of class names.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="07a9b-138">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="07a9b-138">-ComputerName</span></span>

<span data-ttu-id="07a9b-139">CIM 작업을 실행 하려는 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="07a9b-139">Specifies the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="07a9b-140">FQDN (정규화 된 도메인 이름)에 NetBIOS 이름 또는 IP 주소를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a9b-140">You can specify a fully qualified domain name (FQDN) a NetBIOS name, or an IP address.</span></span>

<span data-ttu-id="07a9b-141">이 매개 변수를 지정 하면 cmdlet이 WsMan 프로토콜을 사용 하 여 지정 된 컴퓨터에 대 한 임시 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="07a9b-141">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span>

<span data-ttu-id="07a9b-142">이 매개 변수를 지정 하지 않으면 cmdlet은 COM (구성 요소 개체 모델)을 사용 하 여 로컬 컴퓨터에서 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="07a9b-142">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="07a9b-143">동일한 컴퓨터에서 여러 작업을 수행 하는 경우에는 CIM 세션을 사용 하면 성능이 향상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="07a9b-143">If multiple operations are being performed on the same computer, using a CIM session gives better performance.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="07a9b-144">-MethodName</span><span class="sxs-lookup"><span data-stu-id="07a9b-144">-MethodName</span></span>

<span data-ttu-id="07a9b-145">이 이름과 일치 하는 메서드가 있는 클래스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="07a9b-145">Finds the classes that have a method matching this name.</span></span> <span data-ttu-id="07a9b-146">이 매개 변수와 함께 와일드 카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a9b-146">You can use wildcard characters with this parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="07a9b-147">-Namespace</span><span class="sxs-lookup"><span data-stu-id="07a9b-147">-Namespace</span></span>

<span data-ttu-id="07a9b-148">CIM 작업에 대 한 네임 스페이스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="07a9b-148">Specifies the namespace for CIM operation.</span></span> <span data-ttu-id="07a9b-149">기본 네임 스페이스는 **root/cimv2** 입니다.</span><span class="sxs-lookup"><span data-stu-id="07a9b-149">The default namespace is **root/cimv2** .</span></span> <span data-ttu-id="07a9b-150">PowerShell에서 네임 스페이스 목록을 제공 하기 위해 로컬 WMI 서버에서 네임 스페이스 목록을 가져오기 때문에 탭 완성 기능을 사용 하 여 네임 스페이스 목록을 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a9b-150">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="07a9b-151">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="07a9b-151">-OperationTimeoutSec</span></span>

<span data-ttu-id="07a9b-152">Cmdlet이 컴퓨터의 응답을 기다리는 시간을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="07a9b-152">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="07a9b-153">기본적으로이 매개 변수의 값은 0 이며이는 cmdlet이 서버에 대 한 기본 시간 제한 값을 사용 함을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="07a9b-153">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="07a9b-154">**Operationtimeoutsec** 매개 변수가 강력한 연결 다시 시도 시간 제한 3 분 보다 작은 값으로 설정 된 경우, 서버에서 작업을 다시 연결할 수 있기 때문에 **operationtimeoutsec** 매개 변수의 값 보다 마지막으로 네트워크 오류가 복구 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="07a9b-154">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="07a9b-155">-PropertyName</span><span class="sxs-lookup"><span data-stu-id="07a9b-155">-PropertyName</span></span>

<span data-ttu-id="07a9b-156">이 이름과 일치 하는 속성이 있는 클래스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="07a9b-156">Finds the classes which have a property matching this name.</span></span> <span data-ttu-id="07a9b-157">이 매개 변수와 함께 와일드 카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a9b-157">You can use wildcard characters with this parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="07a9b-158">-QualifierName</span><span class="sxs-lookup"><span data-stu-id="07a9b-158">-QualifierName</span></span>

<span data-ttu-id="07a9b-159">클래스 수준 한정자 이름별로 클래스를 필터링 합니다.</span><span class="sxs-lookup"><span data-stu-id="07a9b-159">Filters the classes by class level qualifier name.</span></span> <span data-ttu-id="07a9b-160">이 매개 변수와 함께 와일드 카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a9b-160">You can use wildcard characters with this parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="07a9b-161">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="07a9b-161">CommonParameters</span></span>

<span data-ttu-id="07a9b-162">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="07a9b-162">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="07a9b-163">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="07a9b-163">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="07a9b-164">입력</span><span class="sxs-lookup"><span data-stu-id="07a9b-164">INPUTS</span></span>

### <span data-ttu-id="07a9b-165">없음</span><span class="sxs-lookup"><span data-stu-id="07a9b-165">None</span></span>

<span data-ttu-id="07a9b-166">이 cmdlet은 입력 개체를 허용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="07a9b-166">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="07a9b-167">출력</span><span class="sxs-lookup"><span data-stu-id="07a9b-167">OUTPUTS</span></span>

### <span data-ttu-id="07a9b-168">CimClass.</span><span class="sxs-lookup"><span data-stu-id="07a9b-168">Microsoft.Management.Infrastructure.CimClass</span></span>

<span data-ttu-id="07a9b-169">이 cmdlet은 CIM 클래스 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="07a9b-169">This cmdlet returns a CIM class object.</span></span>

## <span data-ttu-id="07a9b-170">참고</span><span class="sxs-lookup"><span data-stu-id="07a9b-170">NOTES</span></span>

## <span data-ttu-id="07a9b-171">관련 링크</span><span class="sxs-lookup"><span data-stu-id="07a9b-171">RELATED LINKS</span></span>

[<span data-ttu-id="07a9b-172">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="07a9b-172">New-CimSession</span></span>](New-CimSession.md)
