---
description: PackageManagement는 소프트웨어 패키지 관리자를 위한 집계입니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_packagemanagement?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PackageManagement
ms.openlocfilehash: 8fd5d8e059d09556f0e7efa6b68ab4a7c018d3c0
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221426"
---
# <a name="about-packagemanagement"></a>PackageManagement 정보

## <a name="short-description"></a>간단한 설명
PackageManagement는 소프트웨어 패키지 관리자를 위한 집계입니다.

## <a name="long-description"></a>자세한 설명

PackageManagement 기능은 Windows PowerShell 5.0에서 도입 되었습니다.

PackageManagement는 소프트웨어 패키지 관리 시스템에 대 한 통합 인터페이스입니다. PackageManagement cmdlet을 실행 하 여 SDII (소프트웨어 검색, 설치 및 인벤토리) 작업을 수행할 수 있습니다. 기본 설치 기술에 관계 없이 PackageManagement 모듈에서 일반 cmdlet을 실행 하 여 패키지를 검색, 설치 또는 제거할 수 있습니다. 패키지 리포지토리 추가, 제거 및 쿼리 그리고 컴퓨터에서 쿼리를 실행 하 여 설치 된 소프트웨어 패키지를 확인 합니다.

PackageManagement는 다른 소프트웨어 패키지 관리 시스템을 지원할 수 있도록 하는 유연한 플러그 인 모델을 지원 합니다.

PackageManagement 모듈은 PowerShell의 Windows PowerShell 5.0 이상 릴리스에 포함 되어 있으며 패키지 공급자, 패키지 원본 및 패키지 자체의 세 가지 패키지 관리 구조 수준에서 작동 합니다. 몇 가지 용어를 정의 해 보겠습니다.

- 패키지 관리자: 소프트웨어 패키지 관리 시스템. PackageManagement 용어로는 패키지 공급자입니다.
- 패키지 공급자: 패키지 관리자에 대 한 PackageManagement 용어입니다. 예를 들면 Windows Installer, Chocolatey 등이 있습니다.
- 패키지 원본: 리포지토리로 사용할 패키지 공급자를 구성 하는 URL, 로컬 폴더 또는 네트워크 공유 폴더입니다.
- 패키지: 패키지 공급자가 관리 하며 특정 패키지 원본에 저장 되는 소프트웨어의 일부입니다.

PackageManagement 모듈에는 다음 cmdlet이 포함 되어 있습니다. 자세한 내용은 [PackageManagement](/powershell/module/packagemanagement) 도움말을 참조 하세요.

- `Get-PackageProvider`: PackageManagement에 연결 된 패키지 공급자의 목록을 반환 합니다.
- `Get-PackageSource`: 패키지 공급자에 대해 등록 된 패키지 소스 목록을 가져옵니다.
- `Register-PackageSource`: 지정 된 패키지 공급자에 대 한 패키지 소스를 추가 합니다.
- `Set-PackageSource`: 기존 패키지 소스에 대 한 속성을 설정 합니다.
- `Unregister-PackageSource`: 등록 된 패키지 원본을 제거 합니다.
- `Get-Package`: 설치 된 소프트웨어 패키지의 목록을 반환 합니다.
- `Find-Package`: 사용 가능한 패키지 소스에서 소프트웨어 패키지를 찾습니다.
- `Install-Package`: 하나 이상의 소프트웨어 패키지를 설치 합니다.
- `Save-Package`: 패키지를 설치 하지 않고 로컬 컴퓨터에 저장 합니다.
- `Uninstall-Package`: 하나 이상의 소프트웨어 패키지를 제거 합니다.

### <a name="package-provider-bootstrapping-and-dynamic-cmdlet-parameters"></a>패키지 공급자 부트스트래핑 및 동적 Cmdlet 매개 변수

기본적으로 PackageManagement는 핵심 부트스트랩 공급자와 함께 제공 됩니다. 공급자를 부트스트래핑 하 여 필요에 따라 추가 패키지 공급자를 설치할 수 있습니다. 즉, 웹 서비스에서 공급자를 자동으로 설치 하 라는 메시지에 응답 합니다. 모든 PackageManagement cmdlet을 사용 하 여 패키지 공급자를 지정할 수 있습니다. 지정 된 공급자를 사용할 수 없는 경우 PackageManagement는 공급자를 부트스트랩 하거나 자동으로 설치 하 라는 메시지를 표시 합니다. 다음 예에서는 Chocolatey 공급자가 아직 설치 되지 않은 경우 PackageManagement 부트스트래핑에서 공급자를 설치 합니다.

```powershell
Find-Package -Provider Chocolatey <PackageName>
```

Chocolatey 공급자가 아직 설치 되지 않은 경우 앞의 명령을 실행할 때 설치 하 라는 메시지가 표시 됩니다.

```powershell
Install-Package <Chocolatey package Name> -ForceBootstrap
```

Chocolatey 공급자가 아직 설치 되지 않은 경우 위의 명령을 실행 하면 공급자가 설치 됩니다. 그러나 ForceBootstrap 매개 변수가 명령에 추가 되었기 때문에 설치 하 라는 메시지가 표시 되지 않습니다. 공급자와 패키지는 모두 자동으로 설치 됩니다.

패키지를 설치 하려고 할 때 지원 공급자를 아직 설치 하지 않은 경우 명령에 ForceBootstrap 매개 변수를 추가 하지 않은 경우 PackageManagement에서 공급자를 설치할지 묻는 메시지를 표시 합니다.

PackageManagement 명령에 패키지 공급자를 지정 하면 해당 패키지 공급자와 관련 된 동적 매개 변수를 사용할 수 있습니다. 특정 PackageManagement cmdlet에 대 한 Get-Help를 실행 하면 매개 변수 집합 목록이 반환 되 고, 사용 가능한 패키지 공급자에 대 한 동적 매개 변수를 별도의 매개 변수 집합에서 그룹화 합니다.

PackageManagement 프로젝트에 대 한 자세한 정보

Packagemanagement 패키지 공급자를 만드는 방법을 비롯 한 PackageManagement open development 프로젝트에 대 한 자세한 내용은 GitHub의 PackageManagement 프로젝트를 참조 https://oneget.org 하세요.

## <a name="see-also"></a>참고 항목

[Get-PackageProvider](xref:PackageManagement.Get-PackageProvider)

[Get-PackageSource](xref:PackageManagement.Get-PackageSource)

[Register-PackageSource](xref:PackageManagement.Register-PackageSource)

[Set-PackageSource](xref:PackageManagement.Set-PackageSource)

[Unregister-PackageSource](xref:PackageManagement.Unregister-PackageSource)

[Get-Package](xref:PackageManagement.Get-Package)

[Find-Package](xref:PackageManagement.Find-Package)

[Install-Package](xref:PackageManagement.Install-Package)

[Save-Package](xref:PackageManagement.Save-Package)

[Uninstall-Package](xref:PackageManagement.Uninstall-Package)
