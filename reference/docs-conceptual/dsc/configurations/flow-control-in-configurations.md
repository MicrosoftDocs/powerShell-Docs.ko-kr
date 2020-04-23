---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: 구성의 조건문 및 루프
ms.openlocfilehash: 86f75be4a3d1c1760dd6269335431e8ab9fd8d09
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736899"
---
# <a name="conditional-statements-and-loops-in-a-configuration"></a>구성의 조건문 및 루프

PowerShell 흐름 제어 키워드를 사용하여 더 동적인 [구성](configurations.md)을 만들 수 있습니다. 이 문서에서는 조건문 및 루프를 사용하여 더 동적인 `Configuration`을 만드는 방법을 보여 줍니다. 조건문 및 루프를 [매개 변수](add-parameters-to-a-configuration.md) 및 [구성 데이터](configData.md)와 결합하면 `Configuration`을 컴파일할 때 유연성을 높이고 제어를 강화할 수 있습니다.

함수 및 스크립트 블록처럼, `Configuration` 내에서 모든 PowerShell 언어를 사용할 수 있습니다.
사용하는 문은 `Configuration`을 호출하여 `.mof` 파일을 컴파일할 때만 평가됩니다. 아래 예제에서는 개념을 설명하는 시나리오를 보여 줍니다. 조건문 및 루프는 매개 변수 및 구성 데이터에서 더 자주 사용됩니다.

이 간단한 예제에서 **Service** 리소스 블록은 컴파일 시간에 서비스의 현재 상태를 검색하여 현재 상태를 유지 관리하는 `.mof` 파일을 생성합니다.

> [!NOTE]
> 동적 리소스 블록을 사용하면 IntelliSense의 효과를 대체할 수 있습니다. PowerShell 파서는 `Configuration`이 컴파일될 때까지 지정된 값이 허용 가능한지 확인할 수 없습니다.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Service Spooler
        {
            Name = "Spooler"
            State = $(Get-Service -Name 'spooler').Status
            StartType = $(Get-Service -Name 'spooler').StartType
        }
    }
}
```

또한 **루프를 사용하여 현재 머신에 있는 모든 서비스의**Service`foreach` 리소스 블록을 만들 수 있습니다.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        foreach ($service in $(Get-Service))
        {
            Service $service.Name
            {
                Name = $service.Name
                State = $service.Status
                StartType = $service.StartType
            }
        }
    }
}
```

`Configuration` 문을 사용하여 온라인 상태인 컴퓨터에 대해서만 `if`을 만들 수도 있습니다.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    foreach ($computer in @('Server01', 'Server02', 'Server03'))
    {
        if (Test-Connection -ComputerName $computer)
        {
            Node $computer
            {
                Service "Spooler"
                {
                    Name = "Spooler"
                    State = "Started"
                }
            }
        }
    }
}
```

> [!NOTE]
> 위 예제의 동적 리소스 블록은 현재 머신을 참조합니다. 이 경우 현재 머신은 대상 노드가 아니라 `Configuration`을 작성 중인 머신입니다.

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a>요약

요약하면, `Configuration` 내에서 모든 PowerShell 언어를 사용할 수 있습니다.

여기에는 다음과 같은 항목이 포함됩니다.

- 사용자 지정 개체
- 해시 테이블
- 문자열 조작
- 원격
- WMI 및 CIM
- ActiveDirectory 개체
- 추가...

`Configuration`에 정의된 모든 PowerShell 코드는 컴파일 시간에 평가되지만, `Configuration`을 포함하는 스크립트에 코드를 넣을 수도 있습니다. `Configuration` 블록 외부의 코드는 `Configuration`을 가져올 때 실행됩니다.

## <a name="see-also"></a>참고 항목

- [구성에 매개 변수 추가](add-parameters-to-a-configuration.md)
- [구성과 구성 데이터 분리](configData.md)
