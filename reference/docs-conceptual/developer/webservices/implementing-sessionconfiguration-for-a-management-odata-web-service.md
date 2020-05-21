---
title: 관리 OData 웹 서비스에 대 한 SessionConfiguration 구현 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0b2a7ce2-3c33-469c-a4a4-b8fe3bd05324
caps.latest.revision: 5
ms.openlocfilehash: ac597359d81184157a71dc497cca07358f3a3492
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557280"
---
# <a name="implementing-sessionconfiguration-for-a-management-odata-web-service"></a><span data-ttu-id="45e77-102">관리 OData 웹 서비스에 대한 SessionConfiguration 구현</span><span class="sxs-lookup"><span data-stu-id="45e77-102">Implementing SessionConfiguration for a Management OData web service</span></span>

<span data-ttu-id="45e77-103">Windows PowerShell 웹 서비스를 사용 하려면 Windows PowerShell cmdlet을 노출 하기 위해 [register-pssessionconfiguration](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration) 인터페이스를 구현 하는 타사가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="45e77-103">Using the Windows PowerShell Web Service requires a third party to implement the [System.Management.Automation.Remoting.Pssessionconfiguration](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration) interface to expose Windows PowerShell cmdlets.</span></span> <span data-ttu-id="45e77-104">이 인터페이스는 웹 서비스가 서버에서 cmdlet을 실행 하는 데 사용 하는 원격 세션에 대 한 정보에 대 한 액세스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="45e77-104">This interface provides access to information about the remote session that the web service uses to run the cmdlets on the server.</span></span> <span data-ttu-id="45e77-105">인터페이스를 구현 하는 코드를 작성 한 후에는 웹 응용 프로그램에서 사용할 DLL로 컴파일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45e77-105">After writing the code to implement the interface, you must compile it into a DLL to be used in the web application.</span></span>

## <a name="implementation-of-pssessionconfiguration-interface"></a><span data-ttu-id="45e77-106">Register-pssessionconfiguration 인터페이스 구현</span><span class="sxs-lookup"><span data-stu-id="45e77-106">Implementation of PSSessionConfiguration interface</span></span>

<span data-ttu-id="45e77-107">다음 코드는 [register-pssessionconfiguration](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration) 인터페이스를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="45e77-107">The following code implements the [System.Management.Automation.Remoting.Pssessionconfiguration](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration) interface.</span></span>

```csharp
//-----------------------------------------------------------------------
// <copyright file="SessionConfiguration.cs" company="Microsoft Corporation">
//     Copyright (C) 2011 Microsoft Corporation
// </copyright>
//-----------------------------------------------------------------------

namespace Microsoft.Samples.Management.OData.RoleBasedPlugins
{
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Management.Automation;
    using System.Management.Automation.Remoting;
    using System.Management.Automation.Runspaces;

    /// <summary>
    /// Custom Session configuration implementation
    /// </summary>
    public class SessionConfiguration : PSSessionConfiguration
    {
        /// <summary>
        /// Gets application private data
        /// </summary>
        /// <param name="senderInfo">Sender information</param>
        /// <returns>Always returns null</returns>
        public override PSPrimitiveDictionary GetApplicationPrivateData(PSSenderInfo senderInfo)
        {
            return null;
        }

        /// <summary>
        /// Gets custom initial session state
        /// It relies on the RBAC system to give list of commands allowed for a user
        /// and creates Initial Session state from that
        /// </summary>
        /// <param name="senderInfo">Sender information</param>
        /// <returns>Custom initial Session state</returns>
        public override InitialSessionState GetInitialSessionState(PSSenderInfo senderInfo)
        {
            if (senderInfo == null)
            {
                throw new ArgumentNullException("senderInfo");
            }

            if (senderInfo.UserInfo == null)
            {
                throw new ArgumentException("senderInfo.UserInfo is null");
            }

            InitialSessionState initialSessionState = InitialSessionState.CreateDefault();
            foreach (SessionStateCommandEntry command in initialSessionState.Commands)
            {
                command.Visibility = SessionStateEntryVisibility.Private;
            }

            List<string> scripts = RbacSystem.Current.GetScripts(senderInfo.UserInfo);
            foreach (string script in scripts)
            {
                initialSessionState.Commands.Add(new SessionStateScriptEntry(script));
            }

            List<string> modules = RbacSystem.Current.GetModules(senderInfo.UserInfo);
            if (modules.Count > 0)
            {
                initialSessionState.ImportPSModule(modules.ToArray());
            }

            // enable execution of scripts in this process
            System.Environment.SetEnvironmentVariable("PSExecutionPolicyPreference", "unrestricted");

            List<string> cmdletsFromRbac = RbacSystem.Current.GetCmdlets(senderInfo.UserInfo);

            // Add all commands from Rbac system to Initial Session State commands
            foreach (string cmdlet in cmdletsFromRbac)
            {
                SessionStateCommandEntry cmdletFromRbac = initialSessionState.Commands.FirstOrDefault(item => string.Equals(item.Name, cmdlet, StringComparison.OrdinalIgnoreCase));
                if (cmdletFromRbac == null)
                {
                    throw new ArgumentException("Command not found in InitialSessionState " + cmdlet);
                }

                cmdletFromRbac.Visibility = SessionStateEntryVisibility.Public;
            }

            return initialSessionState;
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="45e77-108">참고 항목</span><span class="sxs-lookup"><span data-stu-id="45e77-108">See Also</span></span>

[<span data-ttu-id="45e77-109">관리 OData 웹 서비스에 대한 사용자 지정 권한 부여 구현</span><span class="sxs-lookup"><span data-stu-id="45e77-109">Implementing Custom Authorization for a Management OData web service</span></span>](./implementing-custom-authorization-for-a-management-odata-web-service.md)
