---
title: Visual Studio 도구 상자에 Windows PowerShell 활동을 추가 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c8ef289-0659-42d1-9976-044b144201eb
caps.latest.revision: 6
ms.openlocfilehash: 2a8372d937fc3c959f7d829bb52495048423d506
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080478"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a>Visual Studio 도구 상자에 Windows PowerShell 활동 추가

워크플로 디자이너를 사용 하 여 PowerShell 워크플로 작성 하기 전에 Visual Studio 워크플로 콘솔 응용 프로그램 프로젝트 도구 상자에는 PowerShell 작업을 먼저 추가 해야 합니다. 다음 절차에는 Microsoft.PowerShell.Core.Activities 어셈블리에서 Visual Studio 도구 상자에 활동을 추가 하는 방법을 보여 줍니다.

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a>도구 상자에 Windows PowerShell 활동을 추가합니다.

1. Visual Studio에서 새 워크플로 콘솔 응용 프로그램 프로젝트를 만듭니다.

2. 에 **뷰** 메뉴에서 클릭 **도구 상자**합니다.

3. 도구 상자 내부를 마우스 오른쪽 단추로 클릭 하 고 클릭 하 여 도구 상자에서 새 탭을 추가 **추가 탭**을 고 새 탭에 "PowerShell 활동" 같은 이름을 지정 합니다.

   탭 추가 도구 상자에서 다른 도구에서 별도 PowerShell 작업을 그룹화 할 수 있습니다.

4. 새 도구 상자 탭 클릭 **항목 선택...** . 합니다 **도구 상자 항목 선택** 대화 상자가 나타납니다.

5. 에 **도구 상자 항목 선택** 대화 상자에서 클릭 합니다 **System.Activities** 탭 합니다.

6. **찾아보기**를 클릭합니다.

7. %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e 폴더로 이동한 후 Microsoft.PowerShell.Core.Activities.dll를 두 번 클릭 합니다.

8. **확인**을 클릭합니다. Microsoft.PowerShell.Core.Activities 어셈블리에서 정의 된 활동 도구 상자에서 사용할 수 있습니다.

## <a name="see-also"></a>참고 항목

[Windows PowerShell 워크플로 작성](./writing-a-windows-powershell-workflow.md)

[Windows PowerShell 작업을 사용 하 여 워크플로 만들기](./creating-a-workflow-with-windows-powershell-activities.md)