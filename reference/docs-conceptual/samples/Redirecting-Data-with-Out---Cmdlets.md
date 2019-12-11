---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Out Cmdlet을 사용하여 데이터 리디렉션
ms.openlocfilehash: d4cc14e26bdef0f973f948177d0c1e68929605fa
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030087"
---
# <a name="redirecting-data-with-out--cmdlets"></a>Out-* Cmdlet을 사용하여 데이터 리디렉션

Windows PowerShell에는 데이터 출력을 직접 제어할 수 있는 여러 가지 cmdlet이 있습니다. 이러한 cmdlet은 두 가지 중요한 특성을 공유합니다.

첫째, 일반적으로 이러한 cmdlet은 데이터를 특정 텍스트 형식으로 변환합니다. 이는 텍스트 입력을 필요로 하는 시스템 구성 요소에 데이터를 출력하기 위한 것입니다. 즉, 개체를 텍스트로 표시해야 합니다. 따라서 Windows PowerShell 콘솔 창에 표시되는 대로 텍스트의 형식이 지정됩니다.

둘째, 이러한 cmdlet은 Windows PowerShell에서 다른 위치로 정보를 내보내기 때문에 Windows PowerShell의 동사 **Out**을 사용합니다. **Out-Host** cmdlet은 항상 호스트 창을 Windows PowerShell의 외부에 표시합니다. 이는 Windows PowerShell에서 데이터를 내보내면 실제로 데이터가 제거되기 때문에 중요합니다. 다음과 같이 데이터를 호스트 창으로 페이징하는 파이프라인을 만든 다음 목록 형식으로 지정해 보면 이 동작을 재현할 수 있습니다.

```powershell
Get-Process | Out-Host -Paging | Format-List
```

이 명령을 실행하면 프로세스 정보 페이지가 목록 형식으로 표시되어야 하지만 다음과 같이 기본 표 형식 목록으로 표시됩니다.

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    101       5     1076       3316    32     0.05   2888 alg
...
    618      18    39348      51108   143   211.20    740 explorer
    257       8     9752      16828    79     3.02   2560 explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

**Out-Host** cmdlet은 데이터를 콘솔에 직접 보내기 때문에 **Format-List** 명령에는 서식을 지정할 데이터가 전달되지 않습니다.

이 명령을 구성하는 올바른 방법은 다음과 같이 **Out-Host** cmdlet을 파이프라인 끝에 배치하는 것입니다. 이렇게 하면 프로세스 데이터가 페이징되어 표시되기 전에 목록으로 형식이 지정됩니다.

```
PS> Get-Process | Format-List | Out-Host -Paging

Id      : 2888
Handles : 101
CPU     : 0.046875
Name    : alg
...

Id      : 740
Handles : 612
CPU     : 211.703125
Name    : explorer

Id      : 2560
Handles : 257
CPU     : 3.015625
Name    : explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

이러한 내용은 모든 **Out** cmdlet에 적용되므로 **Out** cmdlet을 항상 파이프라인 끝에 배치해야 합니다.

> [!NOTE]
> 모든 **Out** cmdlet은 줄 길이 제한과 같은 콘솔 창에 적용되는 형식을 사용하여 출력을 텍스트로 렌더링합니다.

## <a name="paging-console-output-out-host"></a>콘솔 출력 페이징(Out-Host)

기본적으로 Windows PowerShell은 데이터를 호스트 창으로 보내는데, 이는 Out-Host cmdlet이 수행하는 작업과 똑같습니다. Out-Host cmdlet의 주된 용도는 앞에서 설명한 대로 데이터를 페이징하는 것입니다. 예를 들어 다음 명령은 Out-Host를 사용하여 Get-Command cmdlet의 출력을 페이징합니다.

```powershell
Get-Command | Out-Host -Paging
```

**more** 함수를 사용하여 데이터를 페이징할 수도 있습니다. Windows PowerShell에서 **more**는 **Out-Host -Paging**을 호출하는 함수입니다. 다음 명령은 **more** 함수를 사용하여 Get-Command의 출력을 페이징하는 방법을 보여 줍니다.

```powershell
Get-Command | more
```

하나 이상의 파일 이름을 more 함수에 대한 인수로 포함하면 more 함수는 이러한 파일을 읽고 해당 내용을 호스트로 페이징합니다.

```
PS> more c:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
...
```

## <a name="discarding-output-out-null"></a>출력 삭제(Out-Null)

**Out-Null** cmdlet은 수신한 입력을 즉시 삭제하도록 설계되었습니다. 이 cmdlet은 명령 실행의 부작용으로 수신되는 불필요한 데이터를 삭제하는 데 유용합니다. 다음 명령을 입력하면 명령에서 아무 것도 반환되지 않습니다.

```powershell
Get-Command | Out-Null
```

**Out-Null** cmdlet은 오류 출력을 삭제하지 않습니다. 예를 들어 다음 명령을 입력하면 Windows PowerShell이 'Is-NotACommand'를 인식할 수 없다는 메시지가 나타납니다.

```
PS> Get-Command Is-NotACommand | Out-Null
Get-Command : 'Is-NotACommand' is not recognized as a cmdlet, function, operabl
e program, or script file.
At line:1 char:12
+ Get-Command  <<<< Is-NotACommand | Out-Null
```

## <a name="printing-data-out-printer"></a>데이터 인쇄(Out-Printer)

**Out-Printer** cmdlet을 사용하여 데이터를 인쇄할 수 있습니다. 프린터 이름을 제공하지 않으면 **Out-Printer** cmdlet은 기본 프린터를 사용합니다. 표시 이름만 지정하면 아무 Windows 기반 컴퓨터나 사용할 수 있습니다. 프린터 포트 매핑이나 심지어 실제 프린터도 필요하지 않습니다. 예를 들어 Microsoft Office Document Imaging 도구가 설치되어 있으면 다음과 같이 입력하여 데이터를 이미지 파일로 보낼 수 있습니다.

```powershell
Get-Command Get-Command | Out-Printer -Name 'Microsoft Office Document Image Writer'
```

## <a name="saving-data-out-file"></a>데이터 저장(Out-File)

**Out-File** cmdlet을 사용하여 출력을 콘솔 창이 아니라 파일로 보낼 수 있습니다. 다음 명령줄은 프로세스 목록을 **C:\\temp\\processlist.txt** 파일로 보냅니다.

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt
```

이전의 출력 리디렉션에 익숙한 경우 **Out-File** cmdlet을 사용하면 알고 있는 것과 다른 결과가 나타날 수 있습니다. 이 동작을 이해하려면 **Out-File** cmdlet이 작동하는 컨텍스트를 알고 있어야 합니다.

기본적으로 **Out-File** cmdlet은 유니코드 파일을 만듭니다. 이 형식은 최선의 기본 출력 형식이지만 이 기본 출력 형식을 사용할 경우 ASCII 파일을 출력하는 도구가 올바로 작동하지 않습니다. 다음과 같이 **Encoding** 매개 변수를 사용하면 기본 출력 형식을 ASCII로 변경할 수 있습니다.

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
```

**Out-file**은 콘솔에 표시되는 것처럼 파일 내용의 형식을 지정하기 때문에 대부분의 경우 콘솔 창에서처럼 출력이 잘립니다. 예를 들어 다음 명령을 실행할 수 있습니다.

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt
```

출력은 다음과 같이 표시됩니다.

```output
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
...
```

출력할 때 화면 너비에 맞추기 위해 강제로 줄을 바꾸지 않으려면 **Width** 매개 변수를 사용하여 줄 너비를 지정하면 됩니다. **Width**는 32비트 정수 매개 변수이기 때문에 에 지정할 수 있는 최대값은 2147483647입니다. 줄 길이를 최대값으로 설정하려면 다음과 같이 입력합니다.

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647
```

**Out-File** cmdlet은 콘솔에 표시된 상태로 출력을 저장하려는 경우에 가장 유용합니다. 출력 형식을 보다 자세히 제어하려면 고급 도구가 필요합니다. 이러한 도구에 대해서는 다음 장에서 개체 조작에 대해 설명할 때 함께 다룹니다.
