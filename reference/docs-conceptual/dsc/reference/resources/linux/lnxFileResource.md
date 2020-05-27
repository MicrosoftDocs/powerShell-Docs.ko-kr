---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Linux용 DSC nxFile 리소스
ms.openlocfilehash: 71096b2d269340b3568c95071089e114ef5c5db9
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560868"
---
# <a name="dsc-for-linux-nxfile-resource"></a><span data-ttu-id="0a6f5-103">Linux용 DSC nxFile 리소스</span><span class="sxs-lookup"><span data-stu-id="0a6f5-103">DSC for Linux nxFile Resource</span></span>

<span data-ttu-id="0a6f5-104">PowerShell DSC(필요한 상태 구성)의 **nxFile** 리소스에서는 Linux 노드 상의 파일 및 디렉터리를 관리하는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-104">The **nxFile** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and directories on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="0a6f5-105">구문</span><span class="sxs-lookup"><span data-stu-id="0a6f5-105">Syntax</span></span>

```Syntax
nxFile <string> #ResourceName
{
    DestinationPath = <string>
    [ SourcePath = <string> ]
    [ Type = <string> { directory | file | link } ]
    [ Contents = <string> ]
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Recurse = <bool> ]
    [ Force = <bool> ]
    [ Links = <string> { follow | manage | ignore } ]
    [ Group = <string> ]
    [ Mode = <string> ]
    [ Owner = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="0a6f5-106">속성</span><span class="sxs-lookup"><span data-stu-id="0a6f5-106">Properties</span></span>

|<span data-ttu-id="0a6f5-107">속성</span><span class="sxs-lookup"><span data-stu-id="0a6f5-107">Property</span></span> |<span data-ttu-id="0a6f5-108">Description</span><span class="sxs-lookup"><span data-stu-id="0a6f5-108">Description</span></span> |
|---|---|
|<span data-ttu-id="0a6f5-109">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="0a6f5-109">DestinationPath</span></span> |<span data-ttu-id="0a6f5-110">파일 또는 디렉터리에 대한 상태를 확인하려는 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-110">Specifies the location where you want to ensure the state for a file or directory.</span></span> |
|<span data-ttu-id="0a6f5-111">SourcePath</span><span class="sxs-lookup"><span data-stu-id="0a6f5-111">SourcePath</span></span> |<span data-ttu-id="0a6f5-112">파일 또는 폴더 리소스를 복사해 올 소스 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-112">Specifies the path from which to copy the file or folder resource.</span></span> <span data-ttu-id="0a6f5-113">이 경로는 로컬 경로이거나 `http/https/ftp` URL일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-113">This path may be a local path, or an `http/https/ftp` URL.</span></span> <span data-ttu-id="0a6f5-114">원격 `http/https/ftp` URL은 **Type** 속성의 값이 **file**일 때에만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-114">Remote `http/https/ftp` URLs are only supported when the value of the **Type** property is **file**.</span></span> |
|<span data-ttu-id="0a6f5-115">Type</span><span class="sxs-lookup"><span data-stu-id="0a6f5-115">Type</span></span> |<span data-ttu-id="0a6f5-116">구성되는 리소스가 디렉터리인지 아니면 파일인지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-116">Specifies whether the resource being configured is a directory or a file.</span></span> <span data-ttu-id="0a6f5-117">리소스가 디렉터리임을 나타내려면 이 속성을 **directory**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-117">Set this property to **directory** to indicate that the resource is a directory.</span></span> <span data-ttu-id="0a6f5-118">리소스가 파일을 나타내려면 이 속성을 **file**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-118">Set it to **file** to indicate that the resource is a file.</span></span> <span data-ttu-id="0a6f5-119">기본값은 **file**입니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-119">The default value is **file**.</span></span> |
|<span data-ttu-id="0a6f5-120">콘텐츠</span><span class="sxs-lookup"><span data-stu-id="0a6f5-120">Contents</span></span> |<span data-ttu-id="0a6f5-121">특정 문자열과 같이 파일의 내용을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-121">Specifies the contents of a file, such as a particular string.</span></span> |
|<span data-ttu-id="0a6f5-122">체크섬</span><span class="sxs-lookup"><span data-stu-id="0a6f5-122">Checksum</span></span> |<span data-ttu-id="0a6f5-123">두 파일이 동일한 것인지 결정할 때 사용할 형식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-123">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="0a6f5-124">**Checksum**을 지정하지 않은 경우 비교에 파일 또는 디렉터리 이름만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-124">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="0a6f5-125">값은 **ctime**, **mtime** 또는 **md5**입니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-125">Values are: **ctime**, **mtime**, or **md5**.</span></span> |
|<span data-ttu-id="0a6f5-126">Recurse</span><span class="sxs-lookup"><span data-stu-id="0a6f5-126">Recurse</span></span> |<span data-ttu-id="0a6f5-127">하위 디렉터리가 포함되어 있는지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-127">Indicates if subdirectories are included.</span></span> <span data-ttu-id="0a6f5-128">하위 디렉터리가 포함되도록 하려면 이 속성을 `$true`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-128">Set this property to `$true` to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="0a6f5-129">기본값은 `$false`입니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-129">The default is `$false`.</span></span> <span data-ttu-id="0a6f5-130">**Type** 속성이 **directory**로 설정되어 있을 때에만 이 속성이 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-130">This property is only valid when the **Type** property is set to **directory**.</span></span> |
|<span data-ttu-id="0a6f5-131">Force</span><span class="sxs-lookup"><span data-stu-id="0a6f5-131">Force</span></span> |<span data-ttu-id="0a6f5-132">특정 파일 작업(예: 파일 덮어쓰기나 비어 있지 않은 디렉터리 삭제)을 수행하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-132">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="0a6f5-133">**Force** 속성을 사용하면 이러한 오류가 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-133">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="0a6f5-134">기본값은 `$false`입니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-134">The default value is `$false`.</span></span> |
|<span data-ttu-id="0a6f5-135">링크</span><span class="sxs-lookup"><span data-stu-id="0a6f5-135">Links</span></span> |<span data-ttu-id="0a6f5-136">바로 가기 링크에 대해 원하는 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-136">Specifies the desired behavior for symbolic links.</span></span> <span data-ttu-id="0a6f5-137">기호화된 링크를 따르고 링크 대상에 대해 작업을 수행하도록 하려면 이 속성을 **follow**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-137">Set this property to **follow** to follow symbolic links and act on the links target.</span></span> <span data-ttu-id="0a6f5-138">예를 들어 링크 대신 파일을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-138">For example, copy the file instead of the link.</span></span> <span data-ttu-id="0a6f5-139">링크에 대해 작업을 수행하도록 하려면 이 속성을 **manage**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-139">Set this property to **manage** to act on the link.</span></span> <span data-ttu-id="0a6f5-140">예를 들어 링크 자체를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-140">For example, copy the link itself.</span></span> <span data-ttu-id="0a6f5-141">바로 가기 링크를 무시하려면 이 속성을 **ignore**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-141">Set this property to **ignore** to ignore symbolic links.</span></span> |
|<span data-ttu-id="0a6f5-142">그룹</span><span class="sxs-lookup"><span data-stu-id="0a6f5-142">Group</span></span> |<span data-ttu-id="0a6f5-143">파일 또는 디렉터리에 대한 사용 권한이 있는 **Group**의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-143">The name of the **Group** to have permissions to the file or directory.</span></span> |
|<span data-ttu-id="0a6f5-144">Mode</span><span class="sxs-lookup"><span data-stu-id="0a6f5-144">Mode</span></span> |<span data-ttu-id="0a6f5-145">리소스에 대해 원하는 사용 권한을 8진수 또는 기호 표기법으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-145">Specifies the desired permissions for the resource, in octal or symbolic notation.</span></span> <span data-ttu-id="0a6f5-146">예를 들어 **777** 또는 **rwxrwxrwx**입니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-146">For example, **777** or **rwxrwxrwx**.</span></span> <span data-ttu-id="0a6f5-147">기호 표기법을 사용하는 경우, 디렉터리나 파일을 나타내는 첫 번째 문자를 제공하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-147">If using symbolic notation, do not provide the first character which indicates directory or file.</span></span> |
|<span data-ttu-id="0a6f5-148">소유자</span><span class="sxs-lookup"><span data-stu-id="0a6f5-148">Owner</span></span> |<span data-ttu-id="0a6f5-149">파일 또는 디렉터리를 소유하는 그룹의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-149">The name of the group to own the file or directory.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="0a6f5-150">공용 속성</span><span class="sxs-lookup"><span data-stu-id="0a6f5-150">Common properties</span></span>

|<span data-ttu-id="0a6f5-151">속성</span><span class="sxs-lookup"><span data-stu-id="0a6f5-151">Property</span></span> |<span data-ttu-id="0a6f5-152">Description</span><span class="sxs-lookup"><span data-stu-id="0a6f5-152">Description</span></span> |
|---|---|
|<span data-ttu-id="0a6f5-153">DependsOn</span><span class="sxs-lookup"><span data-stu-id="0a6f5-153">DependsOn</span></span> |<span data-ttu-id="0a6f5-154">이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-154">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="0a6f5-155">예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-155">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="0a6f5-156">Ensure</span><span class="sxs-lookup"><span data-stu-id="0a6f5-156">Ensure</span></span> |<span data-ttu-id="0a6f5-157">해당 파일이 존재하는지를 확인할지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-157">Determines whether to check if the file exists.</span></span> <span data-ttu-id="0a6f5-158">해당 파일이 존재하도록 하려면 이 속성을 **Present**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-158">Set this property to **Present** to ensure the file exists.</span></span> <span data-ttu-id="0a6f5-159">해당 파일이 존재하지 않도록 하려면 이 속성을 **Absent**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-159">Set it to **Absent** to ensure the file does not exist.</span></span> <span data-ttu-id="0a6f5-160">기본값은 **Present**입니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-160">The default value is **Present**.</span></span> |

## <a name="additional-information"></a><span data-ttu-id="0a6f5-161">추가 정보</span><span class="sxs-lookup"><span data-stu-id="0a6f5-161">Additional Information</span></span>

<span data-ttu-id="0a6f5-162">Linux 및 Windows에서는 텍스트 파일에서 기본적으로 서로 다른 줄 바꿈 문자를 사용하며, 이로 인해 Linux 컴퓨터에서 **nxFile**을 사용하여 일부 파일을 구성할 때 예기치 않은 결과가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-162">Linux and Windows use different line break characters in text files by default, and this can cause unexpected results when configuring some files on a Linux computer with **nxFile**.</span></span> <span data-ttu-id="0a6f5-163">예기치 않은 줄 바꿈 문자로 인한 문제를 방지하면서 Linux 파일의 내용을 관리하는 방법에는 여러 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-163">There are multiple ways to manage the content of a Linux file while avoiding issues caused by unexpected line break characters:</span></span>

1. <span data-ttu-id="0a6f5-164">원격 원본(http, https 또는 ftp)에서 파일을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-164">Copy the file from a remote source (http, https, or ftp)</span></span>

   <span data-ttu-id="0a6f5-165">원하는 내용으로 Linux에서 파일을 만들고, 구성할 노드에 액세스할 수 있는 웹 서버나 ftp 서버에 이 파일을 올립니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-165">Create a file on Linux with the desired contents, and stage it on a web or ftp server accessible the node(s) you will configure.</span></span> <span data-ttu-id="0a6f5-166">**nxFile** 리소스에 있는 **SourcePath** 속성을 파일의 웹 또는 ftp URL로 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-166">Define the **SourcePath** property in the **nxFile** resource with the web or ftp URL to the file.</span></span>

   ```powershell
   Import-DSCResource -Module nx

   Node $Node
   {
      nxFile resolvConf
      {
         SourcePath = "http://10.185.85.11/conf/resolv.conf"
         DestinationPath = "/etc/resolv.conf"
         Mode = "644"
         Type = "file"
      }
   }
   ```

1. <span data-ttu-id="0a6f5-167">Linux 줄 바꿈 문자를 사용하도록 [$OFS](https://technet.microsoft.com/library/hh849787.aspx) 속성을 설정한 후 **Get-Content**로 PowerShell 스크립트에 있는 파일 내용을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-167">Read the file contents in the PowerShell script with [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) after setting the **$OFS** property to use the Linux line-break character.</span></span>

   ```powershell
   Import-DSCResource -Module nx

   Node $Node
   {
      $OFS = "`n"
      $Contents = Get-Content C:\temp\resolv.conf

      nxFile resolvConf
      {
         DestinationPath = "/etc/resolv.conf"
         Mode = "644"
         Type = "file"
         Contents = "$Contents"
      }
   }
   ```

1. <span data-ttu-id="0a6f5-168">PowerShell 함수를 사용하여 Windows 줄 바꿈을 Linux 줄 바꿈 문자로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-168">Use a PowerShell function to replace Windows line breaks with Linux line-break characters.</span></span>

   ```powershell
   Function LinuxString($inputStr){
      $outputStr = $inputStr.Replace("`r`n","`n")
      $outputStr += "`n"
      Return $outputStr
   }

   Import-DSCResource -Module nx

   Node $Node
   {
      $Contents = @'
   search contoso.com
   domain contoso.com
   nameserver 10.185.85.11
   '@
       $Contents = LinuxString $Contents

      nxFile resolvConf
      {
         DestinationPath = "/etc/resolv.conf"
         Mode = "644"
         Type = "file"
         Contents = $Contents
      }
   }
   ```

## <a name="example"></a><span data-ttu-id="0a6f5-169">예제</span><span class="sxs-lookup"><span data-stu-id="0a6f5-169">Example</span></span>

<span data-ttu-id="0a6f5-170">다음 예제에서는 디렉터리 `/opt/mydir`이 존재하고, 지정된 내용의 파일이 이 디렉터리에 존재하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a6f5-170">The following example ensures that the directory `/opt/mydir` exists, and that a file with specified contents exists this directory.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node {
    nxFile DirectoryExample
    {
        Ensure = "Present"
        DestinationPath = "/opt/mydir"
        Type = "Directory"
    }

    nxFile FileExample
    {
        Ensure = "Present"
        Destinationpath = "/opt/mydir/myfile"
        Contents=@"
#!/bin/bash`necho "hello world"`n
"@
        Mode = "755"
        DependsOn = "[nxFile]DirectoryExample"
    }
}
```
