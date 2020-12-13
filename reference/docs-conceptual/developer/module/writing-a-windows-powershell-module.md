---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell 모듈 작성
description: Windows PowerShell 모듈 작성
ms.openlocfilehash: 307241f0fb4d12c1a5cbd651a0ae4d5303098b27
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659427"
---
# <a name="writing-a-windows-powershell-module"></a>Windows PowerShell 모듈 작성

이 문서는 Windows PowerShell cmdlet을 패키지 하 고 배포 해야 하는 관리자, 스크립트 개발자 및 cmdlet 개발자를 위해 작성 되었습니다. Windows PowerShell 모듈을 사용 하 여 컴파일된 언어를 사용 하지 않고 Windows PowerShell 솔루션을 패키지 하 고 배포할 수 있습니다.

Windows PowerShell 모듈을 사용 하 여 Windows PowerShell 코드를 독립적이 고 재사용 가능한 단위로 분할, 구성 및 추상화할 수 있습니다. 이러한 재사용 가능한 단위를 사용 하면 모듈을 다른 사용자와 직접 쉽게 공유할 수 있습니다. 스크립트 개발자 인 경우 타사 모듈을 다시 패키지 하 여 사용자 지정 스크립트 기반 응용 프로그램을 만들 수도 있습니다. Perl 및 Python과 같은 다른 스크립팅 언어의 모듈과 유사한 모듈은 재사용 가능한 재배포 가능 구성 요소를 사용 하는 프로덕션 지원 스크립팅 솔루션을 지원 하며, 여러 구성 요소를 다시 패키징 하 고 추상화 하 여 사용자 지정 솔루션을 만들 수 있습니다.

가장 기본적인 Windows PowerShell은 .psm1 파일에 저장 된 모든 유효한 Windows PowerShell 스크립트 코드를 모듈로 처리 합니다. 또한 PowerShell은 모든 이진 cmdlet 어셈블리를 모듈로 자동으로 처리 합니다. 그러나 모듈 (또는 구체적으로 모듈 매니페스트)을 사용 하 여 전체 솔루션을 함께 묶을 수도 있습니다. 다음 시나리오는 Windows PowerShell 모듈의 일반적인 용도를 설명 합니다.

### <a name="libraries"></a>라이브러리

모듈을 사용 하 여 일반적인 작업을 수행 하는 함수에 대 한 긴밀 한 라이브러리를 패키지 하 고 배포할 수 있습니다. 일반적으로 이러한 함수의 이름은 일반적으로 사용 되는 작업을 반영 하는 하나 이상의 명사를 공유 합니다. 이러한 함수는 public 및 private 멤버를 가질 수 있다는 점에서 .NET Framework 클래스와 유사할 수도 있습니다. 예를 들어 라이브러리에 파일 전송에 대 한 함수 집합이 포함 될 수 있습니다. 이 경우 공통 작업을 반영 하는 명사는 "file" 일 수 있습니다.

### <a name="configuration"></a>Configuration

모듈은 특정 cmdlet, 공급자, 함수 및 변수를 추가 하 여 환경을 사용자 지정 하는 데 사용할 수 있습니다.

### <a name="compiled-code-development-and-distribution"></a>컴파일된 코드 개발 및 배포

Cmdlet 및 공급자 개발자는 스냅인을 만들 필요 없이 모듈을 사용 하 여 컴파일된 코드를 테스트 하 고 배포할 수 있습니다. 스냅인을 만들고 등록할 필요 없이 컴파일된 코드를 포함 하는 어셈블리를 모듈 (이진 모듈)로 가져올 수 있습니다.

## <a name="see-also"></a>참고 항목

[Windows PowerShell 모듈 이해](./understanding-a-windows-powershell-module.md)

[PowerShell 스크립트 모듈을 작성하는 방법](./how-to-write-a-powershell-script-module.md)

[PowerShell 이진 모듈을 작성하는 방법](./how-to-write-a-powershell-binary-module.md)

[PowerShell 모듈 매니페스트를 작성하는 방법](how-to-write-a-powershell-module-manifest.md)

[PSModulePath 설치 경로 수정](./modifying-the-psmodulepath-installation-path.md)

[PowerShell 모듈 가져오기](./importing-a-powershell-module.md)

[PowerShell 모듈 설치](./installing-a-powershell-module.md)
