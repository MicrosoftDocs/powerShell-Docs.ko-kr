---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: Just Enough Administration 개요
ms.openlocfilehash: 4b74e5be9558810748a8844a325c8213e1b3ebc9
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726659"
---
# <a name="just-enough-administration"></a>JEA(Just Enough Administration)

JEA(Just Enough Administration)는 PowerShell에서 관리하는 모든 항목에 대한 위임된 관리를 가능하게 하는 보안 기술입니다. JEA를 사용하면 다음이 가능합니다.

- **머신의 관리자 수 감소**: 일반 사용자를 대신하여 권한 있는 작업을 수행하는 가상 계정 또는 그룹 관리 서비스 계정을 사용합니다.
- **사용자가 수행할 수 있는 작업 제한**: 사용자가 실행할 수 있는 cmdlet, 함수 및 외부 명령을 지정합니다.
- **사용자가 수행하고 있는 작업을 보다 효과적으로 이해**: 사용자가 해당 세션 중에 실행한 명령을 정확하게 보여 주는 기록 및 로그를 사용합니다.

**JEA가 중요한 이유는 무엇인가요?**

서버를 관리하는 데 사용된 높은 권한이 있는 계정은 심각한 보안 위험을 일으킵니다. 공격자가 이러한 계정 중 하나를 손상시키면 조직 전체에서 [lateral attacks](https://aka.ms/pth)(측면 공격)를 시작할 수 있습니다. 손상된 각 계정은 더 많은 계정 및 리소스에 대한 액세스 권한을 공격자에게 부여하여 회사 기밀을 훔치거나 서비스 거부 공격을 시작하는 등을 하는데 한 걸음 더 다가서게 할 수 있습니다.

관리자 권한을 제거하거하는 것이 항상 쉬운 것은 아닙니다. Active Directory 도메인 컨트롤러와 같은 컴퓨터에 DNS 역할이 설치되어 있는 일반적인 시나리오를 생각해 봅니다. DNS 관리자는 DNS 서버 문제를 해결할 수 있는 로컬 관리자 권한이 필요합니다. 하지만 그렇게 하려면 높은 권한을 가진 **Domain Admins** 보안 그룹의 구성원이어야 합니다. 이 접근 방식을 통해 DNS 관리자는 효과적으로 전체 도메인을 제어하고 해당 컴퓨터의 모든 리소스에 액세스할 수 있습니다.

JEA는 **최소 권한**의 원칙을 통해 이 문제를 해결합니다. JEA를 사용하면 작업을 수행하는 데 필요한 PowerShell 명령에 대해서만 액세스 권한을 부여하는 DNS 관리자용 관리 엔드포인트를 구성할 수 있습니다. 즉, 의도치 않게 Active Directory에 대한 권한이나 파일 시스템을 검색하거나 잠재적으로 위험한 스크립트를 실행할 수 있는 권한을 부여하는 일 없이 손상된 DNS 캐시를 복구하거나 DNS 서버를 다시 시작하는 데 적합한 액세스 권한을 제공할 수 있습니다. 더 좋은 점은 JEA 세션이 임시 권한 있는 가상 계정을 사용하도록 구성된 경우 DNS 관리자는 **비관리자** 자격 증명을 사용하여 서버에 연결하고 일반적으로 관리자 권한이 필요한 명령을 계속 실행할 수 있다는 것입니다. JEA를 사용하면 광범위한 권한이 있는 로컬/도메인 관리자 역할에서 사용자를 제거하고 각 머신에서 수행할 수 있는 작업을 신중하게 제어할 수 있습니다.

## <a name="next-steps"></a>다음 단계

JEA를 사용하기 위한 요구 사항에 대한 자세한 내용은 [필수 구성 요소](prerequisites.md) 문서를 참조하세요.

## <a name="samples-and-dsc-resource"></a>샘플 및 DSC 리소스

샘플 JEA 구성 및 JEA DSC 리소스는 [JEA GitHub 리포지토리](https://github.com/PowerShell/JEA)에서 찾을 수 있습니다.
