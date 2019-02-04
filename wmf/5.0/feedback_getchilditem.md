---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: cc5d2d799c1292f68de5fb2360fcba220c2c010b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682333"
---
# <a name="get-childitem-has--depth-parameter"></a>Get-ChildItem의 -Depth 매개 변수
이제 **Get-ChildItem**은 **–Recurse**와 함께 사용되어 재귀를 제한하는 **–Depth** 매개 변수를 제공합니다.

PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0

디렉터리: C:\\사용자가\\slee\\다운로드\\예제

Mode LastWriteTime Length Name

---- ------------- ------ ----

d----- 4/14/2015 5:36 PM Depth0

-a---- 4/14/2015 1:19 PM 0 File1.txt

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1

디렉터리: C:\\사용자가\\slee\\다운로드\\예제

Mode LastWriteTime Length Name

---- ------------- ------ ----

d----- 4/14/2015 5:36 PM Depth0

-a---- 4/14/2015 1:19 PM 0 File1.txt

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

디렉터리: C:\\사용자가\\slee\\다운로드\\예제\\Depth0

Mode LastWriteTime Length Name

---- ------------- ------ ----

d----- 4/14/2015 5:33 PM Depth1
