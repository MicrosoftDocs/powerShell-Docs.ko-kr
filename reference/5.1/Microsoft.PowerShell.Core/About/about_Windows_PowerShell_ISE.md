---
description: Windows PowerShell ISE (통합 스크립팅 환경)의 기능 및 시스템 요구 사항에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_windows_powershell_ise?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Windows_PowerShell_ISE
ms.openlocfilehash: ff543024d7c62c70217eeaf3ded192a5a24c4757
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388844"
---
# <a name="about-windows-powershell-ise"></a>Windows PowerShell ISE 정보

## <a name="short-description"></a>간단한 설명

Windows PowerShell ISE (통합 스크립팅 환경)의 기능 및 시스템 요구 사항에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명

Windows PowerShell ISE은 Windows PowerShell 용 그래픽 호스트 응용 프로그램입니다.
Windows PowerShell ISE에서는 명령을 실행 하 고 단일 Windows 기반 그래픽 사용자 인터페이스에서 스크립트를 작성, 테스트 및 디버그할 수 있습니다. 이러한 기능에는 Intellisense, 여러 줄 편집, 탭 완성, 자동 저장, 구문 색 지정, 선택적 실행, 상황에 맞는 도움말, 표시 명령 (창에 작성 명령) 및 더블 바이트 문자 집합 및 오른쪽에서 왼쪽으로 쓰기 언어에 대 한 지원이 포함 됩니다.

Windows PowerShell ISE은 초보자를 위한 훌륭한 도구입니다. 명령 창 및 새 원격 PowerShell 표시 탭에서는 첫 번째 시도에서 성공할 수 있도록 작업을 안내 합니다. 코드 조각 및 오류 표시기를 사용 하면 Windows PowerShell 언어를 학습 하는 데 도움이 됩니다.

고급 사용자는 정교한 디버깅 기능, 추가 기능 및 Windows PowerShell ISE 개체 모델을 활용할 수 있습니다.

Windows PowerShell 4.0에 Windows PowerShell ISE의 새로운 기능

Windows PowerShell ISE에는 Windows PowerShell 4.0의 두 가지 새로운 기능이 도입 되었습니다.

- Windows PowerShell ISE는 이제 Windows PowerShell 워크플로 디버깅과 원격 스크립트 디버깅을 모두 지원 합니다. 자세한 내용은 about_Debuggers를 참조 하세요.

- Windows PowerShell 필요한 상태 구성 공급자 및 구성에 대한 IntelliSense 지원이 추가되었습니다.

## <a name="starting-windows-powershell-ise"></a>시작 Windows PowerShell ISE

Windows PowerShell ISE은 지원 되는 모든 Windows 버전에서 사용할 수 있습니다.

- Windows 8.1, Windows 8, Windows Server 2012 R2 및 Windows Server 2012의 시작 화면에서 PowerShell_ISE를 입력 한 다음 PowerShell_ISE 또는 Windows PowerShell ISE를 클릭 합니다.

- Windows Server 2012 R2 및 Windows Server 2012의 서버 관리자에 있는 도구 메뉴에서 Windows PowerShell ISE를 클릭 합니다.

- 이전 버전의 Windows에서는 시작, 모든 프로그램, 보조 프로그램, Windows PowerShell을 차례로 클릭 한 다음 Windows PowerShell ISE를 클릭 합니다.

- Windows에서 Windows PowerShell 콘솔, Cmd.exe 또는 실행 또는 검색 상자에 "PowerShell_ise.exe"를 입력 합니다. NoProfile 스위치를 포함 하 여 명령줄 매개 변수를 사용할 수도 있습니다. 자세한 내용은 [PowerShell_ISE.exe 콘솔 도움말](about_powershell_ise_exe.md)을 참조 하세요.

## <a name="running-interactive-commands"></a>대화형 명령 실행

Windows PowerShell ISE에서 모든 Windows PowerShell 식 또는 명령을 실행할 수 있습니다. Windows PowerShell 콘솔에서 사용할 때와 마찬가지로 cmdlet, 공급자, 스냅인 및 모듈을 사용할 수 있습니다.

콘솔 창에서 대화형 명령을 입력 하거나 붙여 넣을 수 있습니다. 명령을 실행 하려면 단추, 메뉴 항목 및 바로 가기 키를 사용할 수 있습니다.

여러 줄 편집 기능을 사용 하 여 한 번에 여러 줄의 코드를 콘솔 창에 입력 하거나 붙여 넣을 수 있습니다. 위쪽 화살표 키를 눌러 이전 명령을 회수할 때 명령의 모든 줄이 회수 됩니다. 명령을 입력 하는 경우 SHIFT + ENTER를 눌러 현재 줄 아래에 새 빈 줄이 표시 되도록 합니다.

## <a name="viewing-output"></a>출력 보기

명령 및 스크립트의 결과는 콘솔 창에 표시 됩니다. 콘솔 창에서 바로 가기 키 또는 도구 모음의 복사 단추를 사용 하 여 결과를 이동 하거나 복사할 수 있으며 스크립트 창이 나 콘솔 창이 나 다른 프로그램에 결과를 붙여 넣을 수 있습니다. 콘솔 창을 지우려면 "출력 창 지우기" 단추를 클릭 하거나 다음 명령 중 하나를 입력 합니다.

```
Clear-Host
cls
```

## <a name="writing-scripts-and-functions"></a>스크립트 및 함수 작성

스크립트 창에서 스크립트를 열고, 작성 하 고, 편집 하 고, 실행할 수 있습니다. 스크립트 창에서 단추 및 바로 가기 키를 사용 하 여 스크립트를 편집할 수 있습니다. 스크립트 창과 콘솔 창 사이에서 텍스트를 복사 하 고 잘라내어 붙여 넣을 수도 있습니다.

선택적 실행 기능을 사용 하 여 스크립트 전체 또는 일부를 실행할 수 있습니다. 스크립트의 일부를 실행 하려면 실행할 텍스트를 선택한 다음 실행 선택 단추를 클릭 하거나 F8 키를 누릅니다. 기본적으로 F8는 현재 줄을 실행 합니다.

고급 편집 기능에는 중괄호 일치, 확장-축소, 줄 번호, 오류 표시기, 블록 편집 및 들여쓰기, 다양 한 복사 및 대/소문자 변환이 포함 됩니다.

## <a name="getting-help"></a>도움말 보기

Windows PowerShell ISE에는 사용을 설명 하는 도움말 항목이 포함 되어 있습니다. 또한 모든 설치 된 도움말 파일은 스크립트와 명령 창에서 액세스할 수 있습니다.

Windows PowerShell ISE는 상황에 맞는 도움말도 지원 합니다. 특정 cmdlet, 공급자 또는 키워드에 대 한 도움말을 보려면 항목 이름에 커서를 놓고 F1 키를 누릅니다. 도움말 항목을 검색 하려면 F1 키를 누르고 검색어를 입력 합니다.

컴퓨터에서 도움말 항목을 업데이트 하려면 도움말 메뉴에서 Windows PowerShell 업데이트 도움말 항목을 사용 합니다. 이 항목은 현재 UI 문화권의 현재 세션에 있는 모듈에 대 한 도움말을 업데이트 합니다. 매개 변수 없이 Update-Help cmdlet을 실행 하는 것과 같습니다. Windows PowerShell과 함께 제공 되는 cmdlet에 대 한 도움말을 업데이트 하려면 "관리자 권한으로 실행" 옵션을 사용 하 여 Windows PowerShell ISE를 시작 합니다.

Windows PowerShell 콘솔에서 사용 하는 것 처럼 Get-help, Save Help 및 Update-Help cmdlet을 Windows PowerShell ISE에서 사용할 수도 있습니다. 그러나 Windows PowerShell ISE 도움말 함수는 전체 도움말 항목을 표시 하 고 한 번에 한 페이지씩 표시 하지 않습니다.

## <a name="debugging-scripts"></a>스크립트 디버깅

Windows PowerShell ISE 디버거를 사용 하 여 Windows PowerShell 스크립트 또는 함수를 디버그할 수 있습니다. 스크립트를 디버그할 때 메뉴 항목 및 바로 가기 키를 사용 하 여 Windows PowerShell 콘솔에서 수행 하는 것과 동일한 많은 작업을 수행할 수 있습니다. 예를 들어 스크립트에서 줄 중단점을 설정 하려면 코드 줄을 마우스 오른쪽 단추로 클릭 한 다음 중단점 설정/해제를 클릭 합니다.

디버깅 하는 동안 스크립트를 단계별로 실행 하는 동안 디버깅 형광펜은 실행 중인 명령의 일부를 정확 하 게 표시 하 고, 호출 된 함수 및 스크립트를 포함 하는 파일을 자동으로 엽니다.

기본적으로 중단점 설정/해제 메뉴 항목은 스크립트의 전체 줄에 중단점을 설정 하지만 변수나 명령 이름에 중단점을 설정할 수 있습니다.
줄 및 열 번호를 기준으로 명령에 중단점을 설정 하 여 긴 파이프라인 명령을 더 쉽게 디버그할 수 있습니다.

Windows PowerShell ISE에서 스크립트 파일을 열어 스크립트에서 구문 오류를 디버그할 수 있는 경우가 많습니다. 오류 표시기는 구문 오류를 식별 하 고 개요 기능을 사용 하면 스크립트의 일부를 축소 하 여 문제에 초점을 맞출 수 있습니다.

콘솔에서 사용 하는 것 처럼 명령 창에서 Windows PowerShell 디버거 cmdlet을 사용할 수도 있습니다.

## <a name="running-remote-commands"></a>원격 명령 실행

새 원격 PowerShell 탭 기능을 사용 하면 로컬 컴퓨터 또는 원격 컴퓨터에 대 한 영구 사용자 관리 Windows PowerShell 세션 ("PSSession")을 쉽게 설정할 수 있습니다. 명령을 실행 하면 원격 컴퓨터에서 명령을 실행할 수 있는 권한이 있는 사용자 계정 및 컴퓨터 이름을 입력 하 라는 팝업 창이 열립니다.

## <a name="customizing-the-view"></a>뷰 사용자 지정

Windows PowerShell ISE 기능을 사용 하 여 콘솔 창과 스크립트 창을 이동 하 고 크기를 조정할 수 있습니다. 창을 표시 하거나 숨길 수 있으며 모든 창의 텍스트 크기를 변경할 수 있습니다.

옵션 창을 사용 하 여 Windows PowerShell ISE의 모양과 연산을 사용자 지정할 수도 있습니다. 또한 Windows PowerShell ISE에는 메뉴 및 메뉴 항목 추가를 비롯 하 여 Windows PowerShell ISE을 사용자 지정 하는 데 사용할 수 있는 사용자 지정 호스트 변수 $psISE 있습니다.

## <a name="windows-powershell-ise-profile"></a>Windows PowerShell ISE 프로필

Windows PowerShell ISE에는 Microsoft.PowerShellISE_profile.ps1 자체 Windows PowerShell 프로필이 있습니다. 이 프로필에는 Windows PowerShell ISE에서 사용 하는 함수, 별칭, 변수 및 명령을 저장할 수 있습니다.

Windows PowerShell AllHosts 프로필 (CurrentUser \\ allhosts 및 AllUsers \\ allhosts)의 항목은 windows powershell 호스트 프로그램에 있는 것 처럼 Windows PowerShell ISE 에서도 사용할 수 있습니다. 그러나 Windows PowerShell 콘솔 프로필의 항목은 Windows PowerShell ISE에서 사용할 수 없습니다.

프로필 이동 및 다시 구성에 대 한 지침은 Windows PowerShell ISE 도움말 및 about_Profiles에서 사용할 수 있습니다.

## <a name="notes"></a>참고

Windows PowerShell ISE은 Windows의 클라이언트 및 서버 버전에서 기본적으로 설정 되는 선택적 Windows 기능입니다. 클라이언트 버전의 Windows에서 Windows PowerShell ISE를 사용 하거나 사용 하지 않도록 설정 하려면 제어판에서 Windows 기능 사용/사용 안 함을 사용 합니다. 서버 버전의 Windows에서 Windows PowerShell ISE를 사용 하거나 사용 하지 않도록 설정 하려면 서버 관리자에서 역할 및 기능 추가 마법사를 사용 합니다.

Windows PowerShell ISE에는 사용자 인터페이스가 필요 하므로 Windows Server의 Server Core 설치에서는 작동 하지 않습니다. 그러나 Windows PowerShell ISE 기능을 추가 하는 경우 설치는 GUI 포함 서버를 자동으로 변환 합니다.

Windows PowerShell ISE는 WPF(Windows Presentation Foundation)를 기반으로 합니다.
Windows PowerShell ISE의 그래픽 요소가 시스템에서 제대로 렌더링 되지 않는 경우 시스템에서 "WPF 하드웨어 가속 사용 안 함" 그래픽 렌더링 설정을 추가 하거나 조정 하 여 문제를 해결할 수 있습니다. 자세한 내용은 [그래픽 렌더링 레지스트리 설정](/dotnet/framework/wpf/graphics-multimedia/graphics-rendering-registry-settings)을 참조하세요.

## <a name="see-also"></a>참고 항목

[about_Debuggers](about_Debuggers.md)

[about_Profiles](about_Profiles.md)

[about_Updatable_Help](about_Updatable_Help.md)

[Get-Help](xref:Microsoft.PowerShell.Core.Get-Help)

[Get-IseSnippet](xref:ISE.Get-IseSnippet)

[Import-IseSnippet](xref:ISE.Import-IseSnippet)

[New-IseSnippet](xref:ISE.New-IseSnippet)

[Save-Help](xref:Microsoft.PowerShell.Core.Save-Help)

[Show-Command](xref:Microsoft.PowerShell.Utility.Show-Command)

[Update-Help](xref:Microsoft.PowerShell.Core.Update-Help)
