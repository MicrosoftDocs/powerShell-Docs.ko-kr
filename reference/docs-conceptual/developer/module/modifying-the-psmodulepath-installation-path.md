---
title: PSModulePath 설치 경로 수정 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 795f2bd52aeceddd3c0ca092d0c0cf2ef44bcf23
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784846"
---
# <a name="modifying-the-psmodulepath-installation-path"></a>PSModulePath 설치 경로 수정

`PSModulePath`환경 변수는 디스크에 설치 된 모듈의 위치에 대 한 경로를 저장 합니다. PowerShell에서는 사용자가 모듈의 전체 경로를 지정 하지 않은 경우이 변수를 사용 하 여 모듈을 찾습니다. 이 변수의 경로는 표시 된 순서 대로 검색 됩니다.

PowerShell이 시작 되 면 `PSModulePath` 는 `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` Windows 및 `$HOME/.local/share/powershell/Modules: usr/local/share/powershell/Modules` Linux, Mac 및 `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` windows PowerShell의 기본 값을 사용 하 여 시스템 환경 변수로 만들어집니다.

> [!NOTE]
> 사용자 고유의 **CurrentUser** 위치는 `WindowsPowerShell\Modules` 사용자 프로필의 **문서** 위치에 있는 폴더입니다. 해당 위치의 특정 경로는 Windows의 버전에 따라 다르며 폴더 리디렉션을 사용 하는지 여부에 따라 다릅니다. 기본적으로 Windows 10의 경우 해당 위치는 `$HOME\Documents\WindowsPowerShell\Modules` 입니다.

## <a name="to-view-the-psmodulepath-variable"></a>PSModulePath 변수를 보려면

변수에 지정 된 경로를 보려면 `PSModulePath` 다음 명령을 입력 합니다.

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a>PSModulePath 변수에 위치를 추가 하려면

이 변수에 경로를 추가 하려면 다음 방법 중 하나를 사용 합니다.

- 현재 세션에 대해서만 사용할 수 있는 임시 값을 추가 하려면 명령줄에서 다음 명령을 실행 합니다.

  `$env:PSModulePath = $env:PSModulePath + "$([System.IO.Path]::PathSeparator)$MyModulePath"`

- 세션이 열릴 때마다 사용할 수 있는 영구 값을 추가 하려면 위의 명령을 PowerShell 프로필 파일 ()에 추가 `$PROFILE` >

  프로필에 대한 자세한 내용은 [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)를 참조하세요.

- 레지스트리에 영구 변수를 추가 하려면 `PSModulePath` **시스템 속성** 대화 상자에서 환경 변수 편집기를 사용 하 여 라는 새 사용자 환경 변수를 만듭니다.

- 스크립트를 사용 하 여 영구 변수를 추가 하려면 [system.web](/dotnet/api/system.environment) 클래스에서 .Net 메서드 [SetEnvironmentVariable](/dotnet/api/system.environment.setenvironmentvariable) 를 사용 합니다. 예를 들어 다음 스크립트는 컴퓨터의 `C:\Program Files\Fabrikam\Module` 환경 변수 값에 대 한 경로를 추가 합니다 `PSModulePath` . 사용자 환경 변수에 대 한 경로를 추가 하려면 `PSModulePath` 대상을 "user"로 설정 합니다.

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + [System.IO.Path]::PathSeparator + "C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a>PSModulePath에서 위치를 제거 하려면

유사한 메서드를 사용 하 여 변수에서 경로를 제거할 수 있습니다. 예를 들어 `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` 는 현재 세션에서 **C:\modulepath** 경로를 제거 합니다.

## <a name="see-also"></a>참고 항목

[Windows PowerShell 모듈 작성](./writing-a-windows-powershell-module.md)

[about_Modules](/powershell/module/microsoft.powershell.core/about/about_modules)
