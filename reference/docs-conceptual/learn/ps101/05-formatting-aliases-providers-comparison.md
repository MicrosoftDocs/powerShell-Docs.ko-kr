---
title: 서식 지정, 별칭, 공급자 및 비교
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
description: 이 챕터에서는 출력 형식 지정, 명령 별칭, 공급자 및 비교 작업의 개념을 소개합니다.
ms.openlocfilehash: 5573ca58601af0c6af15736b772a9792d8d77a79
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/14/2021
ms.locfileid: "99602223"
---
# <a name="chapter-5---formatting-aliases-providers-comparison"></a><span data-ttu-id="e45fa-103">5장 - 서식 지정, 별칭, 공급자 및 비교</span><span class="sxs-lookup"><span data-stu-id="e45fa-103">Chapter 5 - Formatting, aliases, providers, comparison</span></span>

## <a name="requirements"></a><span data-ttu-id="e45fa-104">요구 사항</span><span class="sxs-lookup"><span data-stu-id="e45fa-104">Requirements</span></span>

<span data-ttu-id="e45fa-105">이 장에 표시된 일부 예제에 SQL Server PowerShell 모듈이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-105">The SQL Server PowerShell module is required by some of the examples shown in this chapter.</span></span> <span data-ttu-id="e45fa-106">이 모듈은 [SMSS(SQL Server Management Studio)][SMSS]의 일부로 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-106">The module installs as part of [SQL Server Management Studio (SMSS)][SMSS].</span></span> <span data-ttu-id="e45fa-107">후속 장에서도 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-107">It's also used in subsequent chapters.</span></span> <span data-ttu-id="e45fa-108">이 모듈을 Windows 10 랩 환경 컴퓨터에 다운로드하여 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-108">Download and install it on your Windows 10 lab environment computer.</span></span>

## <a name="format-right"></a><span data-ttu-id="e45fa-109">오른쪽 정렬</span><span class="sxs-lookup"><span data-stu-id="e45fa-109">Format Right</span></span>

<span data-ttu-id="e45fa-110">4장에서는 가능한 한 왼쪽으로 필터링하는 방법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-110">In Chapter 4, you learned to filter as far to the left as possible.</span></span> <span data-ttu-id="e45fa-111">명령의 출력을 수동으로 서식 지정하는 이 규칙은 출력이 가능한 한 오른쪽에서 발생해야 한다는 점을 제외하면 그 규칙과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-111">The rule for manually formatting a command's output is similar to that rule except it needs to occur as far to the right as possible.</span></span>

<span data-ttu-id="e45fa-112">가장 일반적인 format 명령은 `Format-Table` 및 `Format-List`입니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-112">The most common format commands are `Format-Table` and `Format-List`.</span></span> <span data-ttu-id="e45fa-113">`Format-Wide` 및 `Format-Custom`을 사용할 수도 있지만 일반적이지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-113">`Format-Wide` and `Format-Custom` can also be used, but are less common.</span></span>

<span data-ttu-id="e45fa-114">3장에서 설명한 것처럼 사용자 지정 서식을 사용하지 않는 경우 4개 이상의 속성을 반환하는 명령은 기본적으로 목록으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-114">As mentioned in Chapter 3, a command that returns more than four properties defaults to a list unless custom formatting is used.</span></span>

```powershell
Get-Service -Name w32time | Select-Object -Property Status, DisplayName, Can*
```

```Output
Status              : Running
DisplayName         : Windows Time
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
```

<span data-ttu-id="e45fa-115">`Format-Table` cmdlet을 사용하여 서식 지정을 수동으로 재정의하고 목록 대신 테이블에 출력을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-115">Use the `Format-Table` cmdlet to manually override the formatting and show the output in a table instead of a list.</span></span>

```powershell
Get-Service -Name w32time | Select-Object -Property Status, DisplayName, Can* |
Format-Table
```

```Output
 Status DisplayName  CanPauseAndContinue CanShutdown CanStop
 ------ -----------  ------------------- ----------- -------
Running Windows Time               False        True    True
```

<span data-ttu-id="e45fa-116">`Get-Service`의 기본 출력은 테이블의 세 가지 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-116">The default output for `Get-Service` is three properties in a table.</span></span>

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

<span data-ttu-id="e45fa-117">`Format-List` cmdlet을 사용하여 기본 서식 지정을 재정의하고 결과를 목록으로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-117">Use the `Format-List` cmdlet to override the default formatting and return the results in a list.</span></span>

```powershell
Get-Service -Name w32time | Format-List
```

```Output
Name                : w32time
DisplayName         : Windows Time
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
ServiceType         : Win32ShareProcess
```

<span data-ttu-id="e45fa-118">단순히 `Get-Service`를 `Format-List`로 파이프하면 추가 속성이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-118">Notice that simply piping `Get-Service` to `Format-List` made it return additional properties.</span></span> <span data-ttu-id="e45fa-119">특정 명령의 서식 지정이 백그라운드에서 설정되는 방식 때문에 이러한 결과가 모든 명령에서 발생하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-119">This doesn't occur with every command because of the way the formatting for that particular command is set up behind the scenes.</span></span>

<span data-ttu-id="e45fa-120">format cmdlet을 사용할 때 가장 유의할 점은 이들이 PowerShell의 일반 개체와는 다른 형식 개체를 생성한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-120">The number one thing to be aware of with the format cmdlets is they produce format objects that are different than normal objects in PowerShell.</span></span>

```powershell
Get-Service -Name w32time | Format-List | Get-Member
```

```Output
   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatStartData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
autosizeInfo                            Property   Microsoft.PowerShell.Commands.Inter...
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
pageFooterEntry                         Property   Microsoft.PowerShell.Commands.Inter...
pageHeaderEntry                         Property   Microsoft.PowerShell.Commands.Inter...
shapeInfo                               Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.GroupStartData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
shapeInfo                               Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatEntryData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
formatEntryInfo                         Property   Microsoft.PowerShell.Commands.Inter...
outOfBand                               Property   bool outOfBand {get;set;}
writeStream                             Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.GroupEndData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatEndData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
```

<span data-ttu-id="e45fa-121">즉, format 명령은 대부분의 다른 명령으로 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-121">What this means is format commands can't be piped to most other commands.</span></span> <span data-ttu-id="e45fa-122">일부 `Out-*` 명령으로 파이프될 수 있지만 그 이상은 불가능합니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-122">They can be piped to some of the `Out-*` commands, but that's about it.</span></span> <span data-ttu-id="e45fa-123">이 때문에 줄의 끝부분에서 서식 지정을 수행하는 것이 좋습니다(오른쪽 정렬).</span><span class="sxs-lookup"><span data-stu-id="e45fa-123">This is why you want to perform any formatting at the very end of the line (format right).</span></span>

## <a name="aliases"></a><span data-ttu-id="e45fa-124">별칭</span><span class="sxs-lookup"><span data-stu-id="e45fa-124">Aliases</span></span>

<span data-ttu-id="e45fa-125">PowerShell에서 별칭은 특정 명령의 짧은 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-125">An alias in PowerShell is a shorter name for a command.</span></span> <span data-ttu-id="e45fa-126">PowerShell에는 기본 제공 별칭 집합이 포함되어 있으며 사용자 고유의 별칭을 정의할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-126">PowerShell includes a set of built-in aliases and you can also define your own aliases.</span></span>

<span data-ttu-id="e45fa-127">`Get-Alias` cmdlet은 별칭을 찾는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-127">The `Get-Alias` cmdlet is used to find aliases.</span></span> <span data-ttu-id="e45fa-128">명령의 별칭을 이미 알고 있는 경우 **Name** 매개 변수를 사용하여 별칭이 연결된 명령을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-128">If you already know the alias for a command, the **Name** parameter is used to determine what command the alias is associated with.</span></span>

```powershell
Get-Alias -Name gcm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
```

<span data-ttu-id="e45fa-129">**Name** 매개 변수의 값에 여러 개의 별칭을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-129">Multiple aliases can be specified for the value of the **Name** parameter.</span></span>

```powershell
Get-Alias -Name gcm, gm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
Alias           gm -> Get-Member
```

<span data-ttu-id="e45fa-130">**Name** 매개 변수는 위치 매개 변수이기 때문에 생략되는 경우가 종종 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-130">You'll often see the **Name** parameter omitted since it's a positional parameter.</span></span>

```powershell
Get-Alias gm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gm -> Get-Member
```

<span data-ttu-id="e45fa-131">명령의 별칭을 찾으려면 **Definition** 매개 변수를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-131">If you want to find aliases for a command, you'll need to use the **Definition** parameter.</span></span>

```powershell
Get-Alias -Definition Get-Command, Get-Member
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
Alias           gm -> Get-Member
```

<span data-ttu-id="e45fa-132">**Definition** 매개 변수는 위치 기준으로 사용할 수 없으므로 별도로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-132">The **Definition** parameter can't be used positionally so it must be specified.</span></span>

<span data-ttu-id="e45fa-133">별칭은 키 입력을 줄여주므로 콘솔에 명령을 입력할 때는 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-133">Aliases can save you a few keystrokes and they're fine when you're typing commands into the console.</span></span>
<span data-ttu-id="e45fa-134">그러나 저장하거나 다른 사용자와 공유하는 스크립트 또는 코드에서는 사용하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-134">They shouldn't be used in scripts or any code that you're saving or sharing with others.</span></span> <span data-ttu-id="e45fa-135">이 책의 앞부분에서 설명한 것처럼 전체 cmdlet 및 매개 변수 이름을 사용하면 이해하기 더 쉽습니다(자체 문서화).</span><span class="sxs-lookup"><span data-stu-id="e45fa-135">As mentioned earlier in this book, using full cmdlet and parameter names is self-documenting and easier to understand.</span></span>

<span data-ttu-id="e45fa-136">사용자 고유 별칭을 만드는 경우 이러한 별칭은 컴퓨터의 현재 PowerShell 세션에만 존재하므로 주의하세요.</span><span class="sxs-lookup"><span data-stu-id="e45fa-136">Use caution when creating your own aliases because they'll only exist in your current PowerShell session on your computer.</span></span>

## <a name="providers"></a><span data-ttu-id="e45fa-137">공급자</span><span class="sxs-lookup"><span data-stu-id="e45fa-137">Providers</span></span>

<span data-ttu-id="e45fa-138">PowerShell의 공급자는 파일 시스템처럼 데이터 저장소에 액세스할 수 있는 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-138">A provider in PowerShell is an interface that allows file system like access to a datastore.</span></span> <span data-ttu-id="e45fa-139">PowerShell에는 여러 가지 기본 제공 공급자가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-139">There are a number of built-in providers in PowerShell.</span></span>

```powershell
Get-PSProvider
```

```Output
Name                 Capabilities                       Drives
----                 ------------                       ------
Registry             ShouldProcess, Transactions        {HKLM, HKCU}
Alias                ShouldProcess                      {Alias}
Environment          ShouldProcess                      {Env}
FileSystem           Filter, ShouldProcess, Credentials {C, A, D}
Function             ShouldProcess                      {Function}
Variable             ShouldProcess                      {Variable}
Certificate          ShouldProcess                      {Cert}
WSMan                Credentials                        {WSMan}
```

<span data-ttu-id="e45fa-140">이전 결과에서 볼 수 있듯이 레지스트리, 별칭, 환경 변수, 파일 시스템, 함수, 변수, 인증서 및 WSMan에 대한 기본 제공 공급자가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-140">As you can see in the previous results, there are built-in providers for the registry, aliases, environment variables, the file system, functions, variables, certificates, and WSMan.</span></span>

<span data-ttu-id="e45fa-141">이러한 공급자가 데이터 저장소를 노출하는 데 사용하는 실제 드라이브는 `Get-PSDrive` cmdlet을 사용하여 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-141">The actual drives that these providers use to expose their datastore can be determined with the `Get-PSDrive` cmdlet.</span></span> <span data-ttu-id="e45fa-142">`Get-PSDrive` cmdlet은 공급자가 제공하는 드라이브를 표시할 뿐 아니라 네트워크 공유에 매핑된 드라이브를 비롯한 Windows 논리 드라이브도 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-142">The `Get-PSDrive` cmdlet not only displays drives exposed by providers, but it also displays Windows logical drives including drives mapped to network shares.</span></span>

```powershell
Get-PSDrive
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                      FileSystem    A:\
Alias                                  Alias
C                  14.41        112.10 FileSystem    C:\
Cert                                   Certificate   \
D                                      FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
Variable                               Variable
WSMan                                  WSMan
```

<span data-ttu-id="e45fa-143">Active Directory PowerShell 모듈 및 SQLServer PowerShell 모듈과 같은 타사 모듈은 모두 자체 PowerShell 공급자와 PSDrive를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-143">Third-party modules such as the Active Directory PowerShell module and the SQLServer PowerShell module both add their own PowerShell provider and PSDrive.</span></span>

<span data-ttu-id="e45fa-144">Active Directory 및 SQL Server PowerShell 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-144">Import the Active Directory and SQL Server PowerShell modules.</span></span>

```powershell
Import-Module -Name ActiveDirectory, SQLServer
```

<span data-ttu-id="e45fa-145">추가 PowerShell 공급자가 추가되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-145">Check to see if any additional PowerShell providers were added.</span></span>

```powershell
Get-PSProvider
```

```Output
Name                 Capabilities                       Drives
----                 ------------                       ------
Registry             ShouldProcess, Transactions        {HKLM, HKCU}
Alias                ShouldProcess                      {Alias}
Environment          ShouldProcess                      {Env}
FileSystem           Filter, ShouldProcess, Credentials {C, A, D}
Function             ShouldProcess                      {Function}
Variable             ShouldProcess                      {Variable}
ActiveDirectory      Include, Exclude, Filter, Shoul... {AD}
SqlServer            Credentials                        {SQLSERVER}
```

<span data-ttu-id="e45fa-146">이전 결과 집합에서 두 개의 새로운 PowerShell 공급자가 있습니다. 하나는 Active Directory용이고 다른 하나는 SQL Server용입니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-146">Notice that in the previous set of results, two new PowerShell providers now exist, one for Active Directory and another one for SQL Server.</span></span>

<span data-ttu-id="e45fa-147">각 모듈의 PSDrive도 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-147">A PSDrive for each of those modules was also added.</span></span>

```powershell
Get-PSDrive
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                      FileSystem    A:\
AD                                     ActiveDire... //RootDSE/
Alias                                  Alias
C                  19.38        107.13 FileSystem    C:\
Cert                                   Certificate   \
D                                      FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
SQLSERVER                              SqlServer     SQLSERVER:\
Variable                               Variable
WSMan                                  WSMan
```

<span data-ttu-id="e45fa-148">PSDrive는 일반 파일 시스템과 마찬가지로 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-148">PSDrives can be accessed just like a traditional file system.</span></span>

```powershell
Get-ChildItem -Path Cert:\LocalMachine\CA
```

```Output
   PSParentPath: Microsoft.PowerShell.Security\Certificate::LocalMachine\CA

Thumbprint                                Subject
----------                                -------
FEE449EE0E3965A5246F000E87FDE2A065FD89D4  CN=Root Agency
D559A586669B08F46A30A133F8A9ED3D038E2EA8  OU=www.verisign.com/CPS Incorporated LIABI...
109F1CAED645BB78B3EA2B94C0697C740733031C  CN=Microsoft Windows Hardware Compatibility,...
```

## <a name="comparison-operators"></a><span data-ttu-id="e45fa-149">비교 연산자</span><span class="sxs-lookup"><span data-stu-id="e45fa-149">Comparison Operators</span></span>

<span data-ttu-id="e45fa-150">PowerShell에는 값을 비교하거나 특정 패턴과 일치하는 값을 찾는 데 사용되는 다양한 비교 연산자가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-150">PowerShell contains a number of comparison operators that are used to compare values or find values that match certain patterns.</span></span> <span data-ttu-id="e45fa-151">표 5-1은 PowerShell의 비교 연산자 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-151">Table 5-1 contains a list of comparison operators in PowerShell.</span></span>

|    <span data-ttu-id="e45fa-152">연산자</span><span class="sxs-lookup"><span data-stu-id="e45fa-152">Operator</span></span>    |                          <span data-ttu-id="e45fa-153">정의</span><span class="sxs-lookup"><span data-stu-id="e45fa-153">Definition</span></span>                          |
| -------------- | ------------------------------------------------------------ |
| `-eq`          | <span data-ttu-id="e45fa-154">같음</span><span class="sxs-lookup"><span data-stu-id="e45fa-154">Equal to</span></span>                                                     |
| `-ne`          | <span data-ttu-id="e45fa-155">같지 않음</span><span class="sxs-lookup"><span data-stu-id="e45fa-155">Not equal to</span></span>                                                 |
| `-gt`          | <span data-ttu-id="e45fa-156">초과</span><span class="sxs-lookup"><span data-stu-id="e45fa-156">Greater than</span></span>                                                 |
| `-ge`          | <span data-ttu-id="e45fa-157">크거나 같음</span><span class="sxs-lookup"><span data-stu-id="e45fa-157">Greater than or equal to</span></span>                                     |
| `-lt`          | <span data-ttu-id="e45fa-158">보다 작음</span><span class="sxs-lookup"><span data-stu-id="e45fa-158">Less than</span></span>                                                    |
| `-le`          | <span data-ttu-id="e45fa-159">작거나 같음</span><span class="sxs-lookup"><span data-stu-id="e45fa-159">Less than or equal to</span></span>                                        |
| `-Like`        | <span data-ttu-id="e45fa-160">`*` 와일드카드 문자를 사용하여 일치</span><span class="sxs-lookup"><span data-stu-id="e45fa-160">Match using the `*` wildcard character</span></span>                       |
| `-NotLike`     | <span data-ttu-id="e45fa-161">`*` 와일드카드 문자를 사용하여 일치하지 않음</span><span class="sxs-lookup"><span data-stu-id="e45fa-161">Does not match using the `*` wildcard character</span></span>              |
| `-Match`       | <span data-ttu-id="e45fa-162">지정된 정규식과 일치</span><span class="sxs-lookup"><span data-stu-id="e45fa-162">Matches the specified regular expression</span></span>                     |
| `-NotMatch`    | <span data-ttu-id="e45fa-163">지정된 정규식과 일치하지 않음</span><span class="sxs-lookup"><span data-stu-id="e45fa-163">Does not match the specified regular expression</span></span>              |
| `-Contains`    | <span data-ttu-id="e45fa-164">컬렉션에 지정된 값이 포함되는지 확인</span><span class="sxs-lookup"><span data-stu-id="e45fa-164">Determines if a collection contains a specified value</span></span>        |
| `-NotContains` | <span data-ttu-id="e45fa-165">컬렉션에 특정 값이 포함되지 않는지 확인</span><span class="sxs-lookup"><span data-stu-id="e45fa-165">Determines if a collection does not contain a specific value</span></span> |
| `-In`          | <span data-ttu-id="e45fa-166">컬렉션에 지정된 값이 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="e45fa-166">Determines if a specified value is in a collection</span></span>           |
| `-NotIn`       | <span data-ttu-id="e45fa-167">컬렉션에 지정된 값이 없는지 확인</span><span class="sxs-lookup"><span data-stu-id="e45fa-167">Determines if a specified value is not in a collection</span></span>       |
| `-Replace`     | <span data-ttu-id="e45fa-168">지정된 값을 대체</span><span class="sxs-lookup"><span data-stu-id="e45fa-168">Replaces the specified value</span></span>                                 |

<span data-ttu-id="e45fa-169">표 5-1에 나열된 모든 연산자는 대/소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-169">All of the operators listed in Table 5-1 are case-insensitive.</span></span> <span data-ttu-id="e45fa-170">표 5-1에 나열된 연산자 앞에 `c`를 추가하여 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-170">Place a `c` in front of the operator listed in Table 5-1 to make it case-sensitive.</span></span> <span data-ttu-id="e45fa-171">예를 들어 `-ceq`는 `-eq` 비교 연산자의 대/소문자 구분 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-171">For example, `-ceq` is the case-sensitive version of the `-eq` comparison operator.</span></span>

<span data-ttu-id="e45fa-172">적절한 대/소문자의 "PowerShell"은 같음 비교 연산자를 사용하는 소문자 "powershell"과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-172">Proper case "PowerShell" is equal to lower case "powershell" using the equals comparison operator.</span></span>

```powershell
'PowerShell' -eq 'powershell'
```

```Output
True
```

<span data-ttu-id="e45fa-173">같음 비교 연산자의 대/소문자 구분 버전을 사용하는 것과는 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-173">It's not equal using the case-sensitive version of the equals comparison operator.</span></span>

```powershell
'PowerShell' -ceq 'powershell'
```

```Output
False
```

<span data-ttu-id="e45fa-174">같지 않음 비교 연산자는 조건을 반대로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-174">The not equal comparison operator reverses the condition.</span></span>

```powershell
'PowerShell' -ne 'powershell'
```

```Output
False
```

<span data-ttu-id="e45fa-175">보다 큼, 크거나 같음, 보다 작음, 작거나 같음은 모두 문자열 또는 숫자 값에 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-175">Greater than, greater than or equal to, less than, and less than or equal all work with string or numeric values.</span></span>

```powershell
5 -gt 5
```

```Output
False
```

<span data-ttu-id="e45fa-176">이전 예제에서 크거나 같음을 사용하면 5는 5와 같기 때문에 **부울** 이 true를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-176">Using greater than or equal to instead of greater than with the previous example returns the **Boolean** true since five is equal to five.</span></span>

```powershell
5 -ge 5
```

```Output
True
```

<span data-ttu-id="e45fa-177">이전의 두 예제에서 얻은 결과에서 보다 작음과 작거나 같음이 어떻게 작동하는지 추측할 수 있을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-177">Based on the results from the previous two examples, you can probably guess how both less than and less than or equal to work.</span></span>

```powershell
5 -lt 10
```

```Output
True
```

<span data-ttu-id="e45fa-178">숙련된 PowerShell 사용자라도 `-Like` 연산자와 `-Match` 연산자를 혼동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-178">The `-Like` and `-Match` operators can be confusing, even for experienced PowerShell users.</span></span> <span data-ttu-id="e45fa-179">`-Like`는 와일드카드 문자 `*` 및 `?`와 함께 사용하여 "like" 일치를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-179">`-Like` is used with wildcard the characters `*` and `?` to perform "like" matches.</span></span>

```powershell
'PowerShell' -like '*shell'
```

```Output
True
```

<span data-ttu-id="e45fa-180">`-Match`는 정규식을 사용하여 일치를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-180">`-Match` uses a regular expression to perform the matching.</span></span>

```powershell
'PowerShell' -match '^*.shell$'
```

```Output
True
```

<span data-ttu-id="e45fa-181">범위 연산자를 사용하여 변수에서 1부터 10까지의 숫자를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-181">Use the range operator to store the numbers 1 through 10 in a variable.</span></span>

```powershell
$Numbers = 1..10
```

```Output
```

<span data-ttu-id="e45fa-182">`$Numbers` 변수에 15가 포함되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-182">Determine if the `$Numbers` variable includes 15.</span></span>

```powershell
$Numbers -contains 15
```

```Output
False
```

<span data-ttu-id="e45fa-183">숫자 10이 포함되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-183">Determine if it includes the number 10.</span></span>

```powershell
$Numbers -contains 10
```

```Output
True
```

<span data-ttu-id="e45fa-184">`-NotContains`는 논리를 반대로 바꾸어 `$Numbers` 변수에 특정 값이 포함되지 않는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-184">`-NotContains` reverses the logic to see if the `$Numbers` variable doesn't contain a value.</span></span>

```powershell
$Numbers -notcontains 15
```

```Output
True
```

<span data-ttu-id="e45fa-185">이전 예제에서는 `$Numbers` 변수에 15가 포함되지 않기 때문에 **부울** 이 true를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-185">The previous example returns the **Boolean** true because it's true that the `$Numbers` variable doesn't contain 15.</span></span> <span data-ttu-id="e45fa-186">하지만 숫자 10을 포함하므로 테스트하면 false 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-186">It does however contain the number 10 so it's false when it's tested.</span></span>

```powershell
$Numbers -notcontains 10
```

```Output
False
```

<span data-ttu-id="e45fa-187">"in" 비교 연산자는 PowerShell 버전 3.0에 처음 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-187">The "in" comparison operator was first introduced in PowerShell version 3.0.</span></span> <span data-ttu-id="e45fa-188">이는 값이 배열 "내"에 있는지 확인하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-188">It's used to determine if a value is "in" an array.</span></span> <span data-ttu-id="e45fa-189">`$Numbers` 변수는 여러 값을 포함하기 때문에 배열로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-189">The `$Numbers` variable is an array since it contains multiple values.</span></span>

```powershell
15 -in $Numbers
```

```Output
False
```

<span data-ttu-id="e45fa-190">즉, `-in`은 반대 방향이라는 점을 제외하면 contains 비교 연산자와 동일한 테스트를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-190">In other words, `-in` performs the same test as the contains comparison operator except from the opposite direction.</span></span>

```powershell
10 -in $Numbers
```

```Output
True
```

<span data-ttu-id="e45fa-191">`$Numbers` 배열에 15가 없으므로 다음 예제에서 false가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-191">15 isn't in the `$Numbers` array so false is returned in the following example.</span></span>

```powershell
15 -in $Numbers
```

```Output
False
```

<span data-ttu-id="e45fa-192">`-contains` 연산자와 마찬가지로 `not`은 `-in` 연산자에 대한 논리를 반대로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-192">Just like the `-contains` operator, `not` reverses the logic for the `-in` operator.</span></span>

```powershell
10 -notin $Numbers
```

```Output
False
```

<span data-ttu-id="e45fa-193">이전 예제에서는 `$Numbers` 배열에 10이 포함되어 있고 조건이 10이 포함되지 않은 것을 확인하는 테스트였기 때문에 false를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-193">The previous example returns false because the `$Numbers` array does include 10 and the condition was testing to determine if it didn't contain 10.</span></span>

<span data-ttu-id="e45fa-194">15는 `$Numbers` 배열 "내에 없으므로" **부울** 은 true를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-194">15 is "not in" the `$Numbers` array so it returns the **Boolean** true.</span></span>

```powershell
15 -notin $Numbers
```

```Output
True
```

<span data-ttu-id="e45fa-195">`-replace` 연산자는 당연한 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-195">The `-replace` operator does just want you would think.</span></span> <span data-ttu-id="e45fa-196">즉, 무언가를 바꾸는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-196">It's used to replace something.</span></span> <span data-ttu-id="e45fa-197">값을 하나만 지정하면 해당 값이 없어집니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-197">Specifying one value replaces that value with nothing.</span></span> <span data-ttu-id="e45fa-198">다음 예제에서는 "Shell"이 없어집니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-198">In the following example, I replace "Shell" with nothing.</span></span>

```powershell
'PowerShell' -replace 'Shell'
```

```Output
Power
```

<span data-ttu-id="e45fa-199">값을 다른 값으로 바꾸려면 바꾸려는 패턴 뒤에 새 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-199">If you want to replace a value with a different value, specify the new value after the pattern you want to replace.</span></span> <span data-ttu-id="e45fa-200">SQL Saturday in Baton Rouge는 필자가 매년 강연을 하려고 노력하는 행사입니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-200">SQL Saturday in Baton Rouge is an event that I try to speak at every year.</span></span> <span data-ttu-id="e45fa-201">다음 예제에서는 "Saturday"라는 단어를 약어인 "Sat"로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-201">In the following example, I replace the word "Saturday" with the abbreviation "Sat".</span></span>

```powershell
'SQL Saturday - Baton Rouge' -Replace 'saturday','Sat'
```

```Output
SQL Sat - Baton Rouge
```

<span data-ttu-id="e45fa-202">replace 연산자가 작동하는 방식과 비슷하게 항목을 바꾸는 데 사용할 수 있는 **Replace()** 같은 메서드도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-202">There are also methods like **Replace()** that can be used to replace things similar to the way the replace operator works.</span></span> <span data-ttu-id="e45fa-203">그러나 `-Replace` 연산자는 기본적으로 대/소문자를 구분하지 않으며 **Replace()** 메서드는 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-203">However, the `-Replace` operator is case-insensitive by default, and the **Replace()** method is case-sensitive.</span></span>

```powershell
'SQL Saturday - Baton Rouge'.Replace('saturday','Sat')
```

```Output
SQL Saturday - Baton Rouge
```

<span data-ttu-id="e45fa-204">이전 예제에서 "Saturday"라는 단어는 바뀌지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-204">Notice that the word "Saturday" wasn't replaced in the previous example.</span></span> <span data-ttu-id="e45fa-205">원래와 다른 대/소문자로 지정되었기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-205">This is because it was specified in a different case than the original.</span></span> <span data-ttu-id="e45fa-206">"Saturday"라는 단어를 원래와 동일한 대/소문자로 지정하면 **Replace()** 메서드가 예상대로 값을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-206">When the word "Saturday" is specified in the same case as the original, the **Replace()** method does replace it as expected.</span></span>

```powershell
'SQL Saturday - Baton Rouge'.Replace('Saturday','Sat')
```

```Output
SQL Sat - Baton Rouge
```

<span data-ttu-id="e45fa-207">메서드를 사용하여 데이터를 변환할 때는 터키 테스트 실패와 같은 예기치 않은 문제가 발생할 수 있으므로 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-207">Be careful when using methods to transform data because you can run into unforeseen problems, such as failing the _Turkey Test_.</span></span> <span data-ttu-id="e45fa-208">예를 들어 [Pester를 사용하여 다른 문화권에서 PowerShell 코드 테스트][]라는 블로그 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e45fa-208">For an example, see the blog article titled [Using Pester to Test PowerShell Code with Other Cultures][].</span></span> <span data-ttu-id="e45fa-209">이러한 유형의 문제를 방지하려면 가능한 경우 메서드 대신 연산자를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-209">My recommendation is to use an operator instead of a method whenever possible to avoid these types of problems.</span></span>

<span data-ttu-id="e45fa-210">이전 예제와 같이 비교 연산자를 사용할 수 있지만 필자는 일반적으로 `Where-Object` cmdlet과 함께 사용하여 일부 유형의 필터링을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-210">While the comparison operators can be used as shown in the previous examples, I normally find myself using them with the `Where-Object` cmdlet to perform some type of filtering.</span></span>

## <a name="summary"></a><span data-ttu-id="e45fa-211">요약</span><span class="sxs-lookup"><span data-stu-id="e45fa-211">Summary</span></span>

<span data-ttu-id="e45fa-212">이 장에서는 오른쪽 정렬, 별칭, 공급자 및 비교 연산자를 포함하는 다양한 항목을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-212">In this chapter, you've learned a number of different topics to include Formatting Right, Aliases, Providers, and Comparison Operators.</span></span>

## <a name="review"></a><span data-ttu-id="e45fa-213">검토</span><span class="sxs-lookup"><span data-stu-id="e45fa-213">Review</span></span>

1. <span data-ttu-id="e45fa-214">가능한 한 오른쪽으로 서식 지정을 수행해야 하는 이유는 무엇인가요?</span><span class="sxs-lookup"><span data-stu-id="e45fa-214">Why is it necessary to perform Formatting as far to the right as possible?</span></span>
1. <span data-ttu-id="e45fa-215">`%` 별칭에 대한 실제 cmdlet이 무엇인지 확인하는 방법은 무엇인가요?</span><span class="sxs-lookup"><span data-stu-id="e45fa-215">How do you determine what the actual cmdlet is for the `%` alias?</span></span>
1. <span data-ttu-id="e45fa-216">저장하는 스크립트나 다른 사용자와 공유하는 코드에서 별칭을 사용하면 안 되는 이유는 무엇인가요?</span><span class="sxs-lookup"><span data-stu-id="e45fa-216">Why shouldn't you use aliases in scripts you save or code you share with others?</span></span>
1. <span data-ttu-id="e45fa-217">레지스트리 공급자 중 하나와 연결된 드라이브에 대한 디렉터리 목록을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e45fa-217">Perform a directory listing on the drives that are associated with one of the registry providers.</span></span>
1. <span data-ttu-id="e45fa-218">replace 메서드 대신 replace 연산자를 사용할 경우의 주요 이점 중 하나는 무엇인가요?</span><span class="sxs-lookup"><span data-stu-id="e45fa-218">What's one of the main benefits of using the replace operator instead of the replace method?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="e45fa-219">권장 참조 항목</span><span class="sxs-lookup"><span data-stu-id="e45fa-219">Recommended Reading</span></span>

- <span data-ttu-id="e45fa-220">[Format-Table][]</span><span class="sxs-lookup"><span data-stu-id="e45fa-220">[Format-Table][]</span></span>
- <span data-ttu-id="e45fa-221">[Format-List][]</span><span class="sxs-lookup"><span data-stu-id="e45fa-221">[Format-List][]</span></span>
- <span data-ttu-id="e45fa-222">[Format-Wide][]</span><span class="sxs-lookup"><span data-stu-id="e45fa-222">[Format-Wide][]</span></span>
- <span data-ttu-id="e45fa-223">[about_Aliases][]</span><span class="sxs-lookup"><span data-stu-id="e45fa-223">[about_Aliases][]</span></span>
- <span data-ttu-id="e45fa-224">[about_Providers][]</span><span class="sxs-lookup"><span data-stu-id="e45fa-224">[about_Providers][]</span></span>
- <span data-ttu-id="e45fa-225">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="e45fa-225">[about_Comparison_Operators][]</span></span>
- <span data-ttu-id="e45fa-226">[about_Arrays][]</span><span class="sxs-lookup"><span data-stu-id="e45fa-226">[about_Arrays][]</span></span>

<!-- link references -->
[SMSS]: /sql/ssms/download-sql-server-management-studio-ssms
[Format-Table]: /powershell/module/microsoft.powershell.utility/format-table
[Format-List]: /powershell/module/microsoft.powershell.utility/format-list
[Format-Wide]: /powershell/module/microsoft.powershell.utility/format-wide
[about_Aliases]: /powershell/module/microsoft.powershell.core/about/about_aliases
[about_Providers]: /powershell/module/microsoft.powershell.core/about/about_providers
[about_Comparison_Operators]: /powershell/module/microsoft.powershell.core/about/about_comparison_operators
[about_Arrays]: /powershell/module/microsoft.powershell.core/about/about_arrays
[Pester를 사용하여 다른 문화권에서 PowerShell 코드 테스트]: https://mikefrobbins.com/2015/10/22/using-pester-to-test-powershell-code-with-other-cultures/
[Using Pester to Test PowerShell Code with Other Cultures]: https://mikefrobbins.com/2015/10/22/using-pester-to-test-powershell-code-with-other-cultures/
