---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: 구성의 조건문 및 루프
ms.openlocfilehash: 0073d94d28afbb45bb635442129a6cddde4c805a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683143"
---
# <a name="conditional-statements-and-loops-in-configurations"></a>구성의 조건문 및 루프

할 수 있습니다 하 [구성을](configurations.md) PowerShell 흐름 제어 키워드를 사용 하 여 더 동적입니다. 이 문서는 구성을 보다 동적인 있도록 조건문 및 루프를 사용 하는 방법을 보여드리겠습니다를 보여 줍니다. 결합 조건부 및 사용 하 여 루프 [매개 변수](add-parameters-to-a-configuration.md) 하 고 [구성 데이터](configData.md) 구성을 컴파일할 때 더 많은 유연성과 제어 허용 합니다.

함수 또는 스크립트 블록 처럼 구성 내에서 모든 PowerShell 언어를 사용할 수 있습니다. "Mof" 파일을 컴파일하는 데 구성을 호출 하는 경우에 사용 하는 문은 확인 됩니다. 아래 예제에서는 개념을 설명 하는 간단한 시나리오를 보여 줍니다. 매개 변수 및 구성 데이터를 사용 하 여 더 자주 사용 하 여 루프가 하는 조건입니다.

이 간단한 예제는 **서비스** 리소스 블록의 현재 상태를 유지 관리 하는 ".mof" 파일을 생성 하려면 컴파일 시간에 서비스의 현재 상태를 검색 합니다.

> [!NOTE]
> 동적 리소스 블록을 사용 하 여 Intellisense의 효과 선점 됩니다. PowerShell 파서를 지정 된 값은 허용 되는 구성이 컴파일될 때까지 확인할 수 없습니다.

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

또한 만들 수 있습니다는 **서비스** 차단 현재 컴퓨터의 모든 서비스에 대 한 리소스를 사용 하 여를 `foreach` 루프.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Foreach ($service in $(Get-Service))
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

Online을 사용 하 여 간단한 컴퓨터용 구성만 만들 수 있습니다 `if` 문입니다.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    Foreach ($computer in @('Server01', 'Server02', 'Server03'))
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
> 위 예 참조는 현재 컴퓨터 동적 리소스 블록입니다. 컴퓨터 구성에서 제작 하는 것에이 예에서는 대상 노드가 없습니다.

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a>요약

요약 하자면, 구성 내에서 모든 PowerShell 언어를 사용할 수 있습니다.

이 등이 포함 됩니다.

- 사용자 지정 개체
- 해시 테이블
- 문자열 조작
- 원격
- WMI 및 CIM
- Active Directory 개체
- 추가...

구성에 정의 된 모든 PowerShell 코드를 컴파일 시간에 평가 되지만 구성을 포함 하는 스크립트에서 코드를 배치할 수도 있습니다. 구성 블록 외부에서 코드 구성을 가져올 때 실행 됩니다.

## <a name="see-also"></a>참고 항목

- [구성에 매개 변수 추가](add-parameters-to-a-configuration.md)
- [구성과 구성 데이터 분리](configData.md)
