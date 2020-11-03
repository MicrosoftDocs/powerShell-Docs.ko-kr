---
description: 함수
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_function_provider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 함수 공급자
ms.openlocfilehash: ac2f09c6352f936a0b0fece108e87e3fe15b5998
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222745"
---
# <a name="function-provider"></a>함수 공급자

## <a name="provider-name"></a>공급자 이름

함수

## <a name="drives"></a>드라이브

`Function:`

## <a name="capabilities"></a>기능

**ShouldProcess**

## <a name="short-description"></a>간단한 설명

PowerShell에 정의 된 함수에 대 한 액세스를 제공 합니다.

## <a name="detailed-description"></a>자세한 설명

PowerShell **함수** 공급자를 통해 powershell에서 함수 및 필터를 가져오고 추가, 변경 및 삭제할 수 있습니다.

함수는 작업을 수행하는 명명된 코드 블록입니다. 함수 이름을 입력하면 함수 내의 코드가 실행됩니다. 필터는 작업 조건을 설정하는 명명된 코드 블록입니다. 명령에서와 같이 조건 대신 필터 이름을 입력할 수 있습니다 `Where-Object` .

**함수** 드라이브는 함수 및 필터 개체만 포함 하는 플랫 네임 스페이스입니다. 함수와 필터에는 둘 다 하위 항목이 없습니다.

**함수** 공급자는이 문서에서 설명 하는 다음과 같은 cmdlet을 지원 합니다.

- [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Clear-Item](xref:Microsoft.PowerShell.Management.Clear-Item)

## <a name="types-exposed-by-this-provider"></a>이 공급자가 노출 하는 형식

각 함수는 System.web. c o [.](/dotnet/api/system.management.automation.functioninfo) c o. c o. c o. 각 필터는 [system.web. FilterInfo](/dotnet/api/system.management.automation.filterinfo) 클래스의 인스턴스입니다.

## <a name="navigating-the-function-drive"></a>함수 드라이브 탐색

**함수** 공급자는 드라이브에 해당 데이터 저장소를 노출 합니다 `Function:` . 함수를 사용 하 여 작업 하려면 위치를 드라이브 ()로 변경할 수 있습니다 `Function:` `Set-Location Function:` . 또는 다른 PowerShell 드라이브에서 작업할 수 있습니다. 다른 위치에서 함수를 참조 하려면 경로에 드라이브 이름 ()을 사용 `Function:` 합니다.

```powershell
Set-Location Function:
```

파일 시스템 드라이브로 돌아가려면 드라이브 이름을 입력합니다. 예를 들어 다음과 같이 입력합니다.

```powershell
Set-Location C:
```

다른 PowerShell 드라이브에서 **함수** 공급자를 사용할 수도 있습니다. 다른 위치에서 함수를 참조 하려면 경로에 드라이브 이름을 사용 `Function:` 합니다.

> [!NOTE]
> PowerShell은 별칭을 사용 하 여 공급자 경로 작업을 수행할 수 있는 친숙 한 방법을 제공 합니다. `dir`및 등의 명령은 `ls` 이제 [Get childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)에 대 한 별칭입니다 `cd` .는 [집합 위치](xref:Microsoft.PowerShell.Management.Set-Location)에 대 한 별칭입니다. 및 `pwd` 은 [(는) 위치](xref:Microsoft.PowerShell.Management.Get-Location)에 대 한 별칭입니다.

## <a name="getting-functions"></a>함수 가져오기

이 명령은 현재 세션의 모든 함수 목록을 가져옵니다. 모든 PowerShell 드라이브에서이 명령을 사용할 수 있습니다.

```powershell
Get-ChildItem -Path Function:
```

함수 공급자에는 컨테이너가 없으므로에서 사용 하는 경우 위의 명령이 동일한 결과를 가집니다 `Get-ChildItem` .

```powershell
Get-ChildItem -Path Function:
```

아래와 같이 **정의** 속성에 액세스 하 여 함수의 정의를 검색할 수 있습니다.

```powershell
(Get-Item -Path function:more).Definition
```

달러 기호 ()로 시작 하는 공급자 경로를 사용 하 여 함수의 정의를 검색할 수도 있습니다 `$` .

```powershell
$function:more
```

### <a name="getting-selected-functions"></a>선택한 함수 가져오기

이 명령은 `man` 드라이브에서 함수를 가져옵니다 `Function:` . Cmdlet을 사용 하 여 `Get-Item` 함수를 가져옵니다. 파이프라인 연산자 ( `|` )는 결과를로 보냅니다 `Format-Table` . `-Wrap`매개 변수는 줄에 맞지 않는 텍스트를 다음 줄로 보냅니다. `-Autosize`매개 변수는 텍스트에 맞게 테이블 열의 크기를 조정 합니다.

```powershell
Get-Item -Path man | Format-Table -Wrap -Autosize
```

### <a name="working-with-function-provider-paths"></a>함수 공급자 경로 작업

이러한 명령은 모두 이라는 함수를 가져옵니다 `c:` . 첫 번째 명령은 모든 드라이브에서 사용할 수 있습니다. 두 번째 명령은 드라이브에서 사용 됩니다 `Function:` . 이름이 드라이브의 구문인 콜론으로 끝나기 때문에 드라이브 이름으로 경로를 한정해야 합니다. 드라이브 내에서 `Function:` 두 형식 중 하나를 사용할 수 있습니다. 두 번째 명령에서 점 ()은 `.` 현재 위치를 나타냅니다.

```
PS C:\> Get-Item -Path Function:c:
PS Function:\> Get-Item -Path .\c:
```

## <a name="creating-a-function"></a>함수 만들기

이 명령은 cmdlet을 사용 하 여 `New-Item` 라는 함수를 만듭니다 `Win32:` .
괄호로 묶은 식은 함수 이름으로 표시되는 스크립트 블록입니다.

```powershell
New-Item -Path Function:Win32: -Value {Set-Location C:\Windows\System32}
```

PowerShell 명령줄에 함수를 입력 하 여 만들 수도 있습니다. 예: tpe `Function:Win32: {Set-Location C:\Windows\System32}` . 드라이브에 있는 경우 `Function:` 드라이브 이름을 생략할 수 있습니다.

## <a name="deleting-a-function"></a>함수 삭제

이 명령은 `more:` 현재 세션에서 함수를 삭제 합니다.

```powershell
Remove-Item Function:more:
```

## <a name="changing-a-function"></a>함수 변경

이 명령은 cmdlet을 사용 하 여 `Set-Item` `prompt` 경로 앞에 시간을 표시 하도록 함수를 변경 합니다.

```powershell
Set-Item -Path Function:prompt -Value {
  'PS '+ (Get-Date -Format t) + " " + (Get-Location) + '> '
  }
```

### <a name="rename-a-function"></a>함수 이름 바꾸기

이 명령은 cmdlet을 사용 하 여 `Rename-Item` 함수의 이름을로 변경 `help` `gh` 합니다.

```powershell
Rename-Item -Path Function:help -NewName gh
```

## <a name="copying-a-function"></a>함수 복사

이 명령은 `prompt` 에 함수를 복사 하 여 `oldPrompt` 프롬프트 함수와 연결 된 스크립트 블록의 새 이름을 효과적으로 만듭니다.
프롬프트 함수를 변경하려는 경우 이 명령을 사용하여 원래 프롬프트 함수를 저장할 수 있습니다.
새 함수의 **Options** 속성 값은 `None` 입니다. **Options** 속성의 값을 변경 하려면를 사용 `Set-Item` 합니다.

```powershell
Copy-Item -Path Function:prompt -Destination Function:oldPrompt
```

## <a name="dynamic-parameters"></a>동적 매개 변수

동적 매개 변수는 PowerShell 공급자가 추가 하는 cmdlet 매개 변수 이며, 공급자 사용 드라이브에서 cmdlet을 사용 하는 경우에만 사용할 수 있습니다.

### <a name="options-systemmanagementautomationscopeditemoptions"></a>옵션 < [ScopedItemOptions] >

함수의 **Options** 속성 값을 결정 합니다.

- `None`: 옵션이 없습니다. 기본값은 `None`입니다.
- `Constant`: 함수는 삭제할 수 없으며 해당 속성을 변경할 수 없습니다. `Constant` 는 함수를 만들 때만 사용할 수 있습니다.
  기존 함수의 옵션을로 변경할 수는 없습니다 `Constant` .
- `Private`: 함수는 현재 범위 에서만 볼 수 있습니다.
- (자식 범위에 없음).
- `ReadOnly`: 매개 변수를 사용 하는 경우를 제외 하 고 함수의 속성을 변경할 수 없습니다 `-Force` . 를 사용 하 여 함수를 삭제할 수 있습니다 `Remove-Item` .
- `AllScope`: 함수는 생성 된 모든 새 범위로 복사 됩니다.

### <a name="cmdlets-supported"></a>Cmdlet 지원

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

- [Set-Item](xref:Microsoft.PowerShell.Management.Set-Item)

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
Get-Help Get-ChildItem -Path function:
```

## <a name="see-also"></a>참고 항목

[about_Functions](../About/about_Functions.md)

[about_Providers](../About/about_Providers.md)
