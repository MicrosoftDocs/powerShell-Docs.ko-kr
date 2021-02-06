---
description: PowerShell 실행 정책을 준수 하도록 스크립트에 서명 하는 방법을 설명 합니다.
Locale: en-US
ms.date: 07/31/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_signing?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Signing
ms.openlocfilehash: 560ecc385e970224a23af7a1195c99d8423f503f
ms.sourcegitcommit: 021ea294327dec542ec040619dac0d2171397a90
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/29/2020
ms.locfileid: "99602474"
---
# <a name="about-signing"></a>서명 정보

## <a name="short-description"></a>간단한 설명
PowerShell 실행 정책을 준수 하도록 스크립트에 서명 하는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

제한 된 실행 정책은 스크립트를 실행 하는 것을 허용 하지 않습니다. **AllSigned** 및 **RemoteSigned** 실행 정책은 PowerShell에서 디지털 서명이 없는 스크립트를 실행 하는 것을 방지 합니다.

이 항목에서는 실행 정책이 **RemoteSigned** 때에도 서명 되지 않은 선택한 스크립트를 실행 하는 방법 및 사용자가 직접 사용 하기 위해 스크립트에 서명 하는 방법을 설명 합니다.

PowerShell 실행 정책에 대 한 자세한 내용은 [about_Execution_Policies](about_Execution_Policies.md)를 참조 하세요.

## <a name="to-permit-signed-scripts-to-run"></a>서명 된 스크립트의 실행을 허용 하려면

컴퓨터에서 처음으로 PowerShell을 시작 하면 **제한** 된 실행 정책 (기본값)이 적용 될 가능성이 높습니다.

**제한** 된 정책은 스크립트를 실행 하는 것을 허용 하지 않습니다.

컴퓨터에서 유효한 실행 정책을 찾으려면 다음을 입력 합니다.

```powershell
Get-ExecutionPolicy
```

로컬 컴퓨터에서 작성 하는 서명 되지 않은 스크립트를 실행 하 고 다른 사용자 로부터 서명 된 스크립트를 실행 하려면 관리자 권한으로 실행 옵션을 사용 하 여 PowerShell을 시작 하 고 다음 명령을 사용 하 여 컴퓨터의 실행 정책을 **RemoteSigned** 로 변경 합니다.

```powershell
Set-ExecutionPolicy RemoteSigned
```

자세한 내용은 cmdlet에 대 한 도움말 항목을 참조 하세요 `Set-ExecutionPolicy` .

## <a name="running-unsigned-scripts-using-the-remotesigned-execution-policy"></a>RemoteSigned 실행 정책을 사용 하 여 서명 되지 않은 스크립트 실행

PowerShell 실행 정책이 **RemoteSigned** 인 경우 powershell은 인터넷에서 다운로드 한 서명 되지 않은 스크립트를 실행 하지 않습니다. 즉, 전자 메일 및 인스턴트 메시징 프로그램을 통해 수신 하는 서명 되지 않은 스크립트를 포함 합니다.

다운로드 한 스크립트를 실행 하려고 하면 PowerShell에서 다음과 같은 오류 메시지가 표시 됩니다.

```Output
The file <file-name> cannot be loaded. The file <file-name> is not digitally
signed. The script will not execute on the system. Please see "Get-Help
about_Signing" for more details.
```

스크립트를 실행 하기 전에 코드를 검토 하 여 신뢰 하는지 확인 합니다.
스크립트는 실행 프로그램과 동일한 효과를 가집니다.

서명 되지 않은 스크립트를 실행 하려면 Unblock-File cmdlet을 사용 하거나 다음 절차를 사용 합니다.

1. 컴퓨터에 스크립트 파일을 저장 합니다.
2. 시작을 클릭 하 고 내 컴퓨터를 클릭 한 다음 저장 된 스크립트 파일을 찾습니다.
3. 스크립트 파일을 마우스 오른쪽 단추로 클릭 한 다음 속성을 클릭 합니다.
4. 차단 해제를 클릭합니다.

인터넷에서 다운로드 한 스크립트가 디지털 서명 되어 있지만 아직 게시자를 신뢰 하도록 선택 하지 않은 경우 PowerShell에서 다음 메시지를 표시 합니다.

```Output
Do you want to run software from this untrusted publisher?
The file <file-name> is published by CN=<publisher-name>. This
publisher is not trusted on your system. Only run scripts
from trusted publishers.

[V] Never run  [D] Do not run  [R] Run once  [A] Always run
[?] Help (default is "D"):
```

게시자를 신뢰 하는 경우 "한 번 실행" 또는 "항상 실행"을 선택 합니다. 게시자를 신뢰 하지 않는 경우 "실행 안 함" 또는 "실행 안 함" 중 하나를 선택 합니다. "실행 안 함" 또는 "항상 실행"을 선택 하는 경우 PowerShell에서이 게시자에 대 한 메시지를 다시 표시 하지 않습니다.

## <a name="methods-of-signing-scripts"></a>스크립트 서명 방법

작성 하는 스크립트와 다른 원본에서 가져온 스크립트에 서명할 수 있습니다. 스크립트에 서명 하기 전에 각 명령을 검사 하 여 실행 해도 안전한 지 확인 합니다.

코드 서명에 대 한 모범 사례는 [코드 서명 모범 사례](/previous-versions/windows/hardware/design/dn653556(v=vs.85))를 참조 하세요.

스크립트 파일에 서명 하는 방법에 대 한 자세한 내용은 [get-authenticodesignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)를 참조 하십시오.

`New-SelfSignedCertificate`PowerShell 3.0의 PKI 모듈에 도입 된 cmdlet은 테스트에 적합 한 자체 서명 된 인증서를 만듭니다. 자세한 내용은 New-SelfSignedCertificate cmdlet에 대 한 도움말 항목을 참조 하세요.

스크립트에 디지털 서명을 추가 하려면 코드 서명 인증서를 사용 하 여 서명 해야 합니다. 스크립트 파일에 서명 하는 데 적합 한 두 가지 유형의 인증서는 다음과 같습니다.

- 인증 기관에서 만든 인증서: 유료로 공개 인증 기관에서 id를 확인 하 고 코드 서명 인증서를 제공 합니다. 신뢰할 수 있는 인증 기관에서 인증서를 구매 하는 경우 다른 컴퓨터가 인증 기관을 신뢰 하므로 Windows를 실행 하는 다른 컴퓨터의 사용자와 스크립트를 공유할 수 있습니다.

- 만든 인증서: 인증서를 만드는 기관에 해당 하는 자체 서명 된 인증서를 만들 수 있습니다. 이 인증서는 무료로 제공 되며 컴퓨터에서 스크립트를 작성, 서명 및 실행할 수 있습니다. 그러나 자체 서명 된 인증서로 서명 된 스크립트는 다른 컴퓨터에서 실행 되지 않습니다.

일반적으로 자체 서명 된 인증서를 사용 하 여 사용자가 직접 작성 하는 스크립트에 서명 하 고 안전 하 게 확인 한 다른 원본에서 가져온 스크립트에 서명 합니다. 기업 내 에서도 공유 되는 스크립트에는 적합 하지 않습니다.

자체 서명 된 인증서를 만드는 경우 인증서에서 강력한 개인 키 보호를 사용 하도록 설정 해야 합니다. 그러면 악성 프로그램이 사용자를 대신해 스크립트에 서명 하지 않습니다. 지침은이 항목의 끝부분에 나와 있습니다.

## <a name="create-a-self-signed-certificate"></a>자체 서명된 인증서 만들기

자체 서명 된 인증서를 만들려면 `New-SelfSignedCertificate` PKI 모듈에서 cmdlet을 사용 합니다. 이 모듈은 PowerShell 3.0에 도입 되었으며 Windows 8 및 Windows Server 2012에 포함 되어 있습니다. 자세한 내용은 cmdlet에 대 한 도움말 항목을 참조 하세요 `New-SelfSignedCertificate` .

이전 버전의 Windows에서 자체 서명 된 인증서를 만들려면 인증서 생성 도구를 사용 `MakeCert.exe` 합니다. 이 도구는 Microsoft .NET SDK (버전 1.1 이상) 및 Microsoft Windows SDK에 포함 되어 있습니다.

MakeCert.exe 도구의 구문 및 매개 변수 설명에 대 한 자세한 내용은 [인증서 생성 도구 (MakeCert.exe)](/previous-versions/dotnet/netframework-2.0/bfsktky3(v=vs.80))를 참조 하세요.

MakeCert.exe 도구를 사용 하 여 인증서를 만들려면 SDK 명령 프롬프트 창에서 다음 명령을 실행 합니다.

참고: 첫 번째 명령은 컴퓨터에 대 한 로컬 인증 기관을 만듭니다. 두 번째 명령은 인증 기관에서 개인 인증서를 생성 합니다.

참고: 정확히 표시 된 대로 명령을 복사 하거나 입력할 수 있습니다. 인증서 이름을 변경할 수는 있지만 대체가 필요 하지 않습니다.

```powershell
makecert -n "CN=PowerShell Local Certificate Root" -a sha1 `
-eku 1.3.6.1.5.5.7.3.3 -r -sv root.pvk root.cer `
-ss Root -sr localMachine

makecert -pe -n "CN=PowerShell User" -ss MY -a sha1 `
-eku 1.3.6.1.5.5.7.3.3 -iv root.pvk -ic root.cer
```

MakeCert.exe 도구는 개인 키 암호를 묻는 메시지를 표시 합니다. 암호는 사용자의 동의 없이 인증서를 사용 하거나 액세스할 수 없도록 합니다.
기억할 수 있는 암호를 만들고 입력 합니다. 이 암호는 나중에 인증서를 검색 하는 데 사용 합니다.

인증서가 올바르게 생성 되었는지 확인 하려면 다음 명령을 사용 하 여 컴퓨터의 인증서 저장소에 있는 인증서를 가져옵니다. 파일 시스템 디렉터리에서 인증서 파일을 찾을 수 없습니다.

PowerShell 프롬프트에서 다음을 입력 합니다.

```powershell
Get-ChildItem cert:\CurrentUser\my -codesigning
```

이 명령은 PowerShell 인증서 공급자를 사용 하 여 인증서에 대 한 정보를 확인 합니다.

인증서를 만든 경우 출력에는 다음과 같은 디스플레이에서 인증서를 식별 하는 **지문이** 표시 됩니다.

```Output
Directory: Microsoft.PowerShell.Security\Certificate::CurrentUser\My

Thumbprint                                Subject
----------                                -------
4D4917CB140714BA5B81B96E0B18AAF2C4564FDF  CN=PowerShell User ]
```

## <a name="sign-a-script"></a>스크립트 서명

자체 서명 된 인증서를 만든 후 스크립트에 서명할 수 있습니다. **AllSigned** 실행 정책을 사용 하는 경우 스크립트에 서명 하면 사용자의 컴퓨터에서 스크립트를 실행할 수 있습니다.

다음 샘플 스크립트는 `Add-Signature.ps1` 스크립트에 서명 합니다. 그러나 **AllSigned** 실행 정책을 사용 하는 경우 `Add-Signature.ps1` 스크립트를 실행 하기 전에 서명 해야 합니다.

> [!IMPORTANT]
> ASCII 또는 UTF8NoBOM 인코딩을 사용 하 여 스크립트를 저장 해야 합니다. 다른 인코딩을 사용 하는 스크립트 파일에 서명할 수 있습니다. 하지만 스크립트가 실행 되지 않거나 스크립트를 포함 하는 모듈을 가져오지 못했습니다.

이 스크립트를 사용 하려면 텍스트 파일에 다음 텍스트를 복사 하 고 이름을로 `Add-Signature.ps1` 합니다.

```powershell
## Signs a file
param([string] $file=$(throw "Please specify a filename."))
$cert = @(Get-ChildItem cert:\CurrentUser\My -codesigning)[0]
Set-AuthenticodeSignature $file $cert
```

스크립트 파일에 서명 하려면 `Add-Signature.ps1` PowerShell 명령 프롬프트에서 다음 명령을 입력 합니다.

```powershell
$cert = @(Get-ChildItem cert:\CurrentUser\My -codesigning)[0]
Set-AuthenticodeSignature add-signature.ps1 $cert
```

스크립트가 서명 된 후 로컬 컴퓨터에서 실행할 수 있습니다. 그러나 PowerShell 실행 정책에 신뢰할 수 있는 기관의 디지털 서명이 필요한 컴퓨터에서는 스크립트가 실행 되지 않습니다. 시도 하면 PowerShell에서 다음과 같은 오류 메시지를 표시 합니다.

```Output
The file C:\remote_file.ps1 cannot be loaded. The signature of the
certificate cannot be verified.
At line:1 char:15
+ .\ remote_file.ps1 <<<<
```

작성 하지 않은 스크립트를 실행할 때 PowerShell에서이 메시지가 표시 되는 경우 서명 되지 않은 스크립트를 처리 하는 것 처럼 파일을 처리 합니다. 코드를 검토 하 여 스크립트를 신뢰할 수 있는지 여부를 확인 합니다.

## <a name="enable-strong-private-key-protection-for-your-certificate"></a>인증서에 대해 강력한 개인 키 보호 사용

컴퓨터에 개인 인증서가 있는 경우 악성 프로그램은 사용자를 대신해 스크립트에 서명 하 여 PowerShell을 실행 하도록 인증할 수 있습니다.

사용자를 대신해 자동 서명을 방지 하려면 인증서 관리자를 사용 `Certmgr.exe` 하 여 서명 인증서를 파일로 내보냅니다 `.pfx` . 인증서 관리자는 Microsoft .NET SDK, Microsoft Windows SDK 및 internet Explorer에 포함 되어 있습니다.

인증서를 내보내려면:

1. 인증서 관리자를 시작 합니다.
2. PowerShell 로컬 인증서 루트에서 발급 한 인증서를 선택 합니다.
3. 내보내기를 클릭 하 여 인증서 내보내기 마법사를 시작 합니다.
4. "예, 개인 키를 내보냅니다."를 선택 하 고 다음을 클릭 합니다.
5. "강력한 보호 사용"을 선택 합니다.
6. 암호를 입력 한 다음 다시 입력 하 여 확인 합니다.
7. .Pfx 파일 이름 확장명을 가진 파일 이름을 입력 합니다.
8. 마침을 클릭합니다.

인증서를 다시 가져오려면:

1. 인증서 관리자를 시작 합니다.
2. 가져오기를 클릭 하 여 인증서 가져오기 마법사를 시작 합니다.
3. 내보내기 프로세스 중에 만든 .pfx 파일의 위치를 엽니다.
4. 암호 페이지에서 "강력한 개인 키 보호 사용"을 선택 하 고 내보내기 프로세스 중에 할당 한 암호를 입력 합니다.
5. 개인 인증서 저장소를 선택 합니다.
6. 마침을 클릭합니다.

## <a name="prevent-the-signature-from-expiring"></a>서명이 만료 되지 않도록 방지

스크립트의 디지털 서명은 서명 인증서가 만료 될 때까지 유효 하거나, 타임 스탬프 서버에서 서명 인증서가 유효한 동안 스크립트가 서명 되었는지 확인할 수 있을 때까지 유효 합니다.

대부분의 서명 인증서는 1 년 동안만 유효 하므로 타임 스탬프 서버를 사용 하면 사용자가 스크립트를 사용 하 여 많은 연도를 사용할 수 있습니다.

## <a name="see-also"></a>참고 항목

[about_Execution_Policies](about_Execution_Policies.md)

[about_Profiles](about_Profiles.md)

[Get-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[Set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

[코드 서명 소개](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537361(v=vs.85))
