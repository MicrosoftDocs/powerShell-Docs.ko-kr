---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: 구성 및 환경 데이터 분리
ms.openlocfilehash: 305a766fec81d4ea4afce187756188b067a2048b
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794929"
---
# <a name="separating-configuration-and-environment-data"></a><span data-ttu-id="04667-103">구성 및 환경 데이터 분리</span><span class="sxs-lookup"><span data-stu-id="04667-103">Separating configuration and environment data</span></span>

><span data-ttu-id="04667-104">적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="04667-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="04667-105">구성 데이터를 사용하여 구성 자체에서 DSC 구성에 사용된 데이터를 분리하는 것이 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04667-105">It can be useful to separate the data used in a DSC configuration from the configuration itself by using configuration data.</span></span>
<span data-ttu-id="04667-106">이 작업을 수행하면 여러 환경에 단일 구성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04667-106">By doing this, you can use a single configuration for multiple environments.</span></span>

<span data-ttu-id="04667-107">예를 들어 애플리케이션을 개발할 경우 한 구성을 개발 및 프로덕션 환경 모두에 사용하고 구성 데이터를 사용하여 각 환경의 데이터를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04667-107">For example, if you are developing an application, you can use one configuration for both development and production environments, and use configuration data to specify data for each environment.</span></span>

## <a name="what-is-configuration-data"></a><span data-ttu-id="04667-108">구성 데이터는 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="04667-108">What is configuration data?</span></span>

<span data-ttu-id="04667-109">구성 데이터는 해시 테이블에서 정의되며 해당 구성을 컴파일할 때 DSC 구성에 전달되는 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="04667-109">Configuration data is data that is defined in a hashtable and passed to a DSC configuration when you compile that configuration.</span></span>

<span data-ttu-id="04667-110">**ConfigurationData** 해시 테이블에 대한 자세한 설명은 [구성 데이터 사용](configData.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="04667-110">For a detailed description of the **ConfigurationData** hashtable, see [Using configuration data](configData.md).</span></span>

## <a name="a-simple-example"></a><span data-ttu-id="04667-111">간단한 예</span><span class="sxs-lookup"><span data-stu-id="04667-111">A simple example</span></span>

<span data-ttu-id="04667-112">간단한 예를 통해 이 과정을 알아보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="04667-112">Let's look at a very simple example to see how this works.</span></span>
<span data-ttu-id="04667-113">일부 노드에 **IIS**가 있고 다른 노드에 **Hyper-V**가 있도록 하는 단일 구성을 만들려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="04667-113">We'll create a single configuration that ensures that **IIS** is present on some nodes, and that **Hyper-V** is present on others:</span></span>

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

<span data-ttu-id="04667-114">이 스크립트의 마지막 줄은 `$MyData`를 값 **ConfigurationData** 매개 변수로 전달하여 구성을 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="04667-114">The last line in this script compiles the configuration, passing `$MyData` as the value **ConfigurationData** parameter.</span></span>

<span data-ttu-id="04667-115">결과적으로 다음과 같이 두 개의 MOF 파일이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="04667-115">The result is that two MOF files are created:</span></span>

```
    Directory: C:\DscTests\MyDscConfiguration


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:09 PM           1968 VM-1.mof
-a----        3/31/2017   5:09 PM           1970 VM-2.mof
```

<span data-ttu-id="04667-116">`$MyData`는 각각 `NodeName` 및 `Role`을 가진 서로 다른 두 노드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="04667-116">`$MyData` specifies two different nodes, each with its own `NodeName` and `Role`.</span></span> <span data-ttu-id="04667-117">구성에서는 `$MyData` (특히 `$AllNodes`)로부터 받는 노드의 컬렉션을 받아 동적으로 **Node** 블록을 만들고 `Role` 속성을 기준으로 컬렉션을 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="04667-117">The configuration dynamically creates **Node** blocks by taking the collection of nodes it gets from `$MyData` (specifically, `$AllNodes`) and filters that collection against the `Role` property..</span></span>

## <a name="using-configuration-data-to-define-development-and-production-environments"></a><span data-ttu-id="04667-118">구성 데이터를 사용하여 개발 및 프로덕션 환경 정의</span><span class="sxs-lookup"><span data-stu-id="04667-118">Using configuration data to define development and production environments</span></span>

<span data-ttu-id="04667-119">단일 구성을 사용하여 웹 사이트의 개발 환경과 프로덕션 환경을 모두 설정하는 예 전체를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="04667-119">Let's look at a complete example that uses a single configuration to set up both development and production environments of a website.</span></span> <span data-ttu-id="04667-120">개발 환경에서는 IIS와 SQL Server가 모두 단일 노드에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="04667-120">In the development environment, both IIS and SQL Server are installed on a single nodes.</span></span> <span data-ttu-id="04667-121">프로덕션 환경에서는 IIS와 SQL Server가 별도 노드에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="04667-121">In the production environment, IIS and SQL Server are installed on separate nodes.</span></span> <span data-ttu-id="04667-122">구성 데이터 .psd1 파일을 사용하여 서로 다른 두 환경의 데이터를 지정하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="04667-122">We'll use a configuration data .psd1 file to specify the data for the two different environments.</span></span>

### <a name="configuration-data-file"></a><span data-ttu-id="04667-123">구성 데이터 파일</span><span class="sxs-lookup"><span data-stu-id="04667-123">Configuration data file</span></span>

<span data-ttu-id="04667-124">`DevProdEnvData.psd1`이라는 파일에서 개발 및 프로덕션 환경 데이터를 다음과 같이 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="04667-124">We'll define the development and production environment data in a file named `DevProdEnvData.psd1` as follows:</span></span>

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

### <a name="configuration-script-file"></a><span data-ttu-id="04667-125">구성 스크립트 파일</span><span class="sxs-lookup"><span data-stu-id="04667-125">Configuration script file</span></span>

<span data-ttu-id="04667-126">이제 `.ps1` 파일에 정의된 구성으로 가서 `DevProdEnvData.psd1`에 정의된 노드를 역할(`MSSQL`, `Dev` 또는 둘 모두)에 따라 필터링하고 적절하게 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="04667-126">Now, in the configuration, which is defined in a `.ps1` file, we filter the nodes we defined in `DevProdEnvData.psd1` by their role (`MSSQL`, `Dev`, or both), and configure them accordingly.</span></span>
<span data-ttu-id="04667-127">개발 환경은 SQL Server와 IIS가 모두 한 노드에 있고, 프로덕션 환경은 두 가지가 서로 다른 노드에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04667-127">The development environment has both the SQL Server and IIS on one node, while the production environment has them on two different nodes.</span></span>
<span data-ttu-id="04667-128">`SiteContents` 속성으로 지정된 것처럼 사이트 내용도 서로 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="04667-128">The site contents is also different, as specified by the `SiteContents` properties.</span></span>

<span data-ttu-id="04667-129">구성 스크립트의 끝 부분에서 구성을 호출하며(MOF 문서로 컴파일) `DevProdEnvData.psd1`을 `$ConfigurationData` 매개 변수로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="04667-129">At the end of the configuration script, we call the configuration (compile it into a MOF document), passing `DevProdEnvData.psd1` as the `$ConfigurationData` parameter.</span></span>

><span data-ttu-id="04667-130">**참고:** 이 구성을 사용하려면 `xSqlPs` 및 `xWebAdministration` 모듈을 대상 노드에 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04667-130">**Note:** This configuration requires the modules `xSqlPs` and `xWebAdministration` to be installed on the target node.</span></span>

<span data-ttu-id="04667-131">다음과 같이 이름이 `MyWebApp.ps1`인 파일에서 구성을 정의하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="04667-131">Let's define the configuration in a file named `MyWebApp.ps1`:</span></span>

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

<span data-ttu-id="04667-132">이 구성을 실행하면 다음과 같이 세 개의 MOF 파일이 생성됩니다(각 파일은 **AllNodes** 배열의 항목으로 명명됨).</span><span class="sxs-lookup"><span data-stu-id="04667-132">When you run this configuration, three MOF files are created (one for each named entry in the **AllNodes** array):</span></span>

```
    Directory: C:\DscTests\MyWebApp


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:47 PM           2944 Prod-SQL.mof
-a----        3/31/2017   5:47 PM           6994 Dev.mof
-a----        3/31/2017   5:47 PM           5338 Prod-IIS.mof
```

## <a name="using-non-node-data"></a><span data-ttu-id="04667-133">비노드 데이터 사용</span><span class="sxs-lookup"><span data-stu-id="04667-133">Using non-node data</span></span>

<span data-ttu-id="04667-134">노드와 관련되지 않은 데이터에 대한 추가 키를 **ConfigurationData** 해시 테이블에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04667-134">You can add additional keys to the **ConfigurationData** hashtable for data that is not specific to a node.</span></span>
<span data-ttu-id="04667-135">다음 구성은 두 웹 사이트의 존재를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="04667-135">The following configuration ensures the presence of two websites.</span></span>
<span data-ttu-id="04667-136">각 웹 사이트에 대한 데이터는 **AllNodes** 배열에 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="04667-136">Data for each website are defined in the **AllNodes** array.</span></span>
<span data-ttu-id="04667-137">`Config.xml` 파일은 두 웹 사이트 모두에 사용되므로 `NonNodeData` 이름을 사용하여 추가 키에서 해당 파일을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="04667-137">The file `Config.xml` is used for both websites, so we define it in an additional key with the name `NonNodeData`.</span></span>
<span data-ttu-id="04667-138">원하는 만큼 추가 키를 사용할 수 있으며 원하는 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04667-138">Note that you can have as many additional keys as you want, and you can name them anything you want.</span></span>
<span data-ttu-id="04667-139">`NonNodeData`는 예약어가 아니며, 단지 추가 키 이름을 지정하는 데 사용된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="04667-139">`NonNodeData` is not a reserved word, it is just what we decided to name the additional key.</span></span>

<span data-ttu-id="04667-140">특수 변수 **$ConfigurationData**를 사용하여 추가 키에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="04667-140">You access additional keys by using the special variable **$ConfigurationData**.</span></span>
<span data-ttu-id="04667-141">이 예에서 `ConfigFileContents`는 다음과 같은 줄로 액세스됩니다.</span><span class="sxs-lookup"><span data-stu-id="04667-141">In this example, `ConfigFileContents` is accessed with the line:</span></span>
```powershell
 Contents = $ConfigurationData.NonNodeData.ConfigFileContents
 ```
 <span data-ttu-id="04667-142">`File` 리소스 블록에서</span><span class="sxs-lookup"><span data-stu-id="04667-142">in the `File` resource block.</span></span>


```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName           = “*”
            LogPath            = “C:\Logs”
        },

        @{
            NodeName = “VM-1”
            SiteContents = “C:\Site1”
            SiteName = “Website1”
        },


        @{
            NodeName = “VM-2”;
            SiteContents = “C:\Site2”
            SiteName = “Website2”
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
            Ensure       = “Present”
        }

        File ConfigFile
        {
            DestinationPath = $Node.SiteContents + “\\config.xml”
            Contents = $ConfigurationData.NonNodeData.ConfigFileContents
        }
    }
}
```


## <a name="see-also"></a><span data-ttu-id="04667-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="04667-143">See Also</span></span>
- [<span data-ttu-id="04667-144">구성 데이터 사용</span><span class="sxs-lookup"><span data-stu-id="04667-144">Using configuration data</span></span>](configData.md)
- [<span data-ttu-id="04667-145">구성 데이터의 자격 증명 옵션</span><span class="sxs-lookup"><span data-stu-id="04667-145">Credentials Options in Configuration Data</span></span>](configDataCredentials.md)
- [<span data-ttu-id="04667-146">DSC 구성</span><span class="sxs-lookup"><span data-stu-id="04667-146">DSC Configurations</span></span>](configurations.md)
