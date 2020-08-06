---
title: 사용자 지정 컨트롤 만들기 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c36fa9b778e01501a3c88f735cdefdfbb04411a0
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786121"
---
# <a name="creating-custom-controls"></a>사용자 지정 컨트롤 만들기

사용자 지정 컨트롤은 서식 파일의 가장 유연한 구성 요소입니다. 데이터 테이블과 같은 데이터의 공식 구조를 정의 하는 테이블, 목록 및 넓은 뷰와 달리 사용자 지정 컨트롤을 사용 하면 개별 데이터 조각이 표시 되는 방식을 정의할 수 있습니다. 서식 파일의 모든 뷰에 사용할 수 있는 사용자 지정 컨트롤의 공통 집합을 정의 하거나, 특정 뷰에서 사용할 수 있는 사용자 지정 컨트롤을 정의 하거나, 개체 그룹에 사용할 수 있는 컨트롤 집합을 정의할 수 있습니다.

## <a name="custom-control-example"></a>사용자 지정 컨트롤 예제

다음 예제에서는 Certificates.Format.ps1xml 파일에 정의 된 사용자 지정 컨트롤을 보여 줍니다. 이 사용자 지정 컨트롤을 사용 하 여 테이블 뷰에 표시 되는 [system.web. Signature](/dotnet/api/System.Management.Automation.Signature) 개체를 구분 합니다.

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

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
