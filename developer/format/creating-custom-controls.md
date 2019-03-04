---
title: 사용자 지정 컨트롤 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3baa406-cd33-4420-be5a-07ef09d93480
caps.latest.revision: 8
ms.openlocfilehash: 3504ab1d974c55e9279172d0e851961474ccb926
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853199"
---
# <a name="creating-custom-controls"></a>사용자 지정 컨트롤 만들기

사용자 지정 컨트롤은 형식 지정 파일의 가장 유연한 구성 요소입니다. 테이블, 목록 및 데이터 테이블 같은 데이터 형식 구조를 정의 하는 와이드 뷰가 달리 사용자 지정 컨트롤을 통해 데이터의 개별 부분을 표시 되는 방식을 정의할 수 있습니다. 서식 파일의 모든 보기에 사용할 수 있는 사용자 지정 컨트롤의 공통 집합을 정의할 수 있습니다, 특정 보기를 사용할 수 있는 사용자 지정 컨트롤을 정의할 수 있습니다 또는 개체 그룹을 사용할 수 있는 컨트롤의 집합을 정의할 수 있습니다.

## <a name="custom-control-example"></a>사용자 지정 컨트롤 예제

다음 예제에서는 Certificates.Format.ps1xml 파일에 정의 된 사용자 지정 컨트롤을 보여 줍니다. 이 사용자 지정 컨트롤 구분 하는데 사용 되는 [System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature) 테이블 뷰에 표시 되는 개체입니다.

```xml
<Controls>
  <Control>
    <Name>SignatureTypes-GroupingFormat</Name>
    <CustomControl>
      <CustomEntries>
        <CustomEntry>
          <CustomItem>
            <Frame>
              <LeftIndent>4</LeftIndent>
              <CustomItem>
                <Text AssemblyName="System.Management.Automation" BaseName="FileSystemProviderStrings"
                  ResourceId="DirectoryDisplayGrouping"/>
                <ExpressionBinding>
                  <ScriptBlock>split-path $_.Path</ScriptBlock>
                </ExpressionBinding>
                <NewLine/>
              </CustomItem>
            </Frame>
          </CustomItem>
        </CustomEntry>
      </CustomEntries>
    </CustomControl>
  </Control>
</Controls>

```

## <a name="see-also"></a>참고 항목

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
