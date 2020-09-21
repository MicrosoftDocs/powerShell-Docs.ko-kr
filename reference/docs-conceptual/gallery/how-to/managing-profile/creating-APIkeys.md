---
ms.date: 09/10/2018
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: API 키 관리
ms.openlocfilehash: c428689d065c63716db6bc546434623e9375f8ba
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87777585"
---
# <a name="managing-api-keys"></a>API 키 관리

PowerShell 갤러리는 다양한 API 요구 사항을 지원하기 위해 여러 API 키를 만들 수 있도록 지원합니다. API 키는 하나 이상의 패키지에 적용할 수 있으며, 특정 권한을 부여하고, 만료 날짜가 있습니다.

> [!IMPORTANT]
> 범위가 지정된 API 키를 도입하기 전에 PowerShell 갤러리에 게시된 사용자에게는 "전체 액세스 API 키"가 있습니다. 전체 액세스 키에는 범위가 지정된 API 키에 기본적으로 제공되는 향상된 보안 기능이 없습니다. 전체 액세스 키는 만료되지 않으며, 사용자 소유의 모든 항목에 적용됩니다. 이 키는 삭제되면 다시 만들 수 없습니다.

다음 이미지에서는 범위가 지정된 API 키를 만들 때 사용할 수 있는 옵션을 보여 줍니다.

![API 키 만들기](media/creating-APIkeys/PSGallery_KeyScoped.png)

이 예에서는 **AzureRMDataFactory**라는 API 키를 만들었습니다. 이 키 값은 'AzureRM.DataFactory'로 시작하고 365일 동안 유효한 이름의 패키지를 푸시하는 데 사용할 수 있습니다. 동일한 조직 내의 여러 팀이 서로 다른 패키지에서 작업하는 일반적인 시나리오입니다. 팀 멤버에게는 자신이 작업할 특정 패키지에 대한 권한이 부여되는 키가 있습니다.
만료 값은 부실하거나 잊어버린 키를 사용하지 않도록 방지합니다.

## <a name="using-glob-patterns"></a>GLOB 패턴 사용

여러 패키지에서 작업하는 경우 GLOB 패턴을 사용하여 여러 패키지를 하나의 그룹으로 일치시킬 수 있습니다. API 키 권한은 GLOB 패턴과 일치하는 모든 새 패키지에 적용됩니다. 예를 들어 앞의 예에서는 **GLOB 패턴** 값으로 'AzureRM.DataFactory *'를 사용하고 있습니다. 패키지가 GLOB 패턴과 일치하므로 이 키를 사용하여 'AzureRm.DataFactoryV2.Netcore'라는 패키지를 푸시할 수 있습니다.

## <a name="create-api-keys-securely"></a>안전하게 API 키 만들기

보안을 위해 새로 만든 키 값은 화면에 표시되지 않으며, 아래와 같이 [복사] 단추로만 사용할 수 있습니다.

![새 API 키 값 가져오기](media/creating-APIkeys/PSGallery_CopyCreatedKey.png)

> [!IMPORTANT]
> API 키 값은 만들거나 새로 고친 직후에만 복사할 수 있습니다. 표시되지 않으며, 페이지를 새로 고친 후에는 다시 액세스할 수 없습니다. 키 값을 잃어버리면 [다시 생성]을 사용하고, 다시 생성된 후에 키를 복사해야 합니다.

## <a name="key-permissions-and-expiration"></a>키 권한 및 만료

범위가 지정된 API 키는 다음 권한 중 하나를 할당할 수 있습니다.

- 새 패키지 푸시
- 새 패키지 또는 업데이트 패키지 푸시
- 패키지 나열 취소

모든 새 키는 만료됩니다. 만료 값은 일 단위로 측정됩니다. 만료에 사용할 수 있는 값은 다음과 같습니다.

- 1일
- 90일
- 180일
- 270일
- 365일(기본값)

키를 만든 후에는 이러한 설정을 변경할 수 없습니다. 만료되지 않는 새 키는 만들 수 없습니다.

## <a name="editing-and-deleting-existing-api-keys"></a>기존 API 키 편집 및 삭제

기존 키의 일부 설정은 변경할 수 있습니다. 앞에서 설명한 대로 기존 API 키에 대한 보안 범위를 수정하거나 만료 시간을 변경할 수 없습니다. 변경할 수 있는 옵션은 다음 스크린샷과 같습니다.

![API 키 값 편집](media/creating-APIkeys/PSGallery_EditAPIKey.png)

키로 제어되는 패키지를 변경하려면 목록에서 개별 패키지를 선택하거나 GLOB 패턴을 변경할 수 있습니다.

**다시 생성**을 클릭하면 새 키 값이 만들어집니다. 키를 처음 만들 때와 마찬가지로 키 값을 업데이트하는 즉시 **복사**해야 합니다. 이 페이지에서 나가면 **복사** 옵션을 사용할 수 없습니다.

**삭제**를 클릭하면 확인 메시지가 표시됩니다. 키가 삭제되면 사용할 수 없게 됩니다.

## <a name="key-expiration"></a>키 만료

만료되기 10일 전에 PowerShell 갤러리에서 API 키의 계정 소유자에게 경고 이메일을 보냅니다. 만료 후에는 키를 사용할 수 없습니다. API 키 관리 페이지의 위쪽에 더 이상 유효하지 않은 키를 보여 주는 경고 메시지가 표시됩니다. 그러면 새 키 값을 생성할 수 있습니다.
