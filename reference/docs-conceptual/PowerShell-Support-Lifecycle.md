---
title: PowerShell Core 지원 수명 주기
description: PowerShell Core에 대한 정책 관리 지원
ms.date: 08/06/2018
ms.openlocfilehash: 2e0ca1b9c133e6f316a40aff13365d0489059165
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403495"
---
# <a name="powershell-core-support-lifecycle"></a>PowerShell Core 지원 수명 주기

PowerShell Core는 Windows PowerShell과 별개로 제공, 설치 및 구성되는 도구 및 구성 요소의 고유 집합입니다.
따라서 PowerShell Core는 Windows 7/8.1/10 또는 Windows Server 라이선싱 계약에 포함되어 있지 않습니다.

그러나 PowerShell Core는 [프리미어][], [Microsoft 기업 계약][enterprise-agreement] 및 [Microsoft 소프트웨어 보증][assurance]을 포함한 기존의 Microsoft 지원 계약에서 지원받을 수 있습니다.
또한, 문제가 있는 경우 지원 요청서를 작성하여 PowerShell Core에 대한 [보조 지원][]을 유료로 이용할 수 있습니다.

또한 GitHub에 대한 [커뮤니티 지원][]도 제공하여 문제, 버그 또는 기능 요청을 취합할 수 있습니다.
또는, [Microsoft 커뮤니티][] 또는 Microsoft [PowerShell 기술 커뮤니티][]와 같은 일반적인 커뮤니티에서 다양한 구성원들에게 도움을 받을 수도 있습니다.
단, 문제가 제때 해결된다는 보장은 없습니다.
긴급하게 도움이 필요한 문제가 있는 경우 기존의 유료 지원 옵션을 사용해야 합니다.

## <a name="lifecycle-of-powershell-core"></a>PowerShell Core의 수명 주기

PowerShell Core는 [Microsoft 최신 수명 주기 정책][modern]을 채택합니다.
이 지원 수명 주기는 고객이 항상 최신 버전을 사용할 수 있도록 합니다.

약 6개월 단위로 PowerShell Core의 6.x 버전이 분기별로 업데이트 됩니다(예: 6.0, 6.1, 6.2 등).

> [!IMPORTANT]
> 지원을 계속 받으려면 부 버전이 새로 릴리스될 때마다 6개월 이내에 업데이트해야 합니다.

예를 들어 PowerShell Core 6.1이 2018년 7월 1일에 릴리스 되고, 계속해서 지원을 받고자 하는 경우 2019년 1월 1일까지 PowerShell Core 6.1로 업데이트해야 합니다.

![PowerShell Core 분기 수명 주기][lifecycle-chart]

최신 수명 주기 정책에 따라 Microsoft는 해당 제품(예: PowerShell Core)에 대한 지원을 중단하기 12개월 전에 고객 측에 공지해야 합니다.

즉, PowerShell Core는 "장기 서비스"를 채택하여 6.x의 특정 분기/버전에 대한 지속적인 지원을 위해 서비스 및 보안 업데이트를 요청합니다.

## <a name="supported-platforms"></a>지원되는 플랫폼

사용하는 PowerShell Core 버전에 대해 공식적으로 지원되는 플랫폼에 대해서는 다음 표를 참조하세요.

또한 커뮤니티에서 일부 플랫폼과 관련한 패키지를 제공하였으나 공식적으로 지원되지는 않습니다.
이러한 패키지는 표에서 `Community`로 표시됩니다.

`Experimental`로 나열되는 플랫폼은 공식적으로 지원되지는 않지만, 실험 및 피드백용으로 사용 가능합니다.

|                                                   | 6.0         | 6.1         |
|---------------------------------------------------|:-----------:|:-----------:|
| Windows 7, 8.1 및 10                            | 지원 여부   | 지원 여부   |
| Windows Server 2008 R2, 2012 R2, 2016             | 지원 여부   | 지원 여부   |
| [Windows 서버 반기 채널][semi-annual] | 지원 여부   | 지원 여부   |
| Ubuntu 14.04, 16.04                           | 지원 여부   | 지원 여부   |
| Ubuntu 18.04                                      |             | 지원 여부   |
| Ubuntu 18.10(맞춤 패키지를 통해)                   |             | 커뮤니티   |
| Debian 8.7+, 9                                | 지원 여부   | 지원 여부   |
| CentOS 7                                          | 지원 여부   | 지원 여부   |
| Red Hat Enterprise Linux 7                        | 지원 여부   | 지원 여부   |
| OpenSUSE 42.3                                     | 지원 여부   | 지원 여부   |
| Fedora 27                                         | 지원 여부   | 지원 여부   |
| Fedora 28                                         |             | 지원 여부   |
| macOS 10.12+                                      | 지원 여부   | 지원 여부   |
| Arch                                              | 커뮤니티   | 커뮤니티   |
| Raspbian                                          | 실험적| 커뮤니티   |
| Kali                                              | 커뮤니티   | 커뮤니티   |
| AppImage(여러 Linux 플랫폼에서 사용)     | 커뮤니티   | 커뮤니티   |
| [맞춤 패키지](https://snapcraft.io/powershell)   | 참고 참조    | 참고 참조    |

> [!NOTE]
> 맞춤 패키지는 일정 기간 동안 실험적입니다.  이후에 맞춤에서는 새로운 지원 문제를 일으키지 않을 것입니다. 지원은 패키지를 실행하는 배포를 따릅니다.

## <a name="platform-which-are-out-of-support"></a>지원되지 않는 플랫폼

플랫폼 버전이 플랫폼 소유자가 정의한 수명 종료에 도달하면 PowerShell Core도 해당 플랫폼 버전에 대한 지원 제공을 중단합니다. 이전에 릴리스된 패키지는 액세스가 필요한 고객이 계속 사용할 수는 있지만, 공식 지원 및 업데이트는 더 이상 제공되지 않습니다.

그러므로 다음 버전에 대한 지원은 배포 소유자가 종료했으며, 지원되지 않습니다.

| OS       | 버전 | 수명 종료                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| Fedora   | 24      | [2017년 8월](https://fedoramagazine.org/fedora-24-eol/)                                    |
| Fedora   | 25      | [2017년 12월](https://fedoramagazine.org/fedora-25-end-life/)                             |
| Fedora   | 26      | [2018년 5월](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| openSUSE | 42.1    | [2017년 5월](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| openSUSE | 42.2    | [2018년 1월](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| Ubuntu   | 16.10   | [2017년 7월](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| Ubuntu   | 17.04   | [2018년 1월](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| Ubuntu   | 17.10   | [2018년 7월](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |

## <a name="notes-on-licensing"></a>라이선싱에 대한 메모

PowerShell Core는 [MIT 라이선스][]에서 릴리스 됩니다.
본 라이선스 및 유료 지원 계약이 안 된 경우 사용자는 [커뮤니티 지원][]으로 서비스가 제한됩니다.
커뮤니티 지원을 이용하더라도 Microsoft는 문의 응답 및 해결 방안을 보장하지 않습니다.

## <a name="windows-powershell-module"></a>Windows PowerShell 모듈

PowerShell Core에 대한 지원은 명시적으로 이 모듈이 PowerShell Core를 지원하지 않는 한 다른 제품 모듈로 확장되지 않습니다.
예를 들어, Windows Server에 부분적으로 제공되는 `ActiveDirectory` 모듈을 사용하는 경우 지원되지 않습니다.

그러나 PowerShell Core를 명시적으로 지원하지 않는 모듈은 경우에 따라 호환이 가능합니다.
[`WindowsPSModulePath`][] 모듈을 설치하여 Windows PowerShell `PSModulePath` 를 PowerShell Core `PSModulePath`로 추가할 수 있습니다.

먼저, PowerShell 갤러리에서 `WindowsPSModulePath` 모듈을 설치합니다.

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

이 모듈을 설치한 후에, `Add-WindowsPSModulePath` cmdlet을 실행하여 Windows PowerShell `PSModulePath`를 PowerShell Core에 추가합니다.

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

[프리미어]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[커뮤니티 지원]: https://github.com/powershell/powershell/issues
[Microsoft 커뮤니티]: https://answers.microsoft.com/
[PowerShell 기술 커뮤니티]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[보조 지원]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[MIT 라이선스]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[`WindowsPSModulePath`]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
