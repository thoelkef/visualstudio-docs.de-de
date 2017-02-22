---
title: "&lt;InstallChecks&gt;-Element (Bootstrapper) | Microsoft Docs"
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
  - "<InstallChecks>-Element [Bootstrapper]"
ms.assetid: ad329c87-b0ad-4304-84de-ae9496514c42
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;InstallChecks&gt;-Element (Bootstrapper)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit dem `InstallChecks`\-Element werden auf dem lokalen Computer verschiedene Tests ausgeführt, um sicherzustellen, dass alle erforderlichen Komponenten für eine Anwendung installiert sind.  
  
## Syntax  
  
```  
<InstallChecks>  
    <AssemblyCheck   
        Property  
        Name  
        PublicKeyToken  
        Version  
        Language  
        ProcessorArchitecture  
    />  
    <RegistryCheck  
        Property  
        Key  
        Value  
    />  
    <ExternalCheck   
        PackageFile  
        Property  
        Arguments  
    />  
    <FileCheck   
        Property  
        FileName  
        SearchPath  
        SpecialFolder  
        SearchDepth  
    />  
    <MsiProductCheck   
        Property  
        Product  
        Feature  
    />  
    <RegistryFileCheck   
        Property  
        Key  
        Value  
        FileName  
        SearchDepth  
    />  
</InstallChecks>  
```  
  
## AssemblyCheck  
 Dieses Element ist ein optionales untergeordnetes Element von `InstallChecks`.  Für jede Instanz von `AssemblyCheck` prüft der Bootstrapper, ob die von dem Element bezeichnete Assembly im globalen Assemblycache \(GAC\) enthalten ist.  Das Element enthält keine Elemente und verfügt über die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`Property`|Erforderlich.  Der Name der Eigenschaft, in der das Ergebnis gespeichert werden soll.  Auf diese Eigenschaft kann in einem Test unter dem `InstallConditions`\-Element verwiesen werden. Bei diesem handelt es sich um ein untergeordnetes Element des `Command`\-Elements.  Weitere Informationen finden Sie unter [\<Commands\>\-Element](../deployment/commands-element-bootstrapper.md).|  
|`Name`|Erforderlich.  Der vollqualifizierte Name der zu überprüfenden Assembly.|  
|`PublicKeyToken`|Erforderlich.  Die abgekürzte Form des öffentlichen Schlüssels, der dieser Assembly mit starkem Namen zugeordnet ist.  Alle im GAC gespeicherten Assemblys müssen über einen Namen, eine Version und einen öffentlichen Schlüssel verfügen.|  
|`Version`|Erforderlich.  Die Version der Assembly.<br /><br /> Die Versionsnummer hat das Format \<*Major Version*\>.\<*Minor Version*\>.\<*Build Version*\>.\<*Revision Version*\>.|  
|`Language`|Optional.  Die Sprache einer lokalisierten Assembly.  Der Standardwert lautet `neutral`.|  
|`ProcessorArchitecture`|Optional.  Der für diese Installation verwendete Computerprozessor.  Der Standardwert lautet `msil`.|  
  
## ExternalCheck  
 Dieses Element ist ein optionales untergeordnetes Element von `InstallChecks`.  Für jede Instanz von `ExternalCheck` führt der Bootstrapper das benannte externe Programm in einem separaten Prozess aus und speichert seinen Exitcode in der von `Property` angegebenen Eigenschaft.  `ExternalCheck` ist nützlich für das Implementieren von komplexen Abhängigkeitsüberprüfungen, oder wenn nur durch Instanziierung einer Komponente festgestellt werden kann, ob diese vorhanden ist.  
  
 `ExternalCheck` enthält keine Elemente und verfügt über die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`Property`|Erforderlich.  Der Name der Eigenschaft, in der das Ergebnis gespeichert werden soll.  Auf diese Eigenschaft kann in einem Test unter dem `InstallConditions`\-Element verwiesen werden. Bei diesem handelt es sich um ein untergeordnetes Element des `Command`\-Elements.  Weitere Informationen finden Sie unter [\<Commands\>\-Element](../deployment/commands-element-bootstrapper.md).|  
|`PackageFile`|Erforderlich.  Das externe Programm, das ausgeführt werden soll.  Das Programm muss Teil des Setupverteilungspakets sein.|  
|`Arguments`|Optional.  Gibt Befehlszeilenargumente für die von `PackageFile` benannte ausführbare Datei an.|  
  
## FileCheck  
 Dieses Element ist ein optionales untergeordnetes Element von `InstallChecks`.  Für jede Instanz von `FileCheck` ermittelt der Bootstrapper, ob die benannte Datei vorhanden ist, und gibt die Versionsnummer der Datei zurück.  Wenn die Datei keine Versionsnummer besitzt, legt der Bootstrapper die von `Property` benannte Eigenschaft auf 0 fest.  Wenn die Datei nicht vorhanden ist, wird `Property` auf keinen Wert festgelegt.  
  
 `FileCheck` enthält keine Elemente und verfügt über die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`Property`|Erforderlich.  Der Name der Eigenschaft, in der das Ergebnis gespeichert werden soll.  Auf diese Eigenschaft kann in einem Test unter dem `InstallConditions`\-Element verwiesen werden. Bei diesem handelt es sich um ein untergeordnetes Element des `Command`\-Elements.  Weitere Informationen finden Sie unter [\<Commands\>\-Element](../deployment/commands-element-bootstrapper.md).|  
|`FileName`|Erforderlich.  Der Name der zu suchenden Datei.|  
|`SearchPath`|Erforderlich.  Der Datenträger oder der Ordner, auf bzw. in dem nach der Datei gesucht werden soll.  Wenn `SpecialFolder` zugewiesen ist, muss ein relativer Pfad angegeben werden, andernfalls ein absoluter Pfad.|  
|`SpecialFolder`|Optional.  Ein Ordner mit besonderer Bedeutung für Windows oder [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Standardmäßig wird `SearchPath` als absoluter Pfad interpretiert.  Folgende Werte sind gültig:<br /><br /> `AppDataFolder`.  Der Anwendungsdatenordner für diese [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung. Dieser gilt ausschließlich für den aktuellen Benutzer.<br /><br /> `CommonAppDataFolder`.  Der von allen Benutzern verwendete Anwendungsdatenordner.<br /><br /> `CommonFilesFolder`.  Der Ordner Gemeinsame Dateien für den aktuellen Benutzer.<br /><br /> `LocalDataAppFolder`.  Der Datenordner für nicht roamingfähige Anwendungen.<br /><br /> `ProgramFilesFolder`.  Der Standardordner Programme für 32\-Bit\-Anwendungen.<br /><br /> `StartUpFolder`.  Der Ordner, der alle Anwendungen enthält, die beim Systemstart gestartet werden.<br /><br /> `SystemFolder`.  Der Ordner, der 32\-Bit\-System\-DLLs enthält.<br /><br /> `WindowsFolder`.  Der Ordner, der die Windows\-Systeminstallation enthält.<br /><br /> `WindowsVolume`.  Das Laufwerk oder die Partition, das bzw. die die Windows\-Systeminstallation enthält.|  
|`SearchDepth`|Optional.  Die Suchtiefe, die bei der Suche nach der benannten Datei in Unterordnern berücksichtigt wird.  Es wird die Tiefensuche verwendet.  Der Standardwert ist 0 \(null\), wodurch die Suche auf den von `SpecialFolder` und **SearchPath** angegebenen Ordner der obersten Ebene beschränkt wird.|  
  
## MsiProductCheck  
 Dieses Element ist ein optionales untergeordnetes Element von `InstallChecks`.  Für jede Instanz von `MsiProductCheck` überprüft der Bootstrapper, ob die angegebene Microsoft Windows Installer\-Installation vollständig ausgeführt wurde.  Der Eigenschaftswert wird abhängig vom Zustand dieses installierten Produkts festgelegt.  Ein positiver Wert gibt an, dass das Produkt installiert ist, 0 oder \-1 gibt an, dass es nicht installiert ist.  \(Weitere Informationen erhalten Sie im Zusammenhang mit der Windows Installer SDK\-Funktion MsiQueryFeatureState.\) .  Wenn Windows Installer nicht auf dem Computer installiert wurde, ist `Property` nicht festgelegt.  
  
 `MsiProductCheck` enthält keine Elemente und verfügt über die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`Property`|Erforderlich.  Der Name der Eigenschaft, in der das Ergebnis gespeichert werden soll.  Auf diese Eigenschaft kann in einem Test unter dem `InstallConditions`\-Element verwiesen werden. Bei diesem handelt es sich um ein untergeordnetes Element des `Command`\-Elements.  Weitere Informationen finden Sie unter [\<Commands\>\-Element](../deployment/commands-element-bootstrapper.md).|  
|`Product`|Erforderlich.  Die GUID für das installierte Produkt.|  
|`Feature`|Optional.  Die GUID für ein bestimmtes Feature der installierten Anwendung.|  
  
## RegistryCheck  
 Dieses Element ist ein optionales untergeordnetes Element von `InstallChecks`.  Für jede Instanz von `RegistryCheck` überprüft der Bootstrapper, ob der angegebene Registrierungsschlüssel vorhanden ist oder den angegebenen Wert aufweist.  
  
 `RegistryCheck` enthält keine Elemente und verfügt über die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`Property`|Erforderlich.  Der Name der Eigenschaft, in der das Ergebnis gespeichert werden soll.  Auf diese Eigenschaft kann in einem Test unter dem `InstallConditions`\-Element verwiesen werden. Bei diesem handelt es sich um ein untergeordnetes Element des `Command`\-Elements.  Weitere Informationen finden Sie unter [\<Commands\>\-Element](../deployment/commands-element-bootstrapper.md).|  
|`Key`|Erforderlich.  Der Name des Registrierungsschlüssels.|  
|`Value`|Optional.  Der Name des abzurufenden Registrierungswerts.  Standardmäßig wird der Text des Standardwerts zurückgegeben.  `Value` muss entweder eine Zeichenfolge oder ein DWORD sein.|  
  
## RegistryFileCheck  
 Dieses Element ist ein optionales untergeordnetes Element von `InstallChecks`.  Für jede Instanz von `RegistryFileCheck` ruft der Bootstrapper die Version der angegebenen Datei ab, wobei er zuerst versucht, den Pfad der Datei aus dem angegebenen Registrierungsschlüssel abzurufen.  Dies ist besonders nützlich, wenn Sie eine Datei in einem Verzeichnis suchen, das als Wert in der Registrierung angegeben ist.  
  
 `RegistryFileCheck` enthält keine Elemente und verfügt über die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`Property`|Erforderlich.  Der Name der Eigenschaft, in der das Ergebnis gespeichert werden soll.  Auf diese Eigenschaft kann in einem Test unter dem `InstallConditions`\-Element verwiesen werden. Bei diesem handelt es sich um ein untergeordnetes Element des `Command`\-Elements.  Weitere Informationen finden Sie unter [\<Commands\>\-Element](../deployment/commands-element-bootstrapper.md).|  
|`Key`|Erforderlich.  Der Name des Registrierungsschlüssels.  Der entsprechende Wert wird als der Pfad einer Datei interpretiert, es sei denn, das `File`\-Attribut wird festgelegt.  Wenn dieser Schlüssel nicht vorhanden ist, wird `Property` nicht festgelegt.|  
|`Value`|Optional.  Der Name des abzurufenden Registrierungswerts.  Standardmäßig wird der Text des Standardwerts zurückgegeben.  `Value` muss eine Zeichenfolge sein.|  
|`FileName`|Optional.  Der Name einer Datei.  Wenn dieses Attribut angegeben wird, wird der aus dem Registrierungsschlüssel abgerufene Wert als Verzeichnispfad interpretiert und dieser Name angefügt.  Wird es nicht angegeben, wird der von der Registrierung zurückgegebene Wert als vollständiger Pfad einer Datei interpretiert.|  
|`SearchDepth`|Optional.  Die Suchtiefe, die bei der Suche nach der benannten Datei in Unterordnern berücksichtigt wird.  Es wird die Tiefensuche verwendet.  Der Standardwert lautet 0 \(null\), wodurch die Suche auf den im Wert des Registrierungsschlüssels angegebenen Ordner der obersten Ebene beschränkt wird.|  
  
## Hinweise  
 Die `InstallChecks` untergeordneten Elemente definieren die Tests, die ausgeführt werden sollen, führen diese jedoch nicht aus.  Um die Tests auszuführen, müssen Sie `Command`\-Elemente unter dem `Commands`\-Element erstellen.  
  
## Beispiel  
 Das folgende Codebeispiel veranschaulicht, wie das `InstallChecks`\-Element in der Produktdatei für [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] verwendet wird.  
  
```  
<InstallChecks>  
    <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />  
    <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />  
</InstallChecks>  
```  
  
## InstallConditions  
 Wenn `InstallChecks` ausgewertet werden, erzeugen sie Eigenschaften.  Anhand dieser Eigenschaften bestimmen die `InstallConditions`, ob ein Paket installiert, umgangen oder verworfen werden soll.  Die `InstallConditions` sind in der folgenden Tabelle aufgelistet:  
  
|||  
|-|-|  
|`FailIf`|Wenn eine beliebige `FailIf`\-Bedingung true ergibt, wird das Paket verworfen.  Die übrigen Bedingungen werden nicht ausgewertet.|  
|`BypassIf`|Wenn eine beliebige `BypassIf`\-Bedingung true ergibt, wird das Paket umgangen.  Die übrigen Bedingungen werden nicht ausgewertet.|  
  
## Vordefinierte Eigenschaften  
 In der folgenden Tabelle sind die Elemente `BypassIf` und `FailIf` aufgeführt.  
  
|Property|Hinweise|Mögliche Werte|  
|--------------|--------------|--------------------|  
|`Version9X`|Versionsnummer eines Windows 9X\-Betriebssystems.|4.10 \= Windows 98|  
|`VersionNT`|Versionsnummer eines Windows NT\-basierten Betriebssystems.|Major.Minor.ServicePack<br /><br /> 5.0 \= Windows 2000<br /><br /> 5.1.0 \= Windows XP<br /><br /> 5.1.2 \= Windows XP Professional SP2<br /><br /> 5.2.0 \= Windows Server 2003|  
|`VersionNT64`|Versionsnummer eines 64\-Bit\-Windows NT\-basierten Betriebssystems.|Wie oben erwähnt.|  
|`VersionMsi`|Versionsnummer des Windows Installer\-Dienstes.|2.0 \= Windows Installer 2.0|  
|`AdminUser`|Gibt an, ob ein Benutzer über Administratorrechte für ein Windows NT\-basiertes Betriebssystem verfügt.|0 \= keine Administratorrechte<br /><br /> 1 \= Administratorrechte|  
  
 Um die Installation auf einem Computer mit Windows 95 zu blockieren, verwenden Sie beispielsweise folgenden Code:  
  
```  
<!-- Block install on Windows 95 -->  
    <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatform"/>  
```  
  
## Siehe auch  
 [\<Commands\>\-Element](../deployment/commands-element-bootstrapper.md)   
 [Referenz zum Produkt\- und Paketschema](../deployment/product-and-package-schema-reference.md)