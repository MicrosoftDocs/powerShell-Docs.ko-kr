---
ms.date: 06/20/2018
keywords: dsc,powershell,configuration,setup
title: DSC PackageManagement 리소스
ms.openlocfilehash: 18cbbfe0715c82dcfdf4a5fb6ee36ee814e43d3b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077622"
---
# <a name="dsc-packagemanagement-resource"></a>DSC PackageManagement 리소스

적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1

Windows PowerShell DSC(Desired State Configuration)의 **PackageManagement** 리소스는 대상 노드에서 패키지 관리 패키지를 설치하거나 제거하는 메커니즘을 제공합니다. 이 리소스를 사용하려면 [http://PowerShellGallery.com](http://PowerShellGallery.com)에서 제공하는 **PackageManagement** 모듈이 필요합니다.

> [!IMPORTANT]
> 다음 속성 정보가 올바르려면 **PackageManagement** 모듈이 버전 1.1.7.0 이상이어야 합니다.

## <a name="syntax"></a>구문

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [AdditionalParameters = [HashTable]]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [MaximumVersion = [string]]
    [MinimumVersion = [string]]
    [ProviderName = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [RequiredVersion = [string]]
    [Source = [string]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a>속성

| 속성 | 설명 |
| --- | --- |
| 이름| 설치하거나 제거할 패키지의 이름을 지정합니다.|
| AdditionalParameters| `Get-Package -AdditionalArguments`에 전달되는 매개 변수의 공급자별 해시 테이블입니다. 예를 들어 NuGet 공급자의 경우 DestinationPath와 같은 추가 매개 변수를 전달할 수 있습니다.|
| Ensure| 패키지를 설치할지 또는 제거할지를 결정합니다.|
| MaximumVersion|찾으려는 패키지의 최대 허용 버전을 지정합니다. 이 매개 변수를 추가하지 않으면 리소스는 패키지의 사용 가능한 가장 높은 버전을 찾습니다.|
| MinimumVersion|찾으려는 패키지의 최소 허용 버전을 지정합니다. 이 매개 변수를 추가하지 않으면 리소스는 _MaximumVersion_ 매개 변수로 지정된 최대 지정 버전도 만족하는 패키지의 사용 가능한 가장 높은 버전을 찾습니다.|
| ProviderName| 패키지 검색 범위를 지정할 패키지 공급자 이름을 지정합니다. `Get-PackageProvider` cmdlet을 실행하여 패키지 공급자 이름을 가져올 수 있습니다.|
| RequiredVersion| 설치할 패키지의 정확한 버전을 지정합니다. 이 매개 변수를 지정하지 않으면 이 DSC 리소스는 _MaximumVersion_ 매개 변수로 지정된 최대 버전도 만족하는 패키지의 사용 가능한 최신 버전을 설치합니다.|
| 원본| 패키지를 찾을 수 있는 패키지 원본의 이름을 지정합니다. 이는 `Register-PackageSource` 또는 PackageManagementSource DSC 리소스에 등록된 원본 또는 URI일 수 있습니다.|
| SourceCredential | 지정된 패키지 공급자 또는 원본에 대한 패키지를 설치하는 권한이 있는 사용자 계정을 지정합니다.|

## <a name="additional-parameters"></a>추가 매개 변수

다음 표에는 AdditionalParameters 속성에 대한 옵션이 나와 있습니다.

| 매개 변수 | 설명 |
| --- | --- |
| DestinationPath| 기본 제공 Nuget 공급자와 같은 공급자에서 사용됩니다. 패키지를 설치할 파일 위치를 지정합니다.|
| InstallationPolicy| 기본 제공 Nuget 공급자와 같은 공급자에서 사용됩니다. 패키지 원본을 신뢰할 수 있는지를 결정합니다. 다음 중 하나: `Untrusted`, `Trusted`.|

## <a name="example"></a>예제

이 예제에서는 **PackageManagement** DSC 리소스를 사용하여 **JQuery** NuGet 패키지 및 **GistProvider** PowerShell 모듈을 설치합니다. 이 예제에서는 먼저 필요한 패키지 원본을 사용할 수 있는지를 확인한 다음 **JQuery** 및 **GistProvider** 패키지(각각 NuGet 및 PowerShell)의 필요한 상태를 정의합니다.

```powershell
Configuration PackageTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagementSource PSGallery
    {
        Ensure      = "Present"
        Name        = "psgallery"
        ProviderName= "PowerShellGet"
        SourceLocation   = "https://www.powershellgallery.com/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagement NugetPackage
    {
        Ensure               = "Present"
        Name                 = "JQuery"
        AdditionalParameters = "$env:HomeDrive\nuget"
        RequiredVersion      = "2.0.1"
        DependsOn            = "[PackageManagementSource]SourceRepository"
    }

    PackageManagement PSModule
    {
        Ensure               = "Present"
        Name                 = "gistprovider"
        Source               = "PSGallery"
        DependsOn            = "[PackageManagementSource]PSGallery"
    }
}
```