---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 개체 정렬
description: Sort-Object cmdlet을 사용하면 하나 이상의 속성에 대한 개체 컬렉션을 정렬할 수 있습니다.
ms.openlocfilehash: 836207adfc566003e9714e45920d9b4e24a677e9
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501017"
---
# <a name="sorting-objects"></a>개체 정렬

`Sort-Object` cmdlet을 사용하여 표시된 데이터를 검색하기 쉽게 구성할 수 있습니다.
`Sort-Object`는 정렬 기준으로 사용할 하나 이상의 속성 이름을 선택하고 이러한 속성의 값을 기준으로 정렬된 데이터를 반환합니다.

## <a name="basic-sorting"></a>기본 정렬

현재 디렉터리의 하위 디렉터리 및 파일 나열 관련 문제를 살펴보겠습니다.
정렬 기준으로 **LastWriteTime** 과 **Name** 을 차례로 사용하여 정렬하려면 다음과 같이 입력하면 됩니다.

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

또한 **Descending** 스위치 매개 변수를 지정하여 개체를 반대 순서로 정렬할 수도 있습니다.

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

## <a name="using-hash-tables"></a>해시 테이블 사용

배열에서 해시 테이블을 사용하여 여러 가지 속성을 다양한 순서로 정렬할 수 있습니다.
각 해시 테이블은 **Expression** 키를 사용하여 속성 이름을 문자열로 지정하고 **Ascending** 또는 **Descending** 키를 사용하여 `$true` 또는 `$false`를 기준으로 정렬 순서를 지정합니다.
**Expression** 키는 필수입니다.
**Ascending** 또는 **Descending** 키는 선택 사항입니다.

다음 예제에서는 내림차순 **LastWriteTime** 및 오름차순 **Name** 으로 개체를 정렬합니다.

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

scriptblock을 **Expression** 키로 설정할 수도 있습니다.
`Sort-Object` cmdlet을 실행하면 scriptblock이 실행되고 결과가 정렬에 사용됩니다.

다음 예제에서는 **CreationTime** 및 **LastWriteTime** 사이의 시간 간격을 기준으로 개체를 내림차순으로 정렬합니다.

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

다음과 같이 **Property** 매개 변수 이름을 생략할 수 있습니다.

```powershell
Sort-Object LastWriteTime, Name
```

또한 기본 제공 별칭 `sort`를 통해 `Sort-Object`를 참조할 수 있습니다.

```powershell
sort LastWriteTime, Name
```

정렬을 위한 해시 테이블의 키는 다음과 같이 약식으로 나타낼 수 있습니다.

```powershell
Sort-Object @{ e = 'LastWriteTime'; d = $true }, @{ e = 'Name'; a = $true }
```

이 예제에서 **e** 는 **Expression** 을 나타내고, **d** 는 **Descending** 을 나타내고, **a** 는 **Ascending** 을 나타냅니다.

가독성을 개선하기 위해 해시 테이블을 개별 변수에 넣을 수 있습니다.

```powershell
$order = @(
  @{ Expression = 'LastWriteTime'; Descending = $true }
  @{ Expression = 'Name'; Ascending = $true }
)

Get-ChildItem |
  Sort-Object $order |
  Format-Table LastWriteTime, Name
```
