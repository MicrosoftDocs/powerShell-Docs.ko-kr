---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: 구성 Id (v4/v5)를 사용 하 여 끌어오기 서버에 게시
ms.openlocfilehash: 0144fec43d7a8d65b79891567cc0dc3952175343
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402399"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a>구성 Id (v4/v5)를 사용 하 여 끌어오기 서버에 게시

아래 섹션에서는 끌어오기 서버를 설정한 이미 가정 합니다. 끌어오기 서버를 설정 하지 않은 경우에 다음 가이드를 사용할 수 있습니다.

- [DSC SMB 끌어오기 서버 설정](pullServerSmb.md)
- [DSC HTTP 끌어오기 서버 설정](pullServer.md)

각 대상 노드를 구성, 리소스를 다운로드 하 여 해당 상태를 보고할 수도 구성할 수 있습니다. 이 문서에서는, 다운로드 하 고 리소스를 자동으로 다운로드 하도록 클라이언트 구성에 사용할 수 있도록 리소스를 업로드 하는 방법을 보여 줍니다. 노드를 통해 할당된 된 구성의 받을 때 **끌어오기** 하거나 **푸시** (v5)에 자동으로 다운로드 LCM에 지정 된 위치에서 구성에 필요한 모든 리소스.

## <a name="compile-configurations"></a>구성 컴파일

저장 하 고 첫 번째 단계로 [구성을](../configurations/configurations.md) ".mof" 파일로 컴파일하는 끌어오기 서버에서. 제네릭 및 더 많은 클라이언트에 적용 가능한 구성 되도록 사용 하 여 `localhost` 노드 블록에 있습니다. 아래 예제에서는 표시를 사용 하는 구성 셸을 `localhost` 특정 클라이언트 이름 대신 합니다.

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

일반 구성, 컴파일되면 "localhost.mof" 파일이 있어야 합니다.

## <a name="renaming-the-mof-file"></a>MOF 파일 이름 바꾸기

제공 하는 끌어오기 서버의 구성 ".mof" 파일을 저장할 수 있습니다 **ConfigurationName** 하거나 **ConfigurationID**합니다. 끌어오기 클라이언트 설정 하려는 방법에 따라 올바르게 컴파일된 ".mof" 파일의 이름을 바꾸려면 아래 섹션을 선택할 수 있습니다.

### <a name="configuration-ids-guid"></a>구성 Id (GUID)

하기 위해 "localhost.mof" 파일 이름을 변경 해야 합니다 "<GUID>.mof" 파일입니다. 임의 만들 수 있습니다 **Guid** 아래 또는 사용 하 여 예제를 사용 하 여 [New-guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.

```powershell
[System.Guid]::NewGuid()
```

샘플 출력

```output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

그런 다음 허용 가능한 메서드를 사용 하 여 ".mof" 파일을 바꿀 수 있습니다. 아래 예제에서 사용 하는 [Rename-item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

사용에 대 한 자세한 내용은 **Guid** 환경에서 참조 [Guid에 대 한 계획](/powershell/dsc/secureserver#guids)합니다.

### <a name="configuration-names"></a>구성 이름

하기 위해 "localhost.mof" 파일 이름을 변경 해야 합니다 "<Configuration Name>.mof" 파일입니다. 다음 예제에서는 이전 섹션의 구성 이름을 사용 됩니다. 그런 다음 허용 가능한 메서드를 사용 하 여 ".mof" 파일을 바꿀 수 있습니다. 아래 예제에서 사용 하는 [Rename-item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a>체크섬 만들기

각 ".mof" 파일 연결된 ".checksum" 파일로 있어야 끌어오기 서버 또는 SMB 공유에 저장 합니다. 이 파일에는 클라이언트가 연결된 ".mof" 파일에 변경 하 고 다시 다운로드 해야 하는 경우 알 수 있습니다.

만들 수 있습니다는 **체크섬** 사용 하 여 합니다 [New-dscchecksum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet. 실행할 수도 있습니다 `New-DSCCheckSum` 사용 하 여 파일의 디렉터리와 비교 합니다 `-Path` 매개 변수입니다. 체크섬을 이미 있는 경우 적용할 수 있습니다 사용 하 여 다시 만들어야 합니다 `-Force` 매개 변수입니다. 다음 예제에서는 이전 섹션에서 ".mof" 파일이 포함 된 디렉터리를 지정 하 고 사용 하 여 `-Force` 매개 변수입니다.

```powershell
New-DscChecksum -Path '.\' -Force
```

출력이 표시 됩니다 있지만 이제는 "<GUID or Configuration Name>. mof.checksum" 파일입니다.

## <a name="where-to-store-mof-files-and-checksums"></a>MOF 파일 및 체크섬을 저장할 위치

### <a name="on-a-dsc-http-pull-server"></a>DSC HTTP 끌어오기 서버에서

설정할 때 HTTP 끌어오기 서버에 설명 된 대로 [DSC HTTP 끌어오기 서버 설정](pullServer.md)에 대 한 디렉터리를 지정 합니다 **ModulePath** 및 **ConfigurationPath** 키입니다. 합니다 **ConfigurationPath** 키 ".mof" 파일이 저장 될 위치를 나타냅니다. 합니다 **ConfigurationPath** ".mof" 파일과 ".checksum" 파일 저장 될 위치를 나타냅니다.

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a>SMB 공유에

SMB 공유를 사용 하 여 끌어오기 클라이언트를 설정 하는 경우 지정 된 **ConfigurationRepositoryShare**합니다. 모든 ".mof" 파일과 ".checksum" 다음에 저장할지를 **SourcePath** 에서 디렉터리를 **ConfigurationRepositoryShare** 블록입니다.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a>다음 단계

다음으로, 지정 된 구성을 끌어오기를 끌어오기 클라이언트를 구성 해야 합니다. 자세한 내용은 다음 가이드 중 하나를 참조 하세요.

- [구성 Id (v4)를 사용 하 여 끌어오기 클라이언트 설정](pullClientConfigId4.md)
- [구성 Id (v5)를 사용 하 여 끌어오기 클라이언트 설정](pullClientConfigId.md)
- [구성 이름 (v5)를 사용 하 여 끌어오기 클라이언트 설정](pullClientConfigNames.md)

## <a name="see-also"></a>참고 항목

- [DSC SMB 끌어오기 서버 설정](pullServerSmb.md)
- [DSC HTTP 끌어오기 서버 설정](pullServer.md)
- [패키지 및 끌어오기 서버에 업로드 리소스](package-upload-resources.md)
