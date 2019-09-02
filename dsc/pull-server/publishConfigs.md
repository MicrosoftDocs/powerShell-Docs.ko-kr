---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: 구성 ID를 사용하여 끌어오기 서버에 게시(v4/v5)
ms.openlocfilehash: c258814f480b91eba75c7ce9abf70c558f1f469e
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986575"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a>구성 ID를 사용하여 끌어오기 서버에 게시(v4/v5)

아래 섹션에서는 끌어오기 서버를 이미 설정했다고 가정합니다. 끌어오기 서버를 설정하지 않은 경우에는 다음 가이드를 사용할 수 있습니다.

- [DSC SMB 끌어오기 서버 설정](pullServerSmb.md)
- [DSC HTTP 끌어오기 서버 설정](pullServer.md)

구성, 리소스를 다운로드하고 해당 상태를 보고하도록 각 대상 노드를 구성할 수 있습니다. 이 문서에서는 다운로드할 수 있도록 리소스를 업로드하고 자동으로 리소스를 다운로드하도록 클라이언트를 구성하는 방법을 보여 줍니다. 노드가 할당된 구성을 받으면 **끌어오기** 또는 **밀어넣기**(v5)를 통해 LCM(로컬 구성 관리자)의 지정된 위치에서 구성에 필요한 모든 리소스를 자동으로 다운로드합니다.

## <a name="compile-configurations"></a>구성 컴파일

끌어오기 서버에서 [구성](../configurations/configurations.md)을 저장하는 첫 번째 단계는 구성을 `.mof` 파일로 컴파일하는 것입니다. 구성을 제네릭으로 설정하고 더 많은 클라이언트에 적용하려면 Node 블록에서 `localhost`를 사용합니다. 아래 예제에서는 특정 클라이언트 이름 대신 `localhost`를 사용하는 구성 셸을 보여 줍니다.

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

일반 구성을 컴파일한 후에는 `localhost.mof` 파일이 있어야 합니다.

## <a name="renaming-the-mof-file"></a>MOF 파일 이름 바꾸기

**ConfigurationName** 또는 **ConfigurationID**를 통해 끌어오기 서버에서 구성 `.mof` 파일을 저장할 수 있습니다. 끌어오기 클라이언트 설정을 어떻게 계획하는지에 따라 아래 섹션을 선택하여 컴파일된 `.mof` 파일의 이름을 제대로 바꿀 수 있습니다.

### <a name="configuration-ids-guid"></a>구성 ID(GUID)

파일의 이름을 `localhost.mof` 파일에서 `<GUID>.mof` 파일로 변경해야 합니다. 아래 예제 또는 [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet을 사용하여 임의의 **Guid**를 만들 수 있습니다.

```powershell
[System.Guid]::NewGuid()
```

샘플 출력

```Output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

그런 다음, 허용되는 메서드를 사용하여 `.mof` 파일의 이름을 바꿀 수 있습니다. 아래 예제에서는 [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet을 사용합니다.

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

환경에서 **Guid**를 사용하는 방법에 대한 자세한 내용은 [Guid에 대한 계획](/powershell/dsc/secureserver#guids)을 참조하세요.

### <a name="configuration-names"></a>구성 이름

파일의 이름을 `localhost.mof` 파일에서 `<Configuration Name>.mof` 파일로 변경해야 합니다. 다음 예제에서는 이전 섹션의 구성 이름이 사용됩니다. 그런 다음, 허용되는 메서드를 사용하여 `.mof` 파일의 이름을 바꿀 수 있습니다. 아래 예제에서는 [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet을 사용합니다.

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a>체크섬 만들기

끌어오기 서버에 저장된 각 `.mof` 파일 또는 SMB 공유에는 연결된 `.checksum` 파일이 있어야 합니다.
이 파일을 통해 클라이언트는 연결된 `.mof` 파일이 변경되어 다시 다운로드되어야 하는 시기를 인식합니다.

[New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet을 사용하여 **CheckSum**을 만들 수 있습니다. `-Path` 매개 변수를 사용하여 파일 디렉터리에서 `New-DSCCheckSum`을 실행할 수도 있습니다.
체크섬이 이미 있는 경우 `-Force` 매개 변수를 사용하여 체크섬을 다시 만들 수 있습니다. 다음 예제에서는 이전 섹션의 `.mof` 파일을 포함하는 디렉터리를 지정했고 `-Force` 매개 변수를 사용합니다.

```powershell
New-DscChecksum -Path '.\' -Force
```

출력은 표시되지 않지만 이제 `<GUID or Configuration Name>.mof.checksum` 파일이 표시됩니다.

## <a name="where-to-store-mof-files-and-checksums"></a>MOF 파일 및 체크섬을 저장할 위치

### <a name="on-a-dsc-http-pull-server"></a>DSC HTTP 끌어오기 서버

HTTP 끌어오기 서버를 설정할 때 [DSC HTTP 끌어오기 서버 설정](pullServer.md)에 설명된 대로 **ModulePath** 및 **ConfigurationPath** 키의 디렉터리를 지정합니다. **ModulePath** 키는 모듈의 패키지 `.zip` 파일을 저장할 위치를 나타냅니다. **ConfigurationPath**는 `.mof` 파일과 `.checksum` 파일을 저장해야 하는 위치를 나타냅니다.

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a>SMB 공유

SMB 공유를 사용하도록 끌어오기 클라이언트를 설정할 때 **ConfigurationRepositoryShare**를 지정합니다.
모든 `.mof` 파일과 `.checksum` 파일은 **ConfigurationRepositoryShare** 블록의 **SourcePath** 디렉터리에 저장되어야 합니다.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a>다음 단계

다음으로, 지정된 구성을 끌어오도록 끌어오기 클라이언트를 구성할 수 있습니다. 자세한 내용은 다음 가이드 중 하나를 참조하세요.

- [구성 ID를 사용하여 끌어오기 클라이언트 설정(v4)](pullClientConfigId4.md)
- [구성 ID를 사용하여 끌어오기 클라이언트 설정(v5)](pullClientConfigId.md)
- [구성 이름을 사용하여 끌어오기 클라이언트 설정(v5)](pullClientConfigNames.md)

## <a name="see-also"></a>참고 항목

- [DSC SMB 끌어오기 서버 설정](pullServerSmb.md)
- [DSC HTTP 끌어오기 서버 설정](pullServer.md)
- [리소스 패키지 및 끌어오기 서버에 업로드](package-upload-resources.md)
