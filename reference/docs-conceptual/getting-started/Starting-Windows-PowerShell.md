---
ms.date: 12/05/2019
keywords: powershell,cmdlet
title: Windows PowerShell 시작
ms.openlocfilehash: 97b15a4cd79c77a391451ba917f985f9d99db3f5
ms.sourcegitcommit: 0e4c69d8b5cf71431592fe41da816dec9b70f1f9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/09/2019
ms.locfileid: "74953826"
---
# <a name="starting-windows-powershell"></a>Windows PowerShell 시작

Windows PowerShell은 여러 호스트에 내장된 스크립팅 엔진 `.DLL`입니다. 시작할 가장 일반적인 호스트는 대화형 명령줄 **powershell.exe**와 대화형 스크립팅 환경 **powershell_ise.exe**입니다.

Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012 및 Windows 8에서 Windows PowerShell®을 시작하려면 [Windows의 일반 관리 작업 및 탐색](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831491(v=ws.11))을 참조하세요.

## <a name="powershell-core-has-renamed-binary"></a>PowerShell Core의 이진 이름 변경

PowerShell Core(PowerShell 이라고 함)는 오픈 소스이고 .NET Core를 사용하는 버전 6 이상입니다. 지원되는 버전은 Windows, macOS 및 Linux에서 사용할 수 있습니다.

PowerShell 6부터 PowerShell 바이너리의 이름이 Windows의 경우 **pwsh.exe**, macOS 및 Linux의 경우 **pwsh**로 변경되었습니다. **pwsh-preview**를 사용하여 PowerShell 미리 보기 버전을 시작할 수 있습니다. 자세한 내용은 [PowerShell Core 6.0의 새로운 기능](/powershell/scripting/whats-new/what-s-new-in-powershell-core-60#renamed-powershellexe-to-pwshexe) 및 [pwsh 정보](/powershell/module/microsoft.powershell.core/about/about_pwsh?view=powershell-7)를 참조하세요.

PowerShell 7에 대한 cmdlet 참조 및 설치 설명서를 찾으려면 다음 링크를 사용합니다.

| 문서 | 링크 |
| ----- | ----- |
| Cmdlet 참조 | [PowerShell 모듈 브라우저](/powershell/module/?view=powershell-7) |
| Windows에서 설치 | [Windows에서 PowerShell Core 설치](/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7) |
| macOS에서 설치 | [macOS에서 PowerShell Core 설치](/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-7) |
| Linux에서 설치 | [Linux에서 PowerShell Core 설치](/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-7) |

다른 PowerShell 버전에 대한 콘텐츠를 보려면 [PowerShell을 사용하는 방법 설명서](../how-to-use-docs.md)를 참조하세요.

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a>이전 버전의 Windows에서 Windows PowerShell을 시작하는 방법

이 섹션에서는 Windows® 7, Windows Server® 2008 R2 및 Windows Server® 2008에서 Windows PowerShell 및 Windows PowerShell ISE(통합 스크립팅 환경)을 시작하는 방법을 설명합니다. 또한 Windows Server® 2008 R2 및 Windows Server® 2008의 Windows PowerShell 2.0에서 Windows PowerShell ISE에 대한 선택적 기능을 사용하도록 설정하는 방법을 설명합니다.

다음 방법 중 하나를 사용하여 Windows PowerShell 3.0 또는 Windows PowerShell 4.0의 설치된 버전을 시작합니다(해당하는 경우).

#### <a name="from-the-start-menu"></a>시작 메뉴

- **시작**을 클릭하고 **PowerShell**을 입력한 다음 **Windows PowerShell**을 클릭합니다.
- **시작** 메뉴에서 **시작**, **모든 프로그램**, **보조프로그램**, **Windows PowerShell** 폴더, **Windows PowerShell**을 차례로 클릭합니다.

#### <a name="at-the-command-prompt"></a>명령 프롬프트

**cmd.exe**, Windows PowerShell 또는 Windows PowerShell ISE에서 Windows PowerShell을 시작하려면 다음과 같이 입력합니다.

```
PowerShell
```

**powershell.exe** 프로그램의 매개 변수를 사용하여 세션을 사용자 지정할 수도 있습니다. 자세한 내용은 [PowerShell.exe 명령줄 도움말](../core-powershell/console/PowerShell.exe-Command-Line-Help.md)을 참조하세요.

#### <a name="with-administrative-privileges-run-as-administrator"></a>관리자 권한(관리자 권한으로 실행)

**시작**을 클릭하고 **PowerShell**을 입력한 다음 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭하고 **관리자 권한으로 실행**을 클릭합니다.

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a>이전 릴리스의 Windows에서 Windows PowerShell ISE를 시작하는 방법

다음 방법 중 하나를 사용하여 Windows PowerShell ISE를 시작합니다.

#### <a name="from-the-start-menu"></a>시작 메뉴

- **시작**을 클릭하고 **ISE**를 입력한 다음 **Windows PowerShell ISE**를 클릭합니다.
- **시작** 메뉴에서 **시작**, **모든 프로그램**, **보조프로그램**, **Windows PowerShell** 폴더, **Windows PowerShell ISE**를 차례로 클릭합니다.

#### <a name="at-the-command-prompt"></a>명령 프롬프트

**cmd.exe**, Windows PowerShell 또는 Windows PowerShell ISE에서 Windows PowerShell을 시작하려면 다음과 같이 입력합니다.

```
PowerShell_ISE
```

또는

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a>관리자 권한(관리자 권한으로 실행)

**시작**을 클릭하고 **ISE**를 입력한 다음 **Windows PowerShell ISE**를 마우스 오른쪽 단추로 클릭하고 **관리자 권한으로 실행**을 클릭합니다.

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a>이전 릴리스의 Windows에서 Windows PowerShell ISE를 사용하도록 설정하는 방법

Windows PowerShell 4.0 및 Windows PowerShell 3.0의 경우 모든 버전의 Windows에서 Windows PowerShell ISE가 기본적으로 사용됩니다. 아직 사용되지 않는 경우 Windows Management Framework 4.0 또는 Windows Management Framework 3.0에서 사용하도록 설정합니다.

Windows PowerShell 2.0의 경우 Windows 7에서는 Windows PowerShell ISE가 기본적으로 사용됩니다. 그러나 Windows Server 2008 R2 및 Windows Server 2008에서는 선택적 기능입니다.

Windows Server 2008 R2 또는 Windows Server 2008의 Windows PowerShell 2.0에서 Windows PowerShell ISE를 사용하도록 설정하려면 다음 절차를 따르세요.

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a>Windows PowerShell ISE(통합 스크립팅 환경)를 사용하도록 설정하려면

1. 서버 관리자를 시작합니다.
2. **기능**을 클릭한 다음 **기능 추가**를 클릭합니다.
3. 기능 선택에서 Windows PowerShell ISE(통합 스크립팅 환경)를 클릭합니다.

## <a name="starting-the-32-bit-version-of-windows-powershell"></a>Windows PowerShell 32비트 버전 시작

64비트 컴퓨터에 Windows PowerShell을 설치하면 64비트 버전뿐 아니라 Windows PowerShell 32비트 버전인 **Windows PowerShell (x86)** 도 설치됩니다. Windows PowerShell을 실행하는 경우 기본적으로 64비트 버전이 실행됩니다.

그러나 32비트 버전이 필요한 모듈을 사용하거나 32비트 컴퓨터에 원격으로 연결하는 경우와 같이 **Windows PowerShell(x86)** 을 실행해야 하는 경우도 있습니다.

Windows PowerShell 32비트 버전을 시작하려면 다음 절차 중 하나를 따르세요.

#### <a name="in-windows-server-2012-r2"></a>Windows Server® 2012 R2에서

- **시작** 화면에서 **Windows PowerShell(x86)** 을 입력합니다. **Windows PowerShell x86** 타일을 클릭합니다.
- **서버 관리자**의 **도구** 메뉴에서 **Windows PowerShell(x86)** 을 선택합니다.
- 바탕 화면에서 커서를 오른쪽 위 모서리로 이동하고 **검색**을 클릭한 다음 **PowerShell x86**을 입력하고 **Windows PowerShell(x86)** 을 클릭합니다.
- 명령줄을 통해 다음을 입력합니다.`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-server-2012"></a>Windows Server® 2012에서

- **시작** 화면에서 **PowerShell**을 입력하고 **Windows PowerShell(x86)** 을 클릭합니다.
- **서버 관리자**의 **도구** 메뉴에서 **Windows PowerShell(x86)** 을 선택합니다.
- 바탕 화면에서 커서를 오른쪽 위 모서리로 이동하고 **검색**을 클릭한 다음 **PowerShell**을 입력하고 **Windows PowerShell(x86)** 을 클릭합니다.
- 명령줄을 통해 다음을 입력합니다.`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-81"></a>Windows® 8.1에서

- **시작** 화면에서 **Windows PowerShell(x86)** 을 입력합니다. **Windows PowerShell x86** 타일을 클릭합니다.
- Windows 8.1용 [원격 서버 관리 도구](https://go.microsoft.com/fwlink/?LinkID=304145)를 실행하는 경우 **서버 관리자 도구** 메뉴에서 Windows PowerShell x86을 열 수도 있습니다. **Windows PowerShell(x86)** 을 선택합니다.
- 바탕 화면에서 커서를 오른쪽 위 모서리로 이동하고 **검색**을 클릭한 다음 **PowerShell x86**을 입력하고 **Windows PowerShell(x86)** 을 클릭합니다.
- 명령줄을 통해 다음을 입력합니다.`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-8"></a>Windows® 8에서

- **시작** 화면에서 커서를 오른쪽 위 모서리로 이동하고 **설정**, **타일**을 차례로 클릭한 다음 **관리 도구 표시** 슬라이더를 **예**로 이동합니다. **PowerShell**을 입력하고 **Windows PowerShell(x86)** 을 클릭합니다.
- Windows 8용 [원격 서버 관리 도구](https://www.microsoft.com/download/details.aspx?id=28972)를 실행하는 경우 **서버 관리자 도구** 메뉴에서 Windows PowerShell x86을 열 수도 있습니다. **Windows PowerShell(x86)** 을 선택합니다.
- **시작** 화면이나 바탕 화면에서 **PowerShell(x86)** 을 입력하고 **Windows PowerShell(x86)** 을 클릭합니다.
- 명령줄을 통해 다음을 입력합니다.`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`
