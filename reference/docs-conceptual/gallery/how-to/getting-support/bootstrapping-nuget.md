---
ms.date: 06/12/2017
keywords: gallery,powershell,cmdlet,psget
title: NuGet 부트스트랩
ms.openlocfilehash: 139b2c5a9e742eca8f5ac36c9acd721216584335
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83690872"
---
# <a name="bootstrap-the-nuget-provider-and-nugetexe"></a>NuGet 공급자 및 NuGet.exe 부트스트래프

NuGet.exe는 최신 NuGet 공급자에 포함되어 있지 않습니다. 모듈이나 스크립트의 게시 작업을 수행하려면 PowerShellGet에 이진 실행 파일 **NuGet.exe**가 필요합니다. **찾기**, **설치**, **저장**, **제거** 등 기타 모든 작업을 수행할 때는 NuGet 공급자만 있으면 됩니다.
PowerShellGet에는 NuGet 공급자와 NuGet.exe 부트스트랩을 함께 처리하거나 NuGet 공급자 부트스트랩만 처리하는 논리가 포함되어 있습니다. 두 가지 경우 모두 프롬프트 메시지가 하나만 표시되어야 합니다. 컴퓨터가 인터넷에 연결되어 있지 않으면 사용자나 관리자는 연결이 끊긴 컴퓨터에 NuGet 공급자 및/또는 NuGet.exe 파일의 신뢰할 수 있는 인스턴스를 복사해야 합니다.

> [!NOTE]
> 버전 6부터는 NuGet 공급자가 PowerShell 설치에 포함됩니다.

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a>인터넷에 연결된 컴퓨터에 NuGet 공급자가 설치되지 않은 경우의 오류 해결

```powershell
Find-Module -Repository PSGallery -Verbose -Name Contoso
```

```Output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\user1\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): n
Find-Module : NuGet provider is required to interact with NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed.
At line:1 char:1
+ Find-Module -Repository PSGallery -Verbose -Name Contoso
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Find-Module], InvalidOperationException
   + FullyQualifiedErrorId : CouldNotInstallNuGetProvider,Find-Module
```

```powershell
Find-Module -Repository PSGallery -Verbose -Name Contoso
```

```Output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\user1\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Contoso                             Module     PSGallery        Contoso module
```

## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>인터넷에 연결된 컴퓨터에서 게시 작업을 수행하는 중에 NuGet 공급자는 사용할 수 있는데 NuGet.exe는 사용할 수 없는 경우의 오류 해결

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```Output
NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : NuGet.exe is required to interact with NuGet-based repositories. Please ensure that NuGet.exe is available under one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetExe,Publish-Module
```

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```Output
NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>인터넷에 연결된 컴퓨터에서 게시 작업을 수행하는 중에 NuGet 공급자와 NuGet.exe를 모두 사용할 수 없는 경우의 오류 해결

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```Output
NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed and NuGet.exe is available under
one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetBinaries,Publish-Module
```

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```Output
NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a>인터넷에 연결되지 않은 컴퓨터에서 수동으로 NuGet 공급자 부트스트래핑

위에 나와 있는 프로세스에서는 컴퓨터가 인터넷에 연결되어 있으며 공용 위치에서 파일을 다운로드할 수 있다고 가정합니다. 파일을 다운로드할 수 없는 경우에는 위에 제공된 프로세스를 사용하여 컴퓨터를 부트스트래핑하고, 신뢰할 수 있는 오프라인 프로세스를 통해 격리된 노드에 공급자를 수동으로 복사하는 방법만 사용할 수 있습니다. 격리된 환경을 지원하는 비공개 갤러리를 사용할 수 있는 경우에 이 시나리오를 가장 흔히 사용합니다.

위의 프로세스에 따라 인터넷에 연결된 컴퓨터를 부트스트래핑하고 나면 다음 위치에서 공급자 파일을 확인할 수 있습니다.

`C:\Program Files\PackageManagement\ProviderAssemblies\`

NuGet 공급자의 폴더/파일 구조는 다음과 같습니다(버전 번는 다를 수 있음).

```
NuGet
--2.8.5.208
----Microsoft.PackageManagement.NuGetProvider.dll
```

신뢰할 수 있는 프로세스를 사용하여 오프라인 컴퓨터에 이러한 폴더와 파일을 복사합니다. 오프라인 컴퓨터에서 공급자를 사용하려면 해당 공급자를 가져와야 합니다. 오프라인 컴퓨터에서 다음 명령을 실행합니다.

```powershell
Import-PackageProvider -Name NuGet
```

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a>인터넷에 연결되지 않은 컴퓨터에서 게시 작업을 지원하도록 수동으로 NuGet.exe 부트스트래핑

컴퓨터를 사용하여 `Publish-Module` 또는 `Publish-Script` cmdlet을 통해 개인 갤러리에 모듈이나 스크립트를 게시하려는 경우에는 NuGet 공급자를 수동으로 부트스트래핑하는 프로세스 외에 NuGet.exe 이진 실행 파일도 필요합니다.

격리된 환경을 지원하는 비공개 갤러리를 사용할 수 있는 경우에 이 시나리오를 가장 흔히 사용합니다. 두 가지 옵션을 통해 NuGet.exe 파일을 가져올 수 있습니다.

첫 번째 옵션은 인터넷에 연결된 컴퓨터를 부트스트래핑하고 신뢰할 수 있는 프로세스를 사용하여 오프라인 컴퓨터에 파일을 복사하는 것입니다. 인터넷에 연결된 컴퓨터를 부트스트래핑하고 나면 NuGet.exe 이진 파일이 두 폴더 중 하나에 저장됩니다.

- `Publish-Module` 또는 `Publish-Script` cmdlet을 관리자 권한으로 실행한 경우

   ```powershell
   $env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
   ```

- cmdlet을 관리자 권한이 없는 사용자로 실행한 경우

  ```powershell
  $env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
  ```

두 번째 옵션은 NuGet.Org 웹 사이트 [https://dist.nuget.org/index.html](https://www.nuget.org/downloads)에서 NuGet.exe를 다운로드하는 것입니다. 프로덕션 컴퓨터용 NuGet 버전을 선택할 때는 "권장" 레이블이 있는 2.8.5.208 이상 버전을 선택해야 합니다. 브라우저를 사용하여 다운로드한 파일의 경우 차단을 해제해야 합니다. `Unblock-File` cmdlet을 사용하여 차단을 해제할 수 있습니다.

두 가지 방법 중 어떤 쪽을 사용하든 `$env:path`의 모든 위치에 NuGet.exe 파일을 복사할 수 있지만, 표준 위치는 다음과 같습니다.

- 모든 사용자가 `Publish-Module` 및 `Publish-Script` cmdlet을 사용할 수 있도록 실행 파일을 제공하려는 경우

  ```powershell
  $env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
  ```

- 특정 사용자에게만 실행 파일을 제공하려는 경우(해당 사용자의 프로필 내 위치에만 복사)

  ```powershell
  $env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
  ```
