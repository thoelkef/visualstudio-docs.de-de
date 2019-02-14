---
title: '&lt;Datei&gt; -Element (ClickOnce-Anwendung) | Microsoft-Dokumentation'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f2d71192b38ea14ade737ecb4b34e3cc25f8b91d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54984716"
---
# <a name="ltfilegt-element-clickonce-application"></a>&lt;Datei&gt; -Element (ClickOnce-Anwendung)
Identifiziert alle Nichtassemblydateien heruntergeladen und von der Anwendung verwendet.  

## <a name="syntax"></a>Syntax  

```xml  
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
 Das `file`-Element ist optional. Das Element weist folgende Attribute auf.  

|Attribut|Beschreibung|  
|---------------|-----------------|  
|`name`|Erforderlich. Identifiziert den Namen der Datei.|  
|`size`|Erforderlich. Gibt die Größe in Bytes der Datei an.|  
|`group`|Optional, wenn die `optional` Attribut nicht angegeben oder legen Sie auf `false`; erforderlich, wenn `optional` ist `true`. Der Name der Gruppe, zu dem diese Datei gehört. Der Name kann eine Unicode-Zeichenfolge, die vom Entwickler ausgewählt werden und dient zum Herunterladen von Dateien bei Bedarf mit der <xref:System.Deployment.Application.ApplicationDeployment> Klasse.|  
|`optional`|Dies ist optional. Gibt an, ob diese Datei muss herunterladen, wenn die Anwendung erstmals ausführen, oder gibt an, ob Sie nur auf dem Server verbleiben soll, bis die Anwendung bei Bedarf angefordert. Wenn `false` oder nicht definiert, die Datei wird heruntergeladen, wenn die Anwendung zuerst ausführen oder installiert wird. Wenn `true`, `group` muss angegeben werden, für das Anwendungsmanifest gültig ist. `optional` darf nicht "true" sein. wenn `writeableType` angegeben ist, mit dem Wert `applicationData`.|  
|`writeableType`|Dies ist optional. Gibt an, dass diese Datei eine Datendatei ist. Derzeit ist `applicationData` der einzige gültige Wert.|  

## <a name="typelib"></a>typelib  
 Die `typelib` Element ist ein optionales untergeordnetes Element des File-Elements. Das Element beschreibt die Bibliothek, zu dem die COM-Komponente gehört. Das Element weist folgende Attribute auf.  

|Attribut|Beschreibung|  
|---------------|-----------------|  
|`tlbid`|Erforderlich. Die GUID der Typbibliothek zugewiesen.|  
|`version`|Erforderlich. Die Versionsnummer der Typbibliothek.|  
|`helpdir`|Erforderlich. Das Verzeichnis, das die Hilfedateien für die Komponente enthält. Kann mit der Länge Null sein.|  
|`resourceid`|Dies ist optional. Die hexadezimale Zeichenfolgendarstellung des Gebietsschemabezeichners (LCID). Es ist eine bis vier hexadezimale Ziffern ohne Präfix 0 X und ohne führende Nullen. Die LCID möglicherweise eine neutralen untersprachen-ID an.|  
|`flags`|Dies ist optional. Die Zeichenfolgendarstellung der Flags der Typbibliothek für diese Typbibliothek. Insbesondere sollten sie eine der "RESTRICTED", "CONTROL", "HIDDEN" und "HASDISKIMAGE" sein.|  

## <a name="comclass"></a>comClass  
 Die `comClass` Element ist ein optionales untergeordnetes Element von der `file` -Element, jedoch ist erforderlich, wenn die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung enthält eine COM-Komponente, die Sie mithilfe von COM ohne Registrierung bereitstellen möchte Das Element weist folgende Attribute auf.  

|Attribut|Beschreibung|  
|---------------|-----------------|  
|`clsid`|Erforderlich. Die Klassen-ID der COM-Komponente als eine GUID.|  
|`description`|Dies ist optional. Der Klassenname.|  
|`threadingModel`|Dies ist optional. Das Threadingmodell von in-Process-COM-Klassen verwendet. Wenn diese Eigenschaft auf null festgelegt ist, wird kein threading-Modell verwendet. Die Komponente wird auf dem Hauptthread des Clients erstellt, und Aufrufe von anderen Threads werden für diesen Thread gemarshallt. Die folgende Liste zeigt die gültigen Werte an:<br /><br /> `Apartment`, `Free`, `Both`und `Neutral`.|  
|`tlbid`|Dies ist optional. Die GUID für die Typbibliothek der COM-Komponente.|  
|`progid`|Dies ist optional. Versionsabhängige programmatische Bezeichner der COM-Komponente zugeordnet. Das Format einer `ProgID` ist `<vendor>.<component>.<version>`.|  
|`miscStatus`|Dies ist optional. Duplikate in der Assembly manifest die Informationen der `MiscStatus` Registrierungsschlüssel. Wenn Werte für die `miscStatusIcon`, `miscStatusContent`, `miscStatusDocprint`, oder `miscStatusThumbnail` Attribute nicht gefunden werden, wird der zugehörige Standardwert aufgeführt, `miscStatus` wird für die fehlenden Attribute verwendet. Der Wert kann es sich um eine durch Trennzeichen getrennte Liste der Attributwerte aus der folgenden Tabelle sein. Sie können dieses Attribut verwenden, wenn die COM-Klasse eine OCX-Klasse, die erforderlich sind `MiscStatus` Registrierungsschlüsselwerte.|  
|`miscStatusIcon`|Dies ist optional. Dupliziert im manifest von DVASPECT_ICON bereitgestellten Informationen. Es kann ein Symbol eines Objekts bereitstellen. Der Wert kann es sich um eine durch Trennzeichen getrennte Liste der Attributwerte aus der folgenden Tabelle sein. Sie können dieses Attribut verwenden, wenn die COM-Klasse eine OCX-Klasse, die erforderlich sind `Miscstatus` Registrierungsschlüsselwerte.|  
|`miscStatusContent`|Dies ist optional. Dupliziert im manifest von DVASPECT_CONTENT bereitgestellten Informationen. Sie können einem Bildschirm oder Drucker ein Verbunddokument handeln bereit. Der Wert kann es sich um eine durch Trennzeichen getrennte Liste der Attributwerte aus der folgenden Tabelle sein. Sie können dieses Attribut verwenden, wenn die COM-Klasse eine OCX-Klasse, die erforderlich sind `MiscStatus` Registrierungsschlüsselwerte.|  
|`miscStatusDocPrint`|Dies ist optional. Dupliziert im manifest von DVASPECT_DOCPRINT bereitgestellten Informationen. Es kann eine objektdarstellung anzeigbaren auf dem Bildschirm bereitstellen, als ob an einen Drucker gedruckt. Der Wert kann es sich um eine durch Trennzeichen getrennte Liste der Attributwerte aus der folgenden Tabelle sein. Sie können dieses Attribut verwenden, wenn die COM-Klasse eine OCX-Klasse, die erforderlich sind `MiscStatus` Registrierungsschlüsselwerte.|  
|`miscStatusThumbnail`|Dies ist optional. Duplikate in einer Assembly manifest von DVASPECT_THUMBNAIL bereitgestellte Informationen. Sie können eine Miniaturansicht eines Objekts in einem Browser darstellbaren bereitstellen. Der Wert kann es sich um eine durch Trennzeichen getrennte Liste der Attributwerte aus der folgenden Tabelle sein. Sie können dieses Attribut verwenden, wenn die COM-Klasse eine OCX-Klasse, die erforderlich sind `MiscStatus` Registrierungsschlüsselwerte.|  

## <a name="cominterfaceexternalproxystub"></a>comInterfaceExternalProxyStub  
 Der `comInterfaceExternalProxyStub` Element ist ein optionales untergeordnetes Element des der `file` -Element, wenn möglicherweise erforderlich, aber der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung enthält eine COM-Komponente, die Sie mithilfe von COM ohne Registrierung bereitstellen möchte Das Element enthält die folgenden Attribute.  

|Attribut|Beschreibung|  
|---------------|-----------------|  
|`iid`|Erforderlich. Die Schnittstelle-ID (IID) der von diesem Proxy verarbeitet wird. Die IID muss geschweiften Klammern stehen.|  
|`baseInterface`|Dies ist optional. Die IID der Schnittstelle aus der die Schnittstelle verweist `iid` abgeleitet ist.|  
|`numMethods`|Dies ist optional. Die Anzahl der Methoden, die von der Schnittstelle implementiert.|  
|`name`|Dies ist optional. Der Name der Schnittstelle, wie sie wird im Code angezeigt.|  
|`tlbid`|Dies ist optional. Die Typbibliothek, die die Beschreibung der die angegebene Schnittstelle enthält die `iid` Attribut.|  
|`proxyStubClass32`|Dies ist optional. Ordnet eine IID CLSID in 32-Bit-Proxy-DLLs.|  

## <a name="cominterfaceproxystub"></a>comInterfaceProxyStub  
 Der `comInterfaceProxyStub` Element ist ein optionales untergeordnetes Element des der `file` -Element, wenn möglicherweise erforderlich, aber der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung enthält eine COM-Komponente, die Sie mithilfe von COM ohne Registrierung bereitstellen möchte Das Element enthält die folgenden Attribute.  

|Attribut|Beschreibung|  
|---------------|-----------------|  
|`iid`|Erforderlich. Die Schnittstelle-ID (IID) der von diesem Proxy verarbeitet wird. Die IID muss geschweiften Klammern stehen.|  
|`baseInterface`|Dies ist optional. Die IID der Schnittstelle aus der die Schnittstelle verweist `iid` abgeleitet ist.|  
|`numMethods`|Dies ist optional. Die Anzahl der Methoden, die von der Schnittstelle implementiert.|  
|`Name`|Dies ist optional. Der Name der Schnittstelle, wie sie wird im Code angezeigt.|  
|`Tlbid`|Dies ist optional. Die Typbibliothek, die die Beschreibung der die angegebene Schnittstelle enthält die `iid` Attribut.|  
|`proxyStubClass32`|Dies ist optional. Ordnet eine IID CLSID in 32-Bit-Proxy-DLLs.|  
|`threadingModel`|Dies ist optional. Dies ist optional. Das Threadingmodell von in-Process-COM-Klassen verwendet. Wenn diese Eigenschaft auf null festgelegt ist, wird kein threading-Modell verwendet. Die Komponente wird auf dem Hauptthread des Clients erstellt, und Aufrufe von anderen Threads werden für diesen Thread gemarshallt. Die folgende Liste zeigt die gültigen Werte an:<br /><br /> `Apartment`, `Free`, `Both`und `Neutral`.|  

## <a name="windowclass"></a>windowClass  
 Der `windowClass` Element ist ein optionales untergeordnetes Element des der `file` -Element, wenn möglicherweise erforderlich, aber der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung enthält eine COM-Komponente, die Sie mithilfe von COM ohne Registrierung bereitstellen möchte Das Element bezieht sich auf eine Fensterklasse, definiert durch die COM-Komponente, die eine Version, die angewendet werden muss. Das Element enthält die folgenden Attribute.  

|Attribut|Beschreibung|  
|---------------|-----------------|  
|`versioned`|Dies ist optional. Steuert, ob der interne Name der Fensterklasse in der Registrierung verwendete die Version der Assembly enthält, die Fensterklasse. Der Wert dieses Attributs kann sein `yes` oder `no`. Die Standardeinstellung ist `yes`. Der Wert `no` sollte nur verwendet werden, wenn die gleichen Fensterklasse wird durch eine Seite-an-Seite-Komponente und einer entsprechenden nicht-Seite-an-Seite-Komponente definiert, und Sie sie als der gleichen Fensterklasse behandeln möchten. Beachten Sie, die die üblichen Regeln zur fensterklassenregistrierung gelten – nur die erste Komponente, der die Fensterklasse registriert werden, registrieren, da es eine Version, angewendetes keine.|  

## <a name="hash"></a>hash  
 Die `hash` Element ist ein optionales untergeordnetes Element von der `file` Element. Das `hash` -Element weist keine Attribute auf.  

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] verwendet einen algorithmischen Hash aller Dateien in einer Anwendung als eine sicherheitsüberprüfung, um sicherzustellen, dass keine der Dateien nach der Bereitstellung geändert wurden. Wenn die `hash` Element nicht enthalten ist, diese Überprüfung wird nicht ausgeführt werden. Daher wird das Auslassen der `hash` Element wird nicht empfohlen.  

 Ein Manifest enthält eine Datei, die nicht in der Hashwert berechnet wird, dieses nicht digital signiert werden, da der Benutzer den Inhalt der gehashter Dateien nicht überprüfen können.  

## <a name="dsigtransforms"></a>dsig:Transforms  
 Die `dsig:Transforms` Element ist ein erforderliches untergeordnetes Element von der `hash` Element. Das `dsig:Transforms` -Element weist keine Attribute auf.  

## <a name="dsigtransform"></a>dsig:Transform  
 Die `dsig:Transform` Element ist ein erforderliches untergeordnetes Element von der `dsig:Transforms` Element. Das `dsig:Transform` -Element weist folgende Attribute auf.  


| Attribut | Beschreibung |
|-------------| - |
| `Algorithm` | Der Algorithmus verwendet, um den Hashwert für diese Datei zu berechnen. Zurzeit der einzige Wert ein, die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ist `urn:schemas-microsoft-com:HashTransforms.Identity`. |

## <a name="dsigdigestmethod"></a>dsig:DigestMethod  
 Die `dsig:DigestMethod` Element ist ein erforderliches untergeordnetes Element von der `hash` Element. Das `dsig:DigestMethod` -Element weist folgende Attribute auf.  


| Attribut | Beschreibung |
|-------------| - |
| `Algorithm` | Der Algorithmus verwendet, um den Hashwert für diese Datei zu berechnen. Zurzeit der einzige Wert ein, die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ist `http://www.w3.org/2000/09/xmldsig#sha1`. |

## <a name="dsigdigestvalue"></a>dsig:DigestValue  
 Die `dsig:DigestValue` Element ist ein erforderliches untergeordnetes Element von der `hash` Element. Das `dsig:DigestValue` -Element weist keine Attribute auf. Der Textwert ist der berechnete Hash für die angegebene Datei.  

## <a name="remarks"></a>Hinweise  
 Dieses Element identifiziert alle Nichtassemblydateien, aus denen die Anwendung besteht, und insbesondere die Hashwerte für die Überprüfung der Datei. Dieses Element kann auch mit Component Object Model (COM) Isolationsdaten, die mit der Datei verknüpften enthalten. Wenn eine Datei geändert wird, muss die Anwendungsmanifestdatei ebenfalls aktualisiert werden, um die Änderung zu übernehmen.  

## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, `file` Elemente in einer Anwendung für eine Anwendung bereitgestellt wird, mithilfe von manifest [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  

```xml  
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