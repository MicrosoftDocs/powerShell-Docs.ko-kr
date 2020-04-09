---
title: RunSpace09 코드 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 136e451f-767b-42e0-bd6f-6486693abd5e
caps.latest.revision: 6
ms.openlocfilehash: d7fa39485eea833483682c91c96417a76e5d770f
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80977542"
---
# <a name="runspace09-code-sample"></a>RunSpace09 코드 샘플

다음은 [비동기적으로 파이프라인을 호출 하는 콘솔 응용 프로그램 만들기](https://msdn.microsoft.com/198c1c94-2a06-457e-93ce-c0d910618e47)에서 설명한 Runspace09 샘플에 대 한 소스 코드입니다.
이 샘플 응용 프로그램은 runspace를 만들어 열고, 파이프라인을 만들고 비동기식으로 호출한 다음 파이프라인 이벤트를 사용 하 여 비동기적으로 스크립트를 처리 합니다. 이 응용 프로그램에서 실행 하는 스크립트는 0.5 초 간격 (500 밀리초)의 정수 1 ~ 10을 만듭니다.

## <a name="code-sample"></a>코드 예제

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs" range="11-113":::

## <a name="see-also"></a>참고 항목

[Windows PowerShell SDK](../windows-powershell-reference.md)
