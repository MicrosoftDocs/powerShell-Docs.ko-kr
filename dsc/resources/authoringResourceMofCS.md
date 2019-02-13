---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: C#에서 DSC 리소스 작성
ms.openlocfilehash: dcda36d27f2191f140eaaf209e1c85263d2cd8e1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683128"
---
# <a name="authoring-a-dsc-resource-in-c"></a>C#에서 DSC 리소스 작성

> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

일반적으로, Windows PowerShell DSC(필요한 상태 구성) 사용자 지정 리소스는 PowerShell 스크립트로 구현됩니다. 그러나 C#으로 cmdlet을 작성하여 DSC 사용자 지정 리소스의 기능을 구현할 수도 있습니다. C#에서 cmdlet을 작성하는 방법을 알려면 [Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)](/powershell/developer/windows-powershell)을 참조합니다.

C#에서 리소스를 cmdlet으로 구현하는 것 외에 MOF 스키마 만들기, 폴더 구조 만들기, 사용자 지정 DSC 리소스 가져오기 및 사용 프로세스는 [MOF를 사용하여 사용자 지정 DSC 리소스 작성](authoringResourceMOF.md)에 설명된 것과 동일합니다.

## <a name="writing-a-cmdlet-based-resource"></a>cmdlet 기반 리소스 작성
이 예의 경우, 텍스트 파일과 그 내용을 관리하는 간단한 리소스를 구현하게 됩니다.

### <a name="writing-the-mof-schema"></a>MOF 스키마 작성

다음은 MOF 리소스 정의입니다.

```
[ClassVersion("1.0.0"), FriendlyName("xDemoFile")]
class MSFT_XDemoFile : OMI_BaseResource
{
                [Key, Description("path")] String Path;
                [Write, Description("Should the file be present"), ValueMap{"Present","Absent"}, Values{"Present","Absent"}] String Ensure;
                [Write, Description("Contentof file.")] String Content;
};
```

### <a name="setting-up-the-visual-studio-project"></a>Visual Studio 프로젝트 설정
#### <a name="setting-up-a-cmdlet-project"></a>cmdlet 프로젝트 설정

1. Visual Studio를 엽니다.
1. C# 프로젝트를 만들고 이름을 입력합니다.
1. 사용 가능한 프로젝트 템플릿에서 **클래스 라이브러리**를 선택합니다.
1. **확인**을 클릭합니다.
1. System.Automation.Management.dll에 대한 어셈블리 참조를 프로젝트에 추가합니다.
1. 어셈블리 이름을 리소스 이름과 일치하도록 변경합니다. 이 경우 어셈블리의 이름은 **MSFT_XDemoFile**로 지정해야 합니다.

### <a name="writing-the-cmdlet-code"></a>cmdlet 코드 작성

다음 C# 코드는 **Get-TargetResource**, **Set-TargetResource** 및 **Test-TargetResource** cmdlet을 구현합니다.

```C#


namespace cSharpDSCResourceExample
{
    using System;
    using System.Collections.Generic;
    using System.IO;
    using System.Management.Automation;  // Windows PowerShell assembly.

    #region Get-TargetResource

    [OutputType(typeof(System.Collections.Hashtable))]
    [Cmdlet(VerbsCommon.Get, "TargetResource")]
    public class GetTargetResource : PSCmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        /// <summary>
        /// Implement the logic to return the current state of the resource as a hashtable with keys being the resource properties
        /// and the values are the corresponding current value on the machine.
        /// </summary>
        protected override void ProcessRecord()
        {
            var currentResourceState = new Dictionary<string, string>();
            if (File.Exists(Path))
            {
                currentResourceState.Add("Ensure", "Present");

                // read current content
                string CurrentContent = "";
                using (var reader = new StreamReader(Path))
                {
                    CurrentContent = reader.ReadToEnd();
                }
                currentResourceState.Add("Content", CurrentContent);
            }
            else
            {
                currentResourceState.Add("Ensure", "Absent");
                currentResourceState.Add("Content", "");
            }
            // write the hashtable in the PS console.
            WriteObject(currentResourceState);
        }
    }

    # endregion

    #region Set-TargetResource
    [OutputType(typeof(void))]
    [Cmdlet(VerbsCommon.Set, "TargetResource")]
    public class SetTargetResource : PSCmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        [Parameter(Mandatory = false)]

        [ValidateSet("Present", "Absent", IgnoreCase = true)]
        public string Ensure {
            get
            {
                // set the default to present.
               return (this._ensure ?? "Present") ;
            }
            set
            {
                this._ensure = value;
            }
        }

        [Parameter(Mandatory = false)]
        public string Content {
            get { return (string.IsNullOrEmpty(this._content) ? "" : this._content); }
            set { this._content = value; }
        }

        private string _ensure;
        private string _content;

        /// <summary>
        /// Implement the logic to set the state of the machine to the desired state.
        /// </summary>
        protected override void ProcessRecord()
        {
            WriteVerbose(string.Format("Running set with parameters {0}{1}{2}", Path, Ensure, Content));
            if (File.Exists(Path))
            {
                if (Ensure.Equals("absent", StringComparison.InvariantCultureIgnoreCase))
                {
                    File.Delete(Path);
                }
                else
                {
                    // file already exist and ensure "present" is specified. start writing the content to a file
                    if (!string.IsNullOrEmpty(Content))
                    {
                        string existingContent = null;
                        using (var reader = new StreamReader(Path))
                        {
                            existingContent = reader.ReadToEnd();
                        }
                        // check if the content of the file mathes the content passed
                        if (!existingContent.Equals(Content, StringComparison.InvariantCultureIgnoreCase))
                        {
                            WriteVerbose("Existing content did not match with desired content updating the content of the file");
                            using (var writer = new StreamWriter(Path))
                            {
                                writer.Write(Content);
                                writer.Flush();
                            }
                        }
                    }
                }

            }
            else
            {
                if (Ensure.Equals("present", StringComparison.InvariantCultureIgnoreCase))
                {
                    // if nothing is passed for content just write "" otherwise write the content passed.
                    using (var writer = new StreamWriter(Path))
                    {
                        WriteVerbose(string.Format("Creating a file under path {0} with content {1}", Path, Content));
                        writer.Write(Content);
                    }
                }

            }

            /* if you need to reboot the VM. please add the following two line of code.
            PSVariable DscMachineStatus = new PSVariable("DSCMachineStatus", 1, ScopedItemOptions.AllScope);
            this.SessionState.PSVariable.Set(DscMachineStatus);
             */

        }

    }

    # endregion

    #region Test-TargetResource

    [Cmdlet("Test", "TargetResource")]
    [OutputType(typeof(Boolean))]
    public class TestTargetResource : PSCmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        [Parameter(Mandatory = false)]

        [ValidateSet("Present", "Absent", IgnoreCase = true)]
        public string Ensure
        {
            get
            {
                // set the default to present.
                return (this._ensure ?? "Present");
            }
            set
            {
                this._ensure = value;
            }
        }

        [Parameter(Mandatory = false)]
        public string Content
        {
            get { return (string.IsNullOrEmpty(this._content) ? "" : this._content); }
            set { this._content = value; }
        }

        private string _ensure;
        private string _content;

        /// <summary>
        /// Return a boolean value which indicates wheather the current machine is in desired state or not.
        /// </summary>
        protected override void ProcessRecord()
        {
            if (File.Exists(Path))
            {
                if( Ensure.Equals("absent", StringComparison.InvariantCultureIgnoreCase))
                {
                    WriteObject(false);
                }
                else
                {
                    // check if the content matches

                    string existingContent = null;
                    using (var stream = new StreamReader(Path))
                    {
                        existingContent = stream.ReadToEnd();
                    }

                    WriteObject(Content.Equals(existingContent, StringComparison.InvariantCultureIgnoreCase));
                }
            }
            else
            {
                WriteObject(Ensure.Equals("Absent", StringComparison.InvariantCultureIgnoreCase));
            }
        }
    }

    # endregion

}
```

### <a name="deploying-the-resource"></a>리소스 배포

컴파일된 dll 파일은 스크립트 기반 리소스와 비슷한 파일 구조에 저장됩니다. 다음은 이 리소스에 대한 폴더 구조입니다.

```
$env: psmodulepath (folder)
    |- MyDscResources (folder)
        |- MyDscResources.psd1 (file, required)
        |- DSCResources (folder)
            |- MSFT_XDemoFile (folder)
                |- MSFT_XDemoFile.psd1 (file, optional)
                |- MSFT_XDemoFile.dll (file, required)
                |- MSFT_XDemoFile.schema.mof (file, required)
```

### <a name="see-also"></a>참고 항목
#### <a name="concepts"></a>개념
[Writing a custom DSC resource with MOF(MOF를 사용하여 사용자 지정 DSC 리소스 작성)](authoringResourceMOF.md)
#### <a name="other-resources"></a>관련 자료
[Writing a Windows PowerShell Cmdlet](/powershell/developer/windows-powershell)(Windows PowerShell Cmdlet 작성)