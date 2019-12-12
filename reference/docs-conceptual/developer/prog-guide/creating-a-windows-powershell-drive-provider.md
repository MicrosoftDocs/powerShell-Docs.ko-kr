---
title: Windows PowerShell 드라이브 공급자 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- drive providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], drive provider
- drives [PowerShell Programmer's Guide]
ms.assetid: 2b446841-6616-4720-9ff8-50801d7576ed
caps.latest.revision: 6
ms.openlocfilehash: 2e3d97e224b06bdf36ac0bc1237911e029ea762d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366832"
---
# <a name="creating-a-windows-powershell-drive-provider"></a>Windows PowerShell 드라이브 공급자 만들기

이 항목에서는 Windows PowerShell 드라이브를 통해 데이터 저장소에 액세스 하는 방법을 제공 하는 Windows PowerShell 드라이브 공급자를 만드는 방법에 대해 설명 합니다. 이 유형의 공급자는 Windows PowerShell 드라이브 공급자 라고도 합니다. 공급자가 사용 하는 Windows PowerShell 드라이브는 데이터 저장소에 연결 하는 방법을 제공 합니다.

여기에 설명 된 Windows PowerShell 드라이브 공급자는 Microsoft Access 데이터베이스에 대 한 액세스를 제공 합니다. 이 공급자의 경우 Windows PowerShell 드라이브는 데이터베이스를 나타내고 (드라이브 공급자에 원하는 수의 드라이브를 추가할 수 있음) 드라이브의 최상위 컨테이너는 데이터베이스의 테이블을 나타내고 컨테이너의 항목은의 행을 나타냅니다. 테이블입니다.

## <a name="defining-the-windows-powershell-provider-class"></a>Windows PowerShell 공급자 클래스 정의

드라이브 공급자는 [system.object](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 에서 파생 되는 .net 클래스를 정의 해야 합니다 .이 클래스는. 이 드라이브 공급자에 대 한 클래스 정의는 다음과 같습니다.

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L29-L30 "AccessDBProviderSample02.cs")]

이 예에서 [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) 특성은 공급자에 대해 사용자에 게 친숙 한 이름을 지정 하 고, 명령을 처리 하는 동안 공급자가 windows powershell 런타임에 노출 하는 windows powershell 관련 기능을 지정 합니다. 공급자 기능에 사용할 수 있는 값은 [system.web](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . x m m. 이 드라이브 공급자는 이러한 기능을 지원 하지 않습니다.

## <a name="defining-base-functionality"></a>기본 기능 정의

[Windows PowerShell 공급자 디자인](./designing-your-windows-powershell-provider.md)에 설명 된 대로, [system.object](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 를 초기화 하 고 초기화 하는 데 필요한 메서드를 정의 하는 [system.web](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) . n a m e. c s d. 세션 관련 초기화 정보를 추가 하 고 공급자가 사용 하는 리소스를 해제 하는 기능을 구현 하려면 [기본 Windows PowerShell 공급자 만들기](./creating-a-basic-windows-powershell-provider.md)를 참조 하세요. 그러나 여기에 설명 된 공급자를 비롯 한 대부분의 공급자는 Windows PowerShell에서 제공 하는이 기능의 기본 구현을 사용할 수 있습니다.

## <a name="creating-drive-state-information"></a>드라이브 상태 정보 만들기

모든 Windows PowerShell 공급자는 상태 비저장으로 간주 됩니다. 즉, 드라이브 공급자가 공급자를 호출할 때 Windows PowerShell 런타임에 필요한 상태 정보를 만들어야 합니다.

이 드라이브 공급자의 경우 상태 정보에는 드라이브 정보의 일부로 유지 되는 데이터베이스에 대 한 연결이 포함 됩니다. 다음은 드라이브를 설명 하는 [PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) 개체에이 정보를 저장 하는 방법을 보여 주는 코드입니다.

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L130-L151 "AccessDBProviderSample02.cs")]

## <a name="creating-a-drive"></a>드라이브 만들기

Windows PowerShell 런타임에서 드라이브를 만들 수 있도록 하려면 드라이브 공급자가 [Newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 메서드를 구현 해야 합니다 (예를 들어, 다음 코드에서는이 드라이브 공급자에 대 한 [Newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 메서드를 구현 하는 방법을 보여 줍니다.

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L42-L84 "AccessDBProviderSample02.cs")]

이 메서드의 재정의는 다음을 수행 해야 합니다.

- [PSDriveinfo *](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) 멤버가 있고 데이터 저장소에 대 한 연결을 만들 수 있는지 확인 하십시오.

- `New-PSDrive` cmdlet을 지원 하 여 드라이브를 만들고 연결 멤버를 채웁니다.

- 제안 된 드라이브에 대 한 [PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) 개체의 유효성을 검사 합니다.

- 필요한 성능 또는 안정성 정보를 사용 하 여 드라이브를 설명 하는 [PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) 개체를 수정 하거나 드라이브를 사용 하는 호출자에 게 추가 데이터를 제공 합니다.

- [WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) 메서드를 사용 하 여 오류를 처리 한 다음 `null`을 반환 합니다.

  이 메서드는 메서드에 전달 된 드라이브 정보 또는 공급자별 버전을 반환 합니다.

## <a name="attaching-dynamic-parameters-to-newdrive"></a>NewDrive에 동적 매개 변수 연결

드라이브 공급자가 지 원하는 `New-PSDrive` cmdlet에는 추가 매개 변수가 필요할 수 있습니다. 이러한 동적 매개 변수를 cmdlet에 연결 하기 위해 공급자는 [Newdrivedynamicparameters *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) 메서드를 구현 합니다. 이 메서드는 cmdlet 클래스 또는 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체와 유사한 구문 분석 특성이 있는 속성 및 필드가 있는 개체를 반환 합니다.

이 드라이브 공급자는이 메서드를 재정의 하지 않습니다. 그러나 다음 코드는이 메서드의 기본 구현을 보여 줍니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a>드라이브 제거

데이터베이스 연결을 종료 하려면 드라이브 공급자가 [Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) 메서드를 구현 해야 합니다 (예를 들어, 이 메서드는 공급자별 정보를 모두 정리 하 고 나 서 드라이브에 대 한 연결을 닫습니다.

다음 코드에서는이 드라이브 공급자에 대 한 [Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) 메서드를 구현 하는 방법을 보여 줍니다.

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L91-L116 "AccessDBProviderSample02.cs")]

드라이브를 제거할 수 있는 경우 메서드는 `drive` 매개 변수를 통해 메서드에 전달 된 정보를 반환 해야 합니다. 드라이브를 제거할 수 없는 경우 메서드는 예외를 작성 한 다음 `null`을 반환 해야 합니다. 공급자가이 메서드를 재정의 하지 않는 경우이 메서드의 기본 구현에서는 입력으로 전달 된 드라이브 정보만 반환 합니다.

## <a name="initializing-default-drives"></a>기본 드라이브 초기화

드라이브 공급자는 드라이브를 탑재 하는 데 [system.webserver](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) . n a m d. 예를 들어 컴퓨터가 도메인에 가입 되어 있는 경우 Active Directory 공급자는 기본 명명 컨텍스트로 드라이브를 탑재할 수 있습니다.

이 메서드는 초기화 된 드라이브 또는 빈 컬렉션에 대 한 드라이브 정보의 컬렉션을 반환 합니다. 이 메서드에 대 한 호출은 Windows PowerShell 런타임이 공급자를 초기화 하기 위해 [system.web](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) . n a m a.

이 드라이브 공급자는 [system.object](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) 를 재정의 하지 않습니다... n a m. 그러나 다음 코드는 빈 드라이브 컬렉션을 반환 하는 기본 구현을 보여 줍니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a>InitializeDefaultDrives 구현에 대해 기억할 사항

모든 드라이브 공급자는 사용자가 검색 기능을 지원할 수 있도록 루트 드라이브를 탑재 해야 합니다. 루트 드라이브에는 다른 탑재 된 드라이브의 루트로 사용 되는 위치가 나열 될 수 있습니다. 예를 들어 Active Directory 공급자는 DSE (루트 분산 시스템 환경)의 `namingContext` 특성에 있는 명명 컨텍스트를 나열 하는 드라이브를 만들 수 있습니다. 이렇게 하면 사용자가 다른 드라이브의 탑재 위치를 검색할 수 있습니다.

## <a name="code-sample"></a>코드 예제

전체 샘플 코드는 [AccessDbProviderSample02 코드 샘플](./accessdbprovidersample02-code-sample.md)을 참조 하세요.

## <a name="testing-the-windows-powershell-drive-provider"></a>Windows PowerShell 드라이브 공급자 테스트

Windows powershell 공급자를 Windows PowerShell에 등록 한 경우에는 파생에서 사용할 수 있는 모든 cmdlet을 포함 하 여 명령줄에서 지원 되는 cmdlet을 실행 하 여 테스트할 수 있습니다. 샘플 드라이브 공급자를 테스트해 보겠습니다.

1. `Get-PSProvider` cmdlet을 실행 하 여 공급자 목록을 검색 하 여 AccessDB 드라이브 공급자가 있는지 확인 합니다.

   **PS > `Get-PSProvider`**

   다음과 같은 출력이 나타납니다.

   ```output
   Name                 Capabilities                  Drives
   ----                 ------------                  ------
   AccessDB             None                          {}
   Alias                ShouldProcess                 {Alias}
   Environment          ShouldProcess                 {Env}
   FileSystem           Filter, ShouldProcess         {C, Z}
   Function             ShouldProcess                 {function}
   Registry             ShouldProcess                 {HKLM, HKCU}
   ```

2. 운영 체제에 대 한 **관리 도구의** **데이터 원본** 부분에 액세스 하 여 데이터베이스에 대 한 데이터베이스 서버 이름 (DSN)이 존재 하는지 확인 합니다. **사용자 DSN** 테이블에서 **MS Access 데이터베이스** 를 두 번 클릭 하 고 C:\ps\northwind.mdb. 드라이브 경로를 추가 합니다.

3. 샘플 드라이브 공급자를 사용 하 여 새 드라이브를 만듭니다.

   **PS > psdrive-name mydb-root c:\ps\northwind.mdb-psprovider AccessDb**

   다음과 같은 출력이 나타납니다.

   ```output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. 연결의 유효성을 검사 합니다. 연결은 드라이브의 멤버로 정의 되므로 Get-help Drive cmdlet을 사용 하 여 확인할 수 있습니다.

   > [!NOTE]
   > 공급자에 게 해당 상호 작용에 대 한 컨테이너 기능이 필요 하므로 사용자는 아직 공급자와의 상호 작용을 수행할 수 없습니다. 자세한 내용은 [Windows PowerShell 컨테이너 공급자 만들기](./creating-a-windows-powershell-container-provider.md)를 참조 하세요.

   **PS > (psdrive mydb). 연결**

   다음과 같은 출력이 나타납니다.

   ```output
   ConnectionString  : Driver={Microsoft Access Driver (*.mdb)};DBQ=c:\ps\northwind.mdb
   ConnectionTimeout : 15
   Database          : c:\ps\northwind
   DataSource        : ACCESS
   ServerVersion     : 04.00.0000
   Driver            : odbcjt32.dll
   State             : Open
   Site              :
   Container         :
   ```

5. 드라이브를 제거 하 고 셸을 종료 합니다.

   **PS > psdrive mydb**

   **PS > 종료**

## <a name="see-also"></a>참고 항목

[Windows PowerShell 공급자 만들기](./how-to-create-a-windows-powershell-provider.md)

[Windows PowerShell 공급자 디자인](./designing-your-windows-powershell-provider.md)

[기본 Windows PowerShell 공급자 만들기](./creating-a-basic-windows-powershell-provider.md)
