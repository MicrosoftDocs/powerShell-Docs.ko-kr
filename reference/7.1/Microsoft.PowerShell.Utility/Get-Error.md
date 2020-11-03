---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Error
ms.openlocfilehash: c29115a65b46d38039d78b10eee293e6944cede5
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213105"
---
# Get-Error

## 개요

현재 세션에서 가장 최근의 오류 메시지를 가져오고 표시 합니다.

## SYNTAX

### 최신 (기본값)

```
Get-Error [[-Newest] <Int32>] [<CommonParameters>]
```

### 오류

```
Get-Error [-InputObject <PSObject>] [<CommonParameters>]
```

## 설명

`Get-Error`Cmdlet은 세션에서 발생 한 마지막 오류에서 현재 오류 정보를 나타내는 **PSExtendedError** 개체를 가져옵니다.

`Get-Error` **최신** 매개 변수를 사용 하 여 현재 세션에서 발생 한 지정 된 수의 오류를 표시 하는 데 사용할 수 있습니다.

`Get-Error`또한 cmdlet은와 같은 컬렉션에서 오류 개체를 받아 `$Error` 현재 세션의 여러 오류를 표시 합니다.

## 예제

### 예 1: 최신 오류 세부 정보 가져오기

이 예에서는 `Get-Error` 현재 세션에서 발생 한 최신 오류의 세부 정보를 표시 합니다.

```powershell
Get-Childitem -path /NoRealDirectory
Get-Error
```

```
Get-ChildItem: Cannot find path 'C:\NoRealDirectory' because it does not exist.

Exception             :
    ErrorRecord          :
        Exception             :
            Message : Cannot find path 'C:\NoRealDirectory' because it does not exist.
            HResult : -2146233087
        TargetObject          : C:\NoRealDirectory
        CategoryInfo          : ObjectNotFound: (C:\NoRealDirectory:String) [], ParentContainsErrorRecordException
        FullyQualifiedErrorId : PathNotFound
    ItemName             : C:\NoRealDirectory
    SessionStateCategory : Drive
    TargetSite           :
        Name          : GetChildItems
        DeclaringType : System.Management.Automation.SessionStateInternal
        MemberType    : Method
        Module        : System.Management.Automation.dll
    StackTrace           :
   at System.Management.Automation.SessionStateInternal.GetChildItems(String path, Boolean recurse, UInt32 depth,
CmdletProviderContext context)
   at System.Management.Automation.ChildItemCmdletProviderIntrinsics.Get(String path, Boolean recurse, UInt32
depth, CmdletProviderContext context)
   at Microsoft.PowerShell.Commands.GetChildItemCommand.ProcessRecord()
    Message              : Cannot find path 'C:\NoRealDirectory' because it does not exist.
    Source               : System.Management.Automation
    HResult              : -2146233087
TargetObject          : C:\NoRealDirectory
CategoryInfo          : ObjectNotFound: (C:\NoRealDirectory:String) [Get-ChildItem], ItemNotFoundException
FullyQualifiedErrorId : PathNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
InvocationInfo        :
    MyCommand        : Get-ChildItem
    ScriptLineNumber : 1
    OffsetInLine     : 1
    HistoryId        : 57
    Line             : Get-Childitem -path c:\NoRealDirectory
    PositionMessage  : At line:1 char:1
                       + Get-Childitem -path c:\NoRealDirectory
                       + ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    InvocationName   : Get-Childitem
    CommandOrigin    : Internal
ScriptStackTrace      : at <ScriptBlock>, <No file>: line 1
PipelineIterationInfo :
```

### 예 2: 현재 세션에서 발생 한 지정 된 수의 오류 메시지 가져오기

이 예제에서는를 `Get-Error` **최신** 매개 변수와 함께 사용 하는 방법을 보여 줍니다. 이 예제에서 **최신** 은이 세션에서 발생 한 최신 오류의 3 개에 대 한 세부 정보를 반환 합니다.

```powershell
Get-Error -Newest 3
```

### 예제 3: 자세한 메시지를 수신 하는 오류 컬렉션 보내기

`$Error`자동 변수는 현재 세션에 있는 오류 개체의 배열을 포함 합니다. 개체의 배열을로 파이프 하 여 `Get-Error` 자세한 오류 메시지를 수신할 수 있습니다.

이 예에서는 `$Error` 가 cmdlet으로 파이프 됩니다 `Get-Error` . 결과는 예 1의 결과와 유사한 자세한 오류 메시지의 목록입니다.

```powershell
$Error | Get-Error
```

## PARAMETERS

### -최신

현재 세션에서 발생 한 오류 수를 지정 합니다.

```yaml
Type: System.Int32
Parameter Sets: Newest
Aliases: Last

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

이 매개 변수는 파이프라인 입력에 사용 됩니다.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: Error
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### PSObject

는 모든 **PSObject** 의 입력을 지원 하지만 **ErrorRecord** 또는 **Exception** 개체를 제공 하지 않으면 결과가 달라 집니다.

## 출력

### ErrorRecord # PSExtendedError

**PSExtendedError** 개체의 출력입니다.

## 참고

`Get-Error` 파이프라인 입력을 허용 합니다. 예들 들어 `$Error | Get-Error`입니다.

## 관련 링크

[about_Try_Catch_Finally](../Microsoft.PowerShell.Core/About/about_Try_Catch_Finally.md)
