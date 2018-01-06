---
title: "&lt;Abhängigkeit&gt; Element (ClickOnce-Bereitstellung) | Microsoft Docs"
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
helpviewer_keywords: <dependency> element [ClickOnce deployment manifest]
ms.assetid: 9b4d2082-0347-4922-ac70-85f11b913039
caps.latest.revision: "27"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 8716da20c989a1a8d1e36d9e071e9802a06219bf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ltdependencygt-element-clickonce-deployment"></a>&lt;Abhängigkeit&gt; Element (ClickOnce-Bereitstellung)
Identifiziert die Version der Anwendung zu installieren und den Speicherort des Anwendungsmanifests.  
  
## <a name="syntax"></a>Syntax  
  
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
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Die `dependency` Element ist erforderlich. Es wurden keine Attribute. Ein Bereitstellungsmanifest kann verfügen über mehrere `dependency` Elemente.  
  
 Die `dependency` Element drückt Abhängigkeiten für die Hauptassembly der Anwendung in der Regel auf Assemblys, die als Bestandteil einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung. Wenn Ihre Anwendung Main.exe eine Assembly mit dem Namen DotNetAssembly.dll verwendet wird, muss diese Assembly in einem Abhängigkeitsabschnitt aufgeführt werden. Abhängigkeit kann jedoch auch andere Typen von Abhängigkeiten, z. B. Abhängigkeiten von einer bestimmten Version der common Language Runtime auf eine Assembly im globalen Assemblycache (GAC) oder auf ein COM-Objekt Ausdrücken. Da es sich um eine bereitstellungstechnologie ohne handelt [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] kann nicht initiieren heruntergeladen und installiert diese Typen von Abhängigkeiten, sondern verhindert, dass die Anwendung ausgeführt wird, wenn eine oder mehrere der angegebenen Abhängigkeiten nicht vorhanden sind.  
  
## <a name="dependentassembly"></a>dependentAssembly  
 Erforderlich. Dieses Element enthält die `assemblyIdentity` Element. Die folgende Tabelle zeigt die Attribute der `dependentAssembly` unterstützt.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`preRequisite`|Dies ist optional. Gibt an, dass diese Assembly im globalen Assemblycache bereits vorhanden sein sollte. Gültige Werte sind `true` und `false`. Wenn `true`, und die angegebene Assembly im GAC nicht vorhanden, wird die Anwendung nicht ausgeführt.|  
|`visible`|Dies ist optional. Identifiziert die obersten Ebene Anwendungsidentität, einschließlich der zugehörigen Abhängigkeiten an. Verwendet intern von [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendungsspeicher und Aktivierung zu verwalten.|  
|`dependencyType`|Erforderlich. Die Beziehung zwischen dieser Abhängigkeit und der Anwendung. Gültige Werte sind:<br /><br /> -   `install`. Komponente stellt eine separate Installation aus der aktuellen Anwendung.<br />-   `preRequisite`. Komponente ist von der aktuellen Anwendung erforderlich.|  
|`codebase`|Dies ist optional. Der vollständige Pfad zum Anwendungsmanifest.|  
|`size`|Dies ist optional. Die Größe des Anwendungsmanifests in Bytes.|  
  
## <a name="assemblyidentity"></a>assemblyIdentity  
 Erforderlich. Dieses Element ist ein untergeordnetes Element des `dependentAssembly`-Elements. Der Inhalt des `assemblyIdentity` muss identisch mit der Beschreibung in der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendungsmanifest. Die folgende Tabelle zeigt die Attribute der `assemblyIdentity` Element.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Name`|Erforderlich. Identifiziert den Namen der Anwendung.|  
|`Version`|Erforderlich. Gibt die Versionsnummer der Anwendung, in folgendem Format an:`major.minor.build.revision`|  
|`publicKeyToken`|Erforderlich. Gibt eine hexadezimale Zeichenfolge von 16-Zeichen, die die letzten 8 Bytes des SHA-1-Hashs des öffentlichen Schlüssels darstellt, unter dem die Anwendung oder Assembly signiert wurde. Der öffentliche Schlüssel zum Signieren verwendet, muss auf 2048 Bits betragen.|  
|`processorArchitecture`|Erforderlich. Gibt den Mikroprozessor an. Gültige Werte sind `x86` für Windows 32-Bit- und `IA64` für 64-Bit-Windows.|  
|`Language`|Dies ist optional. Identifiziert die zweiteiligen Sprachcodes der Assembly an. Dabei steht z. B. EN-US, der für Englisch (USA). Die Standardeinstellung ist `neutral`. Dieses Element ist der `asmv2` Namespace.|  
|`type`|Dies ist optional. Abwärtskompatibilität der Kompatibilität mit Windows-Seite-an-Seite-Technologie installieren. Der einzige zulässige Wert ist `win32`.|  
  
## <a name="hash"></a>hash  
 Die `hash` Element ist ein optionales untergeordnetes Element von der `file` Element. Die `hash` -Element weist keine Attribute.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]einen algorithmischen Hash aller Dateien in einer Anwendung verwendet als eine sicherheitsüberprüfung, um sicherzustellen, dass keine der Dateien nach der Bereitstellung geändert wurden. Wenn die `hash` Element nicht enthalten ist, wird diese Überprüfung nicht ausgeführt werden. Daher wird das Auslassen der `hash` Element wird nicht empfohlen.  
  
## <a name="dsigtransforms"></a>dsig: Transforms  
 Die `dsig:Transforms` Element ist ein erforderliches untergeordnetes Element des dem `hash` Element. Die `dsig:Transforms` -Element weist keine Attribute.  
  
## <a name="dsigtransform"></a>dsig  
 Die `dsig:Transform` Element ist ein erforderliches untergeordnetes Element des dem `dsig:Transforms` Element. Die folgende Tabelle zeigt die Attribute der `dsig:Transform` Element.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Algorithm`|Der Algorithmus zum Berechnen des Digests für diese Datei verwendet wird. Zurzeit der einzige Wert von verwendete [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ist `urn:schemas-microsoft-com:HashTransforms.Identity`.|  
  
## <a name="dsigdigestmethod"></a>DigestMethod  
 Die `dsig:DigestMethod` Element ist ein erforderliches untergeordnetes Element des dem `hash` Element. Die folgende Tabelle zeigt die Attribute der `dsig:DigestMethod` Element.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Algorithm`|Der Algorithmus zum Berechnen des Digests für diese Datei verwendet wird. Zurzeit der einzige Wert von verwendete [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ist `http://www.w3.org/2000/09/xmldsig#sha1`.|  
  
## <a name="dsigdigestvalue"></a>dsig: DigestValue  
 Die `dsig:DigestValue` Element ist ein erforderliches untergeordnetes Element des dem `hash` Element. Die `dsig:DigestValue` -Element weist keine Attribute. Der Textwert ist der berechnete Hash für die angegebene Datei.  
  
## <a name="remarks"></a>Hinweise  
 Bereitstellungsmanifeste verfügen in der Regel über eine einzelne `assemblyIdentity` Element, das den Namen und die Version des Anwendungsmanifests bezeichnet.  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel zeigt eine `dependency` Element in einem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellungsmanifest.  
  
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
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel gibt eine Abhängigkeit auf eine Assembly im globalen Assemblycache bereits installiert.  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="GACAssembly" version="1.0.0.0" language="neutral" processorArchitecture="msil" />  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel gibt eine Abhängigkeit von einer bestimmten Version der common Language Runtime.  
  
```  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50215.0" />  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel gibt ein betriebssystemabhängigkeit an.  
  
```  
<dependency>  
   <dependentOS supportUrl="http://www.microsoft.com" description="Microsoft Windows Operating System">  
      <osVersionInfo>  
         <os majorVersion="4" minorVersion="10" />  
      </osVersionInfo>  
   </dependentOS>  
</dependency>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [ClickOnce-Bereitstellungsmanifest](../deployment/clickonce-deployment-manifest.md)   
 [\<Dependency >-Element](../deployment/dependency-element-clickonce-application.md)