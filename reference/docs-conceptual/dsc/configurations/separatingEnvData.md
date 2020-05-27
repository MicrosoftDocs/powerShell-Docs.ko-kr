---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: 구성 및 환경 데이터 분리
ms.openlocfilehash: 076e17054cfa20fad5ca925df126e239a77268db
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692426"
---
# <a name="separating-configuration-and-environment-data"></a>구성 및 환경 데이터 분리

>적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

구성 데이터를 사용하여 구성 자체에서 DSC 구성에 사용된 데이터를 분리하는 것이 유용할 수 있습니다.
이 작업을 수행하면 여러 환경에 단일 구성을 사용할 수 있습니다.

예를 들어 애플리케이션을 개발할 경우 한 구성을 개발 및 프로덕션 환경 모두에 사용하고 구성 데이터를 사용하여 각 환경의 데이터를 지정할 수 있습니다.

## <a name="what-is-configuration-data"></a>구성 데이터는 무엇입니까?

구성 데이터는 해시 테이블에서 정의되며 해당 구성을 컴파일할 때 DSC 구성에 전달되는 데이터입니다.

**ConfigurationData** 해시 테이블에 대한 자세한 설명은 [구성 데이터 사용](configData.md)을 참조하세요.

## <a name="a-simple-example"></a>간단한 예

간단한 예를 통해 이 과정을 알아보겠습니다.
일부 노드에 **IIS**가 있고 다른 노드에 **Hyper-V**가 있도록 하는 단일 구성을 만들려고 합니다.

```powershell
Configuration MyDscConfiguration {

  Node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
  WindowsFeature IISInstall {
    Ensure = 'Present'
    Name   = 'Web-Server'
  }

 }
    Node $AllNodes.Where{$_.Role -eq "VMHost"}.NodeName
    {
        WindowsFeature HyperVInstall {
            Ensure = 'Present'
            Name   = 'Hyper-V'
        }
    }
}

$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            Role = 'WebServer'
        },

        @{
            NodeName    = 'VM-2'
            Role = 'VMHost'
        }
    )
}

MyDscConfiguration -ConfigurationData $MyData
```

이 스크립트의 마지막 줄은 `$MyData`를 값 **ConfigurationData** 매개 변수로 전달하여 구성을 컴파일합니다.

결과적으로 다음과 같이 두 개의 MOF 파일이 생성됩니다.

```
    Directory: C:\DscTests\MyDscConfiguration


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:09 PM           1968 VM-1.mof
-a----        3/31/2017   5:09 PM           1970 VM-2.mof
```

`$MyData`는 각각 `NodeName` 및 `Role`을 가진 서로 다른 두 노드를 지정합니다. 구성에서는 **(특히**)로부터 받는 노드의 컬렉션을 받아 동적으로 `$MyData`Node`$AllNodes` 블록을 만들고 `Role` 속성을 기준으로 컬렉션을 필터링합니다.

## <a name="using-configuration-data-to-define-development-and-production-environments"></a>구성 데이터를 사용하여 개발 및 프로덕션 환경 정의

단일 구성을 사용하여 웹 사이트의 개발 환경과 프로덕션 환경을 모두 설정하는 예 전체를 살펴보겠습니다. 개발 환경에서는 IIS와 SQL Server가 모두 단일 노드에 설치됩니다. 프로덕션 환경에서는 IIS와 SQL Server가 별도 노드에 설치됩니다. 구성 데이터 .psd1 파일을 사용하여 서로 다른 두 환경의 데이터를 지정하겠습니다.

### <a name="configuration-data-file"></a>구성 데이터 파일

`DevProdEnvData.psd1`이라는 파일에서 개발 및 프로덕션 환경 데이터를 다음과 같이 정의합니다.

```powershell
@{

    AllNodes = @(

        @{
            NodeName        = "*"
            SQLServerName   = "MySQLServer"
            SqlSource       = "C:\Software\Sql"
            DotNetSrc       = "C:\Software\sxs"
            WebSiteName     = "New website"
        },

        @{
            NodeName        = "Prod-SQL"
            Role            = "MSSQL"
        },

        @{
            NodeName        = "Prod-IIS"
            Role            = "Web"
            SiteContents    = "C:\Website\Prod\SiteContents\"
            SitePath        = "\\Prod-IIS\Website\"
        },

        @{
            NodeName         = "Dev"
            Role             = "MSSQL", "Web"
            SiteContents     = "C:\Website\Dev\SiteContents\"
            SitePath         = "\\Dev\Website\"
        }
    )
}
```

### <a name="configuration-script-file"></a>구성 스크립트 파일

이제 `.ps1` 파일에 정의된 구성으로 가서 `DevProdEnvData.psd1`에 정의된 노드를 역할(`MSSQL`, `Dev` 또는 둘 모두)에 따라 필터링하고 적절하게 구성합니다.
개발 환경은 SQL Server와 IIS가 모두 한 노드에 있고, 프로덕션 환경은 두 가지가 서로 다른 노드에 있습니다.
`SiteContents` 속성으로 지정된 것처럼 사이트 내용도 서로 다릅니다.

구성 스크립트의 끝 부분에서 구성을 호출하며(MOF 문서로 컴파일) `DevProdEnvData.psd1`을 `$ConfigurationData` 매개 변수로 전달합니다.

>**참고:** 이 구성을 사용하려면 `xSqlPs` 및 `xWebAdministration` 모듈을 대상 노드에 설치해야 합니다.

다음과 같이 이름이 `MyWebApp.ps1`인 파일에서 구성을 정의하겠습니다.

```powershell
Configuration MyWebApp
{
    Import-DscResource -Module PSDesiredStateConfiguration
    Import-DscResource -Module xSqlPs
    Import-DscResource -Module xWebAdministration

    Node $AllNodes.Where{$_.Role -contains "MSSQL"}.NodeName
   {
        # Install prerequisites
        WindowsFeature installdotNet35
        {
            Ensure      = "Present"
            Name        = "Net-Framework-Core"
            Source      = "c:\software\sxs"
        }

        # Install SQL Server
        xSqlServerInstall InstallSqlServer
        {
            InstanceName = $Node.SQLServerName
            SourcePath   = $Node.SqlSource
            Features     = "SQLEngine,SSMS"
            DependsOn    = "[WindowsFeature]installdotNet35"

        }
   }

   Node $AllNodes.Where{$_.Role -contains "Web"}.NodeName
   {
        # Install the IIS role
        WindowsFeature IIS
        {
            Ensure       = 'Present'
            Name         = 'Web-Server'
        }

        # Install the ASP .NET 4.5 role
        WindowsFeature AspNet45
        {
            Ensure       = 'Present'
            Name         = 'Web-Asp-Net45'

        }

        # Stop the default website
        xWebsite DefaultSite
        {
            Ensure       = 'Present'
            Name         = 'Default Web Site'
            State        = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn    = '[WindowsFeature]IIS'

        }

        # Copy the website content
        File WebContent

        {
            Ensure          = 'Present'
            SourcePath      = $Node.SiteContents
            DestinationPath = $Node.SitePath
            Recurse         = $true
            Type            = 'Directory'
            DependsOn       = '[WindowsFeature]AspNet45'

        }


        # Create the new Website

        xWebsite NewWebsite

        {

            Ensure          = 'Present'
            Name            = $Node.WebSiteName
            State           = 'Started'
            PhysicalPath    = $Node.SitePath
            DependsOn       = '[File]WebContent'
        }

    }

}

MyWebApp -ConfigurationData DevProdEnvData.psd1
```

이 구성을 실행하면 다음과 같이 세 개의 MOF 파일이 생성됩니다(각 파일은 **AllNodes** 배열의 항목으로 명명됨).

```
    Directory: C:\DscTests\MyWebApp


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:47 PM           2944 Prod-SQL.mof
-a----        3/31/2017   5:47 PM           6994 Dev.mof
-a----        3/31/2017   5:47 PM           5338 Prod-IIS.mof
```

## <a name="using-non-node-data"></a>비노드 데이터 사용

노드와 관련되지 않은 데이터에 대한 추가 키를 **ConfigurationData** 해시 테이블에 추가할 수 있습니다.
다음 구성은 두 웹 사이트의 존재를 확인합니다.
각 웹 사이트에 대한 데이터는 **AllNodes** 배열에 정의됩니다.
`Config.xml` 파일은 두 웹 사이트 모두에 사용되므로 `NonNodeData` 이름을 사용하여 추가 키에서 해당 파일을 정의합니다.
원하는 만큼 추가 키를 사용할 수 있으며 원하는 이름을 지정할 수 있습니다.
`NonNodeData`는 예약어가 아니며, 단지 추가 키 이름을 지정하는 데 사용된 것입니다.

특수 변수 **$ConfigurationData**를 사용하여 추가 키에 액세스합니다.
이 예에서 `ConfigFileContents`는 다음과 같은 줄로 액세스됩니다.

```powershell
 Contents = $ConfigurationData.NonNodeData.ConfigFileContents
 ```

 `File` 리소스 블록에서

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName           = "*"
            LogPath            = "C:\Logs"
        },

        @{
            NodeName = "VM-1"
            SiteContents = "C:\Site1"
            SiteName = "Website1"
        },


        @{
            NodeName = "VM-2"
            SiteContents = "C:\Site2"
            SiteName = "Website2"
        }
    );

    NonNodeData =
    @{
        ConfigFileContents = (Get-Content C:\Template\Config.xml)
     }
}

configuration WebsiteConfig
{
    Import-DscResource -ModuleName xWebAdministration -Name MSFT_xWebsite

    node $AllNodes.NodeName
    {
        xWebsite Site
        {
            Name         = $Node.SiteName
            PhysicalPath = $Node.SiteContents
            Ensure       = "Present"
        }

        File ConfigFile
        {
            DestinationPath = $Node.SiteContents + "\\config.xml"
            Contents = $ConfigurationData.NonNodeData.ConfigFileContents
        }
    }
}
```

## <a name="see-also"></a>참고 항목

- [구성 데이터 사용](configData.md)
- [구성 데이터의 자격 증명 옵션](configDataCredentials.md)
- [DSC 구성](configurations.md)
