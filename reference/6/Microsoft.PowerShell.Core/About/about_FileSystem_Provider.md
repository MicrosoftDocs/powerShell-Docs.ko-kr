---
description: FileSystem
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_filesystem_provider?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 파일 시스템 공급자
ms.openlocfilehash: 24c30e311ba43842e759e884424ce3abfb92aae7
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221665"
---
# <a name="filesystem-provider"></a>파일 시스템 공급자

## <a name="provider-name"></a>공급자 이름
FileSystem

## <a name="drives"></a>드라이브

`C:`, `D:` ...

## <a name="capabilities"></a>기능

**필터** , **shouldprocess**

## <a name="short-description"></a>간단한 설명

파일 및 디렉터리에 대한 액세스를 제공합니다.

## <a name="detailed-description"></a>자세한 설명

PowerShell **FileSystem** 공급자를 사용 하 여 powershell에서 파일 및 디렉터리를 가져오고 추가, 변경 및 삭제할 수 있습니다.

**FileSystem** 드라이브는 컴퓨터의 디렉터리와 파일을 포함 하는 계층적 네임 스페이스입니다. **FileSystem** 드라이브는 논리적 또는 물리적 드라이브, 디렉터리 또는 매핑된 네트워크 공유 일 수 있습니다.

**FileSystem** 공급자는이 문서에서 설명 하는 다음과 같은 cmdlet을 지원 합니다.

- [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [Invoke-Item](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [Move-Item](xref:Microsoft.PowerShell.Management.Move-Item)
- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Get-ItemProperty](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [Clear-Item](xref:Microsoft.PowerShell.Management.Clear-Item)
- [Clear-ItemProperty](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Remove-ItemProperty](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [Get-Acl](xref:Microsoft.PowerShell.Security.Get-Acl)
- [Set-Acl](xref:Microsoft.PowerShell.Security.Set-Acl)
- [Get-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)
- [Set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

## <a name="types-exposed-by-this-provider"></a>이 공급자가 노출 하는 형식

파일은 [system.object](/dotnet/api/system.io.fileinfo) 클래스의 인스턴스입니다.  디렉터리는 [system.io.directoryinfo](/dotnet/api/system.io.directoryinfo) 클래스의 인스턴스입니다.

## <a name="navigating-the-filesystem-drives"></a>파일 시스템 드라이브 탐색

**FileSystem** 공급자는 컴퓨터의 논리 드라이브를 PowerShell 드라이브로 매핑하여 해당 데이터 저장소를 노출 합니다. **파일 시스템** 드라이브로 작업 하려면 드라이브 이름 뒤에 콜론 ()을 사용 하 여 위치를 드라이브로 변경할 수 있습니다 `:` .

```powershell
Set-Location C:
```

다른 PowerShell 드라이브에서 **FileSystem** 공급자를 사용할 수도 있습니다. 다른 위치에서 파일 또는 디렉터리를 참조 하려면 경로에 드라이브 이름 ( `C:` , `D:` , ...)을 사용 합니다.

> [!NOTE]
> PowerShell은 별칭을 사용 하 여 공급자 경로 작업을 수행할 수 있는 친숙 한 방법을 제공 합니다. `dir`및 등의 명령은 `ls` 이제 [Get childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)에 대 한 별칭입니다 `cd` .는 [집합 위치](xref:Microsoft.PowerShell.Management.Set-Location)에 대 한 별칭입니다. 및 `pwd` 은 [(는) 위치](xref:Microsoft.PowerShell.Management.Get-Location)에 대 한 별칭입니다.

## <a name="getting-files-and-directories"></a>파일 및 디렉터리 가져오기

`Get-ChildItem`Cmdlet은 현재 위치에 있는 모든 파일과 디렉터리를 반환 합니다. 검색을 위해 다른 경로를 지정 하 고 기본 제공 매개 변수를 사용 하 여 재귀 깊이를 필터링 및 제어할 수 있습니다.

```powershell
Get-ChildItem
```

Cmdlet 사용에 대 한 자세한 내용은 [가져오기-자식 항목](xref:Microsoft.PowerShell.Management.Get-ChildItem)을 참조 하세요.

## <a name="copying-files-and-directories"></a>파일 및 디렉터리 복사

`Copy-Item`Cmdlet은 지정한 위치에 파일 및 디렉터리를 복사 합니다.
매개 변수는와 유사 하 게 필터링 및 재귀적으로 사용할 수 있습니다 `Get-ChildItem` .

다음 명령은 경로 "C:\temp"의 모든 파일 및 디렉터리 \" 를 "C:\\temp" 폴더로 복사 합니다.

```powershell
Copy-Item -Path C:\temp\* -Destination C:\Windows\Temp -Recurse -File
```

`Copy-Item` 확인 메시지를 표시 하지 않고 대상 디렉터리의 파일을 덮어씁니다.

이 명령은 디렉터리의 `a.txt` 파일을 `C:\a` 디렉터리에 복사 `C:\a\bb` 합니다.

```powershell
Copy-Item -Path C:\a\a.txt -Destination C:\a\bb\a.txt
```

디렉터리의 모든 디렉터리와 파일 `C:\a` 을 디렉터리에 복사 `C:\c` 합니다. 복사할 디렉터리가 대상 디렉터리에 이미 있는 경우에는 Force 매개 변수를 사용하지 않은 한 명령이 실패합니다.

```powershell
Copy-Item -Path C:\a\* -Destination C:\c -Recurse
```

자세한 내용은 [복사 항목](xref:Microsoft.PowerShell.Management.Copy-Item)을 참조 하세요.

## <a name="moving-files-and-directories"></a>파일 및 디렉터리 이동

이 명령은 디렉터리의 `c.txt` 파일 `C:\a` 을 디렉터리로 이동 합니다 `C:\a\aa` .

```powershell
Move-Item -Path C:\a\c.txt -Destination C:\a\aa
```

이 명령은 이름이 같은 기존 파일을 자동으로 덮어쓰지 않습니다. cmdlet이 기존 파일을 덮어쓰도록 강제하려면 Force 매개 변수를 지정합니다.

이동할 디렉터리가 현재 위치인 경우에는 해당 디렉터리를 이동할 수 없습니다. `Move-Item`를 사용 하 여 현재 위치에서 디렉터리를 이동 하는 경우이 오류가 표시 됩니다.

```
C:\temp> Move-Item -Path C:\temp\ -Destination C:\Windows\Temp

Move-Item : Cannot move item because the item at 'C:\temp\' is in use.
At line:1 char:1
+ Move-Item C:\temp\ C:\temp2\
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Move-Item], PSInvalidOperationException
    + FullyQualifiedErrorId : InvalidOperation,Microsoft.PowerShell.Commands.MoveItemCommand
```

## <a name="managing-file-content"></a>파일 콘텐츠 관리

### <a name="get-the-content-of-a-file"></a>파일의 콘텐츠 가져오기

이 명령은 "Test.txt" 파일의 콘텐츠를 가져와 콘솔에 표시 합니다.

```powershell
Get-Content -Path Test.txt
```

파일 내용을 다른 cmdlet으로 파이프할 수 있습니다. 예를 들어 다음 명령은 파일의 내용을 읽은 `Test.txt` 다음 [convertto-html](xref:Microsoft.PowerShell.Utility.ConvertTo-Html) cmdlet에 대 한 입력으로 제공 합니다.

```powershell
Get-Content -Path Test.txt | ConvertTo-Html
```

공급자 경로에 달러 기호 ()를 접두사로 사용 하 여 파일의 내용을 검색할 수도 있습니다 `$` . 변수 명명 제한으로 인해 경로를 중괄호로 묶어야 합니다. 자세한 내용은 [about_Variables](about_Variables.md)를 참조 하세요.

```powershell
${C:\Windows\System32\Drivers\etc\hosts}
```

### <a name="add-content-to-a-file"></a>파일에 콘텐츠 추가

이 명령은 "test content" 문자열을 파일에 추가 합니다 `Test.txt` .

```powershell
Add-Content -Path test.txt -Value "test content"
```

파일의 기존 내용은 `Test.txt` 삭제 되지 않습니다.

### <a name="replace-the-content-of-a-file"></a>파일의 내용을 바꿉니다.

이 명령은 파일의 내용을 `Test.txt` "test content" 문자열로 바꿉니다.

```powershell
Set-Content -Path test.txt -Value "test content"
```

의 내용을 덮어씁니다 `Test.txt` . [새 항목](xref:Microsoft.PowerShell.Management.New-Item) Cmdlet의 **Value** 매개 변수를 사용 하 여 파일을 만들 때 파일에 콘텐츠를 추가할 수 있습니다.

### <a name="loop-through-the-contents-of-a-file"></a>파일의 콘텐츠를 반복 합니다.

기본적으로 cmdlet은 `Get-Content` 줄 끝 문자를 구분 기호로 사용 하므로 파일을 문자열 컬렉션으로 가져오고 각 줄을 파일의 한 문자열로 사용 합니다.

매개 변수를 사용 `-Delimiter` 하 여 대체 구분 기호를 지정할 수 있습니다. 이를 섹션의 끝 또는 다음 섹션의 시작을 나타내는 문자로 설정하면 파일을 논리적 부분으로 분할할 수 있습니다.

첫 번째 명령은 파일을 가져와 `Employees.txt` 섹션으로 분할 합니다. 각 섹션은 "직원의 끝 레코드" 라는 단어로 끝나는 후 변수에 저장 합니다 `$e` .

두 번째 명령은 배열 표기법을 사용 하 여에서 컬렉션의 첫 번째 항목을 가져옵니다 `$e` . PowerShell 배열은 0부터 시작 하므로 인덱스는 0을 사용 합니다.

Cmdlet에 대 한 자세한 내용은 `Get-Content` [get-help](xref:Microsoft.PowerShell.Management.Get-Content)의 도움말 항목을 참조 하세요.

배열에 대 한 자세한 내용은 [about_Arrays](../About/about_Arrays.md)를 참조 하세요.

```powershell
$e = Get-Content c:\test\employees.txt -Delimited "End Of Employee Record"
$e[0]
```

## <a name="managing-security-descriptors"></a>보안 설명자 관리

### <a name="view-the-acl-for-a-file"></a>파일에 대 한 ACL 보기

이 명령은 [accesscontrol-namespace. system.security.accesscontrol.filesecurity](/dotnet/api/system.security.accesscontrol.filesecurity) 개체를 반환 합니다.

```powershell
Get-Acl -Path test.txt | Format-List -Property *
```

이 개체에 대 한 자세한 내용은 명령을 [Get Member](xref:Microsoft.PowerShell.Utility.Get-Member) cmdlet에 파이프 합니다. 또는 MSDN (Microsoft Developer Network) 라이브러리의 "[System.security.accesscontrol.filesecurity](/dotnet/api/system.security.accesscontrol.filesecurity) 클래스"를 참조 하십시오.

### <a name="modify-the-acl-for-a-file"></a>파일에 대 한 ACL 수정

### <a name="create-and-set-an-acl-for-a-file"></a>파일에 대 한 ACL을 만들고 설정 합니다.

## <a name="creating-files-and-directories"></a>파일 및 디렉터리 만들기

### <a name="create-a-directory"></a>디렉터리 만들기

이 명령은 `logfiles` 드라이브에 디렉터리를 만듭니다 `C` .

```powershell
New-Item -Path c:\ -Name logfiles -Type directory
```

PowerShell에는 새 `mkdir` `md` 디렉터리를 만드는 데 [새 항목](xref:Microsoft.PowerShell.Management.New-Item) cmdlet을 사용 하는 함수 (별칭)도 포함 되어 있습니다.

### <a name="create-a-file"></a>파일 만들기

이 명령은 `log2.txt` 디렉터리에 파일을 만든 `C:\logfiles` 다음 "test log" 문자열을 파일에 추가 합니다.

```powershell
New-Item -Path c:\logfiles -Name log2.txt -Type file
```

### <a name="create-a-file-with-content"></a>콘텐츠를 포함하는 파일 만들기

디렉터리에 라는 파일을 만들고이 파일 `log2.txt` `C:\logfiles` 에 "test log" 문자열을 추가 합니다.

```powershell
New-Item -Path c:\logfiles -Name log2.txt -Type file -Value "test log"
```

## <a name="renaming-files-and-directories"></a>파일 및 디렉터리 이름 바꾸기

### <a name="rename-a-file"></a>파일 이름 바꾸기

이 명령은 `a.txt` 디렉터리의 파일 이름을 `C:\a` `b.txt` 다음과 같이 바꿉니다.

```powershell
Rename-Item -Path c:\a\a.txt -NewName b.txt
```

### <a name="rename-a-directory"></a>디렉터리 이름 바꾸기

이 명령은 디렉터리의 이름을 `C:\a\cc` `C:\a\dd` 다음과 같이 바꿉니다.

```powershell
Rename-Item -Path c:\a\cc -NewName dd
```

## <a name="deleting-files-and-directories"></a>파일 및 디렉터리 삭제

### <a name="delete-a-file"></a>파일 삭제

이 명령은 `Test.txt` 현재 디렉터리에서 파일을 삭제 합니다.

```powershell
Remove-Item -Path test.txt
```

### <a name="delete-files-using-wildcards"></a>와일드 카드를 사용 하 여 파일 삭제

이 명령은 현재 디렉터리에서 파일 이름 확장명이 인 모든 파일을 삭제 합니다 `.xml` .

```powershell
Remove-Item -Path *.xml
```

## <a name="starting-a-program-by-invoking-an-associated-file"></a>연결 된 파일을 호출 하 여 프로그램 시작

### <a name="invoke-a-file"></a>파일 호출

첫 번째 명령은 [get-help](xref:Microsoft.PowerShell.Management.Get-Service) cmdlet을 사용 하 여 로컬 서비스에 대 한 정보를 가져옵니다.

[내보내기-Csv](xref:Microsoft.PowerShell.Utility.Export-Csv) cmdlet으로 정보를 파이프 한 다음 해당 정보를 파일에 저장 `Services.csv` 합니다.

두 번째 명령은 [Invoke 항목](xref:Microsoft.PowerShell.Management.Invoke-Item) 을 사용 하 여 `services.csv` 확장과 연결 된 프로그램에서 파일을 엽니다 `.csv` .

```powershell
Get-Service | Export-Csv -Path services.csv
Invoke-Item -Path services.csv
```

## <a name="getting-files-and-folders-with-specified-attributes"></a>지정 된 특성을 사용 하 여 파일 및 폴더 가져오기

### <a name="get-system-files"></a>시스템 파일 가져오기

이 명령은 현재 디렉터리 및 하위 디렉터리에 있는 시스템 파일을 가져옵니다.

매개 변수를 사용 하 여 `-File` 디렉터리가 아닌 파일만 가져오고 매개 변수를 사용 하 여 `-System` "system" 특성이 있는 항목만 가져옵니다.

매개 변수를 사용 하 여 `-Recurse` 현재 디렉터리와 모든 하위 디렉터리의 항목을 가져옵니다.

```powershell
Get-ChildItem -File -System -Recurse
```

### <a name="get-hidden-files"></a>숨겨진 파일 가져오기

이 명령은 현재 디렉터리의 숨겨진 파일을 비롯한 모든 파일을 가져옵니다.

이 매개 변수는 두 개의 값이 있는 **Attributes** 매개 변수를 사용 합니다 .이 매개 변수는 `!Directory+Hidden` 숨겨진 파일을 가져오고 `!Directory` 다른 모든 파일을 가져옵니다.

```powershell
Get-ChildItem -Attributes !Directory,!Directory+Hidden
```

`dir -att !d,!d+h` 는이 명령과 동일 합니다.

### <a name="get-compressed-and-encrypted-files"></a>압축 및 암호화 된 파일 가져오기

이 명령은 압축 또는 암호화된 현재 디렉터리의 파일을 가져옵니다.

이 메서드는 `-Attributes` 매개 변수를 두 값 (및)으로 사용 `Compressed` `Encrypted` 합니다. 값은 `,` "OR" 연산자를 나타내는 쉼표로 구분 됩니다.

```powershell
Get-ChildItem -Attributes Compressed,Encrypted
```

## <a name="dynamic-parameters"></a>동적 매개 변수

동적 매개 변수는 PowerShell 공급자가 추가 하는 cmdlet 매개 변수 이며, 공급자 사용 드라이브에서 cmdlet을 사용 하는 경우에만 사용할 수 있습니다.

### <a name="encoding-microsoftpowershellcommandsfilesystemcmdletproviderencoding"></a>Encoding \<Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding\>

파일 인코딩을 지정합니다. 기본값은 ASCII입니다.

- **Ascii** : ascii (7 비트) 문자 집합에 대 한 인코딩을 사용 합니다.
- **BigEndianUnicode** : 빅 endian 바이트 순서를 사용 하 여 utf-16 형식으로 인코딩합니다.
- **문자열** : 문자열에 인코딩 형식을 사용 합니다.
- **Unicode** : 작은 endian 바이트 순서를 사용 하 여 utf-16 형식으로 인코딩합니다.
- **UTF7** : u t f-7 형식으로 인코딩합니다.
- **UTF8** : utf-8 형식으로 인코딩합니다.
- **UTF8BOM** : 바이트 순서 표시 (BOM)를 사용 하 여 utf-8 형식으로 인코딩합니다.
- **UF8NOBOM** : BOM (바이트 순서 표시) 없이 utf-8 형식으로 인코딩합니다.
- **UTF32** : u t f-32 형식으로 인코딩합니다.
- **기본값** : 설치 된 기본 코드 페이지에서 인코딩합니다.
- **OEM** : MS-DOS 및 콘솔 프로그램에 기본 인코딩을 사용 합니다.
- **알 수 없음** : 인코딩 유형을 알 수 없거나 잘못 되었습니다. 데이터가 Binary로 처리될 수 있습니다.

#### <a name="cmdlets-supported"></a>Cmdlet 지원

- [Add-Content](xref:Microsoft.PowerShell.Management.Add-Content)
- [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)
- [Set-Content](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="delimiter-systemstring"></a>Delimiter \<System.String\>

[Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)가 파일을 읽는 동안 파일을 개체로 나누는 데 사용하는 구분 기호를 지정합니다.

기본값은 `\n` 줄 끝 문자입니다.

텍스트 파일을 읽을 때 [Get Content](xref:Microsoft.PowerShell.Management.Get-Content) 는 각각 구분 기호 문자로 끝나는 문자열 개체의 컬렉션을 반환 합니다.

파일에 존재 하지 않는 구분 기호를 입력 하면 [Get Content](xref:Microsoft.PowerShell.Management.Get-Content) 는 전체 파일을 구분 되지 않은 단일 개체로 반환 합니다.

이 매개 변수를 사용하여 "End of Example"과 같은 파일 구분 기호를 지정하여 큰 파일을 여러 개의 더 작은 파일로 분할할 수 있습니다. 구분 기호는 보존되고(삭제되지 않음) 각 파일 섹션의 마지막 항목이 됩니다.

> [!NOTE]
> 현재 `-Delimiter` 매개 변수 값이 빈 문자열인 경우 [Get Content](xref:Microsoft.PowerShell.Management.Get-Content) 는 아무것도 반환 하지 않습니다.
> 이것은 알려진 문제입니다. 강제로 [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)가 전체 파일을 구분되지 않은 단일 문자열로 반환하게 하려면 파일에 존재하지 않는 값을 입력합니다.

#### <a name="cmdlets-supported"></a>Cmdlet 지원

- [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="wait-systemmanagementautomationswitchparameter"></a>Wait \<System.Management.Automation.SwitchParameter\>

내용이 파일에 추가되기를 기다립니다. 내용이 추가되면 추가된 내용을 반환합니다. 내용이 변경된 경우에는 전체 파일을 반환합니다.

기다리는 동안 [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)는 Ctrl+C를 눌러 사용자가 중단할 때까지 1초에 한 번씩 파일을 검사합니다.

#### <a name="cmdlets-supported"></a>Cmdlet 지원

- [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="attributes-flagsexpression"></a>Attributes \<FlagsExpression\>

지정된 특성을 갖는 파일 및 폴더를 가져옵니다. 이 매개 변수는 모든 특성을 지원하며 복잡한 특성 조합을 지정할 수 있도록 합니다.

`-Attributes`매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

`-Attributes`매개 변수는 다음 특성을 지원 합니다.

- **보관**
- **Compressed**
- **디바이스**
- **디렉터리**
- **암호화됨**
- **숨김**
- **보통**
- **NotContentIndexed**
- **라인인**
- **읽기 전용**
- **ReparsePoint**
- **SparseFile**
- **시스템**
- **임시**

이러한 특성에 대 한 설명은 [Fileattributes](/dotnet/api/system.io.fileattributes) 열거를 참조 하세요.

다음 연산자를 사용하여 특성을 결합할 수 있습니다.

- `!` -NOT
- `+` -및
- `,` -또는

연산자 및 해당 특성 사이에는 공백이 허용되지 않습니다. 그러나 쉼표 앞에는 공백이 허용됩니다.

#### <a name="cmdlets-supported"></a>Cmdlet 지원

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="directory-systemmanagementautomationswitchparameter"></a>Directory \<System.Management.Automation.SwitchParameter\>

디렉터리(폴더)를 가져옵니다.

`-Directory`매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

디렉터리만 가져오려면 매개 변수를 사용 하 `-Directory` 고 `-File` 매개 변수를 생략 합니다. 디렉터리를 제외 하려면 매개 변수를 사용 하 고 매개 변수를 `-File` 생략 `-Directory` 하거나 `-Attributes` 매개 변수를 사용 합니다.

#### <a name="cmdlets-supported"></a>Cmdlet 지원

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="file-systemmanagementautomationswitchparameter"></a>File \<System.Management.Automation.SwitchParameter\>

파일을 가져옵니다.

`-File`매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

파일만 가져오려면 매개 변수를 사용 하 `-File` 고 `-Directory` 매개 변수를 생략 합니다. 파일을 제외 하려면 매개 변수를 사용 하 고 매개 변수를 `-Directory` 생략 `-File` 하거나 `-Attributes` 매개 변수를 사용 합니다.

#### <a name="cmdlets-supported"></a>Cmdlet 지원

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="hidden-systemmanagementautomationswitchparameter"></a>Hidden \<System.Management.Automation.SwitchParameter\>

숨겨진 파일 및 디렉터리(폴더)만 가져옵니다. 기본적으로 [Get ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) 은 숨겨지지 않은 항목만 가져옵니다.

`-Hidden`매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

숨겨진 항목만 가져오려면 매개 변수 `-Hidden` , 해당 `h` 또는 `ah` 별칭 또는 매개 변수의 **숨겨진** 값을 사용 합니다 `-Attributes` . 숨겨진 항목을 제외 하려면 매개 변수를 생략 `-Hidden` 하거나 `-Attributes` 매개 변수를 사용 합니다.

#### <a name="cmdlets-supported"></a>Cmdlet 지원

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="readonly-systemmanagementautomationswitchparameter"></a>ReadOnly \<System.Management.Automation.SwitchParameter\>

읽기 전용 파일 및 디렉터리(폴더)만 가져옵니다.

`-ReadOnly`매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

읽기 전용 항목만 가져오려면 매개 변수의 `-ReadOnly` `ar` 별칭 또는 매개 변수의 **ReadOnly** 값을 사용 `-Attributes` 합니다. 읽기 전용 항목을 제외 하려면 `-Attributes` 매개 변수를 사용 합니다.

#### <a name="cmdlets-supported"></a>Cmdlet 지원

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="system-systemmanagementautomationswitchparameter"></a>System \<System.Management.Automation.SwitchParameter\>

시스템 파일 및 디렉터리(폴더)만 가져옵니다.

`-System`매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

시스템 파일 및 폴더만 가져오려면 매개 변수의 `-System` `as` 별칭 또는 매개 변수의 **시스템** 값을 사용 `-Attributes` 합니다. 시스템 파일 및 폴더를 제외 하려면 `-Attributes` 매개 변수를 사용 합니다.

#### <a name="cmdlets-supported"></a>Cmdlet 지원

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="newerthan-systemdatetime"></a>NewerThan \<System.DateTime\>

`$True` `LastWriteTime` 파일의 값이 지정 된 날짜 보다 크면를 반환 합니다. 그 외의 경우 `$False`를 반환합니다.

날짜/시간 개체와 같은 [datetime](/dotnet/api/system.datetime) 개체를 입력 합니다. 예를 들어, 날짜/ [시간](/dotnet/api/system.datetime) 개체 (예: [)](xref:Microsoft.PowerShell.Utility.Get-Date) 로 변환할 수 있는 문자열 `"August 10, 2011 2:00 PM"` 입니다.

#### <a name="cmdlets-supported"></a>Cmdlet 지원

- [Test-Path](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="olderthan-systemdatetime"></a>OlderThan \<System.DateTime\>

`$True` `LastWriteTime` 파일의 값이 지정 된 날짜 보다 작은 경우를 반환 합니다. 그 외의 경우 `$False`를 반환합니다.

날짜/시간 개체와 같은 [datetime](/dotnet/api/system.datetime) 개체를 입력 합니다. 예를 들어, 날짜/ [시간](/dotnet/api/system.datetime) 개체 (예: [)](xref:Microsoft.PowerShell.Utility.Get-Date) 로 변환할 수 있는 문자열 `"August 10, 2011 2:00 PM"` 입니다.

#### <a name="cmdlets-supported"></a>Cmdlet 지원

- [Test-Path](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="stream-systemstring"></a>Stream \<System.String\>

대체 데이터 스트림을 관리합니다. 스트림 이름을 입력합니다. 와일드 카드는 파일 시스템 드라이브의 항목 [가져오기](xref:Microsoft.PowerShell.Management.Get-Item) 및 [제거](xref:Microsoft.PowerShell.Management.Remove-Item) 명령에만 허용 됩니다.

#### <a name="cmdlets-supported"></a>Cmdlet 지원

- [Add-Content](xref:Microsoft.PowerShell.Management.Add-Content)
- [Clear-Content](xref:Microsoft.PowerShell.Management.Clear-Content)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Set-Content](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="raw-switchparameter"></a>Raw \<SwitchParameter\>

줄 바꿈 문자를 무시합니다. 내용을 단일 항목으로 반환합니다.

#### <a name="cmdlets-supported"></a>Cmdlet 지원

- [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="itemtype-string"></a>ItemType \<String\>

이 매개 변수를 사용 하 여 만들 항목의 tye을 지정할 수 있습니다. `New-Item`

이 매개 변수의 사용 가능한 값은 현재 사용 중인 공급자에 따라 달라 집니다.

드라이브에는 `FileSystem` 다음 값을 사용할 수 있습니다.

- 파일
- 디렉터리
- 값인 symboliclink
- 분기 동기화
- Hardlink create

### <a name="cmdlets-supported"></a>Cmdlet 지원

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

## <a name="using-the-pipeline"></a>파이프라인 사용

공급자 cmdlet은 파이프라인 입력을 허용 합니다. 파이프라인을 사용 하 여 cmdlet 간에 공급자 데이터를 전송 하 여 작업을 간소화할 수 있습니다.
공급자 cmdlet에서 파이프라인을 사용 하는 방법에 대 한 자세한 내용은이 문서 전체에서 제공 되는 cmdlet 참조를 참조 하세요.

## <a name="getting-help"></a>도움말 보기

Windows PowerShell 3.0부터는 이러한 cmdlet이 파일 시스템 드라이브에서 동작하는 방식을 설명하는 공급자 cmdlet에 대한 사용자 지정된 도움말 항목을 볼 수 있습니다.

파일 시스템 드라이브에 맞게 사용자 지정 된 도움말 항목을 보려면 파일 시스템 드라이브에서 [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 명령을 실행 하거나 `-Path` [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 의 매개 변수를 사용 하 여 파일 시스템 드라이브를 지정 합니다.

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path c:
```

## <a name="see-also"></a>참고 항목

[about_Providers](../About/about_Providers.md)
