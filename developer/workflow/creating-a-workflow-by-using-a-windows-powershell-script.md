---
title: Windows PowerShell 스크립트를 사용 하 여 워크플로 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: 5eb2186cbceee21f8b4a8c88b812e9c71f15e0af
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853049"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a>Windows PowerShell 스크립트를 사용하여 워크플로 만들기

Windows PowerShell 스크립트를 작성 하 여 워크플로 만들 수 있습니다. 워크플로 만들려면 스크립트의 본문 보다 먼저 워크플로 이름이 뒤 워크플로 키워드를 사용 합니다. 예:

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

다른 Windows PowerShell 명령에는 동일한 방식으로 워크플로 찾을 있습니다.

## <a name="implementing-parallel-and-sequence"></a>Parallel 및 Sequence 구현

[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) 병렬로 활동의 실행을 지원 합니다. Windows PowerShell 스크립트에서이 기능을 구현 하려면 사용 된 `parallel` 스크립트 블록 앞에 키워드입니다. 사용할 수도 있습니다는 `foreach -parallel` 병렬로 개체의 컬렉션을 반복 하는 생성 합니다. 그룹 활동을 순차적으로 병렬 블록 내에서 실행 하려면 스크립트 블록에서 활동의 해당 그룹 묶고 시퀀스 키워드를 사용 하 여 블록 앞에 야 합니다.

## <a name="joining-computers-to-a-domain"></a>컴퓨터를 도메인에 가입

다음 스크립트를 사용자 지정 컴퓨터 그룹의 도메인 상태를 확인, 이미 가입 되지 않으며 다음 상태를 다시 확인 하는 경우 도메인에 조인 하는 워크플로 만듭니다. 에 설명 된 XAML 워크플로 스크립트 버전임 [Windows PowerShell 작업을 사용 하 여 워크플로 만드는](./creating-a-workflow-with-windows-powershell-activities.md)합니다.

```powershell
workflow Join-Domain
{
    param([string[]] $ComputerName, [PSCredential] $DomainCred, [PsCredential] $MachineCred)

    foreach -parallel($Computer in $ComputerName)
    {
        sequence {
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        Add-Computer -PSComputerName $Computer -PSCredential $DomainCred
        Restart-Computer -ComputerName $Computer -Credential $MachineCred -For PowerShell -Force -Wait -PSComputerName ""
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        }
    }
 }

```