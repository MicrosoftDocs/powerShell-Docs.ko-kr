---
title: Windows PowerShell 작업을 사용 하 여 워크플로 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb55971a-4ea4-4c51-aeff-4e0bb05a51b2
caps.latest.revision: 6
ms.openlocfilehash: 98cac43698b3f537ee318cd2570b2174631665a7
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055430"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a>Windows PowerShell 활동을 사용하여 워크플로 만들기

Visual Studio 도구 상자에서 활동을 선택 하 고 워크플로 디자이너 창으로 끌어와 Windows PowerShell 워크플로 만들 수 있습니다. Visual Studio 도구 상자에 Windows PowerShell 활동 추가 대 한 자세한 내용은 [Visual Studio 도구 상자에 Windows PowerShell 활동 추가](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)합니다.

다음 절차에는 사용자 지정 컴퓨터 그룹의 도메인 상태를 확인, 이미 가입 되지 않으며 다음 상태를 다시 확인 하는 경우 도메인에 조인 하는 워크플로 만드는 방법을 설명 합니다.

### <a name="setting-up-the-project"></a>프로젝트 설정

1. 절차에 따라 [Visual Studio 도구 상자에 Windows PowerShell 작업 추가](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) 워크플로 프로젝트 만들기의 활동을 추가 하는 [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) 하고[ Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) 도구 상자에는 어셈블리입니다.

2. 참조 어셈블리와 프로젝트에 대 한 System.Management.Automation "," Microsoft.PowerShell.Activities "," System.Management "," Microsoft.PowerShell.Management.Activities, "및" Microsoft.PowerShell.Commands.Management를 추가 합니다.

### <a name="adding-activities-to-the-workflow"></a>워크플로에 활동을 추가합니다.

1. 추가 된 **시퀀스** 활동을 워크플로.

2. 명명 된 인수를 만듭니다 `ComputerName` 인수 유형으로 `String[]`입니다. 이 인수를 확인 하 고 조인 컴퓨터의 이름을 나타냅니다.

3. 명명 된 인수를 만듭니다 `DomainCred` 형식의 [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential)합니다. 이 인수는 도메인에 컴퓨터를 가입 시킬 권한이 있는 도메인 계정의 도메인 자격 증명을 나타냅니다.

4. 명명 된 인수를 만듭니다 `MachineCred` 형식의 [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential)합니다. 이 인수를 확인 하 고 조인 컴퓨터의 관리자의 자격 증명을 나타냅니다.

5. 추가 **ParallelForEach** 내 활동의 **시퀀스** 활동입니다. 입력 `comp` 하 고 `ComputerName` 에서 루프의 요소를 반복 하는 입력란을 `ComputerName` 배열입니다.

6. 추가 **시퀀스** 활동의 본문에는 **ParallelForEach** 활동입니다. 설정 된 **DisplayName** 시퀀스의 속성 `JoinDomain`합니다.

7. 추가 **GetWmiObject** 작업을 합니다 **JoinDomain** 시퀀스입니다.

8. 속성을 편집 합니다 **GetWmiObject** 같이 작업 합니다.

   |속성|Value|
   |--------------|-----------|
   |**클래스**|"Win32_ComputerSystem"|
   |**PSComputerName**|{comp}|
   |**PSCredential**|MachineCred|

9. 추가 **AddComputer** 작업을 합니다 **JoinDomain** 후 시퀀스를 **GetWmiObject** 활동입니다.

10. 속성을 편집 합니다 **AddComputer** 같이 작업 합니다.

    |속성|Value|
    |--------------|-----------|
    |**ComputerName**|{comp}|
    |**DomainCredential**|DomainCred|

11. 추가 **RestartComputer** 작업을 합니다 **JoinDomain** 후 시퀀스를 **AddComputer** 활동 합니다.

12. 속성을 편집 합니다 **RestartComputer** 같이 작업 합니다.

    |속성|Value|
    |--------------|-----------|
    |**ComputerName**|{comp}|
    |**자격 증명**|MachineCred|
    |**에 대 한**|Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell|
    |**Force**|True|
    |연결 시도 간격|True|
    |PSComputerName|{""}|

13. 추가 **GetWmiObject** 작업을 합니다 **JoinDomain** 후 시퀀스를 **RestartComputer** 활동 합니다. 이전으로 동일 하도록 해당 속성을 편집할 **GetWmiObject** 활동입니다.

    절차를 완료 한 후 워크플로 디자인 창 다음과 같아야 합니다.

    ![Workflow designer의 JoinDomain XAML](../media/joindomainworkflow.png)
    ![Workflow designer의 JoinDomain XAML](../media/joindomainworkflow.png "JoinDomainWorkflow")