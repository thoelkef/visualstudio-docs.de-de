---
title: "Referenz zum Produkt- und Paketschema | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.CircularIncludes"
  - "MSBuild.ResolveManifestFiles.PublishFileNotFound"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce, Bootstrapperelemente"
  - "ClickOnce, Produkt- und Paketdateien"
  - "Paketdateien [ClickOnce]"
  - "Paketdateien [Windows Installer]"
  - "Produktdateien [ClickOnce]"
  - "Produktdateien [Windows Installer]"
  - "Windows Installer, Bootstrapperelemente"
  - "Windows Installer, Produkt- und Paketdateien"
ms.assetid: 5a74878f-b896-4cca-b968-98d00fe78fb0
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 7
---
# Referenz zum Produkt- und Paketschema
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Eine *Produktdatei* ist ein XML\-Manifest, in dem alle externen Abhängigkeiten beschrieben werden, die für eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung erforderlich sind.  Zu den externen Abhängigkeiten zählen z. B. [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] und Microsoft Data Access Components \(MDAC\).  Eine Paketdatei ist mit einer Produktdatei vergleichbar, wird jedoch verwendet, um die kulturspezifischen Komponenten einer Abhängigkeit wie lokalisierte Assemblys, Lizenzverträge und Dokumentation zu installieren.  
  
 Die Produkt\- und Paketdateien bestehen aus einem `Product`\-Element bzw. `Package`\-Element der obersten Ebene, das wiederum die folgenden Elemente enthält.  
  
|Element|Beschreibung|Attribute|  
|-------------|------------------|---------------|  
|[\<Product\>\-Element](../deployment/product-element-bootstrapper.md)|Erforderliches Element der obersten Ebene für Produktdateien.|None|  
|[\<Package\>\-Element](../deployment/package-element-bootstrapper.md)|Erforderliches Element der obersten Ebene für Paketdateien.|`Culture`<br /><br /> `Name`<br /><br /> `EULA`|  
|[\<RelatedProducts\>\-Element](../deployment/relatedproducts-element-bootstrapper.md)|Optionales Element für Produktdateien.  Die anderen Produkte, die dieses Produkt installiert oder von denen es abhängt.|None|  
|[\<InstallChecks\>\-Element](../deployment/installchecks-element-bootstrapper.md)|Erforderliches Element.  Listet die Abhängigkeitsprüfungen auf, die während der Installation auf dem lokalen Computer ausgeführt werden sollen.|None|  
|[\<Commands\>\-Element](../deployment/commands-element-bootstrapper.md)|Erforderliches Element.  Führt eine oder mehrere Installationsprüfungen gemäß der Beschreibung in `InstallChecks` aus und gibt an, welches Paket installiert werden soll, falls die Prüfung negativ ausfällt.|None|  
|[\<PackageFiles\>\-Element](../deployment/packagefiles-element-bootstrapper.md)|Erforderliches Element.  Listet die Pakete auf, die während dieses Installationsprozesses installiert werden können.|None|  
|[\<Strings\>\-Element](../deployment/strings-element-bootstrapper.md)|Erforderliches Element.  Speichert lokalisierte Versionen von Produktnamen und Fehlerzeichenfolgen.|None|  
  
## Hinweise  
 Das Paketschema wird von setup.exe verwendet, einem von der MSBuild\-Bootstrapperaufgabe generierten Stubprogramm, das nur wenig eigene fest programmierte Logik enthält.  Das Schema steuert jeden Aspekt des Installationsprozesses.  
  
 `InstallChecks` sind die Tests, die von "setup.exe" beim Vorhandensein eines angegebenen Pakets ausgeführt werden sollten.  `PackageFiles` listet alle Pakete auf, die möglicherweise installiert werden müssen, wenn ein bestimmter Test negativ ausfällt.  Mit jedem Command\-Eintrag unter Commands wird einer der von `InstallChecks` beschriebenen Tests ausgeführt, und es wird angegeben, welche `PackageFile` ausgeführt werden soll, falls der Test negativ ausfällt.  Mithilfe des `Strings`\-Elements können Sie Produktnamen und Fehlermeldungen lokalisieren, sodass Sie die Anwendung mit einer einzigen binären Installationsdatei für beliebig viele Sprachen installieren können.  
  
## Beispiel  
 Im folgenden Codebeispiel wird eine vollständige Produktdatei für das Installieren von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] veranschaulicht.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
  
<Product  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  ProductCode="Microsoft.Net.Framework.2.0"  
>  
  
    <RelatedProducts>  
        <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
    </RelatedProducts>  
  
    <!-- Defines list of files to be copied on build -->  
    <PackageFiles>  
        <PackageFile Name="instmsia.exe" HomeSite="InstMsiAExe" PublicKey="3082010A0282010100AA99BD39A81827F42B3D0B4C3F7C772EA7CBB5D18C0DC23A74D793B5E0A04B3F595ECE454F9A7929F149CC1A47EE55C2083E1220F855F2EE5FD3E0CA96BC30DEFE58C82732D08554E8F09110BBF32BBE19E5039B0B861DF3B0398CB8FD0B1D3C7326AC572BCA29A215908215E277A34052038B9DC270BA1FE934F6F335924E5583F8DA30B620DE5706B55A4206DE59CBF2DFA6BD154771192523D2CB6F9B1979DF6A5BF176057929FCC356CA8F440885558ACBC80F464B55CB8C96774A87E8A94106C7FF0DE968576372C36957B443CF323A30DC1BE9D543262A79FE95DB226724C92FD034E3E6FB514986B83CD0255FD6EC9E036187A96840C7F8E203E6CF050203010001"/>  
        <PackageFile Name="WindowsInstaller-KB884016-v2-x86.exe" HomeSite="Msi30Exe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
        <PackageFile Name="dotnetfx.exe" HomeSite="DotNetFXExe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
        <PackageFile Name="dotnetchk.exe"/>  
    </PackageFiles>  
  
    <InstallChecks>  
        <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />  
        <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />  
    </InstallChecks>  
  
    <!-- Defines how to invoke the setup for the .NET Framework redist -->  
    <!-- TODO: Needs EstrimatedTempSpace, LogFile, and an update of EstimatedDiskSpace -->  
    <Commands Reboot="Defer">  
        <Command PackageFile="instmsia.exe"  
                 Arguments= ' /q /c:"msiinst /delayrebootq"'  
                 EstimatedInstallSeconds="20" >  
            <InstallConditions>  
                <BypassIf Property="VersionNT" Compare="ValueExists"/>  
                <BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="2.0"/>  
            </InstallConditions>  
            <ExitCodes>  
                <ExitCode Value="0" Result="SuccessReboot"/>  
                <ExitCode Value="1641" Result="SuccessReboot"/>  
                <ExitCode Value="3010" Result="SuccessReboot"/>  
                <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
            </ExitCodes>  
        </Command>  
        <Command PackageFile="WindowsInstaller-KB884016-v2-x86.exe"  
                 Arguments= '/quiet /norestart'   
                 EstimatedInstallSeconds="20" >  
          <InstallConditions>  
              <BypassIf Property="Version9x" Compare="ValueExists"/>  
              <BypassIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3"/>  
              <BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="3.0"/>  
              <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
          </InstallConditions>  
          <ExitCodes>  
              <ExitCode Value="0" Result="Success"/>  
              <ExitCode Value="1641" Result="SuccessReboot"/>  
              <ExitCode Value="3010" Result="SuccessReboot"/>  
              <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
          </ExitCodes>  
        </Command>  
        <Command PackageFile="dotnetfx.exe"   
             Arguments=' /q:a /c:"install /q /l"'   
             EstimatedInstalledBytes="21000000"   
             EstimatedInstallSeconds="300">  
  
            <!-- These checks determine whether the package is to be installed -->  
            <InstallConditions>  
                <!-- Either of these properties indicates the .NET Framework is already installed -->  
                <BypassIf Property="DotNetInstalled" Compare="ValueNotEqualTo" Value="0"/>  
  
                <!-- Block install if user does not have admin privileges -->  
                <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
  
                <!-- Block install on Windows 95 -->  
                <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatformWin9x"/>  
  
                <!-- Block install on Windows 2000 SP 2 or less -->  
                <FailIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3" String="InvalidPlatformWinNT"/>  
  
                <!-- Block install if Internet Explorer 5.01 or greater is not present -->  
                <FailIf Property="IEVersion" Compare="ValueNotExists" String="InvalidPlatformIE" />  
                <FailIf Property="IEVersion" Compare="VersionLessThan" Value="5.01" String="InvalidPlatformIE" />  
  
                <!-- Block install if the platform is not x86 -->  
                <FailIf Property="ProcessorArchitecture" Compare="ValueNotEqualTo" Value="Intel" String="InvalidPlatformArchitecture" />  
            </InstallConditions>  
  
            <ExitCodes>  
                <ExitCode Value="0" Result="Success"/>  
                <ExitCode Value="3010" Result="SuccessReboot"/>  
                <ExitCode Value="4097" Result="Fail" String="AdminRequired"/>  
                <ExitCode Value="4098" Result="Fail" String="WindowsInstallerComponentFailure"/>  
                <ExitCode Value="4099" Result="Fail" String="WindowsInstallerImproperInstall"/>  
                <ExitCode Value="4101" Result="Fail" String="AnotherInstanceRunning"/>  
                <ExitCode Value="4102" Result="Fail" String="OpenDatabaseFailure"/>  
                <ExitCode Value="4113" Result="Fail" String="BetaNDPFailure"/>  
                <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
            </ExitCodes>  
  
        </Command>  
    </Commands>  
</Product>  
```  
  
## Siehe auch  
 [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)