---
title: "&lt;PackageFiles&gt;-Element (Bootstrapper) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<PackageFiles>-Element [Bootstrapper]"
ms.assetid: 3ea252d7-18a3-47d8-af83-47feebcfe82b
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;PackageFiles&gt;-Element (Bootstrapper)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das `PackageFiles`\-Element enthält `PackageFile`\-Elemente, die die als Ergebnis des `Command`\-Elements ausgeführten Installationspakete definieren.  
  
## Syntax  
  
```  
<PackageFiles  
    CopyAllPackageFiles  
>  
    <PackageFile   
        Name  
        HomeSite  
        CopyOnBuild  
        PublicKey  
        Hash  
    />  
</PackageFiles>  
```  
  
## Elemente und Attribute  
 Das `PackageFiles`\-Element verfügt über das folgende Attribut.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`CopyAllPackageFiles`|Optional.  Wenn dies auf `false` festgelegt ist, lädt das Installationsprogramm nur Dateien herunter, auf die vom `Command`\-Element verwiesen wird.  Wenn dies auf `true` festgelegt ist, werden alle Dateien heruntergeladen.<br /><br /> Wenn dies auf `IfNotHomesite` festgelegt ist, verhält sich das Installationsprogramm so wie bei der Einstellung `False`, sofern `ComponentsLocation` auf `HomeSite` festgelegt, andernfalls so wie bei der Einstellung `True`.  Diese Einstellung kann hilfreich sein, damit Pakete, bei denen es sich um Bootstrapper handelt, ihr eigenes Verhalten einem HomeSite\-Szenario ausführen können.<br /><br /> Der Standardwert ist `true`.|  
  
## PackageFile  
 Das `PackageFile`\-Element ist ein untergeordnetes Element des `PackageFiles`\-Elements.  Ein `PackageFiles`\-Element muss über mindestens ein `PackageFile`\-Element verfügen.  
  
 `PackageFile` verfügt über die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`Name`|Erforderlich.  Der Name der Paketdatei.  Dies ist der Name, auf den das `Command`\-Element verweist, wenn es die Bedingungen definiert, unter denen ein Paket installiert wird.  Dieser Wert wird auch als Schlüsselwert für die `Strings`\-Tabelle verwendet, um den lokalisierten Namen abzurufen, mit dem Tools wie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] das Paket beschreiben.|  
|`HomeSite`|Optional.  Der Speicherort des Pakets auf dem Remoteserver, wenn es im Installationsprogramm nicht enthalten ist.|  
|`CopyOnBuild`|Optional.  Gibt an, ob der Bootstrapper die Paketdatei zur Buildzeit auf den Datenträger kopieren soll.  Der Standardwert ist true.|  
|`PublicKey`|Der verschlüsselte öffentliche Schlüssel vom Zertifikatssignaturgeber des Pakets.  Erforderlich, wenn `HomeSite` verwendet wird, andernfalls optional.|  
|`Hash`|Optional.  Ein SHA1\-Hash der Paketdatei.  Er wird verwendet, um die Integrität der Datei bei der Installation zu überprüfen.  Wenn der identische Hash nicht von der Paketdatei berechnet werden kann, wird das Paket nicht installiert.|  
  
## Beispiel  
 Im folgenden Codebeispiel werden Pakete für das verteilbare Paket von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] und die entsprechenden Abhängigkeiten, z. B. Windows Installer, definiert.  
  
```  
<PackageFiles>  
    <PackageFile Name="instmsia.exe" HomeSite="InstMsiAExe" PublicKey="3082010A0282010100AA99BD39A81827F42B3D0B4C3F7C772EA7CBB5D18C0DC23A74D793B5E0A04B3F595ECE454F9A7929F149CC1A47EE55C2083E1220F855F2EE5FD3E0CA96BC30DEFE58C82732D08554E8F09110BBF32BBE19E5039B0B861DF3B0398CB8FD0B1D3C7326AC572BCA29A215908215E277A34052038B9DC270BA1FE934F6F335924E5583F8DA30B620DE5706B55A4206DE59CBF2DFA6BD154771192523D2CB6F9B1979DF6A5BF176057929FCC356CA8F440885558ACBC80F464B55CB8C96774A87E8A94106C7FF0DE968576372C36957B443CF323A30DC1BE9D543262A79FE95DB226724C92FD034E3E6FB514986B83CD0255FD6EC9E036187A96840C7F8E203E6CF050203010001"/>  
    <PackageFile Name="WindowsInstaller-KB884016-v2-x86.exe" HomeSite="Msi30Exe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
    <PackageFile Name="dotnetfx.exe" HomeSite="DotNetFXExe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
    <PackageFile Name="dotnetchk.exe"/>  
</PackageFiles>  
```  
  
## Siehe auch  
 [\<Product\>\-Element](../deployment/product-element-bootstrapper.md)   
 [\<Package\>\-Element](../deployment/package-element-bootstrapper.md)   
 [Referenz zum Produkt\- und Paketschema](../deployment/product-and-package-schema-reference.md)