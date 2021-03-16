---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-pfxcertificate?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PfxCertificate
ms.openlocfilehash: baf06c34511217f23d876843007525b9ce17f35b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605227"
---
# <span data-ttu-id="7a8b4-102">Get-PfxCertificate</span><span class="sxs-lookup"><span data-stu-id="7a8b4-102">Get-PfxCertificate</span></span>

## <span data-ttu-id="7a8b4-103">개요</span><span class="sxs-lookup"><span data-stu-id="7a8b4-103">SYNOPSIS</span></span>
<span data-ttu-id="7a8b4-104">컴퓨터의 PFX 인증서 파일에 대 한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-104">Gets information about PFX certificate files on the computer.</span></span>

## <span data-ttu-id="7a8b4-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7a8b4-105">SYNTAX</span></span>

### <span data-ttu-id="7a8b4-106">ByPath (기본값)</span><span class="sxs-lookup"><span data-stu-id="7a8b4-106">ByPath (Default)</span></span>

```
Get-PfxCertificate [-FilePath] <String[]> [-Password <SecureString>] [-NoPromptForPassword]
 [<CommonParameters>]
```

### <span data-ttu-id="7a8b4-107">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="7a8b4-107">ByLiteralPath</span></span>

```
Get-PfxCertificate -LiteralPath <String[]> [-Password <SecureString>] [-NoPromptForPassword]
 [<CommonParameters>]
```

## <span data-ttu-id="7a8b4-108">설명</span><span class="sxs-lookup"><span data-stu-id="7a8b4-108">DESCRIPTION</span></span>

<span data-ttu-id="7a8b4-109">`Get-PfxCertificate`Cmdlet은 지정 된 각 PFX 인증서 파일을 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-109">The `Get-PfxCertificate` cmdlet gets an object representing each specified PFX certificate file.</span></span>
<span data-ttu-id="7a8b4-110">PFX 파일에는 인증서와 개인 키가 모두 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-110">A PFX file includes both the certificate and a private key.</span></span>

## <span data-ttu-id="7a8b4-111">예제</span><span class="sxs-lookup"><span data-stu-id="7a8b4-111">EXAMPLES</span></span>

### <span data-ttu-id="7a8b4-112">예제 1: PFX 인증서 가져오기</span><span class="sxs-lookup"><span data-stu-id="7a8b4-112">Example 1: Get a PFX certificate</span></span>

```powershell
Get-PfxCertificate -FilePath "C:\windows\system32\Test.pfx"
```

```output
Password: ******
Signer Certificate:      David Chew (Self Certificate)
Time Certificate:
Time Stamp:
Path:                    C:\windows\system32\zap.pfx
```

<span data-ttu-id="7a8b4-113">이 명령은 시스템의 테스트 .pfx 인증서 파일에 대 한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-113">This command gets information about the Test.pfx certificate file on the system.</span></span>

### <span data-ttu-id="7a8b4-114">예 2: 원격 컴퓨터에서 PFX 인증서 가져오기</span><span class="sxs-lookup"><span data-stu-id="7a8b4-114">Example 2: Get a PFX certificate from a remote computer</span></span>

```powershell
Invoke-Command -ComputerName "Server01" -ScriptBlock {Get-PfxCertificate -FilePath "C:\Text\TestNoPassword.pfx"} -Authentication CredSSP
```

<span data-ttu-id="7a8b4-115">이 명령은 Server01 원격 컴퓨터에서 PFX 인증서 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-115">This command gets a PFX certificate file from the Server01 remote computer.</span></span> <span data-ttu-id="7a8b4-116">를 사용 `Invoke-Command` 하 여 `Get-PfxCertificate` 원격으로 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-116">It uses `Invoke-Command` to run a `Get-PfxCertificate` command remotely.</span></span>

<span data-ttu-id="7a8b4-117">PFX 인증서 파일이 암호로 보호 되지 않는 경우의 **Authentication** 매개 변수 값은 CredSSP 여야 합니다 `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="7a8b4-117">When the PFX certificate file is not password-protected, the value of the **Authentication** parameter of `Invoke-Command` must be CredSSP.</span></span>

## <span data-ttu-id="7a8b4-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7a8b4-118">PARAMETERS</span></span>

### <span data-ttu-id="7a8b4-119">-FilePath</span><span class="sxs-lookup"><span data-stu-id="7a8b4-119">-FilePath</span></span>

<span data-ttu-id="7a8b4-120">보안 파일의 PFX 파일에 대 한 전체 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-120">Specifies the full path to the PFX file of the secured file.</span></span> <span data-ttu-id="7a8b4-121">이 매개 변수에 대 한 값을 지정 하는 경우 명령줄에를 입력할 필요가 없습니다 `-FilePath` .</span><span class="sxs-lookup"><span data-stu-id="7a8b4-121">If you specify a value for this parameter, it is not necessary to type `-FilePath` at the command line.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="7a8b4-122">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="7a8b4-122">-LiteralPath</span></span>

<span data-ttu-id="7a8b4-123">보안 파일의 PFX 파일에 대 한 전체 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-123">The full path to the PFX file of the secured file.</span></span> <span data-ttu-id="7a8b4-124">**FilePath** 와 달리 **LiteralPath** 매개 변수 값은 입력 한 대로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-124">Unlike **FilePath**, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="7a8b4-125">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-125">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="7a8b4-126">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-126">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="7a8b4-127">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-127">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="7a8b4-128">-NoPromptForPassword</span><span class="sxs-lookup"><span data-stu-id="7a8b4-128">-NoPromptForPassword</span></span>

<span data-ttu-id="7a8b4-129">암호를 묻는 메시지를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-129">Suppresses prompting for a password.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7a8b4-130">-Password</span><span class="sxs-lookup"><span data-stu-id="7a8b4-130">-Password</span></span>

<span data-ttu-id="7a8b4-131">인증서 파일에 액세스 하는 데 필요한 암호를 지정 합니다 `.pfx` .</span><span class="sxs-lookup"><span data-stu-id="7a8b4-131">Specifies a password required to access a `.pfx` certificate file.</span></span>

<span data-ttu-id="7a8b4-132">이 매개 변수는 PowerShell 6.1에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-132">This parameter was introduced in PowerShell 6.1.</span></span>

> [!NOTE]
> <span data-ttu-id="7a8b4-133">**Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="7a8b4-133">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Security.SecureString
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7a8b4-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7a8b4-134">CommonParameters</span></span>

<span data-ttu-id="7a8b4-135">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7a8b4-136">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7a8b4-137">입력</span><span class="sxs-lookup"><span data-stu-id="7a8b4-137">INPUTS</span></span>

### <span data-ttu-id="7a8b4-138">System.String</span><span class="sxs-lookup"><span data-stu-id="7a8b4-138">System.String</span></span>

<span data-ttu-id="7a8b4-139">파일 경로를 포함 하는 문자열을로 파이프 할 수 있습니다 `Get-PfxCertificate` .</span><span class="sxs-lookup"><span data-stu-id="7a8b4-139">You can pipe a string that contains a file path to `Get-PfxCertificate`.</span></span>

## <span data-ttu-id="7a8b4-140">출력</span><span class="sxs-lookup"><span data-stu-id="7a8b4-140">OUTPUTS</span></span>

### <span data-ttu-id="7a8b4-141">System.Security.Cryptography.X509Certificates.X509Certificate2</span><span class="sxs-lookup"><span data-stu-id="7a8b4-141">System.Security.Cryptography.X509Certificates.X509Certificate2</span></span>

<span data-ttu-id="7a8b4-142">`Get-PfxCertificate` 가져오는 각 인증서에 대 한 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a8b4-142">`Get-PfxCertificate` returns an object for each certificate that it gets.</span></span>

## <span data-ttu-id="7a8b4-143">참고</span><span class="sxs-lookup"><span data-stu-id="7a8b4-143">NOTES</span></span>

<span data-ttu-id="7a8b4-144">Cmdlet을 사용 하 여 `Invoke-Command` 원격으로 `Get-PfxCertificate` 명령을 실행 하 고 PFX 인증서 파일이 암호로 보호 되지 않는 경우의 **Authentication** 매개 변수 값은 CredSSP 여야 합니다 `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="7a8b4-144">When using the `Invoke-Command` cmdlet to run a `Get-PfxCertificate` command remotely, and the PFX certificate file is not password protected, the value of the **Authentication** parameter of `Invoke-Command` must be CredSSP.</span></span>

## <span data-ttu-id="7a8b4-145">관련 링크</span><span class="sxs-lookup"><span data-stu-id="7a8b4-145">RELATED LINKS</span></span>

[<span data-ttu-id="7a8b4-146">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="7a8b4-146">Get-AuthenticodeSignature</span></span>](Get-AuthenticodeSignature.md)

[<span data-ttu-id="7a8b4-147">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="7a8b4-147">Set-AuthenticodeSignature</span></span>](Set-AuthenticodeSignature.md)
