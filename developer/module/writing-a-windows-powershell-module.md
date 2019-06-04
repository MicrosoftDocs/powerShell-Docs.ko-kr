---
title: Windows PowerShell 모듈 작성 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bfbccc5b-2b2b-432a-a971-9f8ab503cdc3
caps.latest.revision: 17
ms.openlocfilehash: 0b7263ea19745e902fff04b993933e443d4d6333
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229354"
---
# <a name="writing-a-windows-powershell-module"></a>Windows PowerShell 모듈 작성

이 문서는 관리자, 스크립트 개발자 및 패키지 및 해당 Windows PowerShell cmdlet을 배포 해야 하는 cmdlet 개발자를 위해 작성 되었습니다. Windows PowerShell 모듈을 사용 하 여 패키지 수 있으며 컴파일된 언어를 사용 하지 않고 Windows PowerShell 솔루션을 배포할 수 있습니다.

Windows PowerShell 모듈을 사용 하면 파티션 수, 구성 및 다시 사용할 수 있는 자체 포함된 단위를 Windows PowerShell 코드를 추상화 합니다. 이러한 재사용 가능한 단위를 사용 하 여 다른 사용자와 직접 모듈을 쉽게 공유할 수 있습니다. 스크립트 개발자 인 경우 사용자 지정 스크립트 기반 응용 프로그램을 만들 뿐만 아니라 타사 모듈을 다시 패키지도 있습니다. 모듈, Perl, Python 등 다른 스크립팅 언어로 모듈을 유사한 다시 패키지 하 고 여러 구성 요소를 추상화할 수의 추가 혜택을 사용 하 여 다시 사용할 수 있는, 재배포 가능 구성 요소를 사용 하는 프로덕션이 준비 된 스크립팅 솔루션을 사용 하도록 설정 사용자 지정 솔루션을 만듭니다.

가장 기본적인에서 Windows PowerShell 모듈. psm1 파일에 저장 된 모든 유효한 Windows PowerShell 스크립트 코드에서 처리 합니다. PowerShell 모듈로 이진 cmdlet 어셈블리도 자동으로 처리 합니다. 그러나 전체 솔루션을 함께 번들로 묶는 모듈 (또는 보다 구체적으로, 모듈 매니페스트)도 사용할 수 있습니다. 다음 시나리오는 Windows PowerShell 모듈에 대 한 일반적인 용도 설명 합니다.

### <a name="libraries"></a>라이브러리

패키지 및 일반적인 작업을 수행 하는 함수의 응집성 라이브러리 배포 모듈을 사용할 수 있습니다. 일반적으로 이러한 함수 중 이름에 사용 되는 일반적인 작업을 반영 하는 하나 이상의 명사를 공유 합니다. 이러한 함수는 public 및 private 멤버를가지고 수.NET Framework 클래스와 유사 수도 있습니다. 예를 들어, 라이브러리 파일 전송에 대 한 일련의 함수를 포함할 수 있습니다. 이 경우 일반적인 작업을 반영 명사 "file." 수 있습니다.

### <a name="configuration"></a>구성

모듈은 특정 cmdlet, 공급자, 함수 및 변수를 추가 하 여 사용자 환경에 맞게 사용할 수 있습니다.

### <a name="compiled-code-development-and-distribution"></a>컴파일된 코드 개발 및 배포

Cmdlet 및 공급자 개발자는 테스트 하 고 스냅인을 만들 필요 없이 컴파일된 코드를 배포 하려면 모듈을 사용할 수 있습니다. 모듈로 (이진 모듈) 컴파일된 코드를 포함 하는 어셈블리를 만들고 스냅인을 등록할 필요 없이 가져올 수 있습니다.

## <a name="see-also"></a>참고 항목

[Windows PowerShell 모듈 이해](./understanding-a-windows-powershell-module.md)

[PowerShell 스크립트 모듈을 작성 하는 방법](./how-to-write-a-powershell-script-module.md)

[PowerShell 이진 모듈을 작성 하는 방법](./how-to-write-a-powershell-binary-module.md)

[PowerShell 모듈 매니페스트를 작성 하는 방법](how-to-write-a-powershell-module-manifest.md)

[PSModulePath 설치 경로 수정](./modifying-the-psmodulepath-installation-path.md)

[PowerShell 모듈 가져오기](./importing-a-powershell-module.md)

[PowerShell 모듈 설치](./installing-a-powershell-module.md)
