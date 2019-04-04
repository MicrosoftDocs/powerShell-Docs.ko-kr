---
title: PowerShell Core 6.2의 새로운 기능
description: PowerShell Core 6.2에서 릴리스된 새로운 기능 및 변경 내용
ms.date: 03/28/2019
ms.openlocfilehash: 2224d23a244175059a705c07001e8ad8d6ab3aa0
ms.sourcegitcommit: 8dd4394cf867005a8b9ef0bb74b744c964fbc332
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/30/2019
ms.locfileid: "58750058"
---
# <a name="whats-new-in-powershell-core-62"></a>PowerShell Core 6.2의 새로운 기능

다음은 PowerShell Core 6.2에 도입된 몇 가지 새로운 주요 기능 및 변경 내용의 선택 항목입니다.

PowerShell을 더 빠르고 더 안정적으로 만들어주는 “지루한 작업”도 **많이** 있습니다(또한 아주 많은 버그 수정도)!
변경 사항의 전체 목록은 [GitHub의 changelog](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md)를 확인하세요.

다음 이름 중 일부를 호출하는 동안 이 릴리스를 가능하게 해준 [커뮤니티 기여자 모두에게](https://github.com/PowerShell/PowerShell/graphs/contributors) 감사의 말씀을 드립니다.

## <a name="engine-updates-and-fixes"></a>엔진 업데이트 및 수정

- PowerShell 원격 cmdlet 경고 메시지 사용/사용 안 함 추가([#9203][])
- `FormatTable` 원격 deserialization 재발 수정([#9116][])
- 작업 개체를 직접 반환하도록 PowerShell에 추가된 작업 기반 `async` API 업데이트([#9079][])
- `PowerShell` 유형에 5개의 `InvokeAsync` 오버로드 및 `StopAsync` 추가([#8056][]) (@KirkMunro 님 감사합니다!)

## <a name="general-cmdlet-updates-and-fixes"></a>일반 Cmdlet 업데이트 및 수정

- 일반 텍스트를 저장하여 Windows가 아닌 환경에서도 `SecureString` cmdlets을 사용하도록 설정([#9199][])
- `Send-MailMessage`에 사용되지 않는 메시지 추가([#9178][])
- WinRM이 없을 때 `localhost`에서 `Restart-Computer`가 작동하도록 수정([#9160][])
- PowerShell이 호스트될 때 `Start-Job`이 종료 오류를 throw하도록 설정([#9128][])
- `PowerShell.Native` 및 호스팅 테스트 버전 업데이트([#8983][])

## <a name="breaking-changes"></a>주요 변경 내용

-NoEnumerate 동작이 Write-Output에서 Windows PowerShell과 일치하도록 수정([#9069][]) (@vexx32 님 감사합니다!)

<!-- Link references -->
[#8056]: https://github.com/PowerShell/PowerShell/pull/8056
[#8983]: https://github.com/PowerShell/PowerShell/pull/8983
[#9069]: https://github.com/PowerShell/PowerShell/pull/9069
[#9079]: https://github.com/PowerShell/PowerShell/pull/9079
[#9116]: https://github.com/PowerShell/PowerShell/pull/9116
[#9128]: https://github.com/PowerShell/PowerShell/pull/9128
[#9160]: https://github.com/PowerShell/PowerShell/pull/9160
[#9178]: https://github.com/PowerShell/PowerShell/pull/9178
[#9199]: https://github.com/PowerShell/PowerShell/pull/9199
[#9203]: https://github.com/PowerShell/PowerShell/pull/9203
