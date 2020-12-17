---
title: ARM에서 PowerShell Core 설치
description: ARM 기반 시스템에 PowerShell Core 설치
ms.date: 11/11/2020
ms.openlocfilehash: 85a2cccb18341ffee8c81430bc8490e5d3e97b41
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892075"
---
# <a name="powershell-core-on-arm"></a>ARM에서 PowerShell Core

ARM 기반 PowerShell 지원은 **.NET Core 지원 OS 수명 주기 정책** 을 기반으로 합니다.

PowerShell 7.1은 [.NET Core 3.1 지원 OS 수명 주기 정책](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md)을 기반으로 하며 다음 플랫폼을 지원합니다.

|         OS          |          버전           | 아키텍처 |          수명 주기           |
| ------------------- | -------------------------- | ------------- | ---------------------------- |
| Windows Nano Server | 버전 1803+              | Arm32         | [Windows][Windows-lifecycle] |
| Alpine Linux        | 3.10+                      | Arm64         | [Alpine][Alpine-lifecycle]   |
| Debian              | 9+                         | Arm32, Arm64  | [Debian][Debian-lifecycle]   |
| Ubuntu              | 20.10, 20.04, 18.04, 16.04 | Arm32, Arm64  | [Ubuntu][Ubuntu-lifecycle]   |

PowerShell 7.0은 [.NET Core 5.0 지원 OS 수명 주기 정책](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md)을 기반으로 하며 다음 플랫폼을 지원합니다.

|        OS         |          버전           | 아키텍처 |          수명 주기           |
| ----------------- | -------------------------- | ------------- | ---------------------------- |
| Windows 10 클라이언트 | 버전 1607+              | Arm64         | [Windows][Windows-lifecycle] |
| Alpine Linux      | 3.11+                      | Arm64         | [Alpine][Alpine-lifecycle]   |
| Debian            | 9+                         | Arm32, Arm64  | [Debian][Debian-lifecycle]   |
| Ubuntu            | 20.10, 20.04, 18.04, 16.04 | Arm32, Arm64  | [Ubuntu][Ubuntu-lifecycle]   |

[Windows-lifecycle]: https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet
[Alpine-lifecycle]: https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases
[Debian-lifecycle]: https://wiki.debian.org/DebianReleases
[Ubuntu-lifecycle]: https://wiki.ubuntu.com/Releases

설치 지침은 다음 문서를 참조하세요.

- [ARM에서 Windows 10](installing-powershell-core-on-windows.md#installing-the-zip-package)
- [Windows 10 IoT Enterprise](installing-powershell-core-on-windows.md#deploying-on-windows-10-iot-enterprise)
- [Windows 10 IoT Core](installing-powershell-core-on-windows.md#deploying-on-windows-10-iot-core)
- [Raspbian](installing-powershell-core-on-linux.md#raspbian)
