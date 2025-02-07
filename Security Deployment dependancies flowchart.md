```mermaid

flowchart LR

    %% Core Zero Trust 
    Zero[Zero Trust/Security Suite Deployed]
    Data[Protect and govern sensitive data]
    Threats[Defend against threats]
    Foundation[Zero trust foundation]

    Foundation-->Zero
    Data-->Zero
    Threats-->Zero
    
    click Zero "https://"

    %% Data Security
    AI[GenAI Data Safety]-->Data
    DSPM[Microsoft Purview Data Security Posture Management DPSM]-->AI
    DSPM-->Data
    PurAud[Purview Audit]-->DSPM
    EndpointDLP[Endpoint DLP Policy]-->DSPM
    EndpointDLP-->Data
    OnboardDevices[Onboard Windows devices into Microsoft 365]
    Purbrowserext[Deploy Purview browser extension]-->Data
    Purbrowserext-->DSPM

    %%Theats

    XDR[M365 Defender for XDR]
    DID[Defender for Identity]-->XDR
    MDO[Defender for Office 365]-->XDR
    MDE[Defender for Endpoint]-->XDR
    MDCA[Defender for Cloud Apps]-->XDR
    XDR-->Threats
    MDVM[Defender for Volnerability Management]-->Threats

    %%Foundations
    IntuneEnroll[Enroll devices into management]-->IntuneCompPol[Configure complianece policies]
    MFA[Deploy Multifactor Authentication]-->CA[Configure Conditional Access Policies]
    IntuneCompPol-->CA
    CA-->Foundation
    CloudID[Configure Cloud Identity]-->MFA



    %% Links 

    M365ZeroTrustDeployment[Zero Trust deployment plan with Microsoft 365]
    click M365ZeroTrustDeployment "https://learn.microsoft.com/en-us/microsoft-365/security/microsoft-365-zero-trust?view=o365-worldwide"
    ZeroTrustAssessmentWorkshop[Zero Trust Assessment Workshop]
    click ZeroTrustAssessmentWorkshop "https://microsoft.github.io/zerotrustassessment/"
    ZeroTrustAssessmentTool[Zero Trust Assessment Tool]
    click ZeroTrustAssessmentTool "https://microsoft.github.io/zerotrustassessment/docs/app-permissions"
    PurviewBlueprint[Purview Deployment Models]
    click PurviewBlueprint "https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-overview" 
    
    subgraph Resources
    M365ZeroTrustDeployment
    ZeroTrustAssessmentWorkshop
    ZeroTrustAssessmentTool
    PurviewBlueprint

'''