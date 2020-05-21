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
ms.openlocfilehash: 2c9d6040b7a9c17dc5204c8eb835fd69780f62c5
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564260"
---
# <a name="configuring-role-based-authorization"></a><span data-ttu-id="0d794-102">역할 기반 권한 부여 구성</span><span class="sxs-lookup"><span data-stu-id="0d794-102">Configuring Role-based Authorization</span></span>

<span data-ttu-id="0d794-103">이 항목에서는 [관리 ODATA IIS 확장에 대 한 사용자 지정 권한 부여 구현](./implementing-custom-authorization-for-a-management-odata-web-service.md)에 설명 된 [Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) 인터페이스의 샘플 구현에 대 한 역할 기반 권한 부여 정책을 구성 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0d794-103">This topic demonstrates how to configure the role-based authorization policy for the sample implementation of the [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) interface described in [Implementing Custom Authorization for Management OData IIS Extension](./implementing-custom-authorization-for-a-management-odata-web-service.md).</span></span>

<span data-ttu-id="0d794-104">이 예제에서는 샘플 관리 OData 응용 프로그램에서 권한 부여 정책을 정의 하는 데 사용 하는 XML 파일을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d794-104">In this example, you will configure an XML file that is used by the sample Management OData application to define the authorization policy.</span></span> <span data-ttu-id="0d794-105">두 개의 역할을 만들고 워크플로를 포함 하는 여러 Windows PowerShell 모듈을 해당 역할과 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d794-105">You will create two roles and associate different Windows PowerShell modules that contain workflows with those roles.</span></span> <span data-ttu-id="0d794-106">XML 파일을 정의 하는 스키마는 [역할 기반 권한 부여 구성 스키마](./role-based-authorization-configuration-schema.md)에 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d794-106">The schema that defines the XML file is listed at [Role-Based Authorization Configuration Schema](./role-based-authorization-configuration-schema.md).</span></span>

## <a name="modifying-the-rbacconfigurationxml-file"></a><span data-ttu-id="0d794-107">RBacConfiguration 파일 수정</span><span class="sxs-lookup"><span data-stu-id="0d794-107">Modifying the RBacConfiguration.xml File</span></span>

<span data-ttu-id="0d794-108">이 파일은 응용 프로그램에 대 한 권한 부여 정책을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d794-108">This file defines the authorization policy for the application.</span></span> <span data-ttu-id="0d794-109">역할은 노드를 사용 하 여 정의 됩니다 `Group` .</span><span class="sxs-lookup"><span data-stu-id="0d794-109">Roles are defined by using `Group` nodes.</span></span> <span data-ttu-id="0d794-110">`Group`노드는 해당 그룹에 할당 된 사용자가 실행할 수 있는 Windows PowerShell 명령을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d794-110">A `Group` node defines the Windows PowerShell commands that users assigned to that group can run.</span></span> <span data-ttu-id="0d794-111">사용자는 노드를 사용 하 여 그룹에 할당 됩니다 `User` .</span><span class="sxs-lookup"><span data-stu-id="0d794-111">Users are assigned to groups by using `User` nodes.</span></span>

<span data-ttu-id="0d794-112">이 예에서는 관리자 노드에 모듈을 추가 하 `Group` 고 각 그룹에 사용자를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d794-112">In these examples, you will add a module to the Administrator `Group` node, and add a user to each group.</span></span>

#### <a name="adding-a-module-to-a-group-node"></a><span data-ttu-id="0d794-113">그룹 노드에 모듈 추가</span><span class="sxs-lookup"><span data-stu-id="0d794-113">Adding a Module to a Group Node</span></span>

1. <span data-ttu-id="0d794-114">텍스트 편집기에서 **RBacConfiguration** 이라는 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0d794-114">Create a file named **RBacConfiguration.xml** in a text editor.</span></span> <span data-ttu-id="0d794-115">이 파일은 웹 서비스의 기본 응용 프로그램 디렉터리에 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d794-115">This file should be saved to the main application directory for your web service.</span></span> <span data-ttu-id="0d794-116">파일에 다음 텍스트를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d794-116">Insert the following text in the file.</span></span>

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

2. <span data-ttu-id="0d794-117">이 파일에는 두 개의 노드가 포함 되어 있습니다 `Group` .</span><span class="sxs-lookup"><span data-stu-id="0d794-117">The file contains two `Group` nodes.</span></span> <span data-ttu-id="0d794-118">이는이 예제에서 사용 되는 두 개의 역할인 `NonAdminGroup` 및 역할을 나타냅니다 `AdminGroup` .</span><span class="sxs-lookup"><span data-stu-id="0d794-118">These represent the two roles used in this example, the `NonAdminGroup` and the `AdminGroup` roles.</span></span>

   <span data-ttu-id="0d794-119">`Cmdlets`첫 번째 노드의 닫는 태그 바로 뒤에 `Group` 다음 XML을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d794-119">Directly after the closing `Cmdlets` tag in the first `Group` node, add the following XML:</span></span>

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a><span data-ttu-id="0d794-120">그룹 노드에 사용자 추가</span><span class="sxs-lookup"><span data-stu-id="0d794-120">Adding a User to a Group Node</span></span>

1. <span data-ttu-id="0d794-121">텍스트 편집기에서 **RBacConfiguration** 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0d794-121">Open the **RBacConfiguration.xml** file in a text editor.</span></span> <span data-ttu-id="0d794-122">이 파일은 \\ 설치 전에 끝점 이름을 변경 하지 않은 경우 C: \inetpub\wwwroot\Modata 폴더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d794-122">This file is located in the folder C:\\\inetpub\wwwroot\Modata  if you did not change the endpoint name before installation.</span></span>

2. <span data-ttu-id="0d794-123">노드의 닫는 태그 바로 뒤에 `Users` 다음 XML을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d794-123">Directly after the closing tag in the `Users` node, add the following XML:</span></span>

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. <span data-ttu-id="0d794-124">이전 단계에서 추가한 XML 바로 뒤에 다음 XML을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d794-124">Directly after the XML added in the previous step, add the following XML:</span></span>

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```
