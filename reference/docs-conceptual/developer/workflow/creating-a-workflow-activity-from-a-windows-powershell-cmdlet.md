---
title: Windows PowerShell Cmdlet에서 워크플로 작업 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4174e84f-d516-4aca-b418-273047dcfb07
caps.latest.revision: 7
ms.openlocfilehash: f45b5e985fa38ca4ff41707f1842ddb8b930e2b1
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557502"
---
# <a name="creating-a-workflow-activity-from-a-windows-powershell-cmdlet"></a>Windows PowerShell Cmdlet에서 워크플로 활동 만들기

모든 Windows PowerShell 모듈 또는 cmdlet을 워크플로 작업으로 패키지할 수 [있습니다 .이 클래스의](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator) 메서드를 사용 합니다. 활동을 나타내는 c # 코드를 생성 하려면 [microsoft. c](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromModuleInfo)o n. c o n. c o n. c o n. c o n [. c](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator) o [Microsoft.Powershell.Activities.Activitygenerator.Generatefromname*](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromName) n. c o n. c o n. c o n c o [n.](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromCommandInfo) 그런 다음 결과로 생성 되는 c # 코드를 프로젝트에 활동으로 추가할 수 있는 어셈블리로 컴파일할 수 있습니다.

그러면 결과 c # 코드를 다음 형식의 명령줄을 사용 하 여 프로젝트에 작업으로 추가할 수 있는 어셈블리로 컴파일할 수 있습니다.

**csc/nologo/out: AssemblyName/target: library/reference: codefile.cs/reference: Microsoft. 작업**

## <a name="example"></a>예제

다음 예제에서는 Windows PowerShell 모듈에서 활동에 대 한 c # 코드를 생성 하는 방법을 보여 줍니다.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.IO;
using System.Management.Automation;
using System.Collections.ObjectModel;
using Microsoft.PowerShell.Activities;

namespace MakeActivity
{
    class Program
    {
        static void Main(string[] args)

        {
            StreamWriter CodeFile = new StreamWriter("c:\\\\testmodule\\codefile.cs");
            Collection<PSModuleInfo> ModuleInfos = new Collection<PSModuleInfo> { };
            PSModuleInfo ModuleInfo;
            string ActivityCode = "";
            string ModulePath = "";
            Console.Write("Type the full path and filename of the module to process:");
            ModulePath = Console.ReadLine();

            PowerShell ps = PowerShell.Create();

            ps.AddCommand("Import-Module").AddArgument(ModulePath);
            ps.AddParameter("PassThru");
            ModuleInfos = ps.Invoke<PSModuleInfo>();

            ModuleInfo = (PSModuleInfo)ModuleInfos[0];

            ActivityCode = ActivityGenerator.GenerateFromModuleInfo(ModuleInfo, "MyNamespace").First<String>();

           CodeFile.Write(ActivityCode);
            Console.ReadLine();

        }
    }
}

```

## <a name="example"></a>예제

다음 예제에서는 Windows PowerShell cmdlet에서 작업에 대 한 c # 코드를 생성 하는 방법을 보여 줍니다.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.IO;
using System.Management.Automation;
using System.Collections.ObjectModel;
using Microsoft.PowerShell.Activities;

namespace MakeActivity
{
    class Program
    {
        static void Main(string[] args)

        {
            StreamWriter CodeFile = new StreamWriter("c:\\\\testmodule\\codefile.cs");
            Collection<PSModuleInfo> ModuleInfos = new Collection<PSModuleInfo> { };
            PSModuleInfo ModuleInfo;
            Collection<CommandInfo> CommandInfos = new Collection<CommandInfo> { };
            CommandInfo MyCommand;
            string ActivityCode = "";
            string ModulePath = "";
            Console.Write("Type the full path and filename of the module to process:");
            ModulePath = Console.ReadLine();

            PowerShell ps = PowerShell.Create();

            ps.AddCommand("Import-Module").AddArgument(ModulePath);
            ps.AddParameter("PassThru");
            ModuleInfos = ps.Invoke<PSModuleInfo>();

            ModuleInfo = (PSModuleInfo)ModuleInfos[0];

            ps.AddCommand("Get-Command").AddArgument(ModuleInfo);
            CommandInfos = ps.Invoke<CommandInfo>();

            MyCommand = CommandInfos[0];

            ActivityCode = ActivityGenerator.GenerateFromCommandInfo(MyCommand, "MyNamespace");

           CodeFile.Write(ActivityCode);
            Console.ReadLine();

        }
    }
}

```
