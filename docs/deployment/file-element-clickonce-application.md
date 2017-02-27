---
title: "&lt;file&gt; Element (ClickOnce Application) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://www.w3.org/2000/09/xmldsig#Transform"
  - "urn:schemas-microsoft-com:asm.v2#file"
  - "http://www.w3.org/2000/09/xmldsig#DigestValue"
  - "http://www.w3.org/2000/09/xmldsig#DigestMethod"
  - "http://www.w3.org/2000/09/xmldsig#Transforms"
  - "urn:schemas-microsoft-com:asm.v2#hash"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<file> element [ClickOnce application manifest]"
  - "manifests [ClickOnce], file element"
ms.assetid: 56e3490c-eed5-4841-b1bf-eefe778b6ac9
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 24
---
# &lt;file&gt; Element (ClickOnce Application)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Identifiziert alle Nichtassemblydateien, die von der Anwendung heruntergeladen und verwendet werden.  
  
## Syntax  
  
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
  
## Elemente und Attribute  
 Das `file`\-Element ist optional.  Das Element verfügt über die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`name`|Erforderlich.  Identifiziert den Namen der Datei.|  
|`size`|Erforderlich.  Gibt die Größe der Datei in Bytes an.|  
|`group`|Optional, wenn das `optional`\-Attribut nicht angegeben oder auf `false` festgelegt wird; erforderlich, wenn `optional``true` ist.  Der Name der Gruppe, zu der diese Datei gehört.  Der Name kann eine vom Entwickler gewählte Unicode\-Zeichenfolge sein. Er wird verwendet, um Dateien bei Bedarf mit der <xref:System.Deployment.Application.ApplicationDeployment>\-Klasse herunterzuladen.|  
|`optional`|Optional.  Gibt an, ob diese Datei bei der ersten Ausführung der Anwendung heruntergeladen werden muss oder ob sie auf dem Server verbleiben soll, bis die Anwendung sie bei Bedarf anfordert.  Wenn das Attribut den Wert `false` aufweist oder nicht definiert ist, wird die Datei bei der ersten Ausführung oder der Installation der Anwendung heruntergeladen.  Wenn `true` gilt, muss eine `group` angegeben werden, damit das Anwendungsmanifest gültig ist.  `optional` kann nicht gültig sein, wenn `writeableType` mit dem Wert `applicationData` angegeben ist.|  
|`writeableType`|Optional.  Gibt an, dass es sich bei dieser Datei um eine Datendatei handelt.  Derzeit lautet der einzige gültige Wert `applicationData`.|  
  
## typelib  
 Das `typelib`\-Element ist ein optionales untergeordnetes Element des Dateielements.  Das Element beschreibt die zur COM\-Komponente gehörige Typbibliothek.  Das Element verfügt über die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`tlbid`|Erforderlich.  Die der Typbibliothek zugewiesene GUID.|  
|`version`|Erforderlich.  Die Versionsnummer der Typbibliothek.|  
|`helpdir`|Erforderlich.  Das Verzeichnis, das die Hilfedateien für die Komponente enthält.  Kann die Länge 0 \(null\) haben.|  
|`resourceid`|Optional.  Die hexadezimale Zeichenfolgendarstellung des Gebietsschemabezeichners \(LCID\).  Dieser besteht aus bis zu vier Hexadezimalziffern ohne das Präfix 0x und ohne führende Nullen \(0\).  Die LCID hat möglicherweise einen neutralen Sprachvariantenbezeichner.|  
|`flags`|Optional.  Die Zeichenfolgendarstellung der Typbibliothekflags für diese Typbibliothek.  Sollte insbesondere "RESTRICTED", "CONTROL", "HIDDEN" oder "HASDISKIMAGE" entsprechen.|  
  
## comClass  
 Das `comClass`\-Element ist ein optionales untergeordnetes Element des `file`\-Elements. Es ist jedoch erforderlich, wenn die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung eine COM\-Komponente enthält, die über COM ohne Registrierung bereitgestellt werden soll.  Das Element verfügt über die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`clsid`|Erforderlich.  Die Klassen\-ID der als GUID ausgedrückten COM\-Komponente.|  
|`description`|Optional.  Der Klassenname.|  
|`threadingModel`|Optional.  Das von prozessinternen COM\-Klassen verwendete Threadmodell.  Wenn diese Eigenschaft NULL ist, wird kein Threadmodell verwendet.  Die Komponente wird im Hauptthread des Clients erstellt, und Aufrufe von anderen Threads werden an diesen Thread gemarshallt.  Die folgende Liste zeigt die gültigen Werte:<br /><br /> `Apartment`, `Free`, `Both` und `Neutral`.|  
|`tlbid`|Optional.  GUID für die Typbibliothek dieser COM\-Komponente.|  
|`progid`|Optional.  Versionsabhängiger programmgesteuerter Bezeichner dieser COM\-Komponente.  Das Format von `ProgID` entspricht `<vendor>.<component>.<version>`.|  
|`miscStatus`|Optional.  Dupliziert im Assemblymanifest die vom `MiscStatus`\-Registrierungsschlüssel bereitgestellten Informationen.  Wenn für die Attribute `miscStatusIcon`, `miscStatusContent`, `miscStatusDocprint` oder `miscStatusThumbnail` keine Werte gefunden werden, wird der entsprechende unter `miscStatus` aufgeführte Standardwert für die fehlenden Attribute verwendet.  Der Wert kann einer durch Kommas getrennten Liste der Attributwerte aus der folgenden Tabelle entsprechen.  Dieses Attribut kann verwendet werden, wenn die COM\-Klasse einer OCX\-Klasse entspricht, die `MiscStatus`\-Registrierungsschlüsselwerte erfordert.|  
|`miscStatusIcon`|Optional.  Dupliziert im Assemblymanifest die von DVASPECT\_ICON bereitgestellten Informationen.  Dabei kann ein Symbol eines Objekts bereitgestellt werden.  Der Wert kann einer durch Kommas getrennten Liste der Attributwerte aus der folgenden Tabelle entsprechen.  Dieses Attribut kann verwendet werden, wenn die COM\-Klasse einer OCX\-Klasse entspricht, die `Miscstatus`\-Registrierungsschlüsselwerte erfordert.|  
|`miscStatusContent`|Optional.  Dupliziert im Assemblymanifest die von DVASPECT\_CONTENT bereitgestellten Informationen.  Dabei kann es sich um ein Verbunddokument handeln, das auf einem Bildschirm oder Drucker ausgegeben werden kann.  Der Wert kann einer durch Kommas getrennten Liste der Attributwerte aus der folgenden Tabelle entsprechen.  Dieses Attribut kann verwendet werden, wenn die COM\-Klasse einer OCX\-Klasse entspricht, die `MiscStatus`\-Registrierungsschlüsselwerte erfordert.|  
|`miscStatusDocPrint`|Optional.  Dupliziert im Assemblymanifest die von DVASPECT\_DOCPRINT bereitgestellten Informationen.  Dabei kann eine Objektdarstellung bereitgestellt werden, die auf dem Bildschirm angezeigt werden kann und der Ausgabe auf dem Drucker entspricht.  Der Wert kann einer durch Kommas getrennten Liste der Attributwerte aus der folgenden Tabelle entsprechen.  Dieses Attribut kann verwendet werden, wenn die COM\-Klasse einer OCX\-Klasse entspricht, die `MiscStatus`\-Registrierungsschlüsselwerte erfordert.|  
|`miscStatusThumbnail`|Optional.  Dupliziert im Assemblymanifest die von DVASPECT\_THUMBNAIL bereitgestellten Informationen.  Dabei kann eine Miniaturansicht eines Objekts bereitgestellt werden, die in einem Browsertool dargestellt werden kann.  Der Wert kann einer durch Kommas getrennten Liste der Attributwerte aus der folgenden Tabelle entsprechen.  Dieses Attribut kann verwendet werden, wenn die COM\-Klasse einer OCX\-Klasse entspricht, die `MiscStatus`\-Registrierungsschlüsselwerte erfordert.|  
  
## comInterfaceExternalProxyStub  
 Das `comInterfaceExternalProxyStub`\-Element ist ein optionales untergeordnetes Element des `file`\-Elements. Es ist jedoch möglicherweise erforderlich, wenn die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung eine COM\-Komponente enthält, die über COM ohne Registrierung bereitgestellt werden soll.  Das Element verfügt über die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`iid`|Erforderlich.  Die Schnittstellen\-ID \(IID\), die von diesem Proxy verarbeitet wird.  Die IID muss in geschweiften Klammern stehen.|  
|`baseInterface`|Optional.  Die IID der Schnittstelle, von der die Schnittstelle abgeleitet wird, auf die durch `iid` verwiesen wird.|  
|`numMethods`|Optional.  Die Anzahl der von der Schnittstelle implementierten Methoden.|  
|`name`|Optional.  Der Name der Schnittstelle, wie im Code verwendet.|  
|`tlbid`|Optional.  Die Typbibliothek, die die Beschreibung der vom `iid`\-Attribut angegebenen Schnittstelle enthält.|  
|`proxyStubClass32`|Optional.  Ordnet einer CLSID in 32\-Bit\-Proxy\-DLLs eine IID zu.|  
  
## comInterfaceProxyStub  
 Das `comInterfaceProxyStub`\-Element ist ein optionales untergeordnetes Element des `file`\-Elements. Es ist jedoch möglicherweise erforderlich, wenn die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung eine COM\-Komponente enthält, die über COM ohne Registrierung bereitgestellt werden soll.  Das Element verfügt über die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`iid`|Erforderlich.  Die Schnittstellen\-ID \(IID\), die von diesem Proxy verarbeitet wird.  Die IID muss in geschweiften Klammern stehen.|  
|`baseInterface`|Optional.  Die IID der Schnittstelle, von der die Schnittstelle abgeleitet wird, auf die durch `iid` verwiesen wird.|  
|`numMethods`|Optional.  Die Anzahl der von der Schnittstelle implementierten Methoden.|  
|`Name`|Optional.  Der Name der Schnittstelle, wie im Code verwendet.|  
|`Tlbid`|Optional.  Die Typbibliothek, die die Beschreibung der vom `iid`\-Attribut angegebenen Schnittstelle enthält.|  
|`proxyStubClass32`|Optional.  Ordnet einer CLSID in 32\-Bit\-Proxy\-DLLs eine IID zu.|  
|`threadingModel`|Optional.  Optional.  Das von prozessinternen COM\-Klassen verwendete Threadmodell.  Wenn diese Eigenschaft NULL ist, wird kein Threadmodell verwendet.  Die Komponente wird im Hauptthread des Clients erstellt, und Aufrufe von anderen Threads werden an diesen Thread gemarshallt.  Die folgende Liste zeigt die gültigen Werte:<br /><br /> `Apartment`, `Free`, `Both` und `Neutral`.|  
  
## windowClass  
 Das `windowClass`\-Element ist ein optionales untergeordnetes Element des `file`\-Elements. Es ist jedoch möglicherweise erforderlich, wenn die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung eine COM\-Komponente enthält, die über COM ohne Registrierung bereitgestellt werden soll.  Das Element verweist auf eine von der COM\-Komponente definierte Fensterklasse, auf die eine Version angewendet werden muss.  Das Element verfügt über die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`versioned`|Optional.  Steuert, ob der in der Registrierung verwendete interne Name der Fensterklasse die Version der Assembly aufweist, in der die Fensterklasse enthalten ist.  Der Wert dieses Attributs kann `yes` oder `no` sein.  Der Standardwert lautet `yes`.  Der Wert `no` sollte nur verwendet werden, wenn dieselbe Fensterklasse von einer parallelen Komponente und einer entsprechenden nicht parallelen Komponente definiert wurde und diese als identische Fensterklasse behandelt werden sollen.  Ansonsten sind die üblichen Regeln zur Registrierung von Fensterklassen zu beachten: Die Fensterklasse kann nur von der ersten Komponente registriert werden, die die Registrierung ausführt, da auf die Klasse keine Version angewendet wurde.|  
  
## hash  
 Das `hash`\-Element ist ein optionales untergeordnetes Element des `file`\-Elements.  Das `hash`\-Element weist keine Attribute auf.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] verwendet als Sicherheitsüberprüfung einen algorithmischen Hash aller Dateien in einer Anwendung, um sicherzustellen, dass keine der Dateien nach der Bereitstellung geändert wurde.  Wenn das `hash`\-Element nicht enthalten ist, wird diese Überprüfung nicht ausgeführt. Daher wird das Auslassen des `hash`\-Elements nicht empfohlen.  
  
 Wenn ein Manifest eine nicht gehashte Datei enthält, kann es nicht digital signiert werden, da Benutzer die Inhalte nicht gehashter Dateien nicht überprüfen können.  
  
## dsig:Transforms  
 Das `dsig:Transforms`\-Element ist ein erforderliches untergeordnetes Element des `hash`\-Elements.  Das `dsig:Transforms`\-Element weist keine Attribute auf.  
  
## dsig:Transform  
 Das `dsig:Transform`\-Element ist ein erforderliches untergeordnetes Element des `dsig:Transforms`\-Elements.  Das `dsig:Transform`\-Element verfügt über die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`Algorithm`|Der Algorithmus, der zum Berechnen des Digests für diese Datei verwendet wird.  Derzeit wird von [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nur ein Wert verwendet, nämlich `urn:schemas-microsoft-com:HashTransforms.Identity`.|  
  
## dsig:DigestMethod  
 Das `dsig:DigestMethod`\-Element ist ein erforderliches untergeordnetes Element des `hash`\-Elements.  Das `dsig:DigestMethod`\-Element verfügt über die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`Algorithm`|Der Algorithmus, der zum Berechnen des Digests für diese Datei verwendet wird.  Derzeit wird von [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nur ein Wert verwendet, nämlich `http://www.w3.org/2000/09/xmldsig#sha1`.|  
  
## dsig:DigestValue  
 Das `dsig:DigestValue`\-Element ist ein erforderliches untergeordnetes Element des `hash`\-Elements.  Das `dsig:DigestValue`\-Element weist keine Attribute auf.  Sein Textwert ist der berechnete Hash für die angegebene Datei.  
  
## Hinweise  
 Dieses Element identifiziert alle Nichtassemblydateien, aus denen die Anwendung besteht, und besonders die Hashwerte für die Dateiüberprüfung.  Dieses Element kann auch der Datei zugeordnete COM\-Isolationsdaten \(Component Object Model\) umfassen.  Wenn eine Datei geändert wird, muss die Anwendungsmanifestdatei auch entsprechend aktualisiert werden.  
  
## Beispiel  
 Im folgenden Codebeispiel werden `file`\-Elemente in einem Anwendungsmanifest für eine mit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bereitgestellte Anwendung veranschaulicht.  
  
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
  
## Siehe auch  
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)