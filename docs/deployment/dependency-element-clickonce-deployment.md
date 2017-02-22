---
title: "&lt;dependency&gt; Element (ClickOnce Deployment) | Microsoft Docs"
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
  - "<dependency> element [ClickOnce deployment manifest]"
ms.assetid: 9b4d2082-0347-4922-ac70-85f11b913039
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;dependency&gt; Element (ClickOnce Deployment)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifiziert die Version der Anwendung, die installiert werden soll, und den Speicherort des Anwendungsmanifests.  
  
## Syntax  
  
```  
  
      <dependency>   
   <dependentAssembly  
      preRequisite  
      visible  
      dependencyType  
      codeBase  
      size  
   >   
      <assemblyIdentity   
         name   
         version   
         publicKeyToken   
         processorArchitecture   
         language  
         type  
      />   
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
  
   </dependentAssembly>   
</dependency>  
```  
  
## Elemente und Attribute  
 Das `dependency`\-Element ist erforderlich.  Es sind keine Attribute vorhanden.  Ein Bereitstellungsmanifest kann über mehrere `dependency`\-Elemente verfügen.  
  
 Das `dependency`\-Element drückt normalerweise Abhängigkeiten der Hauptanwendung von Assemblys aus, die in einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung enthalten sind.  Wenn die Anwendung Main.exe eine Assembly mit dem Namen DotNetAssembly.dll verwendet, muss diese Assembly in einem Abhängigkeitsabschnitt aufgeführt sein.  Es können jedoch auch andere Typen von Abhängigkeiten ausgedrückt werden, z. B. Abhängigkeiten von einer bestimmten Version der Common Language Runtime, von einer Assembly im globalen Assemblycache \(GAC\) oder von einem COM\-Objekt.  Da es sich bei [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] um eine NTD\-Technologie \(No\-Touch Deployment\) handelt, können für diese Typen von Abhängigkeiten weder Download noch Installation eingeleitet werden. Wenn jedoch eine oder mehrere dieser Abhängigkeiten nicht vorhanden sind, kann die Anwendung nicht ausgeführt werden.  
  
## dependentAssembly  
 Erforderlich.  Dieses Element enthält das `assemblyIdentity`\-Element.  In der folgenden Tabelle werden die von `dependentAssembly` unterstützten Attribute aufgeführt.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`preRequisite`|Optional.  Gibt an, dass diese Assembly bereits im GAC vorhanden sein muss.  Gültige Werte sind `true` und `false`.  Wenn der Wert `true` lautet und die angegebene Assembly im GAC nicht vorhanden ist, wird die Anwendung nicht ausgeführt.|  
|`visible`|Optional.  Identifiziert die Anwendungsidentität der obersten Ebene einschließlich der Abhängigkeiten.  Wird intern von [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] verwendet, um Anwendungsspeicher und Aktivierung zu verwalten.|  
|`dependencyType`|Erforderlich.  Die Beziehung zwischen dieser Abhängigkeit und der Anwendung.  Gültige Werte sind:<br /><br /> -   `install`.  Die Komponente stellt eine von der aktuellen Anwendung getrennte Installation dar.<br />-   `preRequisite`.  Die Komponente wird von der aktuellen Anwendung benötigt.|  
|`codebase`|Optional.  Der vollständige Pfad des Anwendungsmanifests.|  
|`size`|Optional.  Die Größe des Anwendungsmanifests in Bytes.|  
  
## assemblyIdentity  
 Erforderlich.  Dieses Element ist ein untergeordnetes Element des `dependentAssembly`\-Elements.  Der Inhalt von `assemblyIdentity` muss mit der Beschreibung im [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungsmanifest identisch sein.  In der folgenden Tabelle werden die Attribute des `assemblyIdentity`\-Elements aufgeführt.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`Name`|Erforderlich.  Identifiziert den Namen der Anwendung.|  
|`Version`|Erforderlich.  Gibt die Versionsnummer der Anwendung im folgenden Format an: `major.minor.build.revision`|  
|`publicKeyToken`|Erforderlich.  Gibt eine aus 16 Zeichen bestehende hexadezimale Zeichenfolge an, die die letzten 8 Bytes des SHA\-1\-Hashs des öffentlichen Schlüssels darstellt, der zum Signieren der Anwendung oder der Assembly verwendet wird.  Der zum Signieren verwendete öffentliche Schlüssel muss mindestens 2048 Bits groß sein.|  
|`processorArchitecture`|Erforderlich.  Gibt den Mikroprozessor an.  Die gültigen Werte sind `x86` für 32\-Bit\-Windows und `IA64` für 64\-Bit\-Windows.|  
|`Language`|Optional.  Identifiziert die zweiteiligen Sprachcodes der Assembly,  zum Beispiel EN\-US für Englisch \(USA\).  Der Standardwert lautet `neutral`.  Dieses Element ist im `asmv2`\-Namespace vorhanden.|  
|`type`|Optional.  Für die Abwärtskompatibilität mit der Windows\-Technologie für parallele Installationen.  Der einzig zulässige Wert ist `win32`.|  
  
## hash  
 Das `hash`\-Element ist ein optionales untergeordnetes Element des `file`\-Elements.  Das `hash`\-Element weist keine Attribute auf.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] verwendet als Sicherheitsüberprüfung einen algorithmischen Hash aller Dateien in einer Anwendung, um sicherzustellen, dass keine der Dateien nach der Bereitstellung geändert wurde.  Wenn das `hash`\-Element nicht enthalten ist, wird diese Überprüfung nicht ausgeführt. Daher wird das Auslassen des `hash`\-Elements nicht empfohlen.  
  
## dsig:Transforms  
 Das `dsig:Transforms`\-Element ist ein erforderliches untergeordnetes Element des `hash`\-Elements.  Das `dsig:Transforms`\-Element weist keine Attribute auf.  
  
## dsig:Transform  
 Das `dsig:Transform`\-Element ist ein erforderliches untergeordnetes Element des `dsig:Transforms`\-Elements.  In der folgenden Tabelle werden die Attribute des `dsig:Transform`\-Elements aufgeführt.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`Algorithm`|Der Algorithmus, der zum Berechnen des Digests für diese Datei verwendet wird.  Derzeit wird von [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nur ein Wert verwendet, nämlich `urn:schemas-microsoft-com:HashTransforms.Identity`.|  
  
## dsig:DigestMethod  
 Das `dsig:DigestMethod`\-Element ist ein erforderliches untergeordnetes Element des `hash`\-Elements.  In der folgenden Tabelle werden die Attribute des `dsig:DigestMethod`\-Elements aufgeführt.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`Algorithm`|Der Algorithmus, der zum Berechnen des Digests für diese Datei verwendet wird.  Derzeit wird von [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nur ein Wert verwendet, nämlich `http://www.w3.org/2000/09/xmldsig#sha1`.|  
  
## dsig:DigestValue  
 Das `dsig:DigestValue`\-Element ist ein erforderliches untergeordnetes Element des `hash`\-Elements.  Das `dsig:DigestValue`\-Element weist keine Attribute auf.  Sein Textwert ist der berechnete Hash für die angegebene Datei.  
  
## Hinweise  
 Bereitstellungsmanifeste verfügen i. d. R. über ein einzelnes `assemblyIdentity`\-Element, das den Namen und die Version des Anwendungsmanifests bezeichnet.  
  
## Beispiel  
 Im folgenden Codebeispiel wird ein `dependency`\-Element in einem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellungsmanifest veranschaulicht.  
  
```  
<!-- Identify the assembly dependencies -->  
<dependency>  
  <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="16384">  
    <assemblyIdentity name="MyApplication" version="0.0.0.0" cultural="neutral" processorArchitecture="msil" />  
    <hash>  
      <dsig:Transforms>  
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
      </dsig:Transforms>  
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
       <dsig:DigestValue>YzXYZJAvj9pgAG3y8jXUjC7AtHg=</dsig:DigestValue>  
    </hash>  
  </dependentAssembly>  
</dependency>  
```  
  
## Beispiel  
 Im folgenden Codebeispiel wird eine Abhängigkeit von einer Assembly angegeben, die bereits im GAC installiert ist.  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="GACAssembly" version="1.0.0.0" language="neutral" processorArchitecture="msil" />  
  </dependentAssembly>  
</dependency>  
```  
  
## Beispiel  
 Im folgenden Codebeispiel wird eine Abhängigkeit von einer bestimmten Version der Common Language Runtime angegeben.  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50215.0" />  
  </dependentAssembly>  
</dependency>  
```  
  
## Beispiel  
 Im folgenden Codebeispiel wird eine Betriebssystemabhängigkeit angegeben.  
  
```  
<dependency>  
   <dependentOS supportUrl="http://www.microsoft.com" description="Microsoft Windows Operating System">  
      <osVersionInfo>  
         <os majorVersion="4" minorVersion="10" />  
      </osVersionInfo>  
   </dependentOS>  
</dependency>  
```  
  
## Siehe auch  
 [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)   
 [\<dependency\> Element](../deployment/dependency-element-clickonce-application.md)