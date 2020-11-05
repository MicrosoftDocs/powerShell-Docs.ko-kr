---
ms.date: 06/12/2017
title: 스크립트 추적 및 로깅
description: Windows PowerShell 5.x는 스크립트 블록 실행을 감사할 수 있는 새 이벤트 로깅을 추가합니다.
ms.openlocfilehash: d47fb6fdd1ee4b9372fab7b81e6dc94fb45b8880
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663120"
---
# <a name="script-tracing-and-logging"></a>스크립트 추적 및 로깅

PowerShell에는 cmdlet의 호출을 기록하는 **LogPipelineExecutionDetails** 그룹 정책 설정이 이미 있지만 PowerShell의 스크립트 언어는 기록 및 감사할 수 있는 여러 기능을 제공합니다. 새로운 세부 스크립트 추적 기능을 사용하여 시스템에서 PowerShell 스크립트 작업을 자세히 추적하고 분석할 수 있습니다. 세부 스크립트 추적을 사용하도록 설정하면 PowerShell에서 모든 스크립트 블록을 ETW 이벤트 로그 **Microsoft-Windows-PowerShell/Operational** 에 기록합니다. 스크립트 블록에서 다른 스크립트 블록을 만드는 경우(예: `Invoke-Expression` 호출) 호출된 스크립트 블록도 기록됩니다.

로깅은 **관리 템플릿** -> **Windows 구성 요소** -> **Windows PowerShell** 에서 **PowerShell 스크립트 블록 로깅 켜기** 그룹 정책 설정을 통해 사용할 수 있습니다.

이벤트는 다음과 같습니다.

| 채널 |                               작동                               |
| ------- | ----------------------------------------------------------------------- |
| Level   | 자세히                                                                 |
| Opcode  | 생성                                                                  |
| Task    | CommandStart                                                            |
| 키워드 | Runspace                                                                |
| EventId | Engine_ScriptBlockCompiled(0x1008 = 4104)                              |
| 메시지 | Scriptblock 텍스트를 만드는 중(%1/%2): </br> %3 </br> ScriptBlock ID: %4 |

메시지에 포함된 텍스트는 컴파일된 스크립트 블록의 범위입니다. ID는 스크립트 블록의 사용 기간 동안 유지되는 GUID입니다.

자세한 정보 로깅을 사용하도록 설정하면 기능에서 시작 및 끝 표식을 기록합니다.

| 채널 |                                 작동                                |
| ------- | -------------------------------------------------------------------------- |
| Level   | 자세히                                                                    |
| Opcode  | 열기/닫기                                                               |
| Task    | CommandStart/CommandStop                                                 |
| 키워드 | Runspace                                                                   |
| EventId | ScriptBlock\_Invoke\_Start\_Detail(0x1009 = 4105) / </br> ScriptBlock\_Invoke\_Complete\_Detail(0x100A = 4106) |
| 메시지 | ScriptBlock ID 호출을 시작/완료했습니다. %1 </br> Runspace ID: %2 |

ID는 이벤트 ID 0x1008과 상호 관련될 수 있는 스크립트 블록을 나타내는 GUID이고 Runspace ID는 이 스크립트 블록이 실행된 runspace를 나타냅니다.

호출 메시지의 백분율 기호는 구조화된 ETW 속성을 나타냅니다. 이러한 속성은 메시지 테스트에서 실제 값으로 대체되지만 액세스할 수 있는 보다 강력한 방법은 Get-WinEvent cmdlet을 사용하여 메시지를 검색한 다음 메시지의 **속성** 배열을 사용하는 것입니다.

다음은 이 기능을 사용하여 스크립트를 암호화하여 난독 처리하려는 악의적인 시도를 해결하는 방법의 예입니다.

```powershell
## Malware
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)

    ## XOR "encryption"
    $xorKey = 0x42
    for($counter = 0; $counter -lt $bytes.Length; $counter++)
    {
        $bytes[$counter] = $bytes[$counter] -bxor $xorKey
    }
    [System.Text.Encoding]::Unicode.GetString($bytes)
}

$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
Invoke-Expression $decrypted
```

이 명령을 실행하면 다음과 같은 로그 항목이 생성됩니다.

```Output
Compiling Scriptblock text (1 of 1):
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)
    ## XOR "encryption"
    $xorKey = 0x42
    for($counter = 0; $counter -lt $bytes.Length; $counter++)
    {
        $bytes[$counter] = $bytes[$counter] -bxor $xorKey
    }
    [System.Text.Encoding]::Unicode.GetString($bytes)

}
ScriptBlock ID: ad8ae740-1f33-42aa-8dfc-1314411877e3

Compiling Scriptblock text (1 of 1):
$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
ScriptBlock ID: ba11c155-d34c-4004-88e3-6502ecb50f52

Compiling Scriptblock text (1 of 1):
Invoke-Expression $decrypted
ScriptBlock ID: 856c01ca-85d7-4989-b47f-e6a09ee4eeb3

Compiling Scriptblock text (1 of 1):
Write-Host 'Pwnd'
ScriptBlock ID: 5e618414-4e77-48e3-8f65-9a863f54b4c8
```

스크립트 블록 길이가 단일 이벤트의 용량을 초과하는 경우 PowerShell이 스크립트를 여러 부분으로 나눕니다. 다음은 로그 메시지에서 스크립트를 다시 결합하는 샘플 코드입니다.

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } |
  Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

보존 버퍼가 제한된 모든 로깅 시스템과 마찬가지로 이 인프라를 공격하는 한 가지 방법은 가상 이벤트로 로그를 넘쳐나게 하여 이전 증거를 숨기는 것입니다. 이 공격으로부터 보호하려면 특정 형식의 이벤트 로그 컬렉션에서 Windows 이벤트 전달을 설정해야 합니다. 자세한 내용은 [Spotting the Adversary with Windows Event Log Monitoring](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm)(Windows 이벤트 로그 모니터링을 통해 악의적 사용자 포착)을 참조하세요.
