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



    %%Foundations
    IntuneEnroll[Enroll devices into management]-->IntuneCompPol[Configure complianece policies]
    MFA[Deploy Multifactor Authentication]-->CA[Configure Conditional Access Policies]
    IntuneCompPol-->CA
    CA-->Foundation



'''