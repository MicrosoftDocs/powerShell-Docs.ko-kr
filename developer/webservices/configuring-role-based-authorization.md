---
title: 역할 기반 권한 부여 구성 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2933a6ca-fe92-4ba2-97ee-ef0f0d5fdfcf
caps.latest.revision: 8
ms.openlocfilehash: b73284adb4bf228510bf8134aa4c6a10561b7ea2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080682"
---
# <a name="configuring-role-based-authorization"></a><span data-ttu-id="e8eb9-102">역할 기반 권한 부여 구성</span><span class="sxs-lookup"><span data-stu-id="e8eb9-102">Configuring Role-based Authorization</span></span>

<span data-ttu-id="e8eb9-103">이 항목의 샘플 구현에 대 한 역할 기반 권한 부여 정책을 구성 하는 방법에 설명 합니다 [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) 인터페이스에 설명 된 [구현 사용자 지정 관리 OData IIS 확장에 대 한 권한 부여](./implementing-custom-authorization-for-a-management-odata-web-service.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="e8eb9-103">This topic demonstrates how to configure the role-based authorization policy for the sample implementation of the [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) interface described in [Implementing Custom Authorization for Management OData IIS Extension](./implementing-custom-authorization-for-a-management-odata-web-service.md).</span></span>

<span data-ttu-id="e8eb9-104">이 예제에서는 권한 부여 정책을 정의 하는 샘플 관리 OData 응용 프로그램에서 사용 되는 XML 파일을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8eb9-104">In this example, you will configure an XML file that is used by the sample Management OData application to define the authorization policy.</span></span> <span data-ttu-id="e8eb9-105">두 개의 역할 만들고 해당 역할을 사용 하 여 워크플로 포함 하는 다른 Windows PowerShell 모듈을 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8eb9-105">You will create two roles and associate different Windows PowerShell modules that contain workflows with those roles.</span></span> <span data-ttu-id="e8eb9-106">XML 파일을 정의 하는 스키마에 나열한 [역할 기반 권한 부여 구성 스키마](./role-based-authorization-configuration-schema.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="e8eb9-106">The schema that defines the XML file is listed at [Role-Based Authorization Configuration Schema](./role-based-authorization-configuration-schema.md).</span></span>

## <a name="modifying-the-rbacconfigurationxml-file"></a><span data-ttu-id="e8eb9-107">RBacConfiguration.xml 파일 수정</span><span class="sxs-lookup"><span data-stu-id="e8eb9-107">Modifying the RBacConfiguration.xml File</span></span>

<span data-ttu-id="e8eb9-108">이 파일은 응용 프로그램에 대 한 권한 부여 정책을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8eb9-108">This file defines the authorization policy for the application.</span></span> <span data-ttu-id="e8eb9-109">역할을 사용 하 여 정의 `Group` 노드.</span><span class="sxs-lookup"><span data-stu-id="e8eb9-109">Roles are defined by using `Group` nodes.</span></span> <span data-ttu-id="e8eb9-110">`Group` 노드는 해당 그룹에 할당 하는 사용자가 실행할 수 있는 Windows PowerShell 명령을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8eb9-110">A `Group` node defines the Windows PowerShell commands that users assigned to that group can run.</span></span> <span data-ttu-id="e8eb9-111">사용자를 사용 하 여 그룹에 할당 된 `User` 노드.</span><span class="sxs-lookup"><span data-stu-id="e8eb9-111">Users are assigned to groups by using `User` nodes.</span></span>

<span data-ttu-id="e8eb9-112">이 예제에서는 관리자에 게 모듈을 추가 합니다 `Group` 노드, 각 그룹에 사용자를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8eb9-112">In these examples, you will add a module to the Administrator `Group` node, and add a user to each group.</span></span>

#### <a name="adding-a-module-to-a-group-node"></a><span data-ttu-id="e8eb9-113">그룹 노드로 모듈을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="e8eb9-113">Adding a Module to a Group Node</span></span>

1. <span data-ttu-id="e8eb9-114">이라는 파일을 만듭니다 **RBacConfiguration.xml** 텍스트 편집기에서.</span><span class="sxs-lookup"><span data-stu-id="e8eb9-114">Create a file named **RBacConfiguration.xml** in a text editor.</span></span> <span data-ttu-id="e8eb9-115">웹 서비스에 대 한 기본 응용 프로그램 디렉터리에이 파일을 저장 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8eb9-115">This file should be saved to the main application directory for your web service.</span></span> <span data-ttu-id="e8eb9-116">파일에 다음 텍스트를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8eb9-116">Insert the following text in the file.</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <RbacConfiguration>
     <Groups>
       <!--Group consists of the following:
         Name:  Name of the group
         UserName (Optional): Windows Identity user name
         Password (Optional): Password of the Windows user name
         DomainName (Optional): Domain for the user. For local machine account either do not include them or give the machine name. Do not give empty string
         MapIncomingUser (Optional): Boolean value indicating whether to execute cmdlet in the context of network client.

         User credentials and MapIncomingUser=true are exclusive.
       -->
       <Group Name="NonAdminGroup" MapIncomingUser="true">
         <Cmdlets>
           <Cmdlet>Get-Service</Cmdlet>
           <Cmdlet>Set-Service</Cmdlet>
           <Cmdlet>Get-Process</Cmdlet>
           <Cmdlet>Get-Item</Cmdlet>
           <Cmdlet>New-Item</Cmdlet>
           <Cmdlet>Get-Command</Cmdlet>
           <Cmdlet>ConvertTo-Xml</Cmdlet>
           <Cmdlet>ConvertTo-Json</Cmdlet>
           <Cmdlet>ConvertFrom-Json</Cmdlet>
         </Cmdlets>
       </Group>
       <Group Name="AdminGroup" MapIncomingUser="true">
         <Cmdlets>
           <Cmdlet>Get-Service</Cmdlet>
           <Cmdlet>Get-Process</Cmdlet>
           <Cmdlet>Get-Item</Cmdlet>
           <Cmdlet>New-Item</Cmdlet>
           <Cmdlet>Get-Command</Cmdlet>
           <Cmdlet>ConvertTo-Xml</Cmdlet>
           <Cmdlet>ConvertTo-Json</Cmdlet>
           <Cmdlet>ConvertFrom-Json</Cmdlet>
         </Cmdlets>
         <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
       </Group>
     </Groups>
     <Users>
       <!-- User consists of the following :
         Name: Name of the user. If a user is from a cer
         AuthenticationType: Authentication type used.
         DomainName (Optional): Domain for the user
       -->
       <User Name="localNonAdmin" AuthenticationType="Basic" GroupName="NonAdminGroup" />
       <User Name="localAdmin" AuthenticationType="Basic" GroupName="AdminGroup" />
     </Users>
   </RbacConfiguration>
   ```

2. <span data-ttu-id="e8eb9-117">파일에는 두 개의 `Group` 노드.</span><span class="sxs-lookup"><span data-stu-id="e8eb9-117">The file contains two `Group` nodes.</span></span> <span data-ttu-id="e8eb9-118">이 예에서 사용 하는 두 가지 역할을 나타내는 이러한 합니다 `NonAdminGroup` 하며 `AdminGroup` 역할입니다.</span><span class="sxs-lookup"><span data-stu-id="e8eb9-118">These represent the two roles used in this example, the `NonAdminGroup` and the `AdminGroup` roles.</span></span>

   <span data-ttu-id="e8eb9-119">닫는 직후 `Cmdlets` 첫 번째에서 태그 `Group` 노드를 다음 XML을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8eb9-119">Directly after the closing `Cmdlets` tag in the first `Group` node, add the following XML:</span></span>

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a><span data-ttu-id="e8eb9-120">사용자를 그룹 노드로 추가</span><span class="sxs-lookup"><span data-stu-id="e8eb9-120">Adding a User to a Group Node</span></span>

1. <span data-ttu-id="e8eb9-121">엽니다는 **RBacConfiguration.xml** 텍스트 편집기에서 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="e8eb9-121">Open the **RBacConfiguration.xml** file in a text editor.</span></span> <span data-ttu-id="e8eb9-122">이 파일은 c: 폴더\\\inetpub\wwwroot\Modata 설치 하기 전에 끝점 이름을 변경 하지 않은 경우.</span><span class="sxs-lookup"><span data-stu-id="e8eb9-122">This file is located in the folder C:\\\inetpub\wwwroot\Modata  if you did not change the endpoint name before installation.</span></span>

2. <span data-ttu-id="e8eb9-123">닫는 태그 바로 뒤의 `Users` 노드를 다음 XML을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8eb9-123">Directly after the closing tag in the `Users` node, add the following XML:</span></span>

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. <span data-ttu-id="e8eb9-124">직접 XML을 이전 단계에서 추가한 후 다음 XML을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8eb9-124">Directly after the XML added in the previous step, add the following XML:</span></span>

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```