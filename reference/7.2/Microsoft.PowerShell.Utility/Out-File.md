---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-file?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-File
ms.openlocfilehash: e3a066957ab1e6935049003f8ccf55aee8bb7c94
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599338"
---
# Out-File

## 개요
출력을 파일로 보냅니다.

## SYNTAX

### ByPath (기본값)

```
Out-File [-FilePath] <string> [[-Encoding] <Encoding>] [-Append] [-Force] [-NoClobber]
 [-Width <int>] [-NoNewline] [-InputObject <psobject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Out-File [[-Encoding] <Encoding>] -LiteralPath <string> [-Append] [-Force] [-NoClobber]
 [-Width <int>] [-NoNewline] [-InputObject <psobject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Out-File`Cmdlet은 출력을 파일로 보냅니다. PowerShell의 형식 지정 시스템을 암시적으로 사용 하 여 파일에 씁니다. 이 파일은 터미널과 동일한 표시 표현을 받습니다. 즉, 모든 입력 개체가 문자열인 경우를 제외 하 고는 출력이 프로그래밍 처리에 적합 하지 않을 수 있습니다.
출력에 대 한 매개 변수를 지정 해야 하는 경우 `Out-File` 리디렉션 연산자 () 대신를 사용 `>` 합니다. 리디렉션에 대 한 자세한 내용은 [about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)를 참조 하세요.

## 예제

### 예제 1: 출력 보내기 및 파일 만들기

이 예제에서는 로컬 컴퓨터의 프로세스 목록을 파일로 보내는 방법을 보여 줍니다. 파일이 없으면 `Out-File` 지정 된 경로에 파일을 만듭니다.

```powershell
Get-Process | Out-File -FilePath .\Process.txt
Get-Content -Path .\Process.txt
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     29    22.39      35.40      10.98   42764   9 Application
     53    99.04     113.96       0.00   32664   0 CcmExec
     27    96.62     112.43     113.00   17720   9 Code
```

`Get-Process`Cmdlet은 로컬 컴퓨터에서 실행 중인 프로세스 목록을 가져옵니다. **프로세스** 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Out-File` . `Out-File`**FilePath** 매개 변수를 사용 하 고 **Process.txt** 이라는 현재 디렉터리에 파일을 만듭니다. `Get-Content`명령은 파일에서 콘텐츠를 가져와 PowerShell 콘솔에 표시 합니다.

### 예 2: 기존 파일을 덮어쓰지 않도록 방지

이 예에서는 기존 파일을 덮어쓰지 않습니다. 기본적으로는 `Out-File` 기존 파일을 덮어씁니다.

```powershell
Get-Process | Out-File -FilePath .\Process.txt -NoClobber
```

```Output
Out-File : The file 'C:\Test\Process.txt' already exists.
At line:1 char:15
+ Get-Process | Out-File -FilePath .\Process.txt -NoClobber
+               ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
```

`Get-Process`Cmdlet은 로컬 컴퓨터에서 실행 중인 프로세스 목록을 가져옵니다. **프로세스** 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Out-File` . `Out-File`**FilePath** 매개 변수를 사용 하 고 **Process.txt** 이라는 현재 디렉터리의 파일에 쓰려고 합니다. **NoClobber** 매개 변수는 파일을 덮어쓰지 않도록 방지 하 고 파일이 이미 존재 한다는 메시지를 표시 합니다.

### 예제 3: ASCII 형식으로 파일에 출력 보내기

이 예제에서는 특정 인코딩 형식을 사용 하 여 출력을 인코딩하는 방법을 보여 줍니다.

```powershell
$Procs = Get-Process
Out-File -FilePath .\Process.txt -InputObject $Procs -Encoding ASCII -Width 50
```

`Get-Process`Cmdlet은 로컬 컴퓨터에서 실행 중인 프로세스 목록을 가져옵니다. **프로세스** 개체는 변수에 저장 됩니다 `$Procs` . `Out-File`**FilePath** 매개 변수를 사용 하 고 **Process.txt** 이라는 현재 디렉터리에 파일을 만듭니다. **InputObject** 매개 변수는 `$Procs` **Process.txt** 파일에 프로세스 개체를 전달 합니다. **Encoding** 매개 변수는 출력을 **ASCII** 형식으로 변환 합니다. **Width** 매개 변수는 파일의 각 줄을 50 자로 제한 하므로 일부 데이터가 잘릴 수 있습니다.

### 예제 4: 공급자를 사용 하 여 출력을 파일로 보내기

이 예제에서는 `Out-File` **파일 시스템** 공급자 드라이브에 없는 경우 cmdlet을 사용 하는 방법을 보여 줍니다. Cmdlet을 사용 `Get-PSProvider` 하 여 로컬 컴퓨터의 공급자를 확인 합니다. 자세한 내용은 [about_Providers](../Microsoft.Powershell.Core/About/about_Providers.md)를 참조하세요.

```
PS> Set-Location -Path Alias:

PS> Get-Location

Path
----
Alias:\

PS> Get-ChildItem | Out-File -FilePath C:\TestDir\AliasNames.txt

PS> Get-Content -Path C:\TestDir\AliasNames.txt

CommandType     Name
-----------     ----
Alias           % -> ForEach-Object
Alias           ? -> Where-Object
Alias           ac -> Add-Content
Alias           cat -> Get-Content
```

이 `Set-Location` 명령은 **Path** 매개 변수를 사용 하 여 현재 위치를 레지스트리 공급자로 설정 합니다 `Alias:` . `Get-Location`Cmdlet은에 대 한 전체 경로를 표시 합니다 `Alias:` .
`Get-ChildItem` 파이프라인의 개체를 cmdlet으로 보냅니다 `Out-File` . `Out-File`**FilePath** 매개 변수를 사용 하 여 출력에 대 한 전체 경로와 파일 이름을 지정 **C:\TestDir\AliasNames.txt** 합니다. `Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 PowerShell 콘솔에 파일의 콘텐츠를 표시 합니다.

## PARAMETERS

### -추가

기존 파일의 끝에 출력을 추가 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Encoding

대상 파일의 인코딩 유형을 지정합니다. 기본값은 `utf8NoBOM`입니다.

이 매개 변수에 허용 되는 값은 다음과 같습니다.

- `ascii`: ASCII (7 비트) 문자 집합에 대 한 인코딩을 사용 합니다.
- `bigendianunicode`: 빅 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.
- `bigendianutf32`: 빅 endian 바이트 순서를 사용 하 여 u t f-32 형식으로 인코딩합니다.
- `oem`: MS-DOS 및 콘솔 프로그램에 기본 인코딩을 사용 합니다.
- `unicode`: 작은 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.
- `utf7`: UTF-7 형식으로 인코딩합니다.
- `utf8`: UTF-8 형식으로 인코딩합니다.
- `utf8BOM`: 바이트 순서 표시 (BOM)를 사용 하 여 UTF-8 형식으로 인코딩합니다.
- `utf8NoBOM`: BOM (바이트 순서 표시) 없이 UTF-8 형식으로 인코딩합니다.
- `utf32`: U t f-32 형식으로 인코딩합니다.

PowerShell 6.2부터 **Encoding** 매개 변수를 사용 하 여 등록 된 코드 페이지의 숫자 id (예: `-Encoding 1251` ) 또는 등록 된 코드 페이지의 문자열 이름을 사용할 수도 있습니다 (예: `-Encoding "windows-1251"` ). 자세한 내용은 [인코딩에](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)대 한 .net 설명서를 참조 하세요.

> [!NOTE]
> **U t f-7** _은 더 이상 사용 하지 않는 것이 좋습니다. PowerShell 7.1에서는 `utf7` _ *Encoding** 매개 변수에 대해를 지정 하는 경우 경고가 기록 됩니다.

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: 1
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

출력 파일의 경로를 지정합니다.

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases: Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

읽기 전용 특성을 재정의 하 고 기존 읽기 전용 파일을 덮어씁니다. **Force** 매개 변수는 보안 제한을 재정의 하지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

파일에 기록할 개체를 지정합니다. 개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

출력 파일의 경로를 지정합니다. **LiteralPath** 매개 변수는 형식화 된 그대로 사용 됩니다.
와일드 카드 문자 허용 되지 않습니다. 이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요. 작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다. 자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NoClobber

**NoClobber** 는 기존 파일을 덮어쓰지 않도록 방지 하 고 파일이 이미 존재 한다는 메시지를 표시 합니다. 기본적으로 지정 된 경로에 파일이 있으면는 `Out-File` 경고 없이 파일을 덮어씁니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoNewline

파일에 기록 된 콘텐츠가 줄 바꿈 문자로 끝나지 않도록 지정 합니다. 입력 개체의 문자열 표현은 연결 되어 출력을 형성 합니다. 출력 문자열 사이에 공백이 나 줄바꿈 삽입 되지 않습니다. 마지막 출력 문자열 뒤에는 줄 바꿈이 추가 되지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -너비

출력의 각 줄에 포함되는 문자 수를 지정합니다. 이 문자보다 많으면 잘리거나 다음 줄로 넘어갑니다. 이 매개 변수를 사용 하지 않으면 호스트의 특성에 따라 너비가 결정 됩니다. PowerShell 콘솔의 기본값은 80 자입니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

cmdlet을 실행하기 전에 확인을 요청합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

cmdlet을 실행할 경우 발생하는 일을 표시합니다. cmdlet은 실행되지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.web. PSObject

모든 개체를로 파이프 할 수 있습니다 `Out-File` .

## 출력

### 없음

`Out-File` 는 출력을 생성 하지 않습니다.

## 참고

입력 개체는 터미널에 있을 때 자동으로 서식이 지정 되지만 cmdlet을 사용 `Format-*` 하 여 파일에 대 한 출력 형식을 명시적으로 제어할 수 있습니다. 예를 들면 `Get-Date | Format-List | Out-File out.txt`과 같습니다.

Cmdlet에 PowerShell 명령의 출력을 보내려면 파이프라인을 `Out-File` 사용 합니다. 또는 변수에 데이터를 저장 하 고 **InputObject** 매개 변수를 사용 하 여 cmdlet에 데이터를 전달할 수 있습니다 `Out-File` .

`Out-File` 데이터를 파일에 저장 하지만 파이프라인에 대 한 출력 개체를 생성 하지 않습니다.

## 관련 링크

[about_Providers](../Microsoft.Powershell.Core/About/about_Providers.md)

[about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[Out-Default](../Microsoft.PowerShell.Core/Out-Default.md)

[Out-Host](../Microsoft.PowerShell.Core/Out-Host.md)

[Out-Null](../Microsoft.PowerShell.Core/Out-Null.md)

[Out-String](Out-String.md)

[Tee-Object](Tee-Object.md)

