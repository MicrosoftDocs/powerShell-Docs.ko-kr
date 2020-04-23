---
title: PowerShell Core 지원 수명 주기
description: PowerShell Core에 대한 정책 관리 지원
ms.date: 03/09/2020
ms.openlocfilehash: c319371778eb4615559ae12e0cd153a535ed22bf
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "80500983"
---
# <a name="powershell-support-lifecycle"></a>PowerShell 지원 수명 주기

PowerShell은 Windows PowerShell과 별개로 제공, 설치 및 구성되는 도구 및 구성 요소의 고유 집합입니다. PowerShell은 Windows 라이선스 계약에 포함 되지 않습니다.

PowerShell은 [유료 지원][], [Microsoft 기업계약][enterprise-agreement] 및 [Microsoft Software Assurance][assurance]를 포함한 기존 Microsoft 지원 계약으로 지원받을 수 있습니다.
또한 문제가 있는 경우 지원 요청서를 작성하여 PowerShell에 대한 [보조 지원][]을 유료로 이용할 수 있습니다.

## <a name="community-support"></a>커뮤니티 지원

또한 GitHub에 대한 [커뮤니티 지원][]도 제공하여 문제, 버그 또는 기능 요청을 취합할 수 있습니다.
또한 Microsoft [PowerShell 기술 커뮤니티][] 또는 [PowerShell][pshub] 허브 페이지의 커뮤니티 섹션에 나열된 포럼에서 커뮤니티의 다른 구성원에 게 도움을 얻을 수 있습니다. 단, 커뮤니티가 발생한 문제를 제때 처리하거나 해결한다는 보장은 없습니다. 긴급하게 도움이 필요한 문제가 있는 경우 기존의 유료 지원 옵션을 사용해야 합니다.

## <a name="lifecycle-of-powershell-7"></a>PowerShell 7의 수명 주기

PowerShell 7 릴리스에서 PowerShell은 [Microsoft 최신 수명 주기 정책][modern]에 따라 계속 지원되며 지원 날짜는 [.NET Core의 지원 수명 주기][Long-Term]와 관련됩니다. 이 서비스 방식에서 고객은 LTS(장기 지원) 릴리스 또는 현재 릴리스를 선택할 수 있습니다. PowerShell 7.0은 LTS 릴리스입니다. 해당 지원은 .NET Core 3.1 지원을 마지막으로 종료됩니다. 다음 LTS 릴리스는 다음 .NET Core LTS 릴리스를 따릅니다. 현재 종료 지원 날짜에 대한 자세한 내용은 [PowerShell 릴리스 수명 종료 표](#powershell-releases-end-of-life)을 참조하세요. LTS 릴리스 업데이트에는 기존 워크로드에 대 한 영향을 방지하거나 최소화하도록 설계된 중요 보안 및 서비스 업데이트/수정 사항만 포함됩니다.

현재 릴리스는 LTS 릴리스 간에 발생하는 릴리스입니다. 현재 릴리스에는 중요 수정 사항, 혁신 및 새 기능이 포함될 수 있습니다. 현재 릴리스는 다음 현재 릴리스 또는 LTS 릴리스 이후 3개월 동안 지원됩니다.

> [!IMPORTANT]
> 지원을 받으려면 최신 패치 업데이트가 설치되어 있어야 합니다. 예를 들어 PowerShell 7.0을 실행 중인데 7.0.1이 릴리스된 경우 지원을 받으려면 7.0.1로 업데이트해야 합니다.

## <a name="lifecycle-of-powershell-core-6x"></a>PowerShell Core 6.x의 수명 주기

PowerShell Core는 [Microsoft 최신 수명 주기 정책][modern]을 사용합니다. 이 지원 수명 주기는 고객이 항상 최신 버전을 사용할 수 있도록 합니다.

PowerShell Core의 6.x 버전은 약 6개월 단위의 분기별로 업데이트되었습니다(예: 6.0, 6.1, 6.2 등). 그러나 PowerShell 7 릴리스에서는 더 이상 6.x 릴리스의 부 버전 릴리스가 없습니다. PowerShell 6.2.x는 여전히 지원되며 계속해서 서비스 업데이트를 받습니다.

> [!IMPORTANT]
> 지원을 계속 받으려면 부 버전이 새로 릴리스될 때마다 6개월 이내에 업데이트해야 합니다.

예를 들어 PowerShell Core 6.1이 2018년 7월 1일에 릴리스 되고, 계속해서 지원을 받고자 하는 경우 2019년 1월 1일까지 PowerShell Core 6.1로 업데이트해야 합니다.

> [!IMPORTANT]
> 지원을 계속 받으려면 새 패치가 릴리스될 때마다 30일 이내에 업데이트해야 합니다.

예를 들어 PowerShell Core 6.1을 실행하고 있으며 6.1.3이 2019년 2월 19일에 릴리스된 경우 해당 릴리스가 지원을 유지하는 30일 후인 2019년 3월 21일까지 PowerShell Core 6.1.3으로 업데이트해야 합니다. 수정 사항이 필요한 경우, 다음 누적 업데이트에서 수정 사항이 릴리스됩니다.

최신 수명 주기 정책에 따라 Microsoft는 해당 제품(즉, PowerShell Core)에 대한 지원을 중단하기 12개월 전에 고객 측에 공지해야 합니다.

## <a name="supported-platforms"></a>지원 플랫폼

PowerShell Core의 플랫폼과 버전이 공식적으로 지원되는지 확인하려면 다음 표를 참조하세요.

또한 커뮤니티에서 일부 플랫폼과 관련한 패키지를 제공하였으나 공식적으로 지원되지는 않습니다. 이러한 패키지는 표에서 `Community`로 표시됩니다.

`Experimental`로 나열되는 플랫폼은 공식적으로 지원되지는 않지만, 실험 및 피드백용으로 사용 가능합니다.

| 플랫폼                                          |      6.2      |    7.0    |
| ------------------------------------------------- | :-----------: | :-------: |
| Windows 8.1 및 10                               |   지원됨   | 지원됨 |
| Windows Server 2012 R2, 2016                      |   지원됨   | 지원됨 |
| [Windows Server 반기 채널][semi-annual] |   지원됨   | 지원됨 |
| Ubuntu 16.04 및 18.04                            |   지원됨   | 지원됨 |
| Ubuntu 19.10(맞춤 패키지를 통해)                   |   커뮤니티   | 커뮤니티 |
| Ubuntu 20.04(맞춤 패키지를 통해)                   |   커뮤니티   | 커뮤니티 |
| Debian 9                                          |   지원됨   | 지원됨 |
| Debian 10                                         | 지원되지 않음 | 지원됨 |
| CentOS 7                                          |   지원됨   | 지원됨 |
| CentOS 8                                          | 지원되지 않음 | 지원됨 |
| Red Hat Enterprise Linux 7                        |   지원됨   | 지원됨 |
| Red Hat Enterprise Linux 8                        | 지원되지 않음 | 지원됨 |
| Fedora 30                                         | 지원되지 않음 | 지원됨 |
| Alpine 3.8                                        |   참고 참조    | 참고 참조  |
| Alpine 3.9 및 3.10                               | 지원되지 않음 | 참고 참조  |
| macOS 10.12 이상                                      |   지원됨   | 지원됨 |
| 아키텍처                                              |   커뮤니티   | 커뮤니티 |
| Raspbian                                          |   커뮤니티   | 커뮤니티 |
| Kali                                              |   커뮤니티   | 커뮤니티 |
| AppImage(여러 Linux 플랫폼에서 사용)      |   커뮤니티   | 커뮤니티 |
| [맞춤 패키지](https://snapcraft.io/powershell)   |   참고 참조    | 참고 참조  |

> [!NOTE]
> 맞춤 패키지는 패키지를 실행하고 있는 배포와 동일하게 지원됩니다.

> [!NOTE]
> CIM, PowerShell Remoting, DSC는 Alpine에서 지원되지 않습니다.

## <a name="powershell-releases-end-of-life"></a>PowerShell 릴리스 수명 종료

[PowerShell의 수명 주기](#lifecycle-of-powershell-7)에 따라 다음 표에는 다양한 릴리스의 지원 중단 날짜가 나와 있습니다.

| 버전 |    수명 종료     |
| :-----: | ------------------ |
|   7.0   | 2022년 12월 3일   |
|   6.2   | 2020년 9월 4일  |
|   6.1   | 2019년 9월 28일 |
|   6.0   | 2019년 2월 13일  |

## <a name="unsupported-platforms"></a>지원되지 않는 플랫폼

플랫폼 버전이 플랫폼 소유자가 정의한 수명 종료에 도달하면 PowerShell Core도 해당 플랫폼 버전의 지원 제공을 중단합니다. 이전에 릴리스된 패키지는 액세스가 필요한 고객이 계속 사용할 수는 있지만, 공식 지원 및 업데이트는 더 이상 제공되지 않습니다.

그러므로 다음 버전의 지원을 배포 소유자가 종료했으며 더 이상 지원되지 않습니다.

|    플랫폼    | 버전 |                                                         수명 종료                                                          |
| -------------- | :-----: | ---------------------------------------------------------------------------------------------------------------------------- |
| Debian         |    8    | [2018년 6월](https://lists.debian.org/debian-security-announce/2018/msg00132.html)                                            |
| Fedora         |   24    | [2017년 8월](https://fedoramagazine.org/fedora-24-eol/)                                                                     |
| Fedora         |   25    | [2017년 12월](https://fedoramagazine.org/fedora-25-end-life/)                                                              |
| Fedora         |   26    | [2018년 5월](https://fedoramagazine.org/fedora-26-end-life/)                                                                   |
| Fedora         |   27    | [2018년 11월](https://fedoramagazine.org/fedora-27-end-of-life/)                                                           |
| Fedora         |   28    | [2019년 5월](https://fedoramagazine.org/fedora-28-end-of-life/)                                                                |
| openSUSE       |  42.1   | [2017년 5월](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)                                      |
| openSUSE       |  42.2   | [2018년 1월](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html)                                  |
| openSUSE       |  42.3   | [2019년 7월](https://lists.opensuse.org/opensuse-security-announce/2019-07/msg00000.html)                                     |
| Ubuntu         |  14.04  | [2019년 4월](https://wiki.ubuntu.com/Releases)                                                                               |
| Ubuntu         |  16.10  | [2017년 7월](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)                                         |
| Ubuntu         |  17.04  | [2018년 1월](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)                                           |
| Ubuntu         |  17.10  | [2018년 7월](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)                                         |
| Windows        |    7    | [2020년 1월](https://support.microsoft.com/help/4057281/windows-7-support-ended-on-january-14-2020)                        |
| Windows Server | 2008 R2 | [2020년 1월](https://support.microsoft.com/help/4456235/end-of-support-for-windows-server-2008-and-windows-server-2008-r2) |

## <a name="notes-on-licensing"></a>라이선싱에 대한 메모

PowerShell Core는 [MIT 라이선스][]에서 릴리스 됩니다. 본 라이선스 및 유료 지원 계약이 안 된 경우 사용자는 [커뮤니티 지원][]으로 서비스가 제한됩니다. 커뮤니티 지원을 이용하더라도 Microsoft는 문의 응답 및 해결 방안을 보장하지 않습니다.

## <a name="windows-powershell-compatibility"></a>Windows PowerShell 호환성

PowerShell의 지원 수명 주기에는 PowerShell 7 릴리스 패키지 외부로 제공되는 모듈은 포함되지 않습니다. 예를 들어 Windows Server에 부분적으로 제공되는 `ActiveDirectory` 모듈을 사용하는 경우 [Windows 지원 수명 주기][]에 따라 지원됩니다.

PowerShell 7은 Windows PowerShell용으로 작성 된 기존 PowerShell 모듈과의 호환성을 향상시킵니다.
자세한 내용은 [about_Windows_Compatibility][] 문서 및 [모듈 호환성 목록][]을 참조하세요.

> [!NOTE]
> [**WindowsPSModulePath**](https://www.powershellgallery.com/packages/WindowsPSModulePath) 모듈은 PowerShell 7에서 더 이상 필요하지 않으므로 지원되지 않습니다.

## <a name="experimental-features"></a>실험적 기능

[실험적 기능][]은 [커뮤니티 지원](#community-support)으로 제한됩니다.

## <a name="release-history"></a>릴리스 기록

다음 표에는 PowerShell의 주요 릴리스 일정이 포함되어 있습니다. 이 표는 기록 참조 목적으로 제공되는 것으로, 지원 수명 주기를 결정하는 데 사용하기 위한 것이 아닙니다.

|       버전        | 출시 날짜 |                                                                     참고                                                                      |
| -------------------- | :----------: | --------------------------------------------------------------------------------------------------------------------------------------------- |
| PowerShell 7.0(LTS) |   2020년 3월   | .NET Core 3.1(LTS) 기반                                                                                                                  |
| PowerShell 6.0       |   2018년 1월   | .NET Core 2.1 기반 첫 번째 릴리스. Windows, Linux 및 macOS에 설치 가능.                                                              |
| PowerShell 5.1       |   2016년 8월   | Windows 10 1주년 업데이트 및 Windows Server 2016에서 릴리스                                                                             |
| PowerShell 5.0       |   2016년 2월   | WMF(Windows Management Framework) 5.0에서 릴리스                                                                                            |
| PowerShell 4.0       |   2013년 10월   | Windows 8.1에서 Windows Server 2012 R2와 통합. Windows 7 SP1, Windows Server 2008 R2 SP1, 및 Windows Server 2012에 설치 가능. |
| PowerShell 3.0       |   2012년 10월   | Windows 8에서 Windows Server 2012와 통합. Windows 7 SP1, Windows Server 2008 SP1, 및 Windows Server 2008 R2 SP1에 설치 가능.  |
| PowerShell 2.0       |   2009년 7월   | Windows 7 및 Windows Server 2008 R2에서 통합. Windows XP SP3, Windows Server 2003 SP2, 및 Windows Vista SP1에 설치 가능.            |
| PowerShell 1.0       |   2006년 11월   | Windows XP SP2, Windows Server 2003 SP1 및 Windows Vista에 설치 가능. Windows Server 2008의 선택적 구성 요소.                          |

<!-- hyperlink references -->
[유료 지원]: https://support.microsoft.com/hub/4343728/support-for-business
[enterprise-agreement]: https://www.microsoft.com/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/licensing/licensing-programs/software-assurance-default.aspx
[커뮤니티 지원]: /powershell/scripting/community/community-support
[pshub]: /powershell
[PowerShell 기술 커뮤니티]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[보조 지원]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[Long-Term]: https://dotnet.microsoft.com/platform/support/policy/dotnet-core
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: /windows-server/get-started/semi-annual-channel-overview
[MIT 라이선스]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[about_Windows_Compatibility]: /powershell/module/microsoft.powershell.core/about/about_windows_powershell_compatibility
[Windows 지원 수명 주기]: https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet
[모듈 호환성 목록]: /powershell/scripting/whats-new/module-compatibility
[WindowsPSModulePath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[실험적 기능]: /powershell/module/microsoft.powershell.core/about/about_powershell_config#experimentalfeatures
