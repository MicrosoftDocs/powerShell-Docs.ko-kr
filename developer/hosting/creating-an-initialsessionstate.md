---
title: 만들기는 InitialSessionState | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ae707db-52e0-408c-87fa-b35c42eaaab1
caps.latest.revision: 5
ms.openlocfilehash: 3a7c47487b632d00643fce0aa082e0dc9a9bb626
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057997"
---
# <a name="creating-an-initialsessionstate"></a>InitialSessionState 만들기

Runspace에 Windows PowerShell 명령을 실행합니다. 응용 프로그램에서 Windows PowerShell 호스트를 만들어야 합니다는 [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) 개체입니다. 모든 runspace에는 [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 개체가 연결 되어 있습니다. 합니다 [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 등 명령, 변수 및 모듈은 해당 runspace에 대 한 사용 가능한 runspace의 특성을 지정 합니다.

## <a name="create-a-default-initialsessionstate"></a>InitialSessionState 기본값 만들기

 합니다 [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault)하 고 [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) 메서드를 사용할 수 있습니다 만들려는 [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 개체입니다. [System.Management.Automation.Runspaces.Initialsessionstate.Createdefault*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault) InitialSessionState를 로드 하는 동안 모든 기본 제공 명령을 사용 하 여 만듭니다 [ System.Management.Automation.Runspaces.Initialsessionstate.Createdefault2*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) (Microsoft.PowerShell.Core 모듈에서 명령 Windows PowerShell을 호스트 하는 데 필요한 명령만 로드 합니다.

 호스트 응용 프로그램에서 사용할 수 있는 명령을 제한 하려는 경우 제한 된 runspace를 만드는 해야 합니다. 정보를 제한 된 runspace 만들기를 참조 하십시오.

 다음 코드에는 InitialSessionState 만들기, runspace에 할당, 해당 runspace에서 파이프라인에 명령을 추가 및 명령을 호출 하는 방법을 보여 줍니다. 추가한 명령을 호출 하는 방법에 대 한 자세한 내용은 명령을 호출 하는 추가 참조 하세요.

```csharp

namespace SampleHost
{
  using System;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;

  class HostP4b
  {
    static void Main(string[] args)
    {
      // Call the InitialSessionState.CreateDefault method to create
      // an empty InitialSessionState object, and then add the
      // elements that will be available when the runspace is opened.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      SessionStateVariableEntry var1 = new
          SessionStateVariableEntry("test1",
                                    "MyVar1",
                                    "Initial session state MyVar1 test");
      iss.Variables.Add(var1);

      SessionStateVariableEntry var2 = new
          SessionStateVariableEntry("test2",
                                    "MyVar2",
                                    "Initial session state MyVar2 test");
      iss.Variables.Add(var2);

      // Call the RunspaceFactory.CreateRunspace(InitialSessionState)
      // method to create the runspace where the pipeline is run.
      Runspace rs = RunspaceFactory.CreateRunspace(iss);
      rs.Open();

      // Call the PowerShell.Create() method to create the PowerShell
      // object,and then specify the runspace and commands to the pipeline.
      // and  create the command pipeline.
      PowerShell ps = PowerShell.Create();
      ps.Runspace = rs;
      ps.AddCommand("Get-Variable");
      ps.AddArgument("test*");

      Console.WriteLine("Variable             Value");
      Console.WriteLine("--------------------------");

      // Call the PowerShell.Invoke() method to run
      // the pipeline synchronously.
        foreach (PSObject result in ps.Invoke())
        {
          Console.WriteLine("{0,-20}{1}",
                  result.Members["Name"].Value,
                  result.Members["Value"].Value);
        } // End foreach.

        // Close the runspace to free resources.
        rs.Close();

    } // End Main.
  } // End SampleHost.
}
```

## <a name="see-also"></a>참고 항목

 [제한 된 runspace 만들기](./creating-a-constrained-runspace.md)
