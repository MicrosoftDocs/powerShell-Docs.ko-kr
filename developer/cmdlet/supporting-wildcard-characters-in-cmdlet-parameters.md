---
title: Cmdlet 매개 변수에서 와일드 카드 문자를 지 원하는 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- wildcards [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide], wildcards
ms.assetid: 9b26e1e9-9350-4a5a-aad5-ddcece658d93
caps.latest.revision: 12
ms.openlocfilehash: 6c762d3889bc4b649252390625525db4735f4c1d
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059612"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a>Cmdlet 매개 변수에서 와일드카드 문자 지원

종종 단일 리소스 아닌 리소스 그룹에 대해 실행 하는 cmdlet를 디자인 해야 합니다. 예를 들어 cmdlet 이름이 없거나 확장 하는 데이터 저장소에서 모든 파일을 찾을 해야 합니다. 리소스 그룹에 대해 실행 되는 cmdlet를 디자인할 때 와일드 카드 문자를 지원 해야 합니다.

> [!NOTE]
> 와일드 카드 문자를 사용 하는 경우에 따라 라고도 *와일드 카드 사용*합니다.

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a>와일드 카드를 사용 하는 Windows PowerShell Cmdlet

 많은 Windows PowerShell cmdlet의 매개 변수 값에 대 한 와일드 카드 문자를 지원 합니다. 예를 들어, 거의 모든 cmdlet는에 `Name` 또는 `Path` 매개 변수는 이러한 매개 변수에 대 한 와일드 카드 문자를 지원 합니다. (하지만 있는 대부분의 cmdlet을 `Path` 매개 변수 수도 `LiteralPath` 와일드 카드 문자를 지원 하지 않는 매개 변수.) 다음 명령을 Get 동사를 포함 하는 이름이 현재 세션의 모든 cmdlet을 반환 하려면 와일드 카드 문자는 사용 하는 방법을 보여 줍니다.

 **PS > get 명령을 get-\***

## <a name="supported-wildcard-characters"></a>지원 되는 와일드 카드 문자

Windows PowerShell 와일드 카드 문자를 지원합니다.

|와일드 카드 문자|설명|예제|일치 항목|일치 하지 않습니다.|
|------------------------|-----------------|-------------|-------------|--------------------|
|*|지정 된 위치 에서부터 0 개 이상의 문자 일치|a*|Apple ag||
|?|지정된 된 위치에 문자 일치|? n|프로그램에서는,에서|실행|
|[ ]|다양 한 문자 일치|[a-l]ook|책, 쿡, 모양|수행한|
|[ ]|지정된 된 문자 일치|[bc]ook|서적, 쿡|look|

와일드 카드 문자를 지 원하는 cmdlet를 디자인할 때 와일드 카드 문자 조합을 허용 합니다. 예를 들어, 다음 명령을 사용 하 여 `Get-ChildItem` c:\Techdocs 폴더에 있으며 문자로 시작 하는 "a"부터 "l." 모든.txt 파일을 검색 하기 위한 cmdlet

**get-childitem c:\techdocs\\[a-l]\*.txt**

이전 명령은 범위 와일드 카드 **[a-l]** "a"부터 "l." 파일 이름은 문자로 시작 해야를 지정 하려면 다음 명령은 * 파일 이름의 첫 번째 문자와.txt 확장명 사이 있는 문자에 대 한 자리 표시자로 와일드 카드 문자입니다.

다음 예제에서는 "d" 문자를 제외 하지만 "a"부터 "f." 다른 모든 문자를 포함 하는 범위 와일드 카드 패턴

**get-childitem c:\techdocs\\[a-cef]\*.txt**

## <a name="handling-literal-characters-in-wildcard-patterns"></a>와일드 카드 패턴의 리터럴 문자를 처리합니다.

지정한 와일드 카드 패턴 리터럴 문자열을 포함 하는 경우 억음 악센트 문자 (') 이스케이프 문자로 사용 합니다. 리터럴 문자를 프로그래밍 방식으로 지정 하는 경우 단일 억음 악센트 기호를 사용 합니다. 명령 프롬프트에서 리터럴 문자를 지정 하는 경우에 두 개의 backtick을 사용 합니다. 예를 들어, 다음 패턴에 문자 그대로 수행 해야 하는 두 개의 대괄호가 포함 되어 있습니다.

"John Smith \`[*']" (프로그래밍 방식으로 지정)

"John Smith \` \`[*\`']" (명령 프롬프트에서 지정 됨)

이 패턴에는 "John Smith [마케팅]" 또는 "John Smith [개발]"와 일치합니다.

## <a name="cmdlet-output-and-wildcard-characters"></a>Cmdlet 출력 및 와일드 카드 문자

Cmdlet 매개 변수는 와일드 카드 문자를 지원 하는 경우 cmdlet은 작업을 일반적으로 배열 출력을 생성 합니다. 경우에 따라이 의미가 없습니다 사용자는 한 번에 하나의 항목만 사용할 수 있으므로 출력 배열을 지원 합니다. 예를 들어를 `Set-Location` cmdlet은 사용자만 단일 위치를 설정 하기 때문에 출력 배열을 지원지 않습니다. 이 예에서는 cmdlet을 계속 와일드 카드 문자를 지원 하지만 단일 위치를 확인 하 게 하기.

## <a name="see-also"></a>참고 항목

[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)

[WildcardPattern 클래스](/dotnet/api/system.management.automation.wildcardpattern)
