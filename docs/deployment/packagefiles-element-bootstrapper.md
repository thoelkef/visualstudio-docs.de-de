---
title: '&lt;PackageFiles&gt; Element (Bootstrapper) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <PackageFiles> element [bootstrapper]
ms.assetid: 3ea252d7-18a3-47d8-af83-47feebcfe82b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f900e1e86c20e4ce59984f2a7a6ff91e9014129d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
ms.locfileid: "31560907"
---
# <a name="ltpackagefilesgt-element-bootstrapper"></a>&lt;PackageFiles&gt; Element (Bootstrapper)
Die `PackageFiles` Element enthält `PackageFile` -Elemente, die die als Ergebnis des ausgeführten Installationspakete definieren die `Command` Element.  
  
## <a name="syntax"></a>Syntax  
  
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
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Die `PackageFiles` Element hat das folgende Attribut.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`CopyAllPackageFiles`|Dies ist optional. Wenn auf festgelegt `false`, Installationsprogramm wird nur Dateien aus dem Herunterladen der `Command` Element. Wenn auf festgelegt `true`, alle Dateien werden heruntergeladen.<br /><br /> Wenn auf festgelegt `IfNotHomesite`, Installationsprogramm wird weisen das gleiche Verhalten wie `False` Wenn `ComponentsLocation` auf festgelegt ist `HomeSite`, und andernfalls verhält als `True`. Diese Einstellung kann hilfreich sein, können Pakete, die selbst werden Bootstrapper ihr eigenes Verhalten in einem Szenario HomeSite ausgeführt.<br /><br /> Die Standardeinstellung ist `true`.|  
  
## <a name="packagefile"></a>PackageFile  
 Die `PackageFile` Element ist ein untergeordnetes Element von der `PackageFiles` Element. Ein `PackageFiles` -Element muss mindestens eine aufweisen `PackageFile` Element.  
  
 `PackageFile` verfügt über die folgenden Attribute aus.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Name`|Erforderlich. Der Name der Paketdatei. Dies ist der Name, der `Command` Element verweist, wenn sie die Bedingungen definiert, unter dem ein Paket wird installiert. Dieser Wert dient auch als Schlüssel in der `Strings` Tabelle, um den lokalisierten Namen abzurufen, die tools wie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verwendet, um das Paket beschreiben.|  
|`HomeSite`|Dies ist optional. Der Speicherort des Pakets auf dem Remoteserver, wenn er nicht mit dem Installationsprogramm enthalten ist.|  
|`CopyOnBuild`|Dies ist optional. Gibt an, ob der Bootstrapper die Paketdatei auf dem Datenträger während des Buildvorgangs kopieren soll. Der Standardwert ist "True".|  
|`PublicKey`|Der verschlüsselte öffentliche Schlüssel des Signaturgebers für das Paket-Zertifikat. Erforderlich, wenn `HomeSite` verwendet, andernfalls optional.|  
|`Hash`|Dies ist optional. Ein SHA1-Hash der Paketdatei. Dies wird verwendet, um die Integrität der Datei zum Zeitpunkt der Installation zu überprüfen. Wenn die identische Hash aus der Paketdatei berechnet werden kann, wird das Paket nicht installiert werden.|  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel definiert die Pakete für die [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] verteilbare Paket und seine Abhängigkeiten, z. B. Windows Installer.  
  
```  
<PackageFiles>  
    <PackageFile Name="instmsia.exe" HomeSite="InstMsiAExe" PublicKey="3082010A0282010100AA99BD39A81827F42B3D0B4C3F7C772EA7CBB5D18C0DC23A74D793B5E0A04B3F595ECE454F9A7929F149CC1A47EE55C2083E1220F855F2EE5FD3E0CA96BC30DEFE58C82732D08554E8F09110BBF32BBE19E5039B0B861DF3B0398CB8FD0B1D3C7326AC572BCA29A215908215E277A34052038B9DC270BA1FE934F6F335924E5583F8DA30B620DE5706B55A4206DE59CBF2DFA6BD154771192523D2CB6F9B1979DF6A5BF176057929FCC356CA8F440885558ACBC80F464B55CB8C96774A87E8A94106C7FF0DE968576372C36957B443CF323A30DC1BE9D543262A79FE95DB226724C92FD034E3E6FB514986B83CD0255FD6EC9E036187A96840C7F8E203E6CF050203010001"/>  
    <PackageFile Name="WindowsInstaller-KB884016-v2-x86.exe" HomeSite="Msi30Exe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
    <PackageFile Name="dotnetfx.exe" HomeSite="DotNetFXExe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
    <PackageFile Name="dotnetchk.exe"/>  
</PackageFiles>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [\<Product >-Element](../deployment/product-element-bootstrapper.md)   
 [\<Package >-Element](../deployment/package-element-bootstrapper.md)   
 [Referenz zum Produkt- und Paketschema](../deployment/product-and-package-schema-reference.md)