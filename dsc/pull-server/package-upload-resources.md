---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: 패키지 및 끌어오기 서버에 업로드 리소스
ms.openlocfilehash: 29a62f96393a53c9e7da57a5e51732dcb0937194
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402300"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a>패키지 및 끌어오기 서버에 업로드 리소스

아래 섹션에서는 끌어오기 서버를 설정한 이미 가정 합니다. 끌어오기 서버를 설정 하지 않은 경우에 다음 가이드를 사용할 수 있습니다.

- [DSC SMB 끌어오기 서버 설정](pullServerSmb.md)
- [DSC HTTP 끌어오기 서버 설정](pullServer.md)

각 대상 노드를 구성, 리소스를 다운로드 하 여 해당 상태를 보고할 수도 구성할 수 있습니다. 이 문서에서는, 다운로드 하 고 리소스를 자동으로 다운로드 하도록 클라이언트 구성에 사용할 수 있도록 리소스를 업로드 하는 방법을 보여 줍니다. 노드를 통해 할당된 된 구성의 받을 때 **끌어오기** 하거나 **푸시** (v5)에 자동으로 다운로드 LCM에 지정 된 위치에서 구성에 필요한 모든 리소스.

## <a name="package-resource-modules"></a>패키지 리소스 모듈

각 리소스를 다운로드 하려면 클라이언트에 사용할 수 있는 ".zip" 파일에 저장 되어야 합니다. 아래 예제를 사용 하는 데 필요한 단계에 표시 됩니다는 [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) 리소스입니다.

> [!NOTE]
> PowerShell 4.0을 사용 하는 모든 클라이언트에 있으면 리소스 폴더 구조를 flaten 해야 하 고 버전 폴더를 제거 합니다. 자세한 내용은 [여러 리소스 버전](../configurations/import-dscresource.md#multiple-resource-versions)합니다.

모든 유틸리티, 스크립트 또는 선호 하는 메서드를 사용 하 여 리소스 디렉터리를 압축할 수 있습니다. Windows를 수행할 수 있습니다 *마우스 오른쪽 단추로 클릭* "xPSDesiredStateConfiguration" 디렉터리에 "송신", 한 다음 "압축 된 폴더"를 선택 합니다.

![마우스 오른쪽 단추로 클릭](../media/right-click.gif)

### <a name="naming-the-resource-archive"></a>리소스 보관 파일 이름 지정

리소스 보관 파일을 다음 형식으로 명명 해야 합니다.

```
{ModuleName}_{Version}.zip
```

위의 예에서 "xPSDesiredStateConfiguration.zip" 이름이 바뀐된 "xPSDesiredStateConfiguration_8.4.4.0.zip" 해야 합니다.

### <a name="create-checksums"></a>체크섬 만들기

만들려는 리소스 모듈 압축 되었으며 이름이 변경 되 면을 **체크섬**합니다.  합니다 **체크섬** 되, 클라이언트에서 LCM에 의해 확인 변경 된 리소스를 다시 다운로드 해야 합니다. 만들 수 있습니다는 **체크섬** 사용 하 여 합니다 [New-dscchecksum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) , 아래 예제와 같이 cmdlet.

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

출력 없음, 표시 되지만 "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum" 표시 됩니다. 실행할 수도 있습니다 `New-DSCCheckSum` 사용 하 여 파일의 디렉터리와 비교 합니다 `-Path` 매개 변수입니다. 체크섬을 이미 있는 경우 적용할 수 있습니다 사용 하 여 다시 만들어야 합니다 `-Force` 매개 변수입니다.

### <a name="where-to-store-resource-archives"></a>리소스 보관 파일을 저장할 위치

#### <a name="on-a-dsc-http-pull-server"></a>DSC HTTP 끌어오기 서버에서

설정할 때 HTTP 끌어오기 서버에 설명 된 대로 [DSC HTTP 끌어오기 서버 설정](pullServer.md)에 대 한 디렉터리를 지정 합니다 **ModulePath** 및 **ConfigurationPath** 키입니다. 합니다 **ConfigurationPath** 키 ".mof" 파일이 저장 될 위치를 나타냅니다. 합니다 **ModulePath** 모든 DSC 리소스 모듈이 저장 될 위치를 나타냅니다.

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a>SMB 공유에

지정한 경우는 **ResourceRepositoryShare**보관 및 체크섬 끌어오기 클라이언트 설정 저장 하는 경우를 **SourcePath** 디렉터리는 **ResourceRepositoryShare** 블록.

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

만 지정한 경우는 **ConfigurationRepositoryShare**보관 및 체크섬 끌어오기 클라이언트 설정 저장 하는 경우를 **SourcePath** 디렉터리는  **ConfigurationRepositoryShare** 블록입니다.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a>리소스 업데이트

보관 파일의 이름에 버전 번호를 변경 하거나 새 체크섬을 만들어 해당 리소스를 업데이트 하려면 노드를 강제할 수 있습니다. 끌어오기 클라이언트는 필요한 리소스의 최신 버전 확인 뿐만 아니라 해당 LCM 새로 고칠 때 체크섬을 업데이트 합니다.

## <a name="see-also"></a>참고 항목

- [DSC SMB 끌어오기 서버 설정](pullServerSmb.md)
- [DSC HTTP 끌어오기 서버 설정](pullServer.md)
