---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 32a1a10ac30f4bccfdbdd4a1e4ca4ea9459a19af
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058066"
---
# <a name="format-hex"></a>Format-Hex
**Format-Hex**를 사용하면 텍스트 또는 이진 데이터를 16진수 형식으로 볼 수 있습니다. [Format-Hex](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/format-hex)를 참조하세요.

## <a name="example-1"></a>예제 1
16진수 형식의 문자열 내용을 봅니다.

```powershell
"This is a very long line to force the line folding in Format-Hex cmdlet" | Format-Hex
```

출력
```
PS C:\> This is a very long line to force the line folding in Format-Hex cmdlet" | Format-Hex


           00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F

00000000   54 68 69 73 20 69 73 20 61 20 76 65 72 79 20 6C  This is a very l
00000010   6F 6E 67 20 6C 69 6E 65 20 74 6F 20 66 6F 72 63  ong line to forc
00000020   65 20 74 68 65 20 6C 69 6E 65 20 66 6F 6C 64 69  e the line foldi
00000030   6E 67 20 69 6E 20 46 6F 72 6D 61 74 2D 48 65 78  ng in Format-Hex
00000040   20 63 6D 64 6C 65 74                              cmdlet


PS C:\>
```
