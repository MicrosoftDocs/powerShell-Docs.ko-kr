---
ms.date: 06/12/2017
title: 새로 제공되거나 업데이트된 cmdlet
description: Windows PowerShell 5.1에는 새로 제공되거나 업데이트된 cmdlet이 여러 개 포함되어 있습니다.
ms.openlocfilehash: bdfbe5a263864a172aefb0aa5731f59b95ab43ca
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663227"
---
# <a name="new-and-updated-cmdlets"></a>새로 제공되거나 업데이트된 cmdlet

커뮤니티 피드백에 따라 새로운 cmdlet을 추가하고 기존 cmdlet을 업데이트했습니다.

## <a name="archive-cmdlets"></a>보관 cmdlet

두 가지 새 cmdlet `Compress-Archive` 및 `Expand-Archive`를 사용하여 ZIP 파일을 압축하고 확장할 수 있습니다.

자세한 내용은 [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/) 모듈 설명서를 참조하세요.

## <a name="catalog-cmdlets"></a>카탈로그 Cmdlet

두 개의 새로운 cmdlet을 Microsoft.PowerShell.Security 모듈에 추가했습니다.

- [New-FileCatalog](/powershell/module/microsoft.powershell.security/New-FileCatalog)
- [Test-FileCatalog](/powershell/module/microsoft.powershell.security/Test-FileCatalog)

이 두 가지 cmdlet은 Windows 카탈로그 파일을 생성하고 유효성을 검사합니다.

## <a name="clipboard-cmdlets"></a>클립보드 cmdlet

`Get-Clipboard` 및 `Set-Clipboard`를 사용하면 Windows PowerShell 세션 간에 콘텐츠를 더 쉽게 전송할 수 있습니다. 클립보드 cmdlet은 이미지, 오디오 파일, 파일 목록 및 텍스트를 지원합니다.

자세한 내용은 다음을 참조하세요.

- [Get-Clipboard](/powershell/module/Microsoft.PowerShell.Management/Get-Clipboard)
- [Set-Clipboard](/powershell/module/Microsoft.PowerShell.Management/Set-Clipboard)

## <a name="cryptographic-message-syntax-cms-cmdlets"></a>암호화 메시지 구문(CMS) cmdlet

암호화 메시지 구문 cmdlet은 [RFC5652](https://tools.ietf.org/html/rfc5652.html) 문서에 기록된 대로 메시지를 암호로 보호하기 위해 IETF 표준 형식을 사용하는 콘텐츠의 암호화 및 암호 해독을 지원합니다.

CMS 암호화 표준은 공개 키 암호화를 구현하는데, 여기서는 콘텐츠를 암호화하는 데 사용되는 키(‘공개 키’)와 콘텐츠를 암호 해독하는 데 사용되는 키(‘프라이빗 키’)가 구분됩니다.  

공개 키는 광범위하게 공유할 수 있으며 중요한 데이터가 아닙니다. 공개 키로 암호화된 모든 콘테츠는 프라이빗 키로만 암호 해독할 수 있습니다. 자세한 내용은 [공개 키 암호화](https://en.wikipedia.org/wiki/Public-key_cryptography)를 참조하세요.

자세한 내용은 다음을 참조하세요.

- [Get-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Get-CmsMessage)
- [Protect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage)
- [Unprotect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/unprotect-CmsMessage)

PowerShell에서 인증서가 데이터 암호화 인증서로 식별되려면 고유 키 사용 식별자(EKU)(예: ‘코드 서명' 또는 ‘암호화된 메일’)가 필요합니다. 인증서 공급자에서 문서 암호화 인증서를 보려면 `Get-ChildItem`의 **DocumentEncryptionCert** 동적 매개 변수를 사용하면 됩니다.

```powershell
Get-ChildItem Cert:\CurrentUser -DocumentEncryptionCert -Recurse
```

## <a name="extract-and-parse-structured-objects-from-string-content"></a>문자열 콘텐츠에서 구조적 개체 추출 및 구문 분석

### <a name="convertfrom-string"></a>ConvertFrom-String

새 `ConvertFrom-String` cmdlet은 다음 두 가지 모드를 지원합니다.

- 기본 구분 기호로 분리된 구문 분석
- 자동 생성된 예제 기반 구문 분석

기본적으로 구분 구문 분석에서는 입력을 공백으로 분할하고 결과 그룹에 속성 이름을 할당합니다.

**UpdateTemplate** 매개 변수는 학습 알고리즘의 결과를 템플릿 파일의 설명에 저장합니다. 이 매개 변수는 학습 프로세스(가장 느린 단계)를 일회 비용으로 만듭니다. 인코딩된 학습 알고리즘이 포함된 템플릿에서 `ConvertFrom-String`을 실행하면 거의 즉각적입니다.

자세한 내용은 [ConvertFrom-String](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String)을 참조하세요.

### <a name="convert-string"></a>Convert-String

`Convert-String`을 사용하여 텍스트가 어떻게 표시되는지에 대한 이전 및 이후 예제를 제공할 수 있습니다. 이 cmdlet은 자동으로 텍스트 서식을 지정합니다.

자세한 내용은 [Convert-String](/powershell/module/Microsoft.PowerShell.Utility/Convert-String)을 참조하세요.

## <a name="updates-to-fileinfo-object"></a>FileInfo 개체에 대한 업데이트

파일 버전 정보는 잘못될 수 있습니다. 특히 파일이 패치된 경우는 더욱 그렇습니다. WMF 5.0에서는 새로운 **FileVersionRaw** 및 **ProductVersionRaw** 스크립트 속성을 **FileInfo** 개체에 추가합니다.
다음은 powershell.exe에 대해 표시되는 속성입니다($pid는 PowerShell 프로세스의 ID로 간주).

```powershell
Get-Process -Id $pid -FileVersionInfo | Format-List *version*
```

```Output
FileVersionRaw    : 10.0.17763.1
ProductVersionRaw : 10.0.17763.1
FileVersion       : 10.0.17763.1 (WinBuild.160101.0800)
ProductVersion    : 10.0.17763.1
```

## <a name="format-hex"></a>Format-Hex

`Format-Hex`를 사용하면 텍스트 또는 이진 데이터를 16진수 형식으로 볼 수 있습니다.

자세한 내용은 [Format-Hex](/powershell/module/microsoft.powershell.utility/format-hex)를 참조하세요.

## <a name="get-childitem-has--depth-parameter"></a>Get-ChildItem의 -Depth 매개 변수

이제 `Get-ChildItem`은 **Recurse** 와 함께 사용되어 재귀를 제한하는 **Depth** 매개 변수를 제공합니다.

## <a name="modules-support-for-declaring-version-ranges-1-etc"></a>모듈의 버전 범위 선언(1.* 등) 지원

이제 **MinimumVersion** 및 **MaximumVersion** 을 결합하여 특정 범위 내의 모듈을 가져올 수 있습니다. 또한 매개 변수는 와일드 카드를 지원합니다.

```powershell
Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*
```

```Output
VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```

## <a name="new-guid"></a>New-Guid

고유 식별자에 필요한 많은 시나리오가 있습니다. `New-GUID` cmdlet은 새 GUID를 만드는 간단한 방법을 제공합니다.

```powershell
New-Guid
```

```Output
Guid
----
e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
```

## <a name="nonewline-parameter"></a>NoNewLine 매개 변수

이제 `Out-File`, `Add-Content` 및 `Set-Content`는 출력 뒤에 오는 새 줄을 생략하는 새로운 **NoNewline** 스위치를 제공합니다. 다음은 그 예입니다.

```powershell
"This is " | Out-File -FilePath Example.txt -NoNewline
"a single " | Add-Content -Path Example.txt -NoNewline
"sentence." | Add-Content -Path Example.txt -NoNewline
Get-Content .\Example.txt
```

```Output
This is a single sentence.
```

**NoNewline** 을 지정하지 않으면 각 조각이 별도의 줄에 있게 됩니다.

```powershell
"This is " | Out-File -FilePath Example.txt
"a single " | Add-Content -Path Example.txt
"sentence." | Add-Content -Path Example.txt
Get-Content .\Example.txt
```

```Output
This is
a single
sentence.
```

## <a name="interact-with-symbolic-links-using-improved-item-cmdlets"></a>향상된 Item cmdlet을 사용하여 기호화된 링크 조작

바로 가기 링크를 지원하기 위해 Item cmdlet과 몇 가지 관련 cmdlet이 확장되었습니다.

### <a name="symbolic-link-files"></a>바로 가기 링크 파일

이 예제에서는 C:\Temp에서 $pshome\profile.ps1에 연결되는 MySymLinkFile.txt라는 새로운 바로 가기 링크 파일을 만듭니다. 세 가지 예제에서 모두 동일한 결과가 생성됩니다.

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="symbolic-link-directories"></a>바로 가기 링크 디렉터리

이 예제에서는 C:\Temp에서 $pshome 폴더에 연결되는 MySymLinkDir이라는 새로운 바로 가기 링크 디렉터리를 만듭니다. 세 가지 예제에서 모두 동일한 결과가 생성됩니다.

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkDir -Value $pshome
```

### <a name="hard-links"></a>하드 링크

위에서 설명한 대로 허용되는 **경로** 및 **이름** 의 동일한 조합입니다.

```powershell
New-Item -ItemType HardLink -Path C:\Temp -Name MyHardLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="directory-junctions"></a>디렉터리 연결

위에서 설명한 대로 허용되는 **경로** 및 **이름** 의 동일한 조합입니다.

```powershell
New-Item -ItemType Junction -Path C:\Temp\MyJunctionDir -Value $pshome
```

### <a name="get-childitem"></a>Get-ChildItem

이제 `Get-ChildItem`은 **Mode** 속성에서 'l'를 표시하여 바로 가기 링크 파일 또는 디렉터리를 나타낼 수 있습니다.

```powershell
Get-ChildItem C:\Temp | sort LastWriteTime -Descending

Directory: C:\Temp

Mode       LastWriteTime Length Name
----       ------------- ------ ----
-a---- 6/13/2014 3:00 PM     16 File.txt
d----- 6/13/2014 3:00 PM        Directory
-a---l 6/13/2014 3:21 PM      0 MySymLinkFile.txt
d----l 6/13/2014 3:22 PM        MySymLinkDir
-a---l 6/13/2014 3:23 PM  23304 MyHardLinkFile.txt
d----l 6/13/2014 3:24 PM        MyJunctionDir
```

### <a name="remove-item"></a>Remove-Item

다른 항목 형식을 제거하는 것처럼 바로 가기 링크를 제거할 수 있습니다.

```powershell
Remove-Item C:\Temp\MySymLinkFile.txt
Remove-Item C:\Temp\MySymLinkDir
```

**Force** 매개 변수를 사용하여 대상 디렉터리의 파일과 바로 가기 링크를 제거합니다.

```powershell
Remove-Item C:\Temp\MySymLinkDir -Force
```

## <a name="new-temporaryfile"></a>New-TemporaryFile

경우에 따라 스크립트에서 임시 파일을 만들어야 합니다. 이제 `New-TemporaryFile` cmdlet으로 이 작업을 수행할 수 있습니다.

```powershell
$tempFile = New-TemporaryFile
$tempFile.FullName
```

```Output
C:\Users\user1\AppData\Local\Temp\tmp375.tmp
```

## <a name="network-switch-management-with-powershell"></a>PowerShell을 사용하여 네트워크 스위치 관리

WMF 5.0에서 도입된 네트워크 스위치 cmdlet을 사용하면 스위치, VLAN(가상 LAN) 및 기본 계층 2 네트워크 스위치 포트 구성을 Windows Server 2012 R2 로고 인증 네트워크 스위치에 적용할 수 있습니다. 이러한 cmdlet을 사용하여 다음을 수행할 수 있습니다.

- 다음과 같은 전역 스위치 구성:
  - 호스트 이름 설정
  - 스위치 배너 설정
  - 구성 유지
  - 기능을 사용하거나 사용하지 않도록 설정

- VLAN 구성:
  - VLAN 만들기 또는 제거
  - VLAN을 사용하거나 사용하지 않도록 설정
  - VLAN 열거
  - VLAN의 식별 이름 설정

- 계층 2 포트 구성:
  - 포트 열거
  - 포트를 사용하거나 사용하지 않도록 설정
  - 포트 모드 및 속성 설정
  - 포트의 트렁크 또는 액세스에 VLAN 추가 또는 연결

자세한 내용은 [NetworkSwitchManager](/powershell/module/networkswitchmanager/) 설명서를 참조하세요.

## <a name="generate-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a>ODataUtils를 사용하여 OData 엔드포인트에 따라 PowerShell cmdlet 생성

ODataUtils 모듈에서는 OData를 지원하는 REST 엔드포인트에서 PowerShell cmdlet을 생성할 수 있습니다. Microsoft.PowerShell.ODataUtils 모듈에는 다음 기능이 포함됩니다.

- 서버 쪽 엔드포인트와 클라이언트 쪽 사이에서 추가 정보 연결
- 클라이언트 쪽 페이징 지원
- -Select 매개 변수를 사용하여 서버 쪽 필터링
- 웹 요청 헤더에 대한 지원

`Export-ODataEndPointProxy` cmdlet에서 생성된 프록시 cmdlet은 **정보** 스트림의 서버 쪽 OData 엔드포인트에서 추가 정보를 제공합니다.

```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
```

다음 예제에서는 최상위 제품을 검색하고 `$infoStream` 변수로 출력을 캡처합니다.

**IncludeTotalResponseCount** 매개 변수를 지정하여 서버에서 사용할 수 있는 모든 **Product** 레코드의 총 개수를 가져옵니다.

```powershell
Import-Module $generatedProxyModuleDir -Force
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
$additionalInfo['odata.count']
```

클라이언트 쪽 페이징 지원을 사용하여 서버에서 레코드를 일괄 처리로 가져올 수 있습니다. 이 방법은 네트워크를 통해 서버에서 많은 양의 데이터를 가져와야 하는 경우에 유용합니다.

```powershell
$skipCount = 0
$batchSize = 3
while($skipCount -le $additionalInfo['odata.count'])
{
  Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
  $skipCount += $batchSize
}
```

생성된 프록시 cmdlet은 클라이언트에 필요한 레코드 속성만 받는 필터로 사용되는 **Select** 매개 변수를 지원합니다. 필터링은 서버에서 수행되므로 네트워크를 통해 전송되는 데이터의 양이 줄어듭니다.

```powershell
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

이제 `Export-ODataEndpointProxy` cmdlet 및 이 cmdlet에서 생성된 프록시 cmdlet은 **Headers** 매개 변수를 지원합니다. OData 엔드포인트에 필요한 추가 정보를 채널로 보내는 데 헤더를 사용할 수 있습니다.

다음 예제에서는 구독 키가 포함된 해시 테이블이 **Headers** 매개 변수에 제공됩니다. 이 예제는 인증에 구독 키가 필요한 서비스에 대한 일반적인 예제입니다.

```powershell
Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
