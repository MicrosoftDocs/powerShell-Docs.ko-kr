---
title: 동적 매개 변수 공급자 도움말 항목을 추가 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e20e5ad6-a6e6-4a63-9d42-1ac54214f748
caps.latest.revision: 5
ms.openlocfilehash: cc4877242a16a9caa99564aeaae985f85e38791e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859879"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a>공급자 도움말 항목에 동적 매개 변수를 추가하는 방법

이 섹션에서는를 채우는 방법을 설명 합니다 **동적 매개 변수** 공급자 도움말 항목의 섹션입니다.

*동적 매개 변수* cmdlet의 매개 변수 또는 함수 에서만 사용할 수 있는 조건을 지정 합니다.

공급자 도움말 항목에 설명 된 동적 매개 변수는 공급자 드라이브에서 cmdlet 또는 함수를 사용 하면 공급자는 cmdlet 또는 함수를 추가 하는 동적 매개 변수입니다.

동적 매개 변수는 공급자에 대 한 사용자 지정 cmdlet 도움말 문서화할 수도 있습니다. 공급자에 대 한 공급자 도움말와 사용자 지정 cmdlet 도움말을 작성 하는 경우 두 문서에서 동적 매개 변수 설명서를 포함 합니다. 사용자 지정 cmdlet 도움말에 대 한 자세한 내용은 참조 하세요. [쓰기 Windows PowerShell 사용자 지정 Cmdlet 도움말 공급자에 대 한](./writing-custom-cmdlet-help-for-windows-powershell-providers.md)합니다.

공급자 도움말 항목을 포함 하면 빈 공급자는 동적 매개 변수를 구현 하지 않으면, `DynamicParameters` 요소입니다.

### <a name="to-add-dynamic-parameters"></a>동적 매개 변수를 추가 하려면

1. 에 *AssemblyName*help.xml.dll 파일 내 합니다 `providerHelp` 요소를 추가 `DynamicParameters` 요소. 합니다 `DynamicParameters` 요소 뒤에 있어야 합니다 `Tasks` 요소 전과 `RelatedLinks` 요소입니다.

   예:

    ```xml
    <providerHelp>
        <Tasks>
        </Tasks>
        <DynamicParameters>
        </DynamicParameters>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

   공급자는 동적 매개 변수를 구현 하지 않는 경우는 `DynamicParameters` 요소는 비어 있을 수 있습니다.

2. 내 합니다 `DynamicParameters` 요소를 각 동적 매개 변수 추가 `DynamicParameter` 요소.

   예:

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. 각 `DynamicParameter` 요소를 추가 된 `Name` 및 `CmdletSupported` 요소입니다.

   |요소 이름|설명|
   |------------------|-----------------|
   |이름|매개 변수 이름을 지정합니다.|
   |CmdletSupported|매개 변수가 올바른지 cmdlet을 지정 합니다. Cmdlet 이름의 쉼표로 구분 된 목록을 입력 합니다.|

   예를 들어, 다음 XML 문서를 `Encoding` Windows PowerShell FileSystem 공급자를 추가 하는 동적 매개 변수를 `Add-Content`를 `Get-Content`, `Set-Content` cmdlet.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. 각 `DynamicParameter` 요소에 추가 된 `Type` 요소. `Type` 요소에 대 한 컨테이너인는 `Name` .NET 유형의 동적 매개 변수 값을 포함 하는 요소입니다.

   예를 들어, 다음 XML을.NET 유형을 표시 합니다 `Encoding` 동적 매개 변수는 합니다 [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) 열거형입니다.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
            <Type>
                <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
            <Type>
    ...
    </DynamicParameters>
    ```

5. 추가 된 `Description` 동적 매개 변수에 대 한 간략 한 설명을 포함 하는 요소입니다. 설명의 작성할 때 모든 cmdlet 매개 변수에 대해 지정 된 지침을 따르세요 [매개 변수 정보를 추가 하는 방법을](./how-to-add-parameter-information.md)합니다.

   예를 들어 다음 XML에 대 한 설명은 `Encoding` 동적 매개 변수입니다.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
            <Type>
                <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
            <Type>
            <Description> Specifies the encoding of the output file that contains the content. </Description>
    ...
    </DynamicParameters>
    ```

6. 추가 된 `PossibleValues` 요소와 해당 자식 요소입니다. 함께 이러한 요소는 동적 매개 변수의 값을 설명합니다. 이 요소는 열거형된 값에 대 한 설계 되었습니다. 스위치 매개 변수를 사용 하는 경우 또는 값을 열거할 수 없습니다. 같은 빈 추가 동적 매개 변수 값을 사용 하지 않는, 경우 `PossibleValues` 요소입니다.

   다음 표에서 나열 하 고 설명 된 `PossibleValues` 요소와 해당 자식 요소입니다.

   |요소 이름|설명|
   |------------------|-----------------|
   |PossibleValues|이 요소는 컨테이너입니다. 자식 요소에 대 한 설명은 다음과 같습니다. 추가 `PossibleValues` 요소 각 공급자 도움말 항목입니다. 요소는 비어 있을 수 있습니다.|
   |PossibleValue|이 요소는 컨테이너입니다. 자식 요소에 대 한 설명은 다음과 같습니다. 추가 `PossibleValue` 각 동적 매개 변수 값에 대 한 요소입니다.|
   |Value|값 이름을 지정합니다.|
   |설명|이 요소에 포함 된 `Para` 요소입니다. 텍스트를 `Para` 요소에 지정 된 값을 설명 합니다.는 `Value` 요소입니다.|

   예를 들어, 다음 XML 하나를 보여 줍니다 `PossibleValue` 의 요소는 `Encoding` 동적 매개 변수입니다.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
    ...
            <Description> Specifies the encoding of the output file that contains the content. </Description>
            <PossibleValues>
                <PossibleValue>
                    <Value> ASCII </Value>
                    <Description>
                        <para> Uses the encoding for the ASCII (7-bit) character set. </para>
                    </Description>
                </PossibleValue>
    ...
            </PossibleValues>
    </DynamicParameters>
    ```

## <a name="example"></a>예제

다음 예제와 합니다 `DynamicParameters` 의 요소를 `Encoding` 동적 매개 변수입니다.

```xml
<DynamicParameters/>
    <DynamicParameter>
        <Name> Encoding </Name>
        <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
        <Type>
            <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
        <Type>
        <Description> Specifies the encoding of the output file that contains the content. </Description>
        <PossibleValues>
            <PossibleValue>
                <Value> ASCII </Value>
                <Description>
                    <para> Uses the encoding for the ASCII (7-bit) character set. </para>
                </Description>
            </PossibleValue>
            <PossibleValue>
                <Value> Unicode </Value>
                <Description>
                    <para> Encodes in UTF-16 format using the little-endian byte order. </para>
                </Description>
            </PossibleValue>
        </PossibleValues>
</DynamicParameters>
```