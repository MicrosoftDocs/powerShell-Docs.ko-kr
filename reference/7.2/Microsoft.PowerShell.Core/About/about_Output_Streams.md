---
description: PowerShell에서 출력 스트림의 가용성 및 용도에 대해 설명 합니다.
Locale: en-US
ms.date: 10/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_output_streams?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Output_Streams
ms.openlocfilehash: 1dd6424ea14aa241b084a0a2c97a7e9bf6927518
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601271"
---
# <a name="about-output-streams"></a>출력 스트림 정보

## <a name="short-description"></a>간단한 설명
PowerShell에서 출력 스트림의 가용성 및 용도에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

PowerShell은 여러 출력 스트림을 제공 합니다. 스트림은 다양 한 유형의 메시지에 대 한 채널을 제공 합니다. 연결 된 cmdlet 또는 리디렉션을 사용 하 여 이러한 스트림에 쓸 수 있습니다. 자세한 내용은 [about_Redirection](about_Redirection.md)를 참조 하세요.

PowerShell에서 지 원하는 출력 스트림은 다음과 같습니다.

| 스트림 # |      설명       | 에 도입 됨  |    쓰기 Cmdlet     |
| -------- | ---------------------- | -------------- | ------------------- |
| 1        | **성공** 스트림     | PowerShell 2.0 | `Write-Output`      |
| 2        | **오류** 스트림       | PowerShell 2.0 | `Write-Error`       |
| 3        | **경고** 스트림     | PowerShell 3.0 | `Write-Warning`     |
| 4        | **자세한 정보** 스트림     | PowerShell 3.0 | `Write-Verbose`     |
| 5        | **디버그** 스트림       | PowerShell 3.0 | `Write-Debug`       |
| 6        | **정보** 스트림 | PowerShell 5.0 | `Write-Information` |
| 해당 없음      | **진행률** 스트림    | PowerShell 3.0 | `Write-Progress`    |

> [!NOTE]
> **진행률** 스트림은 리디렉션을 지원 하지 않습니다.

## <a name="success-stream"></a>성공 스트림

**성공** 스트림은 정상적이 고 성공적인 결과를 위한 기본 스트림입니다.
Cmdlet을 사용 `Write-Output` 하 여이 스트림에 개체를 명시적으로 씁니다. 이 스트림은 PowerShell 파이프라인을 통해 개체를 전달 하는 데 사용 됩니다. **성공** 스트림은 네이티브 응용 프로그램에 대 한 **stdout** 스트림에 연결 됩니다.

## <a name="error-stream"></a>오류 스트림

오류 **스트림은 오류** 결과의 기본 스트림입니다. Cmdlet을 사용 `Write-Error` 하 여이 스트림에 명시적으로 씁니다. **오류** 스트림은 네이티브 응용 프로그램에 대 한 **stderr** 스트림에 연결 됩니다. 대부분의 경우 이러한 오류는 실행 파이프라인을 종료할 수 있습니다. 이 스트림에 기록 된 오류에도 `$Error` 자동 변수가 추가 됩니다. 자세한 내용은 [about_Automatic_Variables](about_Automatic_Variables.md)를 참조 하세요.

## <a name="warning-stream"></a>경고 스트림

**경고** 스트림은 **오류 스트림에 기록 된 오류 보다** 심각 하지 않은 오류 조건에 대 한 것입니다. 정상적인 조건에서 이러한 경고는 실행을 종료 하지 않습니다. 경고는 자동 변수에 기록 되지 않습니다 `$Error` . Cmdlet을 사용 `Write-Warning` 하 여이 스트림에 명시적으로 씁니다.

## <a name="verbose-stream"></a>자세한 정보 표시 스트림

**자세한 정보** 표시 스트림은 대화형으로 또는 스크립트에서 실행 될 때 사용자가 명령 문제를 해결 하는 데 도움이 되는 메시지를 위한 것입니다. Cmdlet을 사용 `Write-Verbose` 하 여이 스트림에 메시지를 명시적으로 씁니다. 많은 cmdlet은 cmdlet의 내부 기능을 이해 하는 데 유용한 자세한 정보 출력을 제공 합니다. 자세한 정보 메시지는 일반 매개 변수를 사용 하는 경우에만 출력 됩니다 `-Verbose` . 자세한 내용은 [about_CommonParameters](about_CommonParameters.md)를 참조하세요.

## <a name="debug-stream"></a>디버그 스트림

**디버그** 스트림은 코드가 실패 한 이유를 스크립터가 이해 하는 데 도움이 되는 메시지에 사용 됩니다. Cmdlet을 사용 `Write-Debug` 하 여이 스트림에 명시적으로 씁니다. 디버그 메시지는 일반 매개 변수를 사용 하는 경우에만 출력 됩니다 `-Debug` . 자세한 내용은 [about_CommonParameters](about_CommonParameters.md)를 참조하세요.

디버그 메시지는 최종 사용자 보다 많은 스크립트 및 cmdlet 개발자를 위한 것입니다. 이러한 디버그 메시지는 심층 문제 해결에 필요한 내부 세부 정보를 포함할 수 있습니다.

## <a name="information-stream"></a>정보 스트림

**정보** 스트림은 사용자가 스크립트가 수행 하는 작업을 이해 하는 데 도움이 되는 메시지를 제공 하기 위한 것입니다. 개발자가 PowerShell을 통해 정보를 전달 하는 데 사용 되는 추가 스트림으로도 사용할 수 있습니다. 개발자는 스트림 데이터에 태그를 지정 하 고 해당 스트림에 대해 특정 처리를 수행할 수 있습니다. Cmdlet을 사용 `Write-Information` 하 여이 스트림에 명시적으로 씁니다.

## <a name="progress-stream"></a>진행률 스트림

**진행률** 스트림은 더 오래 실행 되는 명령 및 스크립트에서 진행률을 전달 하는 메시지에 사용 됩니다. Cmdlet을 사용 `Write-Progress` 하 여이 스트림에 메시지를 명시적으로 씁니다. **진행률** 스트림은 리디렉션을 지원 하지 않습니다.

## <a name="see-also"></a>참고 항목

- [Write-Debug](xref:Microsoft.PowerShell.Utility.Write-Debug)
- [Write-Error](xref:Microsoft.PowerShell.Utility.Write-Error)
- [Write-Host](xref:Microsoft.PowerShell.Utility.Write-Host)
- [Write-Information](xref:Microsoft.PowerShell.Utility.Write-Information)
- [Write-Output](xref:Microsoft.PowerShell.Utility.Write-Output)
- [Write-Progress](xref:Microsoft.PowerShell.Utility.Write-Progress)
- [Write-Verbose](xref:Microsoft.PowerShell.Utility.Write-Verbose)
- [Write-Warning](xref:Microsoft.PowerShell.Utility.Write-Warning)
- [about_CommonParameters](about_CommonParameters.md)
- [about_Redirection](about_Redirection.md)
