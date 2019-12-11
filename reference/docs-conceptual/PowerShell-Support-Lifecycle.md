---
title: PowerShell Core 지원 수명 주기
description: PowerShell Core에 대한 정책 관리 지원
ms.date: 08/06/2018
ms.openlocfilehash: 27738514fc84105a0339eafcdbb540b7d3790052
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416295"
---
# <a name="powershell-core-support-lifecycle"></a>PowerShell Core 지원 수명 주기

PowerShell Core는 Windows PowerShell과 별개로 제공, 설치 및 구성되는 도구 및 구성 요소의 고유 집합입니다. 따라서 PowerShell Core는 Windows 7/8.1/10 또는 Windows Server 라이선싱 계약에 포함되어 있지 않습니다.

그러나 PowerShell Core는 [프리미어][], [Microsoft 기업계약][enterprise-agreement] 및 [Microsoft 소프트웨어 보증][assurance]을 포함한 기존의 Microsoft 지원 계약으로 지원받을 수 있습니다.
또한, 문제가 있는 경우 지원 요청서를 작성하여 PowerShell Core에 대한 [보조 지원][]을 유료로 이용할 수 있습니다.

## <a name="community-support"></a>커뮤니티 지원

또한 GitHub에 대한 [커뮤니티 지원][]도 제공하여 문제, 버그 또는 기능 요청을 취합할 수 있습니다.
또한 Microsoft [PowerShell 기술 커뮤니티][] 또는 [PowerShell][pshub] 허브 페이지의 커뮤니티 섹션에 나열된 포럼에서 커뮤니티의 다른 구성원에 게 도움을 얻을 수 있습니다. 단, 커뮤니티가 발생한 문제를 제때 처리하거나 해결한다는 보장은 없습니다. 긴급하게 도움이 필요한 문제가 있는 경우 기존의 유료 지원 옵션을 사용해야 합니다.

## <a name="lifecycle-of-powershell-core"></a>PowerShell Core의 수명 주기

PowerShell Core는 [Microsoft 최신 수명 주기 정책][modern]을 채택합니다. 이 지원 수명 주기는 고객이 항상 최신 버전을 사용할 수 있도록 합니다.

약 6개월 단위로 PowerShell Core의 6.x 버전이 분기별로 업데이트 됩니다(예: 6.0, 6.1, 6.2 등).

> [!IMPORTANT]
> 지원을 계속 받으려면 부 버전이 새로 릴리스될 때마다 6개월 이내에 업데이트해야 합니다.

예를 들어 PowerShell Core 6.1이 2018년 7월 1일에 릴리스 되고, 계속해서 지원을 받고자 하는 경우 2019년 1월 1일까지 PowerShell Core 6.1로 업데이트해야 합니다.

> [!IMPORTANT]
> 지원을 계속 받으려면 새 패치가 릴리스될 때마다 30일 이내에 업데이트해야 합니다.

예를 들어 PowerShell Core 6.1을 실행하고 있으며 6.1.3이 2019년 2월 19일에 릴리스된 경우 해당 릴리스가 지원을 유지하는 30일 후인 2019년 3월 21일까지 PowerShell Core 6.1.3으로 업데이트해야 합니다. 수정 사항이 필요한 경우, 다음 누적 업데이트에서 수정 사항이 릴리스됩니다.

최신 수명 주기 정책에 따라 Microsoft는 해당 제품(즉, PowerShell Core)에 대한 지원을 중단하기 12개월 전에 고객 측에 공지해야 합니다.

결국 PowerShell Core가 장기 서비스 방식을 채택하는 것을 예상합니다. 이 서비스 방식에서는 6.x의 특정 분기/버전에 필요한 지속적인 지원을 위해 서비스 및 보안 업데이트만 요청합니다.

## <a name="supported-platforms"></a>지원되는 플랫폼

PowerShell Core의 플랫폼과 버전이 공식적으로 지원되는지 확인하려면 다음 표를 참조하세요.

또한 커뮤니티에서 일부 플랫폼과 관련한 패키지를 제공하였으나 공식적으로 지원되지는 않습니다. 이러한 패키지는 표에서 `Community`로 표시됩니다.

`Experimental`로 나열되는 플랫폼은 공식적으로 지원되지는 않지만, 실험 및 피드백용으로 사용 가능합니다.

| 플랫폼                                          |      6.2      |    7.0    |
|---------------------------------------------------|:-------------:|:---------:|
| Windows 7, 8.1 및 10                            |   지원 여부   | 지원 여부 |
| Windows Server 2008 R2, 2012 R2, 2016             |   지원 여부   | 지원 여부 |
| [Windows Server 반기 채널][semi-annual] |   지원 여부   | 지원 여부 |
| Ubuntu 16.04 및 18.04                            |   지원 여부   | 지원 여부 |
| Ubuntu 18.10(맞춤 패키지를 통해)                   |   커뮤니티   | 커뮤니티 |
| Ubuntu 19.04(맞춤 패키지를 통해)                   |   커뮤니티   | 커뮤니티 |
| Debian 9                                          |   지원 여부   | 지원 여부 |
| Debian 10                                         | 지원되지 않음 | 지원 여부 |
| CentOS 7                                          |   지원 여부   | 지원 여부 |
| Red Hat Enterprise Linux 7                        |   지원 여부   | 지원 여부 |
| openSUSE 42.3                                     |   지원 여부   | 지원 여부 |
| Fedora 28                                         |   지원 여부   | 지원 여부 |
| Fedora 29, 30                                     | 지원되지 않음 | 지원 여부 |
| Alpine 3.8                                        |   참고 참조    | 참고 참조  |
| Alpine 3.9 및 3.10                               | 지원되지 않음 | 참고 참조  |
| macOS 10.12+                                      |   지원 여부   | 지원 여부 |
| Arch                                              |   커뮤니티   | 커뮤니티 |
| Raspbian                                          |   커뮤니티   | 커뮤니티 |
| Kali                                              |   커뮤니티   | 커뮤니티 |
| AppImage(여러 Linux 플랫폼에서 사용)      |   커뮤니티   | 커뮤니티 |
| [맞춤 패키지](https://snapcraft.io/powershell)   |   참고 참조    | 참고 참조  |

> [!NOTE]
> 맞춤 패키지는 패키지를 실행하고 있는 배포와 동일하게 지원됩니다.

> [!NOTE]
> CIM, PowerShell Remoting, DSC는 Alpine에서 지원되지 않습니다.

## <a name="powershell-releases-end-of-life"></a>PowerShell 릴리스 수명 종료

[PowerShell Core의 수명 주기](#lifecycle-of-powershell-core)에 따라 다음 표에는 다양한 릴리스의 지원 중단 날짜가 나열되어 있습니다.

| 버전 | 수명 종료                   |
|---------|-------------------------------|
| 6.0     | 2019년 2월 13일             |
| 6.1     | 2019년 9월 28일            |
| 6.2     | 7 릴리스 후 6개월     |

## <a name="unsupported-platforms"></a>지원되지 않는 플랫폼

플랫폼 버전이 플랫폼 소유자가 정의한 수명 종료에 도달하면 PowerShell Core도 해당 플랫폼 버전의 지원 제공을 중단합니다. 이전에 릴리스된 패키지는 액세스가 필요한 고객이 계속 사용할 수는 있지만, 공식 지원 및 업데이트는 더 이상 제공되지 않습니다.

그러므로 다음 버전의 지원을 배포 소유자가 종료했으며 더 이상 지원되지 않습니다.

| 플랫폼 | 버전 | 수명 종료                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| Fedora   | 24      | [2017년 8월](https://fedoramagazine.org/fedora-24-eol/)                                    |
| Fedora   | 25      | [2017년 12월](https://fedoramagazine.org/fedora-25-end-life/)                             |
| Fedora   | 26      | [2018년 5월](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| openSUSE | 42.1    | [2017년 5월](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| openSUSE | 42.2    | [2018년 1월](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| Ubuntu   | 16.10   | [2017년 7월](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| Ubuntu   | 17.04   | [2018년 1월](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| Ubuntu   | 17.10   | [2018년 7월](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |
| Debian   | 8       | [2018년 6월](https://lists.debian.org/debian-security-announce/2018/msg00132.html)           |
| Fedora   | 27      | [2018년 11월](https://fedoramagazine.org/fedora-27-end-of-life/)                          |
| Ubuntu   | 14.04   | [2019년 4월](https://wiki.ubuntu.com/Releases)                                              |

## <a name="notes-on-licensing"></a>라이선싱에 대한 메모

PowerShell Core는 [MIT 라이선스][]에서 릴리스 됩니다. 본 라이선스 및 유료 지원 계약이 안 된 경우 사용자는 [커뮤니티 지원][]으로 서비스가 제한됩니다. 커뮤니티 지원을 이용하더라도 Microsoft는 문의 응답 및 해결 방안을 보장하지 않습니다.

## <a name="windows-powershell-module"></a>Windows PowerShell 모듈

PowerShell Core에 대한 지원은 명시적으로 이 모듈이 PowerShell Core를 지원하지 않는 한 다른 제품 모듈을 포함하지 않습니다. 예를 들어, Windows Server에 부분적으로 제공되는 `ActiveDirectory` 모듈을 사용하는 경우 지원되지 않습니다.

그러나 PowerShell Core를 명시적으로 지원하지 않는 모듈은 경우에 따라 호환이 가능합니다. [WindowsPSModulePath][] 모듈을 설치하여 Windows PowerShell `PSModulePath`를 PowerShell Core `PSModulePath`에 추가할 수 있습니다.

먼저 PowerShell 갤러리에서 **WindowsPSModulePath** 모듈을 설치합니다.

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

이 모듈을 설치한 후에, `Add-WindowsPSModulePath` cmdlet을 실행하여 Windows PowerShell `PSModulePath`를 PowerShell Core에 추가합니다.

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="experimental-features"></a>실험적 기능

[실험적 기능][]은 [커뮤니티 지원](#community-support)으로 제한됩니다.

[프리미어]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[커뮤니티 지원]: https://github.com/powershell/powershell/issues
[pshub]: https://docs.microsoft.com/powershell
[PowerShell 기술 커뮤니티]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[보조 지원]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[MIT 라이선스]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[WindowsPSModulePath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[실험적 기능]: /powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-6#experimentalfeatures
