---
title: '&lt;Datei&gt; Element (ClickOnce-Anwendung) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#file
- http://www.w3.org/2000/09/xmldsig#DigestValue
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <file> element [ClickOnce application manifest]
- manifests [ClickOnce], file element
ms.assetid: 56e3490c-eed5-4841-b1bf-eefe778b6ac9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8fccbd816d578a95e3e43e15c83d615756dcddcb
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="ltfilegt-element-clickonce-application"></a>&lt;Datei&gt; Element (ClickOnce-Anwendung)
Identifiziert alle Nichtassemblydateien heruntergeladen und von der Anwendung verwendet.  
  
## <a name="syntax"></a>Syntax  
  
```  
<file  
    name  
    size  
    group  
    optional  
    writeableType  
>  
    <typelib  
        tlbid  
        version  
        helpdir  
        resourceid  
        flags  
    />  
    <comClass  
        clsid  
        description  
        threadingModel  
        tlbid  
        progid  
        miscStatus  
        miscStatusIcon  
        miscStatusContent  
        miscStatusDocPrint  
        miscStatusThumbnail  
    />  
    <comInterfaceExternalProxyStub  
        iid  
        baseInterface  
        numMethods  
        name  
        tlbid  
        proxyStubClass32  
    />  
    <comInterfaceProxyStub  
        iid  
        baseInterface  
        numMethods  
        name  
        tlbid  
        proxyStubClass32  
    />  
    <windowClass  
        versioned  
    />  
</file>  
```  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Das `file`-Element ist optional. Das Element weist folgende Attribute.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`name`|Erforderlich. Identifiziert den Namen der Datei.|  
|`size`|Erforderlich. Gibt die Größe in Byte der Datei an.|  
|`group`|Optional, wenn die `optional` Attribut nicht angegeben oder auf gesetzt `false`; erforderlich, wenn `optional` ist `true`. Der Name der Gruppe, zu der diese Datei gehört. Der Name kann eine Unicode-Zeichenfolge, die vom Entwickler ausgewählt werden und dient zum Herunterladen von Dateien bei Bedarf mit der <xref:System.Deployment.Application.ApplicationDeployment> Klasse.|  
|`optional`|Dies ist optional. Gibt an, ob diese Datei muss es herunterladen, wenn die Anwendung zuerst ausgeführt, oder gibt an, ob Sie nur auf dem Server verbleiben soll, bis die Anwendung bei Bedarf anfordert. Wenn `false` oder nicht definiert ist, die Datei wird heruntergeladen, wenn die Anwendung zuerst ausgeführt oder installiert wird. Wenn `true`ein `group` muss angegeben werden, für das Anwendungsmanifest, um gültig zu sein. `optional` nicht mit "true" Wenn `writeableType` wird angegeben, mit dem Wert `applicationData`.|  
|`writeableType`|Dies ist optional. Gibt an, dass diese Datei eine Datendatei ist. Zurzeit der einzige gültige Wert ist `applicationData`.|  
  
## <a name="typelib"></a>der Typbibliothek  
 Die `typelib` Element ist ein optionales untergeordnetes Element des File-Elements. Das-Element beschreibt die Typbibliothek, die COM-Komponente gehört. Das Element weist folgende Attribute.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`tlbid`|Erforderlich. Auf die Typbibliothek zugewiesene GUID.|  
|`version`|Erforderlich. Die Versionsnummer der Typbibliothek.|  
|`helpdir`|Erforderlich. Das Verzeichnis, das die Hilfedateien für die Komponente enthält. Kann mit der Länge Null sein.|  
|`resourceid`|Dies ist optional. Die hexadezimale Zeichenfolgendarstellung des Gebietsschemabezeichners (LCID). Es ist ein bis vier hexadezimale Ziffern ohne Präfix 0 X und ohne führende Nullen. Die LCID möglicherweise eine neutrale untersprachen-ID an.|  
|`flags`|Dies ist optional. Die Zeichenfolgendarstellung der Flags der Typbibliothek für diese Typbibliothek. Insbesondere sollten sie eine der "RESTRICTED", "CONTROL", "HIDDEN" und "HASDISKIMAGE" sein.|  
  
## <a name="comclass"></a>comClass  
 Die `comClass` Element ist ein optionales untergeordnetes Element von der `file` Element, jedoch ist erforderlich, wenn die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung enthält eine COM-Komponente, die die Bereitstellung über registrierungsfreies werden soll Das Element weist folgende Attribute.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`clsid`|Erforderlich. Die Klassen-ID der COM-Komponente, ausgedrückt als GUID.|  
|`description`|Dies ist optional. Der Klassenname.|  
|`threadingModel`|Dies ist optional. Das Threadingmodell von in-Process-COM-Klassen verwendet. Wenn diese Eigenschaft null ist, wird kein Threadmodell verwendet. Die Komponente wird auf den Hauptthread des Clients erstellt und Aufrufe von anderen Threads werden an diesen Thread gemarshallt. Die folgende Liste zeigt die gültigen Werte:<br /><br /> `Apartment`, `Free`, `Both` und `Neutral`.|  
|`tlbid`|Dies ist optional. GUID für die Typbibliothek der COM-Komponente.|  
|`progid`|Dies ist optional. Versionsabhängige programmatischen Bezeichner der COM-Komponente zugeordnet. Das Format einer `ProgID` ist `<vendor>.<component>.<version>`.|  
|`miscStatus`|Dies ist optional. Duplikate in der Assembly manifest den Angaben von der `MiscStatus` Registrierungsschlüssel. Wenn Werte für die `miscStatusIcon`, `miscStatusContent`, `miscStatusDocprint`, oder `miscStatusThumbnail` Attribute nicht gefunden werden, wird der zugehörige Standardwert aufgeführt, `miscStatus` wird für die fehlenden Attribute verwendet. Der Wert kann eine durch Trennzeichen getrennte Liste der Attributwerte aus der folgenden Tabelle sein. Sie können dieses Attribut verwenden, wenn die COM-Klasse eine OCX-Klasse ist, die erforderlich sind `MiscStatus` Registrierungsschlüsselwerte.|  
|`miscStatusIcon`|Dies ist optional. Duplikate in der Assembly manifest von DVASPECT_ICON bereitgestellten Informationen. Es kann ein Symbol eines Objekts bereitstellen. Der Wert kann eine durch Trennzeichen getrennte Liste der Attributwerte aus der folgenden Tabelle sein. Sie können dieses Attribut verwenden, wenn die COM-Klasse eine OCX-Klasse ist, die erforderlich sind `Miscstatus` Registrierungsschlüsselwerte.|  
|`miscStatusContent`|Dies ist optional. Duplikate in der Assembly manifest von DVASPECT_CONTENT bereitgestellten Informationen. Es kann ein Verbunddokument handeln für einen Bildschirm oder Drucker bereitstellen. Der Wert kann eine durch Trennzeichen getrennte Liste der Attributwerte aus der folgenden Tabelle sein. Sie können dieses Attribut verwenden, wenn die COM-Klasse eine OCX-Klasse ist, die erforderlich sind `MiscStatus` Registrierungsschlüsselwerte.|  
|`miscStatusDocPrint`|Dies ist optional. Duplikate in der Assembly manifest von DVASPECT_DOCPRINT bereitgestellten Informationen. Es kann auf dem Bildschirm eine objektdarstellung anzeigbaren bereitstellen, als ob Sie an einen Drucker gedruckt. Der Wert kann eine durch Trennzeichen getrennte Liste der Attributwerte aus der folgenden Tabelle sein. Sie können dieses Attribut verwenden, wenn die COM-Klasse eine OCX-Klasse ist, die erforderlich sind `MiscStatus` Registrierungsschlüsselwerte.|  
|`miscStatusThumbnail`|Dies ist optional. Duplikate in einer Assembly manifest von DVASPECT_THUMBNAIL bereitgestellten Informationen. Es kann eine Miniaturansicht eines Objekts in einem anzeigbaren bereitstellen. Der Wert kann eine durch Trennzeichen getrennte Liste der Attributwerte aus der folgenden Tabelle sein. Sie können dieses Attribut verwenden, wenn die COM-Klasse eine OCX-Klasse ist, die erforderlich sind `MiscStatus` Registrierungsschlüsselwerte.|  
  
## <a name="cominterfaceexternalproxystub"></a>comInterfaceExternalProxyStub  
 Die `comInterfaceExternalProxyStub` Element ist ein optionales untergeordnetes Element von der `file` Element, jedoch möglicherweise erforderlich sind, wenn die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung enthält eine COM-Komponente, die die Bereitstellung über registrierungsfreies werden soll Das Element enthält die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`iid`|Erforderlich. Die Schnittstelle-ID (IID) werden durch diesen Proxy verarbeitet wird. Die IID muss geschweiften Klammern stehen.|  
|`baseInterface`|Dies ist optional. Die IID der Schnittstelle, von dem die Schnittstelle verweist `iid` abgeleitet ist.|  
|`numMethods`|Dies ist optional. Die Anzahl der Methoden, die durch die Schnittstelle implementiert.|  
|`name`|Dies ist optional. Der Name der Schnittstelle, wie sie wird im Code angezeigt.|  
|`tlbid`|Dies ist optional. Die Typbibliothek, die die Beschreibung der die angegebene Schnittstelle enthält die `iid` Attribut.|  
|`proxyStubClass32`|Dies ist optional. Ordnet eine IID CLSID in 32-Bit-Proxy-DLLs.|  
  
## <a name="cominterfaceproxystub"></a>comInterfaceProxyStub  
 Die `comInterfaceProxyStub` Element ist ein optionales untergeordnetes Element von der `file` Element, jedoch möglicherweise erforderlich sind, wenn die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung enthält eine COM-Komponente, die die Bereitstellung über registrierungsfreies werden soll Das Element enthält die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`iid`|Erforderlich. Die Schnittstelle-ID (IID) werden durch diesen Proxy verarbeitet wird. Die IID muss geschweiften Klammern stehen.|  
|`baseInterface`|Dies ist optional. Die IID der Schnittstelle, von dem die Schnittstelle verweist `iid` abgeleitet ist.|  
|`numMethods`|Dies ist optional. Die Anzahl der Methoden, die durch die Schnittstelle implementiert.|  
|`Name`|Dies ist optional. Der Name der Schnittstelle, wie sie wird im Code angezeigt.|  
|`Tlbid`|Dies ist optional. Die Typbibliothek, die die Beschreibung der die angegebene Schnittstelle enthält die `iid` Attribut.|  
|`proxyStubClass32`|Dies ist optional. Ordnet eine IID CLSID in 32-Bit-Proxy-DLLs.|  
|`threadingModel`|Dies ist optional. Dies ist optional. Das Threadingmodell von in-Process-COM-Klassen verwendet. Wenn diese Eigenschaft null ist, wird kein Threadmodell verwendet. Die Komponente wird auf den Hauptthread des Clients erstellt und Aufrufe von anderen Threads werden an diesen Thread gemarshallt. Die folgende Liste zeigt die gültigen Werte:<br /><br /> `Apartment`, `Free`, `Both` und `Neutral`.|  
  
## <a name="windowclass"></a>windowClass  
 Die `windowClass` Element ist ein optionales untergeordnetes Element von der `file` Element, jedoch möglicherweise erforderlich sind, wenn die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung enthält eine COM-Komponente, die die Bereitstellung über registrierungsfreies werden soll Das Element bezieht sich auf eine Fensterklasse, die von der COM-Komponente, die eine Version angewendet haben, muss definiert. Das Element enthält die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`versioned`|Dies ist optional. Steuert, ob der interne Name der Fensterklasse in Registrierung verwendet die Version der Assembly enthält, der die Fensterklasse enthalten. Der Wert dieses Attributs kann `yes` oder `no`. Die Standardeinstellung ist `yes`. Der Wert `no` sollte nur verwendet werden, wenn die gleichen Fensterklasse durch eine Seite-an-Seite-Komponente und einer entsprechenden nicht-Seite-an-Seite-Komponente definiert wird und diese als der gleichen Fensterklasse behandelt werden sollen. Beachten Sie, die die üblichen Regeln zur fensterklassenregistrierung gelten – nur die erste Komponente, der die Fensterklasse registriert, registrieren kann, da sie nicht über eine Version angewendet verfügt.|  
  
## <a name="hash"></a>hash  
 Die `hash` Element ist ein optionales untergeordnetes Element von der `file` Element. Die `hash` -Element weist keine Attribute.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] einen algorithmischen Hash aller Dateien in einer Anwendung verwendet als eine sicherheitsüberprüfung, um sicherzustellen, dass keine der Dateien nach der Bereitstellung geändert wurden. Wenn die `hash` Element nicht enthalten ist, wird diese Überprüfung nicht ausgeführt werden. Daher wird das Auslassen der `hash` Element wird nicht empfohlen.  
  
 Ein Manifest enthält eine Datei, die nicht in der Hashwert berechnet wird, Manifest nicht digital signiert werden, da Benutzer den Inhalt der gehashter Dateien überprüft werden können.  
  
## <a name="dsigtransforms"></a>dsig: Transforms  
 Die `dsig:Transforms` Element ist ein erforderliches untergeordnetes Element des dem `hash` Element. Die `dsig:Transforms` -Element weist keine Attribute.  
  
## <a name="dsigtransform"></a>dsig  
 Die `dsig:Transform` Element ist ein erforderliches untergeordnetes Element des dem `dsig:Transforms` Element. Die `dsig:Transform` Element weist folgende Attribute.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Algorithm`|Der Algorithmus zum Berechnen des Digests für diese Datei verwendet wird. Zurzeit der einzige Wert von verwendete [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ist `urn:schemas-microsoft-com:HashTransforms.Identity`.|  
  
## <a name="dsigdigestmethod"></a>DigestMethod  
 Die `dsig:DigestMethod` Element ist ein erforderliches untergeordnetes Element des dem `hash` Element. Die `dsig:DigestMethod` Element weist folgende Attribute.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Algorithm`|Der Algorithmus zum Berechnen des Digests für diese Datei verwendet wird. Zurzeit der einzige Wert von verwendete [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ist `http://www.w3.org/2000/09/xmldsig#sha1`.|  
  
## <a name="dsigdigestvalue"></a>dsig: DigestValue  
 Die `dsig:DigestValue` Element ist ein erforderliches untergeordnetes Element des dem `hash` Element. Die `dsig:DigestValue` -Element weist keine Attribute. Der Textwert ist der berechnete Hash für die angegebene Datei.  
  
## <a name="remarks"></a>Hinweise  
 Dieses Element identifiziert alle Nichtassemblydateien, aus denen die Anwendung besteht, und insbesondere die Hashwerte für die Überprüfung der Datei. Dieses Element kann auch mit der Datei verknüpfte Component Object Model (COM)-Isolationsdaten einschließen. Wenn eine Datei geändert wird, muss die Anwendungsmanifestdatei ebenfalls aktualisiert werden, um die Änderung zu übernehmen.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, `file` Elemente in einer Anwendung für eine Anwendung mit bereitgestellte manifest [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
```  
<file name="Icon.ico" size="9216">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>lVoj+Rh6RQ/HPNLOdayQah5McrI=</dsig:DigestValue>  
  </hash>  
</file>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md)