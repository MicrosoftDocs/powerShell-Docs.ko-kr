---
title: 관리 OData 웹 서비스에 리소스 추가 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e620bf6d-76be-47b0-a7a8-f43418f30c60
caps.latest.revision: 6
ms.openlocfilehash: b81a32b867795ae51c3f5308c2f82c31ed2747fa
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858369"
---
# <a name="adding-resources-to-a-management-odata-web-service"></a>관리 OData 웹 서비스에 리소스 추가

이 예제에는 관리 OData 스키마 디자이너를 사용 하 여 기존 관리 OData 웹 서비스에 리소스를 추가 하는 방법을 보여 줍니다. 합니다 [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) 샘플 프로세스 및 서버 리소스를 노출 하는 웹 서비스를 만듭니다. 이 예제에서는 웹 서비스에 가상 머신 (VM) 리소스를 추가 합니다.

## <a name="prerequisites"></a>필수 구성 요소

이 항목에서는 다운로드 및 설치 했습니다 합니다 [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) 에 설명 된 대로 샘플 [Windows PowerShell 웹 서비스를 만드는](./creating-a-management-odata-web-service.md)를 다운로드 하 고 설치 하 고는 [관리 OData 스키마 디자이너](https://marketplace.visualstudio.com/items?itemName=jlisc0.ManagementODataSchemaDesigner)합니다. 이 항목은 또한 Hyper-v Windows PowerShell 모듈 관리 Odata 끝점을 설정 하면 컴퓨터에 설치 되어 있다고 가정 합니다.

## <a name="adding-vm-as-a-resource-to-the-web-service"></a>웹 서비스에 VM 리소스로 추가

먼저는 스키마 디자이너에 기존 관리 OData 끝점에서 스키마를 가져오는 것입니다. 다음 절차에는 작업을 수행 하는 방법을 설명 합니다.

#### <a name="importing-an-existing-schema-into-the-schema-designer"></a>스키마 디자이너는 기존 스키마 가져오기

1. 관리 OData 스키마 디자이너를 엽니다.

2. **파일** 메뉴에서 **파일** ; **새** ; **파일**합니다. 합니다 **새 파일** 대화 상자가 나타납니다.

3. 클릭 **관리 OData 모델**를 클릭 하 고 **오픈**합니다.

4. 주 창에서 마우스 오른쪽 단추로 클릭 하 고 클릭 **스키마 파일** ; **가져오기**합니다. 합니다 **열고** 대화 상자가 나타납니다.

5. 관리 OData 웹 서비스에 대 한 여기서 설정한 폴더로 이동 합니다 [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) 샘플입니다. 스크립트를 수정 하지 않고 끝점을 설정 하는 샘플을 사용 하 여 제공 되는 Windows PowerShell 스크립트를 사용 하는 경우 해당 폴더는 **C:\inetpub\wwwroot\Modata**합니다. Schema.mof를 선택 하 고 클릭 **열려**합니다.

   이 시점에서 Schema.xml 파일과 Schema.mof을 텍스트 편집기에서 열고 프로세스 및 서비스 리소스에 대 한 매핑을 포함 하는지 확인 합니다. 다음을 사용 하 여 Schema.mof 파일이 [Distributed Management Task Force](https://www.dmtf.org/) (DTMF) MOF (Managed Object) 표준입니다. Schema.xml 파일에 설명 된 XML 스키마를 사용 하 여 [리소스 매핑 스키마](./resource-mapping-schema.md)합니다.

   다음 절차에는 스키마 모델의 Hyper-v cmdlet을 가져오는 방법을 설명 합니다.

#### <a name="importing-cmdlets-into-the-schema"></a>스키마에서 cmdlet 가져오기

1. 스키마 디자이너 창의 빈 영역을 마우스 오른쪽 단추로 클릭 하 고 클릭 **Import Cmdlet**합니다. 합니다 **Cmdlet 가져오기 마법사** 대화 상자가 나타납니다.

2. 했는지 **로컬 컴퓨터** 을 선택 하 고 클릭 **다음**합니다.

3. 설치 된 Windows PowerShell 모듈을 선택 하 고 있는지 확인 하 고 드롭다운 목록에서 Hyper-v를 선택 합니다. 클릭 **다음**합니다. **다음**을 클릭합니다.

4. 에 **Cmdlet 명사** 목록에서 **VM**합니다. **다음**을 클릭합니다.

5. 예를 들어 cmdlet 사용 하 여 Get 및 Delete 명령을 바인딩합니다. 선택을 취소는 **만들기** 및 **업데이트** 확인란, 있는지 확인 합니다 **가져오기** 및 **삭제** 확인란 확인 됩니다. 있는지 확인 합니다 `Get-VM` cmdlet에 대해 선택 되었는지 **가져오기**, 및 `Remove-VM` cmdlet에 대해 선택 되었는지 **삭제**합니다.

6. VM cmdlet에 대 한 메타 데이터는 출력 형식을 지정 하지 않으므로, 출력 형식을 지정 하는 cmdlet을 실행 해야 합니다. 선택 **제공 출력 형식** 누릅니다 **cmdlet을 실행**합니다. 합니다 **Cmdlet을 실행** 대화 상자가 나타납니다. **실행**을 클릭합니다. 합니다 **CLR 형식** 상자가 채워집니다는 `VirtualMachine` 형식입니다. 클릭 **확인**, 클릭 **다음**합니다.

7. 기본적으로 VirtualMachine 개체의 속성을 모두 선택 됩니다. 웹 서비스에서이 리소스를 요청할 때 반환 되는 데이터의 일부분으로 원하지 않는 하는 모든 속성을 지울 수 있습니다. **다음**을 클릭합니다.

8. 키로 사용할 하나 이상의 속성을 선택 해야 합니다. 선택 **이름을** 클릭 하 고 목록에서 **다음**합니다.

9. 다음 창을 사용 하면 기본 cmdlet의 속성 관리 OData 리소스의 속성을 매핑할 수 있습니다. 마법사는 기본적으로 동일한 이름의 속성을 매핑합니다. 예를 들어 합니다 `ComputerName` 리소스의 속성에 매핑되는 `ComputerName` cmdlet의 속성입니다.  지정할 수 있습니다 합니다 `ComputerName` 웹 서비스에 대 한 요청에서 속성 있고 지정할 값을 전달할 수는 `Get-VM` cmdlet. `Id` 및 `Name` 기본적으로 매핑됩니다.

   10. 클릭 **다음**, 클릭 **마침**합니다.

       VM 리소스는 이제 스키마 디자이너 창에 나타납니다. 속성 및 리소스와 연결 된 작업을 검사할 수 있습니다. 다음으로 업데이트 된 스키마 파일을 웹 서비스에 대 한 가상 디렉터리로 내보냅니다.

#### <a name="exporting-schema-files-from-the-schema-designer"></a>스키마 디자이너에서 스키마 파일 내보내기

1. 스키마 디자이너 창의 빈 영역을 마우스 오른쪽 단추로 클릭 하 고 클릭 **스키마 파일** ; **내보내기**합니다. 합니다 **다른 이름으로 저장** 대화 상자가 나타납니다.

2. MOF 파일을 가져올 위치에서 동일한 디렉터리로 이동 합니다. 원래 MOF 파일 (기본적으로 Schema.mof) 같은 파일 이름을 지정 하 고 클릭 **저장할**합니다. 기존 파일을 덮어쓸 것인지 확인 합니다.

   명시적으로 지정 되지 않지만 합니다 **다른 이름으로 저장** 대화 상자에서이 Schema.mof 및 Schema.xml 파일을 대체 합니다.

## <a name="next-steps"></a>다음 단계

관리 OData 웹 서비스에서 새 VM 리소스를 액세스 하면 RbacConfiguration.xml 파일에 설명 된 대로 Hyper-v Windows PowerShell 모듈에 대 한 액세스를 허용 하도록 업데이트 해야 [구성 역할 기반 권한 부여](./configuring-role-based-authorization.md), 및 웹 서비스를 다시 시작 해야 합니다.