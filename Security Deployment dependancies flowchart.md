```mermaid

flowchart LR

    %% Core Zero Trust 
    Zero[Zero Trust/Security Suite Deployed]
    Data[Protect and govern sensitive data]
    Threats[Defend against threats]
    Foundation[Zero trust foundation]

    Foundation-->Zero
    Data-->Zero
    Threats[Defend Against Threats]-->Zero
    
    click Zero "https://aka.ms/zerotrust"
    click Data "https://www.microsoft.com/en-us/security/business/solutions/data-security?msockid=015d6c09ff27605e22fc7f9efecb614d"
    click Threats "https://aka.ms/zerotrust"

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

    subgraph Data Security
    AI
    DSPM
    Data
    PurAud
    EndpointDLP
    Purbrowserext
    end

    %%Theats
    XDR[M365 Defender for XDR]
    DID[Defender for Identity]-->XDR
    MDO[Defender for Office 365]-->XDR
    MDE[Defender for Endpoint]-->XDR
    MDCA[Defender for Cloud Apps]-->XDR
    XDR-->Threats
    MDVM[Defender for Volnerability Management]-->Threats

    subgraph Defend Against Threats
    XDR
    DID
    MDO
    MDE
    MDCA
    MDVM
    Threats
    end

    %%Foundations
    IntuneEnroll[Enroll devices into management]-->IntuneCompPol[Configure complianece policies]
    MFA[Deploy Multifactor Authentication]-->CA[Configure Conditional Access Policies]
    IntuneCompPol-->OnboardDevices
    CA-->Foundation
    CloudID[Configure Cloud Identity]-->MFA
    OnboardDevices-->CA

    subgraph Foundations
    IntuneEnroll
    MFA
    CloudID
    Foundation
    CA
    OnboardDevices
    IntuneCompPol
    end

    %% Entra Suite 

    Foundation-->RCA[Risk Based Conditional Access]
    RCA-->IDProtection[Entra Identity Protection]
    IDProtAlerts[Entra Identity Protection Alerts and Monitoring]-->IDProtection
    IDProtection-->Zero 
    CA-->EPA[Entra Private Access]
    RCA-->EPA
    EPAConn[Deploy Entra Private Access Connector]-->EPA
    EPA-->GSA[Entra Global Secure Access]
    GSA-->Zero


    %% Links and Resources
    M365ZeroTrustDeployment[Zero Trust deployment plan with Microsoft 365]
    click M365ZeroTrustDeployment "https://learn.microsoft.com/en-us/microsoft-365/security/microsoft-365-zero-trust?view=o365-worldwide"
    ZeroTrustAssessmentWorkshop[Zero Trust Assessment Workshop]
    click ZeroTrustAssessmentWorkshop "https://microsoft.github.io/zerotrustassessment/"
    ZeroTrustAssessmentTool[Zero Trust Assessment Tool]
    click ZeroTrustAssessmentTool "https://microsoft.github.io/zerotrustassessment/docs/app-permissions"
    PurviewBlueprint[Purview Deployment Models]
    click PurviewBlueprint "https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-overview"
        
    subgraph Resources
        direction TB
        M365ZeroTrustDeployment
        ZeroTrustAssessmentWorkshop
        ZeroTrustAssessmentTool
        PurviewBlueprint
    end

    subgraph Products
        Entra 
        Intune
        Purview
        Defender
    end



    %% Product
    style Entra fill:green,stroke:black
    style MFA fill:green,stroke:black
    style CA fill:green,stroke:black
    style CloudID fill:green,stroke:black
    style Defender fill:#66f,stroke:#f6f,stroke-width:4px
    style XDR fill:#66f,stroke:#f6f,stroke-width:4px
    style DID fill:#66f,stroke:#f6f,stroke-width:4px
    style MDO fill:#66f,stroke:#f6f,stroke-width:4px
    style MDE fill:#66f,stroke:#f6f,stroke-width:4px
    style MDCA fill:#66f,stroke:#f6f,stroke-width:4px
    style MDVM fill:#66f,stroke:#f6f,stroke-width:4px
    style Intune fill:red,stroke:yellow
    style IntuneEnroll fill:red,stroke:yellow
    style IntuneCompPol fill:red,stroke:yellow
    style OnboardDevices fill:red,stroke:yellow
    style Purview fill:orange,stroke:white
    style AI fill:orange,stroke:white
    style DSPM fill:orange,stroke:white
    style PurAud fill:orange,stroke:white
    style EndpointDLP fill:orange,stroke:white
    style Purbrowserext fill:orange,stroke:white
'''