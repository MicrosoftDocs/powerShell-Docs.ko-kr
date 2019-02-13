---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
contributor: keithb
title: WMF 5.1 설치 및 구성
ms.openlocfilehash: e5c7968744a442b4be9f1e43a45e91429a6d6165
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55680350"
---
# <a name="install-and-configure-wmf-51"></a>WMF 5.1 설치 및 구성 #


## <a name="download-and-install-the-wmf-51-package"></a>WMF 5.1 패키지 다운로드 및 설치

설치하려는 운영 체제 및 아키텍처에 맞는 WMF 5.1 패키지를 다운로드합니다.

| 운영 체제       | 필수 구성 요소           | 패키지 링크                          |
|------------------------|-------------------------|----------------------------------------|
| Windows Server 2012 R2 |                         | [Win8.1AndW2K12R2-KB3191564-x64.msu][] |
| Windows Server 2012    |                         | [W2K12-KB3191565-x64.msu][]            |
| Windows Server 2008 R2 | [.NET Framework 4.5.2][]| [Win7AndW2K8R2-KB3191566-x64.ZIP][]    |
| Windows 8.1            |                         | **x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</br>**x86:** [Win8.1-KB3191564-x86.msu][] |
| Windows 7 SP1          | [.NET Framework 4.5.2][]| **x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</br>**x86:** [Win7-KB3191566-x86.ZIP][] |

[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86.ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64.ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win8.1-KB3191564-x86.msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win8.1AndW2K12R2-KB3191564-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839516

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a>Windows Server 2008 R2 및 Windows 7의 경우 WMF 5.1 설치

> **참고:** Windows Server 2008 R2 및 Windows 7에 대한 설치 지침이 변경되었으며 다른 패키지에 대한 지침과 다릅니다. Windows Server 2012 R2, Windows Server 2012 및 Windows 8.1에 대한 설치 지침은 다음과 같습니다.

**Windows Server 2008 R2 및 Windows 7에 WMF 5.1 설치**

1. ZIP 파일을 다운로드한 폴더로 이동합니다.

2. ZIP 파일을 마우스 오른쪽 단추로 클릭하고 "압축 풀기..."를 선택합니다. Zip에는 2개의 파일 즉, MSU와 Install-WMF5.1.PS1 스크립트 파일이 포함되어 있습니다.
ZIP 파일의 압축을 푼 후 Windows 7 또는 Windows Server 2008 R2를 실행하는 모든 컴퓨터에 콘텐츠를 복사할 수 있습니다.

3. ZIP 파일 내용을 추출한 후 관리자 권한으로 PowerShell을 연 다음 ZIP 파일의 내용이 포함된 폴더로 이동합니다.

4. 해당 폴더의 Install-Wmf5.1.ps1 스크립트를 실행하고 지침을 따릅니다. 이 스크립트는 로컬 컴퓨터에서 필수 조건을 확인하고 필수 조건을 충족한 경우 WMF 5.1을 설치합니다. 필수 조건은 다음과 같습니다.

Install-WMF5.1.ps1은 다음 매개 변수를 사용하여 Windows Server 2008 R2 및 Windows 7에서 쉽게 설치를 자동화합니다.

- AcceptEula 이 매개 변수를 포함 하는 경우 EULA를 자동으로 적용 하 고 표시 되지 않습니다.
- AllowRestart: 이 매개 변수 AcceptEula가 지정 된 경우에 사용할 수 있습니다. 이 매개 변수가 포함된 경우 WMF 5.1을 설치한 후 다시 시작해야 하면 설치가 완료된 직후 메시지가 표시되지 않고 다시 시작됩니다.

**Windows Server 2008 R2 SP1 및 Windows 7 SP1에 대한 WMF 5.1 필수 조건**

Windows Server 2008 R2 SP1 또는 Windows 7 SP1에서 WMF 5.1을 설치하려면 다음이 필요합니다.
- 최신 서비스 팩이 설치되어 있어야 합니다.
- WMF 3.0이 설치되어 있어서는 **안 됩니다**. WMF 3.0 위에 WMF 5.1을 설치하면 PSModulePath가 손실되어 다른 애플리케이션이 작동하지 않을 수 있습니다. WMF 5.1을 설치하기 전에 WMF 3.0을 제거하거나, PSModulePath를 저장한 다음 WMF 5.1 설치가 완료된 후에 수동으로 복원해야 합니다.
- WMF 5.1을 사용 하려면 적어도 [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642)합니다.
다운로드 위치에 있는 지침에 따라 Microsoft .NET Framework 4.5.2을 설치할 수 있습니다.

**WinRM 종속성**

Windows PowerShell DSC(원하는 상태 구성)는 WinRM에 종속됩니다.
WinRM은 Windows Server 2008 R2 및 Windows 7에서 기본적으로 사용하도록 설정되지 않습니다.
Windows PowerShell 관리자 권한 세션에서 `Set-WSManQuickConfig`를 실행하여 WinRM을 사용하도록 설정합니다.


## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a>Windows Server 2012 R2, Windows Server 2012 및 Windows 8.1의 경우 WMF 5.1 설치
**Windows 탐색기(또는 Windows Server 2012 R2나 Windows 8.1의 파일 탐색기)에서 설치**

1. MSU 파일을 다운로드한 폴더로 이동합니다.
2. MSU를 두 번 클릭하여 실행합니다.

**명령 프롬프트에서 설치**

1. 컴퓨터의 아키텍처에 맞는 올바른 패키지를 다운로드한 후 관리자 권한(관리자 권한으로 실행)으로 명령 프롬프트 창을 엽니다. Windows Server 2012 R2, Windows Server 2012 또는 Windows Server 2008 R2 SP1의 Server Core 설치 옵션에서는 명령 프롬프트가 기본적으로 관리자 권한으로 열립니다.
2. WMF 5.1 설치 패키지를 다운로드하거나 복사한 폴더로 디렉터리를 변경합니다.
3. 다음 명령 중 하나를 실행합니다.
   - Windows Server 2012 R2 또는 Windows 8.1 x64를 실행하는 컴퓨터에서 `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`를 실행합니다.
   - Windows Server 2012를 실행하는 컴퓨터에서 `W2K12-KB3191565-x64.msu /quiet`를 실행합니다.
   - Windows 8.1 X86을 실행하는 컴퓨터에서 `Win8.1-KB3191564-x86.msu /quiet`를 실행합니다.

> [!NOTE]
> WMF 5.1을 설치하려면 다시 부팅해야 합니다. `/quiet` 옵션을 사용하면 경고 없이 시스템이 다시 부팅됩니다.
> 다시 부팅되지 않도록 하려면 `/norestart` 옵션을 사용하세요. 그러나 다시 부팅될 때까지 WMF 5.1이 설치되지 않습니다.
