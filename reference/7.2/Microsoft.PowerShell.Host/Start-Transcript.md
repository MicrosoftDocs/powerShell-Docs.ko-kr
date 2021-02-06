---
external help file: Microsoft.PowerShell.ConsoleHost.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Host
ms.date: 01/26/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.host/start-transcript?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Transcript
ms.openlocfilehash: d0987c77e3c2bb8cee08e67610cd6fe4fedc36e4
ms.sourcegitcommit: 11880ca974fe2df308191c9f6dcdfe0b89c2dc67
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/27/2021
ms.locfileid: "99600638"
---
# Start-Transcript

## 개요
텍스트 파일에 대 한 PowerShell 세션의 전체 또는 일부에 대 한 레코드를 만듭니다.

## Syntax

### ByPath (기본값)

```
Start-Transcript [[-Path] <String>] [-Append] [-Force] [-NoClobber] [-IncludeInvocationHeader]
 [-UseMinimalHeader] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

### ByLiteralPath

```
Start-Transcript [[-LiteralPath] <String>] [-Append] [-Force] [-NoClobber]
 [-IncludeInvocationHeader] [-UseMinimalHeader] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

### ByOutputDirectory

```
Start-Transcript [[-OutputDirectory] <String>] [-Append] [-Force] [-NoClobber]
 [-IncludeInvocationHeader] [-UseMinimalHeader] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

## 설명

`Start-Transcript`Cmdlet은 텍스트 파일에 대 한 PowerShell 세션의 전체 또는 일부에 대 한 레코드를 만듭니다. 기록에는 사용자가 입력하는 모든 명령과 콘솔에 나타나는 모든 출력이 포함됩니다.

Windows PowerShell 5.0부터 `Start-Transcript` 은 모든 기록의 생성 된 파일 이름에 호스트 이름을 포함 합니다. 엔터프라이즈 로깅이 중앙 집중화 된 경우 특히 유용 합니다.
Cmdlet을 통해 생성 되는 파일에는 `Start-Transcript` 두 개 이상의 기록이 동시에 시작 될 때 잠재적으로 덮어쓰거나 중복 되지 않도록 이름에 임의의 문자가 포함 됩니다.
또한 중앙 집중식 파일 공유에 저장 된 기록을 무단으로 검색할 수 없습니다.

대상 파일에 BOM (바이트 순서 표시)이 없는 경우은 기본적 `Start-Transcript` 으로 `Utf8NoBom` 대상 파일의 인코딩입니다.

## 예

### 예제 1: 기본 설정을 사용 하 여 기록 파일 시작

```powershell
Start-Transcript
```

이 명령은 기본 파일 위치에서 기록을 시작합니다.

### 예제 2: 특정 위치에서 기록 파일 시작

```powershell
Start-Transcript -Path "C:\transcripts\transcript0.txt" -NoClobber
```

이 명령은의 파일에서 기록을 시작 `Transcript0.txt` `C:\transcripts` 합니다. **NoClobber** 매개 변수를 사용 하기 때문에 명령은 기존 파일을 덮어쓰지 않도록 합니다. `Transcript0.txt`파일이 이미 있으면 명령이 실패 합니다.

## 매개 변수

### -추가

이 cmdlet이 기존 파일의 끝에 새 기록을 추가 함을 나타냅니다. **Path** 매개 변수를 사용 하 여 파일을 지정 합니다.

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

### -Force

cmdlet에서 기록을 기존 읽기 전용 파일에 추가할 수 있도록 합니다. 읽기 전용 파일에서 사용될 경우 이 cmdlet은 파일 권한을 읽기 및 쓰기로 변경합니다. 이 매개 변수를 사용 하는 경우 cmdlet은 보안 제한을 재정의할 수 없습니다.

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

### -IncludeInvocationHeader

명령이 실행 될 때이 cmdlet이 타임 스탬프를 기록 함을 나타냅니다.

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

### -UseMinimalHeader

기본적으로 포함 된 자세한 헤더 대신 간략 한 머리글 앞에 추가 합니다. 이 매개 변수는 PowerShell 6.2에 추가 되었습니다.

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

### -LiteralPath

성적 증명서 파일의 위치를 지정 합니다. **Path** 매개 변수와 달리 **LiteralPath** 매개 변수 값은 입력한 대로 사용됩니다. 어떠한 문자도 와일드카드로 해석되지 않습니다. 이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요. 작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 알립니다.

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoClobber

이 cmdlet이 기존 파일을 덮어쓰지 않음을 나타냅니다. 기본적으로 기록 파일이 지정 된 경로에 있으면 `Start-Transcript` 는 경고 없이 파일을 덮어씁니다.

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

### -OutputDirectory

기록을 저장할 특정 경로 및 폴더를 지정 합니다. PowerShell에서 자동으로 성적 증명서 이름을 할당 합니다.

```yaml
Type: System.String
Parameter Sets: ByOutputDirectory
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

성적 증명서 파일의 위치를 지정 합니다. 파일 경로를 입력 하십시오 `.txt` . 와일드카드는 사용할 수 없습니다.

경로를 지정 하지 않으면는 `Start-Transcript` 전역 변수 값의 경로를 사용 합니다 `$Transcript` . 이 변수를 만들지 않은 경우는 `Start-Transcript` 파일에 기록을 저장 합니다 `$Home\My Documents directory as \PowerShell_transcript.<time-stamp>.txt` .

경로에 디렉터리가 없으면 명령이 실패합니다.

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: False
Position: 0
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

cmdlet을 실행할 경우 발생하는 일을 표시합니다.
cmdlet은 실행되지 않습니다.

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

### 없음

이 cmdlet에 개체를 파이프할 수 없습니다.

## 출력

### System.String

이 cmdlet은 확인 메시지와 출력 파일의 경로를 포함 하는 문자열을 반환 합니다.

## 참고

기록을 중지 하려면 cmdlet을 사용 `Stop-Transcript` 합니다.

전체 세션을 기록 하려면 `Start-Transcript` 프로필에 명령을 추가 합니다. 자세한 내용은 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)를 참조 하세요.

## 관련 링크

[Stop-Transcript](Stop-Transcript.md)
