---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell 공급자 설계
description: Windows PowerShell 공급자 설계
ms.openlocfilehash: 89e1fa9cfc0a2e5928a358aad4244c8e9152fe1a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654526"
---
# <a name="designing-your-windows-powershell-provider"></a>Windows PowerShell 공급자 설계

사용자가 탐색 하거나 탐색할 데이터베이스와 같은 저장 된 데이터 집합을 제품 또는 구성에서 노출 하는 경우 Windows PowerShell 공급자를 구현 해야 합니다. 또한 제품이 다단계 컨테이너가 아니더라도 컨테이너를 제공 하는 경우 Windows PowerShell 공급자를 구현 하는 것이 좋습니다. 예를 들어, cmdlet 동사 복사, 이동, 이름 바꾸기, 새로 만들기 또는 제거를 사용 하 여 제품 또는 구성 데이터에 대 한 작업으로 사용할 수 있는 경우 Windows PowerShell 컨테이너 공급자를 구현할 수 있습니다.

## <a name="windows-powershell-paths-identify-your-provider"></a>공급자를 식별 하는 Windows PowerShell 경로

Windows powershell 런타임은 windows PowerShell 경로를 사용 하 여 적절 한 Windows PowerShell 공급자에 액세스 합니다. Cmdlet이 이러한 경로 중 하나를 지정 하면 런타임에서는 연결 된 데이터 저장소에 액세스 하는 데 사용할 공급자를 알고 있습니다. 이러한 경로에는 드라이브 한정 경로, 공급자 정규화 경로, 공급자-직접 경로 및 공급자 내부 경로가 포함 됩니다. 각 Windows PowerShell 공급자는 이러한 경로를 하나 이상 지원 해야 합니다.

Windows PowerShell 경로에 대 한 자세한 내용은 Windows PowerShell의 작동 방식을 참조 하세요.

### <a name="defining-a-drive-qualified-path"></a>Drive-Qualified 경로 정의

사용자가 실제 드라이브에 있는 데이터에 액세스할 수 있도록 하려면 Windows PowerShell 공급자가 드라이브 한정 경로를 지원 해야 합니다. 이 경로는 드라이브 이름 뒤에 콜론 (:) (예: mydrive: \ abc\bar.)으로 시작 합니다.

### <a name="defining-a-provider-qualified-path"></a>Provider-Qualified 경로 정의

Windows PowerShell 런타임에서 공급자를 초기화 하 고 초기화 하지 못하게 하려면 Windows PowerShell 공급자가 공급자 한정 경로를 지원 해야 합니다. 예를 들어 FileSystem:: \\ \uncshare\abc\bar은 Windows PowerShell에서 제공 하는 filesystem 공급자의 공급자 한정 경로입니다.

### <a name="defining-a-provider-direct-path"></a>Provider-Direct 경로 정의

Windows PowerShell 공급자에 대 한 원격 액세스를 허용 하려면 현재 위치에 대 한 Windows PowerShell 공급자에 직접 전달 하는 공급자 직접 경로를 지원 해야 합니다. 예를 들어 레지스트리 Windows PowerShell 공급자는 \server\regkeypath를 \\ 공급자 직접 경로로 사용할 수 있습니다.

### <a name="defining-a-provider-internal-path"></a>Provider-Internal 경로 정의

공급자 cmdlet이 비 Windows PowerShell Api (응용 프로그래밍 인터페이스)를 사용 하 여 데이터에 액세스할 수 있도록 하려면 Windows PowerShell 공급자가 공급자 내부 경로를 지원 해야 합니다. 이 경로는 공급자 정규화 경로의 "::" 뒤에 표시 됩니다. 예를 들어 filesystem Windows PowerShell 공급자에 대 한 공급자 내부 경로는 \uncshare\abc\bar.입니다. \\

## <a name="changing-stored-data"></a>저장 된 데이터 변경

기본 데이터 저장소를 수정 하는 메서드를 재정의 하는 경우 해당 메서드로 변경 된 항목의 최신 버전을 사용 하 여 항상 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) 를 호출 합니다. 공급자 인프라는 사용자가-PassThru 매개 변수를 지정 하는 경우와 같이 항목 개체를 파이프라인으로 전달 해야 하는지 여부를 결정 합니다. 최신 항목을 검색 하는 작업은 비용이 많이 드는 작업 (성능 단위)입니다. PassThru 속성을 테스트 하 여 실제로 결과 항목을 써야 하는지 여부를 확인할 수 있습니다.

## <a name="choose-a-base-class-for-your-provider"></a>공급자의 기본 클래스를 선택 하십시오.

Windows PowerShell은 고유한 Windows PowerShell 공급자를 구현 하는 데 사용할 수 있는 다양 한 기본 클래스를 제공 합니다. 공급자를 디자인할 때 요구 사항에 가장 적합 한 기본 클래스 (이 섹션에서 설명)를 선택 합니다.

각 Windows PowerShell 공급자 기본 클래스는 cmdlet 집합을 사용할 수 있도록 합니다. 이 섹션에서는 cmdlet에 대해 설명 하지만 매개 변수는 설명 하지 않습니다.

Windows powershell 런타임은 세션 상태를 사용 하 여 `Get-Location` ,, `Set-Location` `Pop-Location` 및 cmdlet과 같은 특정 windows powershell 공급자에서 사용할 수 있는 몇 가지 location cmdlet을 만듭니다 `Push-Location` . Cmdlet을 사용 `Get-Help` 하 여 이러한 위치 cmdlet에 대 한 정보를 가져올 수 있습니다.

### <a name="cmdletprovider-base-class"></a>CmdletProvider 기본 클래스

[System.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) 클래스는 기본 Windows PowerShell 공급자를 정의 합니다. 이 클래스는 공급자 선언을 지원 하 고 모든 Windows PowerShell 공급자가 사용할 수 있는 다양 한 속성 및 메서드를 제공 합니다.
클래스는 cmdlet에 의해 호출 되어 `Get-PSProvider` 세션에 사용할 수 있는 모든 공급자를 나열 합니다.
이 cmdlet의 구현은 세션 상태로 제공 됩니다.

> [!NOTE]
> Windows powershell 공급자는 모든 Windows PowerShell 언어 범위에서 사용할 수 있습니다.

### <a name="drivecmdletprovider-base-class"></a>드라이브 \ 데이터베이스 공급자 기본 클래스

[System.object](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 는 새 드라이브를 추가 하 고, 기존 드라이브를 제거 하 고, 기본 드라이브를 초기화 하는 작업을 지 원하는 Windows PowerShell 드라이브 공급자를 정의 합니다. 예를 들어 Windows PowerShell에서 제공 하는 FileSystem 공급자는 하드 드라이브 및 CD/DVD 장치 드라이브와 같이 탑재 된 모든 볼륨에 대 한 드라이브를 초기화 합니다.

이 클래스는 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) 의 기본 클래스에서 파생 됩니다. 다음 표에서는이 클래스에서 제공 하는 cmdlet을 보여 줍니다. 나열 되는 것 외에도 `Get-PSDrive` cmdlet은 사용 가능한 드라이브를 검색 하는 데 사용 되는 관련 cmdlet입니다.

|      Cmdlet      |                             정의                              |
| ---------------- | ------------------------------------------------------------------- |
| `New-PSDrive`    | 세션에 대 한 새 드라이브를 만들고 드라이브 정보를 스트리밍합니다. |
| `Remove-PSDrive` | 세션에서 드라이브를 제거 합니다.                                   |

### <a name="itemcmdletprovider-base-class"></a>ItemCmdletProvider 기본 클래스

[System.object](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 는 데이터 저장소의 개별 항목에 대 한 작업을 수행 하는 Windows PowerShell 항목 공급자를 정의 하며 컨테이너 또는 탐색 기능을 가정 하지 않습니다. 이 클래스는 System.object에서 파생 된 [공급자](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 기본 클래스입니다. 다음 표에서는이 클래스에서 제공 하는 cmdlet을 보여 줍니다.

|     Cmdlet     |                                                                                                                                                            정의                                                                                                                                                            |
| -------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Clear-Item`   | 지정 된 위치에 있는 항목의 현재 내용을 지우고 공급자가 지정한 "clear" 값으로 바꿉니다. 매개 변수를 지정 하지 않으면이 cmdlet은 파이프라인을 통해 출력 개체를 전달 하지 않습니다 `PassThru` .                                                                                   |
| `Get-Item`     | 지정 된 위치에서 항목을 검색 하 고 결과 개체를 스트리밍합니다.                                                                                                                                                                                                                                                  |
| `Invoke-Item`  | 지정 된 경로에 있는 항목에 대 한 기본 동작을 호출 합니다.                                                                                                                                                                                                                                                                   |
| `Set-Item`     | 지정 된 위치에 있는 항목을 지정 된 값으로 설정 합니다. 매개 변수를 지정 하지 않으면이 cmdlet은 파이프라인을 통해 출력 개체를 전달 하지 않습니다 `PassThru` .                                                                                                                                                   |
| `Resolve-Path` | Windows PowerShell 경로에 대 한 와일드 카드 및 스트림 경로 정보를 확인 합니다.                                                                                                                                                                                                                                              |
| `Test-Path`    | 지정 된 경로를 테스트 하 고, 있는 경우를 반환 하 고, 그렇지 않으면를 반환 `true` `false` 합니다. 이 cmdlet은 `IsContainer` [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) 에 대 한 매개 변수를 지원 하기 위해 구현 됩니다. |

### <a name="containercmdletprovider-base-class"></a>ContainerCmdletProvider 기본 클래스

[Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 클래스는 데이터 저장소 항목에 대 한 컨테이너를 사용자에 게 노출 하는 Windows PowerShell 컨테이너 공급자를 정의 합니다. Windows PowerShell 컨테이너 공급자는 항목을 포함 하는 컨테이너 (중첩 된 컨테이너 없음)가 하나 있는 경우에만 사용할 수 있습니다. 중첩 된 컨테이너가 있는 경우 Windows PowerShell 탐색 공급자를 구현 해야 합니다.

이 클래스는 [system.object](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 의 클래스에서 파생 됩니다. 다음 표에서는이 클래스에서 구현 하는 cmdlet을 정의 합니다.

|     Cmdlet      |                                                                        정의                                                                        |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Copy-Item`     | 항목을 한 위치에서 다른 위치로 복사 합니다. 매개 변수를 지정 하지 않으면이 cmdlet은 파이프라인을 통해 출력 개체를 전달 하지 않습니다 `PassThru` . |
| `Get-Childitem` | 지정 된 위치에 있는 자식 항목을 검색 하 여 개체로 스트리밍합니다.                                                                        |
| `New-Item`      | 지정 된 위치에 새 항목을 만들고 결과 개체를 스트리밍합니다.                                                                           |
| `Remove-Item`   | 지정 된 위치에서 항목을 제거 합니다.                                                                                                               |
| `Rename-Item`   | 지정 된 위치에 있는 항목의 이름을 바꿉니다. 매개 변수를 지정 하지 않으면이 cmdlet은 파이프라인을 통해 출력 개체를 전달 하지 않습니다 `PassThru` . |

### <a name="navigationcmdletprovider-base-class"></a>NavigationCmdletProvider 기본 클래스

[System.object](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 클래스는 둘 이상의 컨테이너를 사용 하는 항목에 대 한 작업을 수행 하는 Windows PowerShell 탐색 공급자를 정의 합니다. 이 클래스는 [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 기본 클래스에서 파생 됩니다. 다음 표에서는이 클래스에서 제공 하는 cmdlet을 나열 합니다.

|    Cmdlet    |                                                                      정의                                                                      |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| Combine-Path | 경로 사이에 공급자별 구분 기호를 사용 하 여 두 개의 경로를 단일 경로로 결합 합니다. 이 cmdlet은 문자열을 스트리밍합니다.                               |
| `Move-Item`  | 항목을 지정 된 위치로 이동 합니다. 매개 변수를 지정 하지 않으면이 cmdlet은 파이프라인을 통해 출력 개체를 전달 하지 않습니다 `PassThru` . |

관련 cmdlet은 Windows PowerShell에서 제공 하는 기본 Parse-Path cmdlet입니다. 이 cmdlet을 사용 하 여 매개 변수를 지원 하기 위해 Windows PowerShell 경로를 구문 분석할 수 있습니다 `Parent` . 부모 경로 문자열을 스트리밍합니다.

## <a name="select-provider-interfaces-to-support"></a>지원할 공급자 인터페이스 선택

Windows powershell 공급자는 Windows PowerShell 기본 클래스 중 하나에서 파생 되는 것 외에도 다음 공급자 인터페이스 중 하나 이상을 파생 시켜 다른 기능을 지원할 수 있습니다. 이 섹션에서는 이러한 인터페이스와 각 인터페이스에서 지 원하는 cmdlet을 정의 합니다. 인터페이스 지원 cmdlet에 대 한 매개 변수는 설명 하지 않습니다. Cmdlet 매개 변수 정보는 및 cmdlet을 사용 하 여 온라인으로 사용할 수 있습니다 `Get-Command` `Get-Help` .

### <a name="icontentcmdletprovider"></a>IContentCmdletProvider

[Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 인터페이스는 데이터 항목의 내용에 대 한 작업을 수행 하는 콘텐츠 공급자를 정의 합니다. 다음 표에서는이 인터페이스에서 노출 하는 cmdlet을 보여 줍니다.

|     Cmdlet      |                                                                                        정의                                                                                        |
| --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Add-Content`   | 지정 된 항목의 내용에 지정 된 값 길이를 추가 합니다. 매개 변수를 지정 하지 않으면이 cmdlet은 파이프라인을 통해 출력 개체를 전달 하지 않습니다 `PassThru` . |
| `Clear-Content` | 지정 된 항목의 내용을 "clear" 값으로 설정 합니다. 매개 변수를 지정 하지 않으면이 cmdlet은 파이프라인을 통해 출력 개체를 전달 하지 않습니다 `PassThru` .               |
| `Get-Content`   | 지정 된 항목의 내용을 검색 하 고 결과 개체를 스트리밍합니다.                                                                                                         |
| `Set-Content`   | 지정 된 항목의 기존 내용을 바꿉니다. 매개 변수를 지정 하지 않으면이 cmdlet은 파이프라인을 통해 출력 개체를 전달 하지 않습니다 `PassThru` .                     |

### <a name="ipropertycmdletprovider"></a>IPropertyCmdletProvider

[System.object](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) 는 데이터 저장소의 항목 속성에 대 한 작업을 수행 하는 속성 Windows PowerShell 공급자를 정의 합니다. 다음 표에서는이 인터페이스에서 노출 하는 cmdlet을 보여 줍니다.

> [!NOTE]
> `Path`이러한 cmdlet의 매개 변수는 속성을 식별 하는 대신 항목에 대 한 경로를 나타냅니다.

|        Cmdlet        |                                                                                   정의                                                                                    |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Clear-ItemProperty` | 지정 된 항목의 속성을 "clear" 값으로 설정 합니다. 매개 변수를 지정 하지 않으면이 cmdlet은 파이프라인을 통해 출력 개체를 전달 하지 않습니다 `PassThru` .      |
| `Get-ItemProperty`   | 지정 된 항목에서 속성을 검색 하 고 결과 개체를 스트리밍합니다.                                                                                                |
| `Set-ItemProperty`   | 지정 된 값을 사용 하 여 지정 된 항목의 속성을 설정 합니다. 매개 변수를 지정 하지 않으면이 cmdlet은 파이프라인을 통해 출력 개체를 전달 하지 않습니다 `PassThru` . |

### <a name="idynamicpropertycmdletprovider"></a>IDynamicPropertyCmdletProvider

[System.object](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider)에서 파생 된 [Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) 인터페이스는 지원 되는 cmdlet에 대 한 동적 매개 변수를 지정 하는 공급자를 정의 합니다. 이 형식의 공급자는 런타임에 속성을 정의할 수 있는 작업 (예: 새 속성 작업)을 처리 합니다. 정적으로 정의 된 속성을 가진 항목에서는 이러한 작업을 수행할 수 없습니다.
다음 표에서는이 인터페이스에서 노출 하는 cmdlet을 보여 줍니다.

|        Cmdlet         |                                                                                정의                                                                                |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `Copy-ItemProperty`   | 지정 된 항목의 속성을 다른 항목에 복사 합니다. 매개 변수를 지정 하지 않으면이 cmdlet은 파이프라인을 통해 출력 개체를 전달 하지 않습니다 `PassThru` . |
| `Move-ItemProperty`   | 지정 된 항목에서 다른 항목으로 속성을 이동 합니다. 매개 변수를 지정 하지 않으면이 cmdlet은 파이프라인을 통해 출력 개체를 전달 하지 않습니다 `PassThru` .  |
| `New-ItemProperty`    | 지정 된 항목에 대 한 속성을 만들고 결과 개체를 스트리밍합니다.                                                                                             |
| `Remove-ItemProperty` | 지정 된 항목의 속성을 제거 합니다.                                                                                                                              |
| `Rename-ItemProperty` | 지정 된 항목의 속성 이름을 바꿉니다. 매개 변수를 지정 하지 않으면이 cmdlet은 파이프라인을 통해 출력 개체를 전달 하지 않습니다 `PassThru` .                 |

### <a name="isecuritydescriptorcmdletprovider"></a>ISecurityDescriptorCmdletProvider

[Isecuritydescriptorcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ISecurityDescriptorCmdletProvider) 인터페이스는 공급자에 보안 설명자 기능을 추가 합니다. 이 인터페이스를 사용 하면 사용자가 데이터 저장소의 항목에 대 한 보안 설명자 정보를 가져오고 설정할 수 있습니다. 다음 표에서는이 인터페이스에서 노출 하는 cmdlet을 보여 줍니다.

|  Cmdlet   |                                                                                                                                                                                                          정의                                                                                                                                                                                                          |
| --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Get-Acl` | 운영 체제 리소스 (예: 파일 또는 개체)를 보호 하는 데 사용 되는 보안 설명자의 일부인 ACL (액세스 제어 목록)에 포함 된 정보를 검색 합니다.                                                                                                                                                                                                                                      |
| `Set-Acl` | ACL에 대 한 정보를 설정 합니다. 지정 된 경로에 대해 지정 된 항목에 대 한 [accesscontrol-namespace](/dotnet/api/System.Security.AccessControl.ObjectSecurity) 의 인스턴스 형식으로 되어 있습니다. Windows PowerShell 공급자가 보안 정보 설정을 지 원하는 경우이 cmdlet은 레지스트리의 파일, 키 및 하위 키에 대 한 정보를 설정할 수 있습니다. |

## <a name="see-also"></a>참고 항목

[Windows PowerShell 공급자 만들기](./how-to-create-a-windows-powershell-provider.md)

[Windows PowerShell 작동 방법](/previous-versions/ms714658(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)
