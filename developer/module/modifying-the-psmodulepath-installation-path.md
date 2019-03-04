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
ms.openlocfilehash: 639d3a28dd2af09fcc498caedc5fe74c1493445d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855569"
---
# <a name="modifying-the-psmodulepath-installation-path"></a>PSModulePath 설치 경로 수정

`PSModulePath` 환경 변수는 디스크에 설치 된 모듈의 위치로 경로 저장 합니다. Windows PowerShell이이 변수를 사용 하 여 사용자는 모듈의 전체 경로 지정 하지 않은 경우 모듈을 찾습니다. 이 변수에서 경로 순서 대로 검색 됩니다.

Windows PowerShell 시작 되 면 `PSModulePath` 다음 기본값을 사용 하 여 시스템 환경 변수를으로 만들어집니다: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`합니다.

## <a name="to-view-the-psmodulepath-variable"></a>PSModulePath 변수를 보려면

에 지정 된 경로를 보려면를 `PSModulePath` 변수인 다음 명령을 입력 합니다.

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a>PSModulePath 변수에 위치를 추가 하려면

경로이 변수를 추가 하려면 다음 방법 중 하나를 사용 합니다.

- 현재 세션에 대해서만 사용할 수 있는 임시 값을 추가 하려면 명령줄에서 다음 명령을 실행 합니다.

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- 영구 세션을 열 때마다 사용할 수 있는 값을 추가 하려면 다음 명령을 Windows PowerShell 프로필에 추가 합니다.

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  프로필에 대 한 자세한 내용은 참조 하세요. [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) Microsoft TechNet 라이브러리에서.

- 영구 변수를 레지스트리에 추가 라는 새로운 사용자 환경 변수를 만듭니다 `PSModulePath` 에서 환경 변수 편집기를 사용 하 여 **시스템 속성** 대화 상자.

- 스크립트를 사용 하 여 영구 변수를 추가 하려면 사용 합니다 **SetEnvironmentVariable** Environment 클래스는 메서드. 예를 들어, 다음 스크립트 경로 추가 "C:\Program Files\Fabrikam\Module 컴퓨터용 PSModulePath 환경 변수의 값입니다. 경로 사용자 PSModulePath 환경 변수를 추가 하려면 대상을 "User"로 설정 합니다.

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a>PSModulePath 위치를 제거 하려면

이와 유사한 메서드를 사용 하 여 변수에서 경로 제거할 수 있습니다: 예를 들어 `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` 제거 됩니다는 **c:\ModulePath** 현재 세션에서 경로.

## <a name="see-also"></a>참고 항목

[Windows PowerShell 모듈 작성](./writing-a-windows-powershell-module.md)
