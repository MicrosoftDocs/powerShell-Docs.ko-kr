---
title: PSModulePath 설치 경로 수정 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: 5957ea4c15cd3778bd09b67c4b97de0ef0cfdd2a
ms.sourcegitcommit: 0e4c69d8b5cf71431592fe41da816dec9b70f1f9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/09/2019
ms.locfileid: "74953843"
---
# <a name="modifying-the-psmodulepath-installation-path"></a>PSModulePath 설치 경로 수정

`PSModulePath` 환경 변수는 디스크에 설치 된 모듈의 위치에 대 한 경로를 저장 합니다. PowerShell에서는 사용자가 모듈의 전체 경로를 지정 하지 않은 경우이 변수를 사용 하 여 모듈을 찾습니다. 이 변수의 경로는 표시 된 순서 대로 검색 됩니다.

PowerShell이 시작 되 면 다음과 같은 기본값을 사용 하는 시스템 환경 변수로 `PSModulePath` 만들어집니다. Windows PowerShell의 경우 `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` 또는 `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules`입니다.

## <a name="to-view-the-psmodulepath-variable"></a>PSModulePath 변수를 보려면

`PSModulePath` 변수에 지정 된 경로를 보려면 다음 명령을 입력 합니다.

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a>PSModulePath 변수에 위치를 추가 하려면

이 변수에 경로를 추가 하려면 다음 방법 중 하나를 사용 합니다.

- 현재 세션에 대해서만 사용할 수 있는 임시 값을 추가 하려면 명령줄에서 다음 명령을 실행 합니다.

  `$env:PSModulePath = $env:PSModulePath + "$([System.IO.Path]::PathSeparator)$MyModulePath"`

- 세션이 열릴 때마다 사용할 수 있는 영구 값을 추가 하려면 위의 명령을 PowerShell 프로필 파일 (`$PROFILE`)에 추가 >

  프로필에 대한 자세한 내용은 [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)를 참조하세요.

- 레지스트리에 영구 변수를 추가 하려면 **시스템 속성** 대화 상자에서 환경 변수 편집기를 사용 하 여 `PSModulePath` 이라는 새 사용자 환경 변수를 만듭니다.

- 스크립트를 사용 하 여 영구 변수를 추가 하려면 [system.web](https://docs.microsoft.com/dotnet/api/system.environment) 클래스에서 .Net 메서드 [SetEnvironmentVariable](https://docs.microsoft.com/dotnet/api/system.environment.setenvironmentvariable) 를 사용 합니다. 예를 들어 다음 스크립트는 컴퓨터의 `PSModulePath` 환경 변수 값에 `C:\Program Files\Fabrikam\Module` 경로를 추가 합니다. 사용자 `PSModulePath` 환경 변수에 대 한 경로를 추가 하려면 대상을 "User"로 설정 합니다.

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + [System.IO.Path]::PathSeparator + "C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a>PSModulePath에서 위치를 제거 하려면

유사한 메서드를 사용 하 여 변수에서 경로를 제거할 수 있습니다. 예를 들어 `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"`는 현재 세션에서 **C:\modulepath** 경로를 제거 합니다.

## <a name="see-also"></a>참고 항목

[Windows PowerShell 모듈 작성](./writing-a-windows-powershell-module.md)
