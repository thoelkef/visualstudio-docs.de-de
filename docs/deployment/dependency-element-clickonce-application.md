---
title: "&lt;dependency&gt; Element (ClickOnce Application) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "urn:schemas-microsoft-com:asm.v2#osVersionInfo"
  - "urn:schemas-microsoft-com:asm.v2#os"
  - "http://www.w3.org/2000/09/xmldsig#Transform"
  - "urn:schemas-microsoft-com:asm.v2#dependency"
  - "http://www.w3.org/2000/09/xmldsig#DigestValue"
  - "urn:schemas-microsoft-com:asm.v2#assemblyIdentity"
  - "http://www.w3.org/2000/09/xmldsig#DigestMethod"
  - "http://www.w3.org/2000/09/xmldsig#Transforms"
  - "urn:schemas-microsoft-com:asm.v2#hash"
  - "urn:schemas-microsoft-com:asm.v2#dependentAssembly"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "manifests [ClickOnce], dependency element"
  - "<dependency> element [ClickOnce application manifest]"
ms.assetid: 09d6a1e0-60f8-4fbd-843b-8e49ee3115a3
caps.latest.revision: 34
caps.handback.revision: 34
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;dependency&gt; Element (ClickOnce Application)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifiziert eine Plattform\- oder Assemblyabhängigkeit, die für die Anwendung erforderlich ist.  
  
## Syntax  
  
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
  
## Elemente und Attribute  
 Das `dependency`\-Element ist erforderlich.  Es gibt möglicherweise mehrere Instanzen von `dependency` im gleichen Anwendungsmanifest.  
  
 Das `dependency`\-Element weist keine Attribute auf und enthält die folgenden untergeordneten Elemente.  
  
### dependentOS  
 Optional.  Enthält das `osVersionInfo`\-Element.  Das `dependentOS`\-Element und das `dependentAssembly`\-Element schließen sich gegenseitig aus, d. h., für ein `dependency`\-Element muss eines von beiden vorhanden sein, beide dürfen jedoch nicht vorhanden sein.  
  
 `dependentOS` unterstützt die folgenden Attribute:  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`supportUrl`|Optional.  Gibt eine Support\-URL für die abhängige Plattform an.  Diese URL wird dem Benutzer angezeigt, wenn die erforderliche Plattform gefunden wird.|  
|`description`|Optional.  Beschreibt das mit dem `dependentOS`\-Element beschriebene Betriebssystem in lesbarem Format.|  
  
### osVersionInfo  
 Erforderlich.  Dieses Element ist ein untergeordnetes Element des `dependentOS`\-Elements und enthält das `os`\-Element.  Dieses Element weist keine Attribute auf.  
  
### os  
 Erforderlich.  Dieses Element ist ein untergeordnetes Element des `osVersionInfo`\-Elements.  Dieses Element verfügt über die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`majorVersion`|Erforderlich.  Gibt die Hauptversionsnummer des Betriebssystems an.|  
|`minorVersion`|Erforderlich.  Gibt die Nebenversionsnummer des Betriebssystems an.|  
|`buildNumber`|Erforderlich.  Gibt die Buildnummer des Betriebssystems an.|  
|`servicePackMajor`|Erforderlich.  Gibt die Service Pack\-Hauptversionsnummer des Betriebssystems an.|  
|`servicePackMinor`|Optional.  Gibt die Service Pack\-Nebenversionsnummer des Betriebssystems an.|  
|`productType`|Optional.  Identifiziert den Wert für den Produkttyp.  Gültige Werte sind `server`, `workstation` und `domainController`.  Bei Windows 2000 Professional z. B. lautet dieser Attributwert `workstation`.|  
|`suiteType`|Optional.  Identifiziert eine Produktsuite, die auf dem System verfügbar ist, oder den Konfigurationstyp des Systems.  Gültige Werte sind `backoffice`, `blade`, `datacenter`, `enterprise`, `home`, `professional`, `smallbusiness`, `smallbusinessRestricted` und `terminal`.  Bei Windows 2000 Professional z. B. lautet dieser Attributwert `professional`.|  
  
### dependentAssembly  
 Optional.  Enthält das `assemblyIdentity`\-Element.  Das `dependentOS`\-Element und das `dependentAssembly`\-Element schließen sich gegenseitig aus, d. h., für ein `dependency`\-Element muss eines von beiden vorhanden sein, beide dürfen jedoch nicht vorhanden sein.  
  
 `dependentAssembly` verfügt über die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`dependencyType`|Erforderlich.  Gibt den Abhängigkeitstyp an.  Gültige Werte sind `preprequisite` und `install`.  Eine `install`\-Assembly wird als Teil der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung installiert.  Im globalen Assemblycache \(GAC\) muss eine `prerequisite`\-Assembly vorhanden sein, bevor die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung installiert werden kann.|  
|`allowDelayedBinding`|Erforderlich.  Gibt an, ob die Assembly zur Laufzeit programmgesteuert geladen werden kann.|  
|`group`|Optional.  Wenn das `dependencyType`\-Attribut auf `install` festgelegt ist, gibt group eine benannte Gruppe von Assemblys an, die nur bei Bedarf installiert werden.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Bedarfsgerechtes Herunterladen von Assemblys mit der API für die ClickOnce\-Bereitstellung unter Verwendung des Designers](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md).<br /><br /> Wenn group auf `framework` und das `dependencyType`\-Attribut auf `prerequisite` festgelegt ist, gibt group die Assembly als Teil von .NET Framework an.  Der globale Assemblycache \(GAC\) wird nicht auf diese Assembly überprüft, wenn die Installation unter [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] oder einer höheren Version erfolgt.|  
|`codeBase`|Erforderlich, wenn das `dependencyType`\-Attribut auf `install` festgelegt ist.  Der Pfad der abhängigen Assembly.  Kann entweder ein absoluter Pfad oder ein zur CodeBase des Manifests relativer Pfad sein.  Dieser Pfad muss ein gültiger URI sein, damit das Assemblymanifest gültig ist.|  
|`size`|Erforderlich, wenn das `dependencyType`\-Attribut auf `install` festgelegt ist.  Die Größe der abhängigen Assembly in Bytes.|  
  
### assemblyIdentity  
 Erforderlich.  Dieses Element ist ein untergeordnetes Element des `dependentAssembly`\-Elements und verfügt über die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`name`|Erforderlich.  Identifiziert den Namen der Anwendung.|  
|`version`|Erforderlich.  Gibt die Versionsnummer der Anwendung im folgenden Format an: `major.minor.build.revision`|  
|`publicKeyToken`|Optional.  Gibt eine aus 16 Zeichen bestehende hexadezimale Zeichenfolge an, die die letzten 8 Bytes des `SHA-1`\-Hashwerts des öffentlichen Schlüssels darstellt, der zum Signieren der Anwendung oder der Assembly verwendet wird.  Der öffentliche Schlüssel, der zum Signieren des Katalogs verwendet wird, muss mindestens 2048 Bits groß sein.|  
|`processorArchitecture`|Optional.  Gibt den Prozessor an.  Die gültigen Werte sind `x86` für 32\-Bit\-Windows und `I64` für 64\-Bit\-Windows.|  
|`language`|Optional.  Identifiziert die zweiteiligen Sprachcodes der Assembly, z. B. EN\-US.|  
  
### hash  
 Das `hash`\-Element ist ein optionales untergeordnetes Element des `assemblyIdentity`\-Elements.  Das `hash`\-Element weist keine Attribute auf.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] verwendet als Sicherheitsüberprüfung einen algorithmischen Hash aller Dateien in einer Anwendung, um sicherzustellen, dass keine der Dateien nach der Bereitstellung geändert wurde.  Wenn das `hash`\-Element nicht enthalten ist, wird diese Überprüfung nicht ausgeführt. Daher wird das Auslassen des `hash`\-Elements nicht empfohlen.  
  
### dsig:Transforms  
 Das `dsig:Transforms`\-Element ist ein erforderliches untergeordnetes Element des `hash`\-Elements.  Das `dsig:Transforms`\-Element weist keine Attribute auf.  
  
### dsig:Transform  
 Das `dsig:Transform`\-Element ist ein erforderliches untergeordnetes Element des `dsig:Transforms`\-Elements.  Das `dsig:Transform`\-Element verfügt über die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`Algorithm`|Der Algorithmus, der zum Berechnen des Digests für diese Datei verwendet wird.  Derzeit wird von [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nur ein Wert verwendet, nämlich `urn:schemas-microsoft-com:HashTransforms.Identity`.|  
  
### dsig:DigestMethod  
 Das `dsig:DigestMethod`\-Element ist ein erforderliches untergeordnetes Element des `hash`\-Elements.  Das `dsig:DigestMethod`\-Element verfügt über die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`Algorithm`|Der Algorithmus, der zum Berechnen des Digests für diese Datei verwendet wird.  Derzeit wird von [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nur ein Wert verwendet, nämlich `http://www.w3.org/2000/09/xmldsig#sha1`.|  
  
### dsig:DigestValue  
 Das `dsig:DigestValue`\-Element ist ein erforderliches untergeordnetes Element des `hash`\-Elements.  Das `dsig:DigestValue`\-Element weist keine Attribute auf.  Sein Textwert ist der berechnete Hash für die angegebene Datei.  
  
## Hinweise  
 Alle von der Anwendung verwendeten Assemblys müssen ein entsprechendes `dependency`\-Element aufweisen.  Abhängige Assemblys umfassen keine Assemblys, die im globalen Assemblycache als Plattformassemblys vorinstalliert werden müssen.  
  
## Beispiel  
 Im folgenden Codebeispiel werden `dependency`\-Elemente in einem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungsmanifest veranschaulicht.  Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels, das für das [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)\-Thema bereitgestellt wird.  
  
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
  
## Siehe auch  
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)   
 [\<dependency\> Element](../deployment/dependency-element-clickonce-deployment.md)