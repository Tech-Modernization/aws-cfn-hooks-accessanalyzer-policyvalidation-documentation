# aws-cfn-hooks-accessanalyzer-policyvalidation-documentation
AWS CloudFormation Public Third Party Hook Documentation

This public cloudformation hook will validate your IAM policies conform AWS Best Practices.

Detailed walkthrough of the hook can be found [here](https://aws.amazon.com/about-aws/whats-new/2022/02/aws-announces-general-availability-aws-cloudformation-hooks/).

## FAQs
### Which region is the hook available?
Currently at the time of launch the CloudFormation Hook is available in the Frankfurt (eu-central-1) region.
If you would like us to make the hook available in more regions get in touch.

### Which CloudFormation resources are validated?
Our hook is triggered on `Create` and `Update` CloudFormation actions.
It validates the policies for the following IAM resource types:
- AWS::IAM::Policy
- AWS::IAM::Role
- AWS::IAM::User
- AWS::IAM::Group
- AWS::IAM::ManagedPolicy

Each of these resources have their own variation of defining the policy document permissions within the CloudFormation syntax, which we have incorporated:
- Policy document
- Inline policies
- Assume role policies

### How do I adapt the functionality of the hook?

You can edit the configuration of the hook deployed in your account. Go to the CloudFormation activated hooks page, find our activated hook, edit configuration in the dropdown menu top right.
See our hook configuration file for an example [configuration](Hook%20Configuration/hook-config.json).

With the configuration you can manipulate the functionality of the hook:
- `TargetStacks`: AWS Parameter to enable/disable the hook. Type: `Str` Accepted values: `"ALL" / "NONE"`
- `FailureMode`: AWS Parameter for mode of failure, Fail the cloudformation execution if hook failed, or raise a warning and continue the execution. Type: `Str` Accepted values: `"FAIL" / "WARN"`
- `languageLocale`: Contino Parameter for setting the language in which IAM Access Analyzer will report their findings. Type: `Str` Allowed values: `"DE" / "EN" / "ES" / "FR" / "IT" / "JA" / "KO" / "PT_BR" / "ZH_CN" / "ZH_TW"`
- `accessAnalyzerMuteGeneralFindings`: Contino Parameter for muting General findings. If enabled we will ignore findings with the `WARNING` type. Type: `Boolean` Accepted values: `true / false`
- `accessAnalyzerMuteSuggestionFindings`: Contino Parameter for muting Suggestion findings. If enabled we will ignore findings with the `SUGGESTION` type. Type: `Boolean` Accepted values: `true / false`
- `accessAnalyzerMuteSecurityFindings`: Contino Parameter for muting Security findings. If enabled we will ignore findings with the `SECURITY_WARNING` type. Type: `Boolean` Accepted values: `true / false`
- `accessAnalyzerMuteErrorFindings`: Contino Parameter for muting Error findings. If enabled we will ignore findings with the `ERROR` type. Type: `Boolean` Accepted values: `true / false`
