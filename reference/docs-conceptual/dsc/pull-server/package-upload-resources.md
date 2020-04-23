---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: 리소스 패키지 및 끌어오기 서버에 업로드
ms.openlocfilehash: 8aac343d7495ecda94ed76d1d97079397eecd65f
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "78278507"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a>리소스 패키지 및 끌어오기 서버에 업로드

아래 섹션에서는 끌어오기 서버를 이미 설정했다고 가정합니다. 끌어오기 서버를 설정하지 않은 경우에는 다음 가이드를 사용할 수 있습니다.

- [DSC SMB 끌어오기 서버 설정](pullServerSmb.md)
- [DSC HTTP 끌어오기 서버 설정](pullServer.md)

구성, 리소스를 다운로드하고 해당 상태를 보고하도록 각 대상 노드를 구성할 수 있습니다. 이 문서에서는 다운로드할 수 있도록 리소스를 업로드하고 자동으로 리소스를 다운로드하도록 클라이언트를 구성하는 방법을 보여 줍니다. 노드가 할당된 구성을 받으면 **끌어오기** 또는 **밀어넣기**(v5)를 통해 LCM에 지정된 위치에서 구성에 필요한 모든 리소스를 자동으로 다운로드합니다.

## <a name="package-resource-modules"></a>패키지 리소스 모듈

다운로드할 클라이언트에 사용 가능한 각 리소스는 ".zip" 파일에 저장해야 합니다. 아래 예제에서는 [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) 리소스를 사용하여 필요한 단계를 보여 줍니다.

> [!NOTE]
> 클라이언트에서 PowerShell 4.0을 사용하는 경우 리소스 폴더 구조를 평면화하고 모든 버전 폴더를 제거해야 합니다. 자세한 내용은 [여러 리소스 버전](../configurations/import-dscresource.md#multiple-resource-versions)을 참조하세요.

원하는 유틸리티, 스크립트 또는 메서드를 사용하여 리소스 디렉터리를 압축할 수 있습니다. Windows에서는 "xPSDesiredStateConfiguration" 디렉터리를 ‘마우스 오른쪽 단추로 클릭’하고 "보내기", "압축 폴더"를 차례로 선택합니다. 

![마우스 오른쪽 단추로 클릭](media/package-upload-resources/right-click.gif)

### <a name="naming-the-resource-archive"></a>리소스 보관 파일 이름 지정

다음 형식을 사용하여 리소스 보관 파일 이름을 지정해야 합니다.

```
{ModuleName}_{Version}.zip
```

위의 예제에서 "xPSDesiredStateConfiguration.zip"의 이름을 "xPSDesiredStateConfiguration_8.4.4.0.zip"으로 바꿔야 합니다.

### <a name="create-checksums"></a>CheckSum 만들기

리소스 모듈이 압축되고 이름이 바뀐 후 **CheckSum**을 만들어야 합니다.  **CheckSum**은 클라이언트의 LCM에서 리소스가 변경되었고 다시 다운로드되어야 하는지 확인하는 데 사용됩니다. 아래 예제와 같이 **New-DSCCheckSum** cmdlet을 사용하여 [CheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum)을 만들 수 있습니다.

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

출력은 표시되지 않지만 이제 "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum" 파일이 표시됩니다. `New-DSCCheckSum` 매개 변수를 사용하여 파일 디렉터리에서 `-Path`을 실행할 수도 있습니다. 체크섬이 이미 있는 경우 `-Force` 매개 변수를 사용하여 체크섬을 다시 만들 수 있습니다.

### <a name="where-to-store-resource-archives"></a>리소스 보관 파일을 저장할 위치

#### <a name="on-a-dsc-http-pull-server"></a>DSC HTTP 끌어오기 서버

HTTP 끌어오기 서버를 설정할 때 [DSC HTTP 끌어오기 서버 설정](pullServer.md)에 설명된 대로 **ModulePath** 및 **ConfigurationPath** 키의 디렉터리를 지정합니다. **ConfigurationPath** 키는 ".mof" 파일을 저장해야 하는 위치를 나타냅니다. **ModulePath**는 DSC 리소스 모듈을 저장해야 하는 위치를 나타냅니다.

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a>SMB 공유

**ResourceRepositoryShare**를 지정한 경우 끌어오기 클라이언트를 설정할 때 **ResourceRepositoryShare** 블록의 **SourcePath** 디렉터리에 보관 파일과 체크섬을 저장합니다.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Configurations'
}

ResourceRepositoryShare SMBResourceServer
{
    SourcePath = '\\SMBPullServer\Resources'
}
```

**ConfigurationRepositoryShare**만 지정한 경우 끌어오기 클라이언트를 설정할 때 **ConfigurationRepositoryShare** 블록의 **SourcePath** 디렉터리에 보관 파일과 체크섬을 저장합니다.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a>리소스 업데이트

보관 파일의 이름에서 버전 번호를 변경하거나 새 체크섬을 만들어 노드가 강제로 해당 리소스를 업데이트하도록 할 수 있습니다. 끌어오기 클라이언트는 필요한 리소스의 최신 버전을 확인할 뿐 아니라 해당 LCM을 새로 고칠 때 업데이트된 체크섬을 확인합니다.

## <a name="see-also"></a>참고 항목

- [DSC SMB 끌어오기 서버 설정](pullServerSmb.md)
- [DSC HTTP 끌어오기 서버 설정](pullServer.md)
