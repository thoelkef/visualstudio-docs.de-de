---
title: '&lt;InstallChecks&gt; Element (Bootstrapper) | Microsoft Docs'
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
- <InstallChecks> element [bootstrapper]
ms.assetid: ad329c87-b0ad-4304-84de-ae9496514c42
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51fcfd8aaa0048cac3fb9a33c7974132655de87a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="ltinstallchecksgt-element-bootstrapper"></a>&lt;InstallChecks&gt; Element (Bootstrapper)
Die `InstallChecks` Element unterstützt das Starten von einer Vielzahl von Tests mit dem lokalen Computer aus, um sicherzustellen, dass alle erforderlichen Komponenten für eine Anwendung installiert wurden.  
  
## <a name="syntax"></a>Syntax  
  
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
  
## <a name="assemblycheck"></a>AssemblyCheck  
 Dieses Element ist ein optionales untergeordnetes Element des `InstallChecks`. Für jede Instanz des `AssemblyCheck`, der Bootstrapper wird Stellen Sie sicher, dass die Assembly, die durch das Element identifiziert im globalen Assemblycache (GAC) vorhanden ist. Es enthält keine Elemente, und weist folgende Attribute.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Property`|Erforderlich. Der Name der Eigenschaft zum Speichern des Ergebnisses. Diese Eigenschaft kann von einem Test unter verwiesen werden die `InstallConditions` Elements, d. ein untergeordnetes Element h. von der `Command` Element. Weitere Informationen finden Sie unter [ \<Befehle >-Element](../deployment/commands-element-bootstrapper.md).|  
|`Name`|Erforderlich. Der vollqualifizierte Name der Assembly zu überprüfen.|  
|`PublicKeyToken`|Erforderlich. Die abgekürzte Form des öffentlichen Schlüssels zugeordnete Assembly einen starken Namen. Alle Assemblys im GAC gespeichert benötigen einen Namen, eine Version und einen öffentlichen Schlüssel.|  
|`Version`|Erforderlich. Die Version der Assembly.<br /><br /> Die Versionsnummer hat das Format \< *Hauptversion*>.\< *Nebenversion*>.\< *Buildversion*>.\< *Revisionsversion*>.|  
|`Language`|Dies ist optional. Die Sprache einer lokalisierten Assembly. Der Standardwert ist `neutral`.|  
|`ProcessorArchitecture`|Dies ist optional. Der Prozessor des Computers von der Installation vorgesehen. Der Standardwert ist `msil`.|  
  
## <a name="externalcheck"></a>ExternalCheck führt  
 Dieses Element ist ein optionales untergeordnetes Element des `InstallChecks`. Für jede Instanz des `ExternalCheck`, der Bootstrapper die benannte externe Programm in einem separaten Prozess ausgeführt wird, und speichert den Exitcode in der angegebenen Eigenschaft von `Property`. `ExternalCheck` eignet sich für die Implementierung von komplexen abhängigkeitsprüfungen, oder wenn die einzige Möglichkeit, überprüfen Sie das Vorhandensein einer Komponente instanziiert wird.  
  
 `ExternalCheck` keine Elemente enthält, und weist folgende Attribute.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Property`|Erforderlich. Der Name der Eigenschaft zum Speichern des Ergebnisses. Diese Eigenschaft kann von einem Test unter verwiesen werden die `InstallConditions` Elements, d. ein untergeordnetes Element h. von der `Command` Element. Weitere Informationen finden Sie unter [ \<Befehle >-Element](../deployment/commands-element-bootstrapper.md).|  
|`PackageFile`|Erforderlich. Das externe Programm ausgeführt werden soll. Das Programm muss Teil des Setup-Verteilung-Pakets.|  
|`Arguments`|Dies ist optional. Stellt die Befehlszeilenargumente an die ausführbare Datei mit dem Namen von `PackageFile`.|  
  
## <a name="filecheck"></a>Menüoptionen Datei  
 Dieses Element ist ein optionales untergeordnetes Element des `InstallChecks`. Für jede Instanz des `FileCheck`, des Bootstrappers bestimmt, ob die angegebene Datei vorhanden ist und die Versionsnummer der Datei zurück. Wenn Sie eine Versionsnummer in die Datei nicht vorhanden ist, legt der Bootstrapper die Eigenschaft mit dem Namen von `Property` auf 0. Wenn die Datei nicht vorhanden ist, `Property` nicht auf einen beliebigen Wert festgelegt ist.  
  
 `FileCheck` keine Elemente enthält, und weist folgende Attribute.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Property`|Erforderlich. Der Name der Eigenschaft zum Speichern des Ergebnisses. Diese Eigenschaft kann von einem Test unter verwiesen werden die `InstallConditions` Elements, d. ein untergeordnetes Element h. von der `Command` Element. Weitere Informationen finden Sie unter [ \<Befehle >-Element](../deployment/commands-element-bootstrapper.md).|  
|`FileName`|Erforderlich. Der Name des zu suchenden Datei.|  
|`SearchPath`|Erforderlich. Der Datenträger oder Ordner, in dem nach der Datei gesucht werden soll. Dies muss ein relativer Pfad sein, wenn `SpecialFolder` zugewiesen ist; andernfalls muss er ein absoluter Pfad.|  
|`SpecialFolder`|Dies ist optional. Ein Ordner, der andere besonderen Bedeutung, entweder für Windows oder hat [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Die Standardeinstellung ist interpretieren `SearchPath` als absoluter Pfad. Folgende Werte sind gültig:<br /><br /> `AppDataFolder`. Der Ordner der Anwendung Daten für diesen [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung; für den aktuellen Benutzer spezifisch.<br /><br /> `CommonAppDataFolder`. Der Ordner der Anwendung Daten von allen Benutzern verwendet.<br /><br /> `CommonFilesFolder`. Der Ordner Gemeinsame Dateien für den aktuellen Benutzer.<br /><br /> `LocalDataAppFolder`. Der Datenordner für Anwendungen kein roaming.<br /><br /> `ProgramFilesFolder`. Standard Ordner "Programme" für 32-Bit-Anwendungen.<br /><br /> `StartUpFolder`. Der Ordner, der alle Anwendungen, die beim Systemstart gestartet enthält.<br /><br /> `SystemFolder`. Der Ordner, der 32-Bit-System-DLLs enthält.<br /><br /> `WindowsFolder`. Der Ordner, der die Windows-System-Installation enthält.<br /><br /> `WindowsVolume`. Das Laufwerk oder Partition, die die Windows-System-Installation enthält.|  
|`SearchDepth`|Dies ist optional. Die Tiefe auf dem Unterordner, nach der benannten Datei gesucht werden soll. Tiefensuchreihenfolge wird bei der Suche. Der Standardwert ist 0 (null) und die Suche zu dem Ordner der obersten Ebene schränkt von `SpecialFolder` und **SearchPath**.|  
  
## <a name="msiproductcheck"></a>MsiProductCheck  
 Dieses Element ist ein optionales untergeordnetes Element des `InstallChecks`. Für jede Instanz des `MsiProductCheck`, der Bootstrapper wird geprüft, ob die angegebene Microsoft Windows Installer-Installation ausgeführt wurde, bis er abgeschlossen ist. Der Eigenschaftswert ist abhängig vom Status des installierten Produkts festgelegt. Ein positiver Wert gibt an, das Produkt installiert ist, 0 oder-1 gibt an, es ist nicht installiert. (Sie finden Sie im Windows Installer SDK-Funktion MsiQueryFeatureState für Weitere Informationen.) . Wenn Windows Installer auf dem Computer nicht installiert ist `Property` ist nicht festgelegt.  
  
 `MsiProductCheck` keine Elemente enthält, und weist folgende Attribute.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Property`|Erforderlich. Der Name der Eigenschaft zum Speichern des Ergebnisses. Diese Eigenschaft kann von einem Test unter verwiesen werden die `InstallConditions` Elements, d. ein untergeordnetes Element h. von der `Command` Element. Weitere Informationen finden Sie unter [ \<Befehle >-Element](../deployment/commands-element-bootstrapper.md).|  
|`Product`|Erforderlich. Die GUID für das installierte Produkt.|  
|`Feature`|Dies ist optional. Die GUID für ein bestimmtes Feature der installierten Anwendung.|  
  
## <a name="registrycheck"></a>RegistryCheck  
 Dieses Element ist ein optionales untergeordnetes Element des `InstallChecks`. Für jede Instanz des `RegistryCheck`, überprüft der Bootstrapper, um festzustellen, ob der angegebene Registrierungsschlüssel vorhanden ist, oder ob sie den angegebenen Wert besitzt.  
  
 `RegistryCheck` keine Elemente enthält, und weist folgende Attribute.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Property`|Erforderlich. Der Name der Eigenschaft zum Speichern des Ergebnisses. Diese Eigenschaft kann von einem Test unter verwiesen werden die `InstallConditions` Elements, d. ein untergeordnetes Element h. von der `Command` Element. Weitere Informationen finden Sie unter [ \<Befehle >-Element](../deployment/commands-element-bootstrapper.md).|  
|`Key`|Erforderlich. Der Name des Registrierungsschlüssels.|  
|`Value`|Dies ist optional. Der Name des Registrierungswerts abgerufen werden soll. Der Standardwert ist den Text des Standardwerts zurückgegeben. `Value` eine Zeichenfolge oder einen DWORD-Wert muss sein.|  
  
## <a name="registryfilecheck"></a>RegistryFileCheck  
 Dieses Element ist ein optionales untergeordnetes Element des `InstallChecks`. Für jede Instanz des `RegistryFileCheck`, ruft der Bootstrapper die Version der angegebenen Datei zuerst versucht, den Pfad zur Datei aus dem angegebenen Registrierungsschlüssel abzurufen. Dies ist besonders nützlich, wenn Sie eine Datei in einem Verzeichnis, das als Wert in der Registrierung angegebene gesucht werden soll.  
  
 `RegistryFileCheck` keine Elemente enthält, und weist folgende Attribute.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Property`|Erforderlich. Der Name der Eigenschaft zum Speichern des Ergebnisses. Diese Eigenschaft kann von einem Test unter verwiesen werden die `InstallConditions` Elements, d. ein untergeordnetes Element h. von der `Command` Element. Weitere Informationen finden Sie unter [ \<Befehle >-Element](../deployment/commands-element-bootstrapper.md).|  
|`Key`|Erforderlich. Der Name des Registrierungsschlüssels. Sein Wert wird als den Pfad zu einer Datei interpretiert, es sei denn, die `File` -Attribut festgelegt ist. Wenn dieser Schlüssel nicht vorhanden ist, `Property` ist nicht festgelegt.|  
|`Value`|Dies ist optional. Der Name des Registrierungswerts abgerufen werden soll. Der Standardwert ist den Text des Standardwerts zurückgegeben. `Value` eine Zeichenfolge muss sein.|  
|`FileName`|Dies ist optional. Der Name einer Datei. Wenn angegeben, wird davon ausgegangen, dass der Wert aus dem Registrierungsschlüssel einen Verzeichnispfad aufweist, und diesen Namen angehängt wird. Wenn nicht angegeben, wird davon ausgegangen, dass aus der Registrierung zurückgegebene Wert den vollständigen Pfad zu einer Datei enthalten.|  
|`SearchDepth`|Dies ist optional. Die Tiefe auf dem Unterordner, nach der benannten Datei gesucht werden soll. Tiefensuchreihenfolge wird bei der Suche. Der Standardwert ist 0 (null) und die Suche zum Ordner obersten Ebene, die durch den Registrierungsschlüssel Wert angegeben schränkt.|  
  
## <a name="remarks"></a>Hinweise  
 Während die Elemente unterhalb `InstallChecks` definieren Sie die Tests ausführen, die sie nicht ausgeführt. Um die Tests auszuführen, müssen Sie erstellen `Command` Elemente unterhalb der `Commands` Element.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, die `InstallChecks` Element, wie er wird verwendet, in der Datei für die [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
```  
<InstallChecks>  
    <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />  
    <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />  
</InstallChecks>  
```  
  
## <a name="installconditions"></a>InstallConditions  
 Wenn `InstallChecks` werden ausgewertet, erzeugen sie Eigenschaften. Die Eigenschaften werden dann von verwendet `InstallConditions` zu bestimmen, ob ein Paket installieren, zu umgehen oder fehlschlagen sollte. Die folgende Tabelle enthält die `InstallConditions`:  
  
|||  
|-|-|  
|`FailIf`|Wenn alle `FailIf` Bedingung auf "true" ausgewertet wird, schlägt das Paket fehl. Der Rest der Bedingungen wird nicht ausgewertet werden.|  
|`BypassIf`|Wenn alle `BypassIf` Bedingung auf "true" ausgewertet wird, wird das Paket umgangen werden. Der Rest der Bedingungen wird nicht ausgewertet werden.|  
  
## <a name="predefined-properties"></a>Bei vordefinierten Eigenschaften  
 Die folgende Tabelle enthält die `BypassIf` und `FailIf` Elemente:  
  
|Eigenschaft|Notizen|Mögliche Werte|  
|--------------|-----------|---------------------|  
|`Version9X`|Versionsnummer der Windows 9 X-Betriebssystems.|4.10 = Windows 98|  
|`VersionNT`|Die Versionsnummer des Betriebssystems Windows NT-basierten.|"Major.minor.Servicepack"<br /><br /> 5.0 = Windows 2000<br /><br /> 5.1.0 = Windows XP<br /><br /> 5.1.2 = Windows XP Professional SP2<br /><br /> 5.2.0 = WindowsServer 2003|  
|`VersionNT64`|Die Versionsnummer eines 64-Bit-Windows NT-basierten Windows-Betriebssystems.|Identisch mit den zuvor erwähnten.|  
|`VersionMsi`|Die Versionsnummer des Windows Installer-Diensts.|2.0 = Windows Installer 2.0|  
|`AdminUser`|Gibt an, ob ein Benutzer über Administratorrechte auf ein Windows NT-basiertes Betriebssystem verfügt.|0 = keine Administratorrechte<br /><br /> 1 = Administratorrechte|  
  
 Verwenden Sie z. B. um die Installation auf einem Computer unter Windows 95 zu blockieren, Code wie den folgenden:  
  
```  
<!-- Block install on Windows 95 -->  
    <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatform"/>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [\<Befehle >-Element](../deployment/commands-element-bootstrapper.md)   
 [Referenz zum Produkt- und Paketschema](../deployment/product-and-package-schema-reference.md)