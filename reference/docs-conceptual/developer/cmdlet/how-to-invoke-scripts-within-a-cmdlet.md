---
title: Cmdlet에서 스크립트를 호출 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc0bc6ce-48a5-4d9c-927e-636bca743e9f
caps.latest.revision: 9
ms.openlocfilehash: 7dcb8bc20ab56225764854f9dc6fdfd858ed7451
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364412"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a>Cmdlet 내에서 스크립트를 호출하는 방법

이 예제에서는 cmdlet에 제공 된 스크립트를 호출 하는 방법을 보여 줍니다. 이 스크립트는 cmdlet에 의해 실행 되며 해당 결과는 cmdlet에 [system.object](/dotnet/api/System.Management.Automation.PSObject) 로 반환 됩니다.

## <a name="to-invoke-a-script-block"></a>스크립트 블록을 호출 하려면

1. 명령은 스크립트 블록이 cmdlet에 제공 되었는지 확인 합니다. 스크립트 블록을 제공한 경우 명령은 필요한 매개 변수를 사용 하 여 스크립트 블록을 호출 합니다.

    ```csharp
    if (script != null)
    {
      WriteDebug("Executing script block.");

      // Invoke the script block with the required arguments.
      Collection<PSObject> PSObjects =
                     script.Invoke(
                                   line,
                                   simpleMatch,
                                   caseSensitive
                                  );
    ```

2. 그런 다음 스크립트는 [system.object](/dotnet/api/System.Management.Automation.PSObject) 의 반환 된 컬렉션을 반복 하 여 필요한 작업을 수행 합니다.

    ```c
    foreach (PSObject psObject in psObjects)
    {
      if (LanguagePrimitives.IsTrue(psObject))
      {
        result = new MatchInfo();
        result.Line = line;
        result.IgnoreCase = !caseSensitive;

        break;
      }
    }

    ```

## <a name="see-also"></a>참고 항목

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)
