---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 개체 정렬
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
ms.openlocfilehash: 06aa15d89888f1ecbe60b8e1dfb4efebb1d73673
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402231"
---
# <a name="sorting-objects"></a>개체 정렬

표시 된 데이터를 사용 하 여 검사를 보다 쉽게 구성할 수 있습니다는 `Sort-Object` cmdlet. `Sort-Object` 정렬 기준으로 하나 이상의 속성 이름을 사용 하 고 이러한 속성의 값을 기준으로 정렬 된 데이터를 반환 합니다.

## <a name="basic-sorting"></a>기본 정렬

현재 디렉터리의 파일과 하위 디렉터리를 나열 하는 문제를 고려해 야 합니다.
기준으로 정렬 하고자 하는 경우 **LastWriteTime** 한 다음 **이름**를 입력 하 여 수행할 수 있습니다.

```powershell
Get-ChildItem |
  Sort-Object -Property LastWriteTime, Name |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
11/6/2017 10:10:11 AM  .localization-config
11/6/2017 10:10:11 AM  .openpublishing.build.ps1
11/6/2017 10:10:11 AM  appveyor.yml
11/6/2017 10:10:11 AM  LICENSE
11/6/2017 10:10:11 AM  LICENSE-CODE
11/6/2017 10:10:11 AM  ThirdPartyNotices
11/6/2017 10:10:15 AM  tests
6/6/2018 7:58:59 PM    CONTRIBUTING.md
6/6/2018 7:58:59 PM    README.md
...
```

지정 하 여 개체를 반대 순서로 정렬할 수도 있습니다는 **Descending** 스위치 매개 변수입니다.

```powershell
Get-ChildItem |
  Sort-Object -Property LastWriteTime, Name -Descending |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
12/1/2018 10:13:50 PM  reference
12/1/2018 10:13:50 PM  dsc
...
6/6/2018 7:58:59 PM    README.md
6/6/2018 7:58:59 PM    CONTRIBUTING.md
11/6/2017 10:10:15 AM  tests
11/6/2017 10:10:11 AM  ThirdPartyNotices
11/6/2017 10:10:11 AM  LICENSE-CODE
11/6/2017 10:10:11 AM  LICENSE
11/6/2017 10:10:11 AM  appveyor.yml
11/6/2017 10:10:11 AM  .openpublishing.build.ps1
11/6/2017 10:10:11 AM  .localization-config
```

## <a name="using-hash-tables"></a>해시 테이블을 사용 하 여

배열에서 해시 테이블을 사용 하 여 서로 다른 속성에서 서로 다른 순서로 정렬할 수 있습니다.
각 해시 테이블에서 사용 하는 **식** 속성 이름을 문자열로 지정 하는 키와 **오름차순** 또는 **내림차순** 하 여 정렬 순서를 지정 하는 키 `$true` 또는 `$false`.
합니다 **식** 키는 필수입니다.
**오름차순** 하거나 **내림차순** 키는 선택 사항입니다.

다음 예제에서는 개체를 내림차순으로 정렬 **LastWriteTime** 주문과 오름차순 **이름** 순서입니다.

```powershell
Get-ChildItem |
  Sort-Object -Property @{ Expression = 'LastWriteTime'; Descending = $true }, @{ Expression = 'Name'; Ascending = $true } |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
12/1/2018 10:13:50 PM  dsc
12/1/2018 10:13:50 PM  reference
11/29/2018 6:56:01 PM  .openpublishing.redirection.json
11/29/2018 6:56:01 PM  gallery
11/24/2018 10:33:22 AM developer
11/20/2018 7:22:19 PM  .markdownlint.json
...
```

Scriptblock 설정할 수도 있습니다는 **식** 키입니다.
실행 하는 경우는 `Sort-Object` cmdlet는 scriptblock 실행 되 고 정렬에 대 한 결과 사용 합니다.

다음 예제에서는 개체를 사이의 시간 범위를 기준으로 내림차순으로 정렬 **CreationTime** 하 고 **LastWriteTime**합니다.

```powershell
Get-ChildItem |
  Sort-Object -Property @{ Expression = { $_.LastWriteTime - $_.CreationTime }; Descending = $true } |
  Format-Table -Property LastWriteTime, CreationTime
```

```output
LastWriteTime          CreationTime
-------------          ------------
12/1/2018 10:13:50 PM  11/6/2017 10:10:11 AM
12/1/2018 10:13:50 PM  11/6/2017 10:10:11 AM
11/7/2018 6:52:24 PM   11/6/2017 10:10:11 AM
11/7/2018 6:52:24 PM   11/6/2017 10:10:15 AM
11/3/2018 9:58:17 AM   11/6/2017 10:10:11 AM
10/26/2018 4:50:21 PM  11/6/2017 10:10:11 AM
11/17/2018 1:10:57 PM  11/29/2017 5:48:30 PM
11/12/2018 6:29:53 PM  12/7/2017 7:57:07 PM
...
```

## <a name="tips"></a>팁

생략할 수 있습니다 합니다 **속성** 다음과 같이 매개 변수 이름:

```powershell
Sort-Object LastWriteTime, Name
```

게다가를 참조할 수 있습니다 `Sort-Object` 해당 기본 제공 별칭 `sort`:

```powershell
sort LastWriteTime, Name
```

다음과 같이 정렬에 대 한 해시 테이블의 키를 축약할 수 있습니다.

```powershell
Sort-Object @{ e = 'LastWriteTime'; d = $true }, @{ e = 'Name'; a = $true }
```

이 예제에서는 합니다 **e** 는 의미 **식**, **d** 는 의미 **내림차순**, 및 **를** 에 대 한 의미 **오름차순**합니다.

가독성을 높이기를 별도 변수에 해시 테이블을 배치할 수 있습니다.

```powershell
$order = @(
  @{ Expression = 'LastWriteTime'; Descending = $true }
  @{ Expression = 'Name'; Ascending = $true }
)

Get-ChildItem |
  Sort-Object $order |
  Format-Table LastWriteTime, Name
```