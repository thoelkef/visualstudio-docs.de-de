---
title: "&lt;Abhängigkeit&gt; Element (ClickOnce-Anwendung) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#osVersionInfo
- urn:schemas-microsoft-com:asm.v2#os
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#dependency
- http://www.w3.org/2000/09/xmldsig#DigestValue
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
- urn:schemas-microsoft-com:asm.v2#dependentAssembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- manifests [ClickOnce], dependency element
- <dependency> element [ClickOnce application manifest]
ms.assetid: 09d6a1e0-60f8-4fbd-843b-8e49ee3115a3
caps.latest.revision: "34"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 7a0604113161fed432219f84ac6c4d8a6a4d7666
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="ltdependencygt-element-clickonce-application"></a>&lt;Abhängigkeit&gt; Element (ClickOnce-Anwendung)
Identifiziert eine Plattform oder Assembly Abhängigkeit, die für die Anwendung erforderlich ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      <dependency>  
   <dependentOS  
      supportURL  
      description  
   >  
      <osVersionInfo>  
         <os  
            majorVersion  
            minorVersion  
            buildNumber  
            servicePackMajor  
            servicePackMinor  
            productType  
            suiteType  
         />   
      </osVersionInfo>  
   </dependentOS>  
   <dependentAssembly  
      dependencyType  
      allowDelayedBinding  
      group  
      codeBase  
      size  
   >  
      <assemblyIdentity  
         name  
         version  
         processorArchitecture  
         language  
      >  
         <hash>  
            <dsig:Transforms>  
               <dsig:Transform  
                  Algorithm  
            />  
            </dsig:Transforms>  
            <dsig:DigestMethod />  
            <dsig:DigestValue>  
            </dsig:DigestValue>  
    </hash>  
  
      </assemblyIdentity>  
   </dependentAssembly>  
</dependency>  
```  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Die `dependency` Element ist erforderlich. Möglicherweise mehrere Instanzen von `dependency` im gleichen Anwendungsmanifest.  
  
 Die `dependency` Element weist keine Attribute und enthält die folgenden untergeordneten Elemente.  
  
### <a name="dependentos"></a>dependentOS  
 Dies ist optional. Enthält die `osVersionInfo` Element. Die `dependentOS` und `dependentAssembly` Elemente schließen sich gegenseitig: eines dieser Zuordnungsverfahren muss vorhanden sein, für eine `dependency` -Element, aber nicht beides.  
  
 `dependentOS`unterstützt die folgenden Attribute an.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`supportUrl`|Dies ist optional. Gibt eine Support-URL für die abhängige Plattform. Diese URL wird dem Benutzer angezeigt, wenn die erforderliche Plattform gefunden wird.|  
|`description`|Dies ist optional. Beschreibt das Betriebssystem beschrieben, indem Sie in einem von Menschen lesbaren Form der `dependentOS` Element.|  
  
### <a name="osversioninfo"></a>osVersionInfo  
 Erforderlich. Dieses Element ist ein untergeordnetes Element des `dependentOS`-Elements und enthält das `os`-Element. Dieses Element weist keine Attribute auf.  
  
### <a name="os"></a>Betriebssystem  
 Erforderlich. Dieses Element ist ein untergeordnetes Element des `osVersionInfo`-Elements. Dieses Element weist folgende Attribute auf.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`majorVersion`|Erforderlich. Gibt die Hauptversionsnummer des Betriebssystems an.|  
|`minorVersion`|Erforderlich. Gibt die Nebenversionsnummer des Betriebssystems an.|  
|`buildNumber`|Erforderlich. Gibt die Buildnummer des Betriebssystems.|  
|`servicePackMajor`|Erforderlich. Gibt die Service Pack-Hauptversionsnummer des Betriebssystems an.|  
|`servicePackMinor`|Dies ist optional. Gibt die Service Pack-Nebenversionsnummer des Betriebssystems an.|  
|`productType`|Dies ist optional. Gibt den Wert der Produkt-Typ. Gültige Werte sind `server`, `workstation` und `domainController`. Für Windows 2000 Professional, wird dieser Attributwert `workstation`.|  
|`suiteType`|Dies ist optional. Identifiziert eine Produktsuite im System oder das System Konfigurationstyp verfügbar. Gültige Werte sind `backoffice`, `blade`, `datacenter`, `enterprise`, `home`, `professional`, `smallbusiness`, `smallbusinessRestricted`, und `terminal`. Für Windows 2000 Professional, wird dieser Attributwert `professional`.|  
  
### <a name="dependentassembly"></a>dependentAssembly  
 Dies ist optional. Enthält die `assemblyIdentity` Element. Die `dependentOS` und `dependentAssembly` Elemente schließen sich gegenseitig: eines dieser Zuordnungsverfahren muss vorhanden sein, für eine `dependency` -Element, aber nicht beides.  
  
 `dependentAssembly`verfügt über die folgenden Attribute aus.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`dependencyType`|Erforderlich. Gibt den Abhängigkeitstyp. Gültige Werte sind `preprequisite` und `install`. Ein `install` Assembly installiert ist, als Teil der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung. Ein `prerequisite` Assembly in den globalen Assemblycache (GAC) vor dem vorhanden sein muss die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung installieren kann.|  
|`allowDelayedBinding`|Erforderlich. Gibt an, ob die Assembly programmgesteuert zur Laufzeit geladen werden kann.|  
|`group`|Dies ist optional. Wenn die `dependencyType` -Attributsatz zur `install`, kennzeichnet eine benannte Gruppe von Assemblys bei Bedarf die einzige Installation. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Bedarfsgerechtes Herunterladen von Assemblys mit der API für die ClickOnce-Bereitstellung unter Verwendung des Designers](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md).<br /><br /> Wenn auf festgelegt `framework` und `dependencyType` -Attributsatz zur `prerequisite`, kennzeichnet die Assembly als Teil von .NET Framework. Der globale Assemblycache (GAC) wird nicht für diese Assembly überprüft, bei der Installation auf [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] und höheren Versionen.|  
|`codeBase`|Erforderlich, wenn die `dependencyType` -Attributsatz zur `install`. Der Pfad der abhängigen Assembly. Entweder ein absoluter Pfad oder ein Pfad relativ zum Code des Manifests kann Basis sein. Dieser Pfad muss ein gültiger URI in der Reihenfolge für das Assemblymanifest gültig ist.|  
|`size`|Erforderlich, wenn die `dependencyType` -Attributsatz zur `install`. Die Größe der abhängigen Assembly, in Bytes.|  
  
### <a name="assemblyidentity"></a>assemblyIdentity  
 Erforderlich. Dieses Element ist ein untergeordnetes Element des `dependentAssembly`-Elements und weist folgende Attribute auf.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`name`|Erforderlich. Identifiziert den Namen der Anwendung.|  
|`version`|Erforderlich. Gibt die Versionsnummer der Anwendung im folgenden Format an:`major.minor.build.revision`|  
|`publicKeyToken`|Dies ist optional. Gibt eine hexadezimale Zeichenfolge von 16-Zeichen, die die letzten 8 Bytes des darstellt der `SHA-1` der Hashwert des öffentlichen Schlüssels unter dem die Anwendung oder Assembly signiert ist. Der öffentliche Schlüssel zum Signieren des Katalogs muss mindestens 2048 Bits betragen.|  
|`processorArchitecture`|Dies ist optional. Gibt den Prozessor. Gültige Werte sind `x86` für Windows 32-Bit- und `I64` für 64-Bit-Windows.|  
|`language`|Dies ist optional. Identifiziert die zweiteiligen Sprachcodes, z. B. EN-US, der Assembly an.|  
  
### <a name="hash"></a>hash  
 Die `hash` Element ist ein optionales untergeordnetes Element von der `assemblyIdentity` Element. Die `hash` -Element weist keine Attribute.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]einen algorithmischen Hash aller Dateien in einer Anwendung verwendet als eine sicherheitsüberprüfung, um sicherzustellen, dass keine der Dateien nach der Bereitstellung geändert wurden. Wenn die `hash` Element nicht enthalten ist, wird diese Überprüfung nicht ausgeführt werden. Daher wird das Auslassen der `hash` Element wird nicht empfohlen.  
  
### <a name="dsigtransforms"></a>dsig: Transforms  
 Die `dsig:Transforms` Element ist ein erforderliches untergeordnetes Element des dem `hash` Element. Die `dsig:Transforms` -Element weist keine Attribute.  
  
### <a name="dsigtransform"></a>dsig  
 Die `dsig:Transform` Element ist ein erforderliches untergeordnetes Element des dem `dsig:Transforms` Element. Die `dsig:Transform` Element weist folgende Attribute.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Algorithm`|Der Algorithmus zum Berechnen des Digests für diese Datei verwendet wird. Zurzeit der einzige Wert von verwendete [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ist `urn:schemas-microsoft-com:HashTransforms.Identity`.|  
  
### <a name="dsigdigestmethod"></a>DigestMethod  
 Die `dsig:DigestMethod` Element ist ein erforderliches untergeordnetes Element des dem `hash` Element. Die `dsig:DigestMethod` Element weist folgende Attribute.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Algorithm`|Der Algorithmus zum Berechnen des Digests für diese Datei verwendet wird. Zurzeit der einzige Wert von verwendete [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ist `http://www.w3.org/2000/09/xmldsig#sha1`.|  
  
### <a name="dsigdigestvalue"></a>dsig: DigestValue  
 Die `dsig:DigestValue` Element ist ein erforderliches untergeordnetes Element des dem `hash` Element. Die `dsig:DigestValue` -Element weist keine Attribute. Der Textwert ist der berechnete Hash für die angegebene Datei.  
  
## <a name="remarks"></a>Hinweise  
 Alle Assemblys, die von der Anwendung verwendeten benötigen eine entsprechende `dependency` Element. Abhängige Assemblys enthalten keine Assemblys, die als Plattformassemblys im globalen Assemblycache vorinstalliert sein müssen.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, `dependency` Elemente in einem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendungsmanifest. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels für die [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md) Thema.  
  
```  
<dependency>  
  <dependentOS>  
    <osVersionInfo>  
      <os   
        majorVersion="4"   
        minorVersion="10"   
        buildNumber="0"   
        servicePackMajor="0" />  
    </osVersionInfo>  
  </dependentOS>  
</dependency>  
<dependency>  
  <dependentAssembly  
    dependencyType="preRequisite"  
    allowDelayedBinding="true">  
    <assemblyIdentity  
      name="Microsoft.Windows.CommonLanguageRuntime"  
      version="4.0.20506.0" />  
  </dependentAssembly>  
</dependency>  
  
<dependency>  
  <dependentAssembly  
    dependencyType="install"  
    allowDelayedBinding="true"  
    codebase="MyApplication.exe"  
    size="4096">  
    <assemblyIdentity  
      name="MyApplication"  
      version="1.0.0.0"  
      language="neutral"  
      processorArchitecture="x86" />  
    <hash>  
      <dsig:Transforms>  
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
      </dsig:Transforms>  
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
      <dsig:DigestValue>DpTW7RzS9IeT/RBSLj54vfTEzNg=</dsig:DigestValue>  
    </hash>  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md)   
 [\<Dependency >-Element](../deployment/dependency-element-clickonce-deployment.md)