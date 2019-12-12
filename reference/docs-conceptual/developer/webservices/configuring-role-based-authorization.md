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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359772"
---
# <a name="configuring-role-based-authorization"></a>역할 기반 권한 부여 구성

이 항목에서는 관리에 대한 사용자 지정 권한 부여 구현 [Implementing Custom Authorization for Management OData IIS Extension](./implementing-custom-authorization-for-a-management-odata-web-service.md)에 설명된 [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) 인터페이스의 샘플 구현에 대한 역할 기반 권한 부여 정책을 구성하는 방법을 보여줍니다.

이 예제에서는 샘플 관리 OData 응용 프로그램에서 권한 부여 정책을 정의 하는 데 사용 하는 XML 파일을 구성 합니다. 두 개의 역할을 만들고 워크플로를 포함 하는 여러 Windows PowerShell 모듈을 해당 역할과 연결 합니다. XML 파일을 정의 하는 스키마는 [역할 기반 권한 부여 구성 스키마](./role-based-authorization-configuration-schema.md)에 나열 됩니다.

## <a name="modifying-the-rbacconfigurationxml-file"></a>RBacConfiguration 파일 수정

이 파일은 응용 프로그램에 대 한 권한 부여 정책을 정의 합니다. 역할은 `Group` 노드를 사용 하 여 정의 됩니다. `Group` 노드는 해당 그룹에 할당 된 사용자가 실행할 수 있는 Windows PowerShell 명령을 정의 합니다. 사용자는 `User` 노드를 사용 하 여 그룹에 할당 됩니다.

이 예에서는 관리자 `Group` 노드에 모듈을 추가 하 고 각 그룹에 사용자를 추가 합니다.

#### <a name="adding-a-module-to-a-group-node"></a>그룹 노드에 모듈 추가

1. 텍스트 편집기에서 **RBacConfiguration** 이라는 파일을 만듭니다. 이 파일은 웹 서비스의 기본 응용 프로그램 디렉터리에 저장 해야 합니다. 파일에 다음 텍스트를 삽입 합니다.

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

2. 이 파일에는 두 개의 `Group` 노드가 포함 되어 있습니다. 이러한 두 역할은이 예제에서 사용 되는 두 역할, `NonAdminGroup` 및 `AdminGroup` 역할을 나타냅니다.

   첫 번째 `Group` 노드의 closing `Cmdlets` 태그 바로 뒤에 다음 XML을 추가 합니다.

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a>그룹 노드에 사용자 추가

1. 텍스트 편집기에서 **RBacConfiguration** 파일을 엽니다. 이 파일은 설치 전에 끝점 이름을 변경 하지 않은 경우 C:\\\inetpub\wwwroot\Modata 폴더에 있습니다.

2. `Users` 노드의 닫는 태그 바로 뒤에 다음 XML을 추가 합니다.

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. 이전 단계에서 추가한 XML 바로 뒤에 다음 XML을 추가 합니다.

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```