---
title: '&lt;Abhängigkeit&gt; -Element (ClickOnce-Anwendung) | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c9172749dc00acf0fd43725f6754373a0ade16e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62900357"
---
# <a name="ltdependencygt-element-clickonce-application"></a>&lt;Abhängigkeit&gt; -Element (ClickOnce-Anwendung)
Identifiziert eine Plattform oder Assembly-Abhängigkeit, die für die Anwendung erforderlich ist.

## <a name="syntax"></a>Syntax

```xml

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
 Die `dependency` Element ist erforderlich. Gibt es möglicherweise mehrere Instanzen von `dependency` im gleichen Anwendungsmanifest.

 Die `dependency` Element weist keine Attribute und enthält die folgenden untergeordneten Elemente.

### <a name="dependentos"></a>dependentOS
 Dies ist optional. Enthält die `osVersionInfo` Element. Die `dependentOS` und `dependentAssembly` Elemente schließen sich gegenseitig: mindestens eine der anderen muss vorhanden sein, für eine `dependency` -Element, aber nicht beides.

 `dependentOS` unterstützt die folgenden Attribute an.

|Attribut|Beschreibung|
|---------------|-----------------|
|`supportUrl`|Dies ist optional. Gibt eine Support-URL für die abhängige Plattform. Diese URL wird für den Benutzer angezeigt, wenn die erforderliche Plattform gefunden wird.|
|`description`|Dies ist optional. Beschreibt das Betriebssystem beschrieben in Menschen lesbarem Format die `dependentOS` Element.|

### <a name="osversioninfo"></a>osVersionInfo
 Erforderlich. Dieses Element ist ein untergeordnetes Element des `dependentOS` -Elements und enthält das `os` -Element. Dieses Element weist keine Attribute auf.

### <a name="os"></a>os
 Erforderlich. Dieses Element ist ein untergeordnetes Element des `osVersionInfo` -Elements. Dieses Element weist folgende Attribute auf.

|Attribut|Beschreibung|
|---------------|-----------------|
|`majorVersion`|Erforderlich. Gibt die Hauptversionsnummer des Betriebssystems an.|
|`minorVersion`|Erforderlich. Gibt die Nummer der Nebenversion des Betriebssystems an.|
|`buildNumber`|Erforderlich. Gibt die Buildnummer des Betriebssystems an.|
|`servicePackMajor`|Erforderlich. Gibt an, die wichtigsten Service Pack-Nummer des Betriebssystems.|
|`servicePackMinor`|Dies ist optional. Gibt die kleinere Service Pack-Nummer des Betriebssystems an.|
|`productType`|Dies ist optional. Gibt die Produkt-Typwert. Gültige Werte sind `server`, `workstation` und `domainController`. Für Windows 2000 Professional, ist der Wert dieses Attributs beispielsweise `workstation`.|
|`suiteType`|Dies ist optional. Identifiziert eine Produktsuite, die auf dem System oder des Systems Konfigurationstyp verfügbar. Gültige Werte sind `backoffice`, `blade`, `datacenter`, `enterprise`, `home`, `professional`, `smallbusiness`, `smallbusinessRestricted` und `terminal`. Für Windows 2000 Professional, ist der Wert dieses Attributs beispielsweise `professional`.|

### <a name="dependentassembly"></a>dependentAssembly
 Dies ist optional. Enthält die `assemblyIdentity` Element. Die `dependentOS` und `dependentAssembly` Elemente schließen sich gegenseitig: mindestens eine der anderen muss vorhanden sein, für eine `dependency` -Element, aber nicht beides.

 `dependentAssembly` hat die folgenden Attribute an.

| Attribut | Beschreibung |
|-----------------------| - |
| `dependencyType` | Erforderlich. Gibt den Typ der Abhängigkeit an. Gültige Werte sind `preprequisite` und `install`. Ein `install` Assembly installiert ist, als Teil der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung. Ein `prerequisite` Assembly muss im globalen Assemblycache (GAC) vor der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung installieren kann. |
| `allowDelayedBinding` | Erforderlich. Gibt an, ob die Assembly zur Laufzeit programmgesteuert geladen werden kann. |
| `group` | Dies ist optional. Wenn die `dependencyType` -Attributsatz auf `install`, kennzeichnet eine benannte Gruppe von Assemblys, nur die Installation bei Bedarf. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Herunterladen von Assemblys bei Bedarf mit der API für die ClickOnce-Bereitstellung unter Verwendung des Designers](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md).<br /><br /> Wenn auf festgelegt `framework` und `dependencyType` -Attributsatz auf `prerequisite`, kennzeichnet die Assembly als Teil von .NET Framework. Der globale Assemblycache (GAC) wird nicht auf diese Assembly überprüft, bei der Installation auf [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] und höhere Versionen. |
| `codeBase` | Erforderlich, wenn die `dependencyType` -Attributsatz auf `install`. Der Pfad der abhängigen Assembly. Entweder ein absoluter Pfad oder einen Pfad relativ zum des Manifests kann Basisklasse sein. Dieser Pfad muss ein gültiger URI in der Reihenfolge für das Assemblymanifest gültig ist. |
| `size` | Erforderlich, wenn die `dependencyType` -Attributsatz auf `install`. Die Größe der abhängigen Assembly, in Bytes. |

### <a name="assemblyidentity"></a>assemblyIdentity
 Erforderlich. Dieses Element ist ein untergeordnetes Element des `dependentAssembly` -Elements und weist folgende Attribute auf.

|Attribut|Beschreibung|
|---------------|-----------------|
|`name`|Erforderlich. Identifiziert den Namen der Anwendung.|
|`version`|Erforderlich. Gibt die Versionsnummer der Anwendung im folgenden Format an: `major.minor.build.revision`|
|`publicKeyToken`|Dies ist optional. Gibt an, eine hexadezimale Zeichenfolge von 16 Zeichen, das die letzten 8 Bytes darstellt. die `SHA-1` Hashwert des öffentlichen Schlüssels unter dem die Anwendung oder Assembly signiert ist. Der öffentliche Schlüssel zum Signieren des Katalogs muss mindestens 2048 Bits sein.|
|`processorArchitecture`|Dies ist optional. Gibt den Prozessor. Gültige Werte sind `x86` für 32-Bit-Windows und `I64` für 64-Bit-Windows.|
|`language`|Dies ist optional. Identifiziert den zweiteiligen Sprachcodes, z. B. EN-US, der Assembly an.|

### <a name="hash"></a>hash
 Die `hash` Element ist ein optionales untergeordnetes Element von der `assemblyIdentity` Element. Das `hash` -Element weist keine Attribute auf.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] verwendet einen algorithmischen Hash aller Dateien in einer Anwendung als eine sicherheitsüberprüfung, um sicherzustellen, dass keine der Dateien nach der Bereitstellung geändert wurden. Wenn die `hash` Element nicht enthalten ist, diese Überprüfung wird nicht ausgeführt werden. Daher wird das Auslassen der `hash` Element wird nicht empfohlen.

### <a name="dsigtransforms"></a>dsig:Transforms
 Die `dsig:Transforms` Element ist ein erforderliches untergeordnetes Element von der `hash` Element. Das `dsig:Transforms` -Element weist keine Attribute auf.

### <a name="dsigtransform"></a>dsig:Transform
 Die `dsig:Transform` Element ist ein erforderliches untergeordnetes Element von der `dsig:Transforms` Element. Das `dsig:Transform` -Element weist folgende Attribute auf.

| Attribut | Beschreibung |
|-------------| - |
| `Algorithm` | Der Algorithmus verwendet, um den Hashwert für diese Datei zu berechnen. Zurzeit der einzige Wert ein, die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ist `urn:schemas-microsoft-com:HashTransforms.Identity`. |

### <a name="dsigdigestmethod"></a>dsig:DigestMethod
 Die `dsig:DigestMethod` Element ist ein erforderliches untergeordnetes Element von der `hash` Element. Das `dsig:DigestMethod` -Element weist folgende Attribute auf.

| Attribut | Beschreibung |
|-------------| - |
| `Algorithm` | Der Algorithmus verwendet, um den Hashwert für diese Datei zu berechnen. Zurzeit der einzige Wert ein, die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ist `http://www.w3.org/2000/09/xmldsig#sha1`. |

### <a name="dsigdigestvalue"></a>dsig:DigestValue
 Die `dsig:DigestValue` Element ist ein erforderliches untergeordnetes Element von der `hash` Element. Das `dsig:DigestValue` -Element weist keine Attribute auf. Der Textwert ist der berechnete Hash für die angegebene Datei.

## <a name="remarks"></a>Hinweise
 Alle Assemblys, die von Ihrer Anwendung verwendeten setzt das Vorhandensein einer entsprechenden `dependency` Element. Abhängige Assemblys enthalten keine Assemblys, die als Testplattform-Assemblys im globalen Assemblycache vorinstalliert sein müssen.

## <a name="example"></a>Beispiel
 Im folgenden Codebeispiel wird veranschaulicht, `dependency` Elemente in einem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] -Anwendungsmanifest. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels für die [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md) Thema.

```xml
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
- [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md)
- [\<Dependency >-Element](../deployment/dependency-element-clickonce-deployment.md)