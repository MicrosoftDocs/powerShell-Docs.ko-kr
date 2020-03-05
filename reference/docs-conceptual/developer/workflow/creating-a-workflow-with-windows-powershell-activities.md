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
ms.openlocfilehash: 7d399786b9b43ee302493359d9702981045212e9
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78277470"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a>Windows PowerShell 활동을 사용하여 워크플로 만들기

Visual Studio 도구 상자에서 작업을 선택 하 고 워크플로 디자이너 창으로 끌어 Windows PowerShell 워크플로를 만들 수 있습니다. Visual Studio 도구 상자에 Windows PowerShell 활동을 추가 하는 방법에 대 한 자세한 내용은 [Visual Studio 도구 상자에 Windows Powershell 활동 추가](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)를 참조 하세요.

다음 절차에서는 사용자 지정 컴퓨터 그룹의 도메인 상태를 확인 하 고 도메인에 가입 되어 있지 않은 경우이를 도메인에 조인 하는 워크플로를 만들고 상태를 다시 확인 하는 방법을 설명 합니다.

### <a name="setting-up-the-project"></a>프로젝트 설정

1. [Visual Studio 도구 상자에 Windows PowerShell 활동 추가](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) 의 절차에 따라 워크플로 프로젝트를 만들고 [microsoft. powershell](/dotnet/api/Microsoft.PowerShell.Activities) 및 [microsoft.](/dotnet/api/Microsoft.PowerShell.Management.Activities) . s s e.

2. 프로젝트에 참조 어셈블리로 서 management. Automation, Microsoft. management, microsoft. management, 및 Microsoft. c r e a t. n e t. n e t. Management를 추가 합니다.

### <a name="adding-activities-to-the-workflow"></a>워크플로에 활동 추가

1. 워크플로에 **시퀀스** 활동을 추가 합니다.

2. 인수 형식이 `String[]`인 `ComputerName` 이라는 인수를 만듭니다. 이 인수는 확인 및 가입할 컴퓨터의 이름을 나타냅니다.

3. [System.object](/dotnet/api/System.Management.Automation.PSCredential)형식의 `DomainCred` 이라는 인수를 만듭니다. 이 인수는 도메인에 컴퓨터를 가입 시킬 수 있는 도메인 계정의 도메인 자격 증명을 나타냅니다.

4. [System.object](/dotnet/api/System.Management.Automation.PSCredential)형식의 `MachineCred` 이라는 인수를 만듭니다. 이 인수는 확인 및 가입할 컴퓨터의 관리자 자격 증명을 나타냅니다.

5. **Sequence** 활동 내에 **ParallelForEach** 활동을 추가 합니다. 루프에서 `ComputerName` 배열의 요소를 반복 하도록 텍스트 상자에 `comp` 및 `ComputerName`을 입력 합니다.

6. **ParallelForEach** 활동의 본문에 **시퀀스** 활동을 추가 합니다. 시퀀스의 **DisplayName** 속성을 `JoinDomain`로 설정 합니다.

7. **JoinDomain** 시퀀스에 **GetWmiObject** 활동을 추가 합니다.

8. 다음과 같이 **GetWmiObject** 활동의 속성을 편집 합니다.

   |속성|값|
   |--------------|-----------|
   |**클래스**|"Win32_ComputerSystem"|
   |**PSComputerName**|생략|
   |**유형이**|MachineCred|

9. **GetWmiObject** 활동 뒤에 **Addcomputer** 활동을 **JoinDomain** 시퀀스에 추가 합니다.

10. 다음과 같이 **Addcomputer** 활동의 속성을 편집 합니다.

    |속성|값|
    |--------------|-----------|
    |**컴퓨터 이름**|생략|
    |**DomainCredential**|DomainCred|

11. **Addcomputer** 활동 이후 **JoinDomain** 시퀀스에 **RestartComputer** 활동을 추가 합니다.

12. 다음과 같이 **RestartComputer** 활동의 속성을 편집 합니다.

    |속성|값|
    |--------------|-----------|
    |**컴퓨터 이름**|생략|
    |**자격 증명**|MachineCred|
    |**에 대 한**|Microsoft. PowerShell. WaitForServiceTypes. PowerShell|
    |**설정**|True|
    |연결 시도 간격|True|
    |PSComputerName|{""}|

13. **RestartComputer** 활동 뒤에 **JoinDomain** 시퀀스에 **GetWmiObject** 활동을 추가 합니다. 해당 속성을 이전 **GetWmiObject** 활동과 동일 하 게 편집 합니다.

    절차를 완료 하면 워크플로 디자인 창이 다음과 같이 표시 됩니다.

    workflow designer의 JoinDomain XAML ![workflow designer ![의 JOINDOMAIN xaml](media/creating-a-workflow-with-windows-powershell-activities/joindomainworkflow.png "JoinDomainWorkflow")](media/creating-a-workflow-with-windows-powershell-activities/joindomainworkflow.png)
    