---
description: .NET framework 클래스에 사용할 수 있는 형식 액셀러레이터에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 05/01/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_type_accelerators?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Type_Accelerators
ms.openlocfilehash: 3c7f7f0d993819da1efbc7ba9f4c26bd2827bc84
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222337"
---
# <a name="about-type-accelerators"></a>형식 액셀러레이터 정보

## <a name="short-desription"></a>SHORT 설명을
.NET framework 클래스에 사용할 수 있는 형식 액셀러레이터에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명

형식 액셀러레이터는 .NET framework 클래스의 별칭입니다. 이를 통해 전체 클래스 이름을 명시적으로 입력 하지 않고도 특정 .NET framework 클래스에 액세스할 수 있습니다. 예를 들어, **AliasAttribute** 클래스를에서로 줄일 수 있습니다 `[System.Management.Automation.AliasAttribute]` `[Alias]` .

> [!NOTE]
> 모든 형식 액셀러레이터는 여전히 대괄호 ()로 묶어야 `[]` 합니다.

## <a name="available-type-accelerators"></a>사용 가능한 형식 액셀러레이터

|        액셀러레이터          |                           전체 클래스 이름                           |
|---------------------------- | ------------------------------------------------------------------- |
|바인딩하려면                         | DirectoryServices                             |
|adsisearcher                 | DirectoryServices                          |
|Alias                        | AliasAttribute.                         |
|AllowEmptyCollection         | AllowEmptyCollectionAttribute.          |
|AllowEmptyString             | AllowEmptyStringAttribute.              |
|AllowNull                    | System.object. AllowNullAttribute                     |
|ArgumentCompleter            | ArgumentCompleterAttribute.             |
|ArgumentCompletions          | ArgumentCompletionsAttribute.           |
|array                        | System.Array                                                        |
|bigint                       | BigInteger                                          |
|bool                         | System.Boolean                                                      |
|byte                         | System.Byte                                                         |
|char                         | System.Char                                                         |
|cimclass                     | CimClass.                        |
|cimconverter                 | CimConverter.                    |
|ciminstance 개체로                  | Ciminstance 개체로.                     |
|CimSession                   | Microsoft.Management.Infrastructure.CimSession                      |
|cimtype                      | CimType.                         |
|CmdletBinding                | System.web. CmdletBindingAttribute                 |
|cultureinfo                  | System.object. CultureInfo                                    |
|Datetime                     | System.DateTime                                                     |
|decimal                      | System.Decimal                                                      |
|double                       | System.Double                                                       |
|Set-dsclocalconfigurationmanager | System.object를 관리 합니다.  |
|DscProperty                  | DscPropertyAttribute.                   |
|DscResource                  | System.object입니다.                   |
|ExperimentAction             | ExperimentAction.                       |
|실험적                 | ExperimentalAttribute.                  |
|ExperimentalFeature          | ExperimentalFeature.                    |
|float                        | System.Single                                                       |
|guid                         | System.Guid                                                         |
|테이블                    | System.Collections.Hashtable                                        |
|initialsessionstate          | System.Management.Automation.Runspaces.InitialSessionState          |
|int                          | System.Int32                                                        |
|int16                        | System.Int16                                                        |
|int32                        | System.Int32                                                        |
|int64                        | System.Int64                                                        |
|\                    | 시스템 .Net. IPAddress                                                |
|IPEndpoint                   | 시스템 .Net. IPEndPoint                                               |
|long                         | System.Int64                                                        |
|mailaddress 특성이 있어야만                  | 시스템 .Net. 메일 주소                                         |
|NullString                   | System.object. NullString                    |
|ObjectSecurity               | Accesscontrol-namespace. ObjectSecurity                        |
|OutputType                   | OutputTypeAttribute.                    |
|매개 변수                    | System.object. ParameterAttribute                     |
|PhysicalAddress              | System.net.networkinformation. PhysicalAddress                       |
|PowerShell                   | System.object. PowerShell                             |
|psaliasproperty              | PSAliasProperty.                        |
|pscredential                 | System.object. PSCredential                           |
|pscustomobject               | System.web. PSObject                               |
|PSDefaultValue               | System.Management.Automation.PSDefaultValueAttribute                |
|pslistmodifier               | System.object. .Iiilistmodifier                         |
|psmoduleinfo                 | System.object..                           |
|ps참고 속성               | System.object 속성입니다.                         |
|psobject                     | System.web. PSObject                               |
|psprimitivedictionary        | PSPrimitiveDictionary.                  |
|pspropertyexpression         | Microsoft. PowerShell. PSPropertyExpression                  |
|psscriptmethod               | PSScriptMethod.                         |
|psscriptproperty             | System.web. n a m a 속성                       |
|PSTypeNameAttribute          | PSTypeNameAttribute.                    |
|system.management.automation.psvariable                   | System.object입니다.                             |
|psvariableproperty           | PSVariableProperty.                     |
|ref                          | System.object를 참조 하십시오.                            |
|regex                        | System.Text.RegularExpressions.Regex                                |
|Runspace                     | Runspace입니다.                     |
|runspacefactory              | Runspace. RunspaceFactory              |
|sbyte                        | System.SByte                                                        |
|scriptblock                  | System.object.                            |
|securestring                 | System.Security.SecureString                                        |
|semver                       | SemanticVersion.                        |
|short                        | System.Int16                                                        |
|single                       | System.Single                                                       |
|문자열                       | System.String                                                       |
|SupportsWildcards            | SupportsWildcardsAttribute.             |
|switch                       | System.Management.Automation.SwitchParameter                        |
|timespan                     | System.TimeSpan                                                     |
|type                         | System.Type                                                         |
|uint                         | System.UInt32                                                       |
|uint16                       | System.UInt16                                                       |
|uint32                       | System.UInt32                                                       |
|uint64                       | System.UInt64                                                       |
|ulong                        | System.UInt64                                                       |
|uri                          | System.Uri                                                          |
|ushort                       | System.UInt16                                                       |
|ValidateCount                | ValidateCountAttribute.                 |
|ValidateDrive                | System.object. ValidateDriveAttribute                 |
|ValidateLength               | ValidateLengthAttribute.                |
|ValidateNotNull              | ValidateNotNullAttribute.               |
|ValidateNotNullOrEmpty       | ValidateNotNullOrEmptyAttribute.        |
|ValidatePattern              | ValidatePatternAttribute.               |
|ValidateRange                | ValidateRangeAttribute.                 |
|ValidateScript               | ValidateScriptAttribute.                |
|ValidateSet                  | ValidateSetAttribute.                   |
|ValidateTrustedData          | ValidateTrustedDataAttribute.           |
|ValidateUserDrive            | System.web. Validateuser드라이브 특성             |
|버전                      | System.Version                                                      |
|void                         | System.Void                                                         |
|WildcardPattern              | WildcardPattern.                        |
|wim                          | System.object 개체                                  |
|wmiclass                     | System.object 클래스                                   |
|wmisearcher                  | 시스템 관리. ManagementObjectSearcher                          |
|System.security.cryptography.x509certificates.x500distinguishedname        | System.security.cryptography.x509certificates.x509certificate2. System.security.cryptography.x509certificates.x500distinguishedname |
|X509Certificate              | System.security.cryptography.x509certificates.x509certificate2입니다.       |
|Xml                          | System.Xml.XmlDocument                                              |

