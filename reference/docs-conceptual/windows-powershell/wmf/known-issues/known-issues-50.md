---
ms.date: 06/12/2017
title: WMF 5.0의 알려진 문제
description: WMF 5.0의 알려진 문제
ms.openlocfilehash: 3f8dcf0f7aab27ff9d3c3a17377959988844a430
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663357"
---
# <a name="known-issues-in-wmf-50"></a>WMF 5.0의 알려진 문제

## <a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a>처음으로 사용할 때 PowerShell 바로 가기가 끊어짐

**해결 방법:** 다음 작업 중 하나를 수행하세요.

1. PowerShell 바로 가기를 마우스 오른쪽 단추로 클릭합니다. “Windows PowerShell”을 선택하여 낮은 권한 모드로 시작합니다.
2. PowerShell 바로 가기를 마우스 오른쪽 단추로 클릭합니다. “Windows PowerShell”을 마우스 오른쪽 단추로 클릭하고 “관리자 권한으로 실행”을 선택하여 관리자 모드로 시작합니다.

위 작업 중 하나를 수행했으면 PowerShell 바로 가기가 작동합니다. 이러한 작업은 한 번만 수행해야 합니다.

## <a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a>PowerShell 모듈 및 DSC 리소스가 Windows 7의 ExecutionPolicy에 대해 오류를 보고함

Windows 7에서 PowerShell 모듈 및 DSC 리소스를 사용하면 ExecutionPolicy에 대해 오류가 보고될 수 있습니다.

**해결 방법:** 다음 명령을 관리자 PowerShell 세션에서 실행(관리자 권한으로 실행)하여 ExecutionPolicy를 **RemoteSigned** 로 설정하세요.

```powershell
Set-ExecutionPolicy RemoteSigned
```

## <a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a>이전 원격 Exchange 엔드포인트에 연결하면 충돌이 발생함

이전 Exchange 엔드포인트는 새 엔드포인트로 리디렉션됩니다. 충돌을 발생시키는 리디렉션 논리에 버그가 있습니다.

**해결 방법:** 새 엔드포인트에 직접 연결하세요.

## <a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a>Windows Server 2012 R2에 WMF 5.0 설치 후 소프트웨어 인벤토리 로깅 기능이 잘못 중지됨

SIL이 이미 실행되고 있는 Windows Server 2012 R2에 WMF 5.0을 설치하면 소프트웨어 인벤토리 로깅 기능이 설치 후 잘못 중지됩니다.

**해결 방법:** 설치 프로세스에서 소프트웨어 인벤토리 로깅 기능을 잘못 중지할 수 있으므로 WMF 설치 후에 `Start-SilLogging` cmdlet을 한 번 실행하세요.

## <a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a>-LiteralPath 및 -Recurse가 함께 사용되는 경우 `Get-ChildItem`이 작동하지 않음

디렉터리 이름에 잘못된 와일드카드 문자가 포함된 경우 -LiteralPath와 -Recurse를 함께 사용하면 `Get-ChildItem`에서 예상된 결과를 생성하지 않습니다.

**해결 방법:** 적합하지는 않지만 현재 해결 방법은 cmdlet을 사용하지 않고 스크립트에서 재귀를 구현하는 것입니다.

## <a name="sysprep-fails-after-wmf-50-installation"></a>WMF 5.0 설치 후 Sysprep 실패

이 문제에 대한 해결 방법에는 실행 중인 Windows Server의 버전에 따라 두 가지가 있습니다.

**해결 방법:**

- **Windows Server 2008 R2** 를 실행 중인 시스템의 경우
  1. 관리자 권한으로 PowerShell을 엽니다.
  2. 다음 명령을 실행합니다.

     ```powershell
     Set-SilLogging -TargetUri https://BlankTarget -CertificateThumbprint 0123456789
     ```

  3. 명령을 실행하고 예상되는 오류는 무시합니다.

     ```powershell
     Publish-SilData
     ```

  4. \Windows\System32\Logfiles\SIL\ 디렉터리에 있는 파일을 삭제합니다.

     ```powershell
     Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
     ```

  5. 모든 사용 가능한 중요 Windows 업데이트를 설치하고 Sysyprep 작업을 정상적으로 시작합니다.

- **Windows Server 2012** 를 실행 중인 시스템의 경우
  1. Sysprep을 실행할 서버에서 WMF 5.0을 설치한 후 관리자로 로그인합니다.
  2. `\Windows\System32\Sysprep\ActionFiles\` 디렉터리의 Generize.xml을 Windows 디렉터리 외부 위치(예: `C:\`)에 복사합니다.
  3. Generalize.xml 복사본을 메모장으로 엽니다.
  4. 다음 텍스트를 찾아 제거합니다. 각 텍스트를 한 번씩 삭제해야 합니다(문서의 끝 부분에 있음).

     ```xml
     <sysprepOrder order="0x3200"></sysprepOrder>
     <sysprepOrder order="0x3300"></sysprepOrder>
     ```

  5. Generalize.xml의 편집된 복사본을 저장하고 파일을 닫습니다.
  6. 관리자 권한으로 명령 프롬프트를 엽니다.
  7. 다음 명령을 실행하여 system32 폴더에서 Generalize.xml 파일의 소유권을 갖도록 합니다.

     ```powershell
     Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

  8. 다음 명령을 실행하여 파일에 대한 적절한 권한을 설정합니다.

     ```powershell
     Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
     ```

     - 확인 프롬프트에서 예를 선택합니다.
     - `<AdministratorUserName>`을 컴퓨터에서 관리자인 사용자 이름으로 대체해야 합니다. 예를 들어, "Administrator"가 있습니다.

  9. 다음 명령을 사용하여 편집 및 저장한 파일을 Sysprep 디렉터리에 복사합니다.

     ```powershell
     xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

     - 예를 선택하여 덮어씁니다(덮어쓸지 여부를 묻는 메시지가 표시되지 않는다면, 입력한 경로를 다시 확인하세요.).
     - Generalize.xml의 편집 복사본이 C:\에 복사되었다고 가정합니다.

  10. 이제 이 해결 방법으로 Generalize.xml이 업데이트됩니다. 활성화된 일반화 옵션으로 Sysprep을 실행하세요.
