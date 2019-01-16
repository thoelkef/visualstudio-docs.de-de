---
title: '&lt;InstallChecks&gt; -Element (Bootstrapper) | Microsoft-Dokumentation'
ms.date: 11/04/2016
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
ms.openlocfilehash: ccd9fa5ea1f7963d4864e276bd05011be817de2c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53865980"
---
# <a name="ltinstallchecksgt-element-bootstrapper"></a>&lt;InstallChecks&gt; -Element (Bootstrapper)
Die `InstallChecks` Element unterstützt das Starten von einer Vielzahl von Tests mit dem lokalen Computer aus, um sicherzustellen, dass alle erforderlichen Komponenten für eine Anwendung installiert wurden.  

## <a name="syntax"></a>Syntax  

```xml  
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
 Dieses Element ist ein optionales untergeordnetes Element des `InstallChecks`. Für jede Instanz der `AssemblyCheck`, der Bootstrapper stellt sicher, dass die Assembly, die durch das Element identifiziert, die im globalen Assemblycache (GAC) vorhanden ist. Es enthält keine Elemente, und weist folgende Attribute.  

|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Property`|Erforderlich. Der Name der Eigenschaft zum Speichern des Ergebnisses. Diese Eigenschaft verwiesen werden kann, in einem Test unter der `InstallConditions` -Element, das ein untergeordnetes Element von der `Command` Element. Weitere Informationen finden Sie unter [ \<Befehle >-Element](../deployment/commands-element-bootstrapper.md).|  
|`Name`|Erforderlich. Der voll gekennzeichnete Name des zu überprüfenden Assembly.|  
|`PublicKeyToken`|Erforderlich. Die abgekürzte Form des öffentlichen Schlüssels zugeordnete Assembly einen starken Namen. Alle Assemblys im GAC gespeichert müssen einen Namen, eine Version und einen öffentlichen Schlüssel.|  
|`Version`|Erforderlich. Die Version der Assembly.<br /><br /> Die Versionsnummer muss im Format \< *Hauptversion*>.\< *Nebenversion*>.\< *Buildversion*>.\< *Revisionsversion*>.|  
|`Language`|Dies ist optional. Die Sprache des eine lokalisierte Assembly. Der Standardwert ist `neutral`.|  
|`ProcessorArchitecture`|Dies ist optional. Der Prozessor des Computers für die Installation. Der Standardwert ist `msil`.|  

## <a name="externalcheck"></a>ExternalCheck führt  
 Dieses Element ist ein optionales untergeordnetes Element des `InstallChecks`. Für jede Instanz der `ExternalCheck`, der Bootstrapper die benannte externe Programm in einem separaten Prozess ausgeführt wird, und speichert Sie in der Eigenschaft, angegeben durch den Exitcode `Property`. `ExternalCheck` eignet sich für die Implementierung komplexer abhängigkeitsprüfungen, oder wenn die einzige Möglichkeit, die überprüft, ob eine Komponente instanziiert.  

 `ExternalCheck` keine Elemente enthält, und weist folgende Attribute.  

|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Property`|Erforderlich. Der Name der Eigenschaft zum Speichern des Ergebnisses. Diese Eigenschaft verwiesen werden kann, in einem Test unter der `InstallConditions` -Element, das ein untergeordnetes Element von der `Command` Element. Weitere Informationen finden Sie unter [ \<Befehle >-Element](../deployment/commands-element-bootstrapper.md).|  
|`PackageFile`|Erforderlich. Das externe Programm ausgeführt werden soll. Das Programm muss Teil des Setuppakets Verteilung sein.|  
|`Arguments`|Dies ist optional. Gibt Befehlszeilenargumente an die ausführbare Datei mit dem Namen von `PackageFile`.|  

## <a name="filecheck"></a>Menüoptionen Datei  
 Dieses Element ist ein optionales untergeordnetes Element des `InstallChecks`. Für jede Instanz der `FileCheck`, der Bootstrapper bestimmen, ob die angegebene Datei vorhanden ist, und geben Sie die Versionsnummer der Datei zurück. Wenn Sie eine Versionsnummer in der Datei nicht vorhanden ist, legt der Bootstrapper die Eigenschaft mit dem Namen von `Property` auf 0. Wenn die Datei nicht vorhanden ist, `Property` nicht auf einen beliebigen Wert festgelegt ist.  

 `FileCheck` keine Elemente enthält, und weist folgende Attribute.  


| Attribut | Beschreibung |
|-----------------| - |
| `Property` | Erforderlich. Der Name der Eigenschaft zum Speichern des Ergebnisses. Diese Eigenschaft verwiesen werden kann, in einem Test unter der `InstallConditions` -Element, das ein untergeordnetes Element von der `Command` Element. Weitere Informationen finden Sie unter [ \<Befehle >-Element](../deployment/commands-element-bootstrapper.md). |
| `FileName` | Erforderlich. Der Name des zu suchenden Datei. |
| `SearchPath` | Erforderlich. Der Datenträger oder ein Ordner, in dem nach der Datei gesucht werden soll. Dies muss ein relativer Pfad sein, wenn `SpecialFolder` zugewiesen ist; andernfalls, muss es sich um einen absoluten Pfad. |
| `SpecialFolder` | Dies ist optional. Ein Ordner, der besondere Bedeutung, entweder auf Windows oder hat [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Der Standardwert ist, interpretiert `SearchPath` als absoluter Pfad. Folgende Werte sind gültig:<br /><br /> `AppDataFolder`. Der Anwendungsdatenordner für diesen [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung; für den aktuellen Benutzer spezifisch.<br /><br /> `CommonAppDataFolder`. Der Anwendungsdatenordner, die von allen Benutzern verwendet wird.<br /><br /> `CommonFilesFolder`. Im Ordner "Gemeinsame Dateien" für den aktuellen Benutzer.<br /><br /> `LocalDataAppFolder`. Der Datenordner für Anwendungen kein roaming.<br /><br /> `ProgramFilesFolder`. Die standardmäßigen Ordner "Programme" für 32-Bit-Anwendungen.<br /><br /> `StartUpFolder`. Der Ordner, der enthält alle Anwendungen, die beim Systemstart gestartet.<br /><br /> `SystemFolder`. Der Ordner, der 32-Bit-System-DLLs enthält.<br /><br /> `WindowsFolder`. Der Ordner, der die Windows-System-Installation enthält.<br /><br /> `WindowsVolume`. Das Laufwerk oder Partition, die die Windows-System-Installation enthält. |
| `SearchDepth` | Dies ist optional. Die Tiefe am dem Unterordner für die angegebene Datei gesucht werden soll. Die Suche ist die Tiefe. Der Standardwert ist 0 (null) und die Suche auf den Ordner der obersten Ebene in beschränkt `SpecialFolder` und **SearchPath**. |

## <a name="msiproductcheck"></a>MsiProductCheck  
 Dieses Element ist ein optionales untergeordnetes Element des `InstallChecks`. Für jede Instanz der `MsiProductCheck`, der Bootstrapper überprüft, ob die angegebene Microsoft Windows Installer-Installation ausgeführt wurde, bis er abgeschlossen ist. Den Wert der Eigenschaft, die je nach Zustand des installierten Produkts festgelegt ist. Ein positiver Wert gibt an, das Produkt installiert ist, 0 oder-1 gibt an, es ist nicht installiert. (Siehe die Funktion mit dem Windows Installer SDK MsiQueryFeatureState, Weitere Informationen.) . Wenn Windows Installer nicht, auf dem Computer installiert ist, `Property` ist nicht festgelegt.  

 `MsiProductCheck` keine Elemente enthält, und weist folgende Attribute.  

|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Property`|Erforderlich. Der Name der Eigenschaft zum Speichern des Ergebnisses. Diese Eigenschaft verwiesen werden kann, in einem Test unter der `InstallConditions` -Element, das ein untergeordnetes Element von der `Command` Element. Weitere Informationen finden Sie unter [ \<Befehle >-Element](../deployment/commands-element-bootstrapper.md).|  
|`Product`|Erforderlich. Die GUID für das installierte Produkt hinzu.|  
|`Feature`|Dies ist optional. Die GUID für eine bestimmte Funktion von der installierten Anwendung.|  

## <a name="registrycheck"></a>RegistryCheck  
 Dieses Element ist ein optionales untergeordnetes Element des `InstallChecks`. Für jede Instanz der `RegistryCheck`, überprüft der Bootstrapper, um festzustellen, ob der angegebene Registrierungsschlüssel vorhanden ist, oder gibt an, ob es sich um den angegebenen Wert aufweist.  

 `RegistryCheck` keine Elemente enthält, und weist folgende Attribute.  

|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Property`|Erforderlich. Der Name der Eigenschaft zum Speichern des Ergebnisses. Diese Eigenschaft verwiesen werden kann, in einem Test unter der `InstallConditions` -Element, das ein untergeordnetes Element von der `Command` Element. Weitere Informationen finden Sie unter [ \<Befehle >-Element](../deployment/commands-element-bootstrapper.md).|  
|`Key`|Erforderlich. Der Name des Registrierungsschlüssels.|  
|`Value`|Dies ist optional. Der Name des Registrierungswerts abgerufen werden soll. Der Standardwert ist den Text des Standardwerts zurückgegeben. `Value` Hierbei muss es sich um eine Zeichenfolge oder einen DWORD-Wert sein.|  

## <a name="registryfilecheck"></a>RegistryFileCheck  
 Dieses Element ist ein optionales untergeordnetes Element des `InstallChecks`. Für jede Instanz der `RegistryFileCheck`, der Bootstrapper Ruft die Version der angegebenen Datei ab zuerst versucht, den Pfad zur Datei aus dem angegebenen Registrierungsschlüssel abzurufen. Dies ist besonders nützlich, wenn Sie eine Datei in einem Verzeichnis, das als Wert in der Registrierung angegeben suchen möchten.  

 `RegistryFileCheck` keine Elemente enthält, und weist folgende Attribute.  

|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Property`|Erforderlich. Der Name der Eigenschaft zum Speichern des Ergebnisses. Diese Eigenschaft verwiesen werden kann, in einem Test unter der `InstallConditions` -Element, das ein untergeordnetes Element von der `Command` Element. Weitere Informationen finden Sie unter [ \<Befehle >-Element](../deployment/commands-element-bootstrapper.md).|  
|`Key`|Erforderlich. Der Name des Registrierungsschlüssels. Der Wert wird als Pfad zu einer Datei, interpretiert, es sei denn, die `File` -Attribut festgelegt ist. Wenn dieser Schlüssel nicht vorhanden ist, `Property` ist nicht festgelegt.|  
|`Value`|Dies ist optional. Der Name des Registrierungswerts abgerufen werden soll. Der Standardwert ist den Text des Standardwerts zurückgegeben. `Value` eine Zeichenfolge muss sein.|  
|`FileName`|Dies ist optional. Der Name einer Datei. Wenn angegeben, wird davon ausgegangen, dass der Wert aus dem Registrierungsschlüssel einen Verzeichnispfad ein, und dieser Name wird an ihn angefügt. Wenn nicht angegeben, wird angenommen, dass der Rückgabewert aus der Registrierung den vollständigen Pfad zu einer Datei enthalten.|  
|`SearchDepth`|Dies ist optional. Die Tiefe am dem Unterordner für die angegebene Datei gesucht werden soll. Die Suche ist die Tiefe. Der Standardwert ist 0 (null) und die Suche zum Ordner obersten Ebene, die durch den Registrierungsschlüssel-Wert angegeben werden schränkt.|  

## <a name="remarks"></a>Hinweise  
 Untergeordneten Elemente `InstallChecks` definieren Sie die auszuführenden Tests, die sie nicht ausgeführt. Um die Tests auszuführen, müssen Sie erstellen `Command` Elemente unterhalb der `Commands` Element.  

## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, die `InstallChecks` Element, wie er wird verwendet, in der Produktdatei für die [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  

```xml  
<InstallChecks>  
    <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />  
    <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />  
</InstallChecks>  
```  

## <a name="installconditions"></a>InstallConditions  
 Wenn `InstallChecks` werden ausgewertet, erzeugen sie Eigenschaften. Die Eigenschaften werden dann verwendet, indem `InstallConditions` zu bestimmen, ob ein Paket installieren, zu umgehen oder fehlschlagen sollte. Die folgende Tabelle enthält die `InstallConditions`:  

|||  
|-|-|  
|`FailIf`|Wenn alle `FailIf` ergibt die Bedingung "true", kann das Paket nicht ausgeführt. Die restlichen Bedingungen wird nicht ausgewertet werden.|  
|`BypassIf`|Wenn alle `BypassIf` ergibt die Bedingung "true", das Paket wird umgangen werden. Die restlichen Bedingungen wird nicht ausgewertet werden.|  

## <a name="predefined-properties"></a>Vordefinierte Eigenschaften  
 Die folgende Tabelle enthält die `BypassIf` und `FailIf` Elemente:  

|Eigenschaft|Hinweise|Mögliche Werte|  
|--------------|-----------|---------------------|  
|`Version9X`|Die Versionsnummer des Betriebssystems Windows 9 X.|4.10 = Windows 98|  
|`VersionNT`|Die Versionsnummer des Betriebssystems Windows NT-basierten.|"Major.minor.Servicepack"<br /><br /> 5.0 = Windows 2000<br /><br /> 5.1.0 = Windows XP<br /><br /> 5.1.2 = Windows XP Professional SP2<br /><br /> 5.2.0 = WindowsServer 2003|  
|`VersionNT64`|Die Versionsnummer eines 64-Bit-Windows NT-basierten Windows-Betriebssystems.|Wie bereits zuvor erwähnt.|  
|`VersionMsi`|Die Versionsnummer des Windows Installer-Diensts.|2.0 = Windows Installer 2.0|  
|`AdminUser`|Gibt an, ob ein Benutzer über Administratorrechte auf einem Windows NT-basierten Betriebssystem verfügt.|0 = keine Administratorrechte<br /><br /> 1 = Administratorrechte|  

 Um die Installation auf einem Computer unter Windows 95 zu blockieren, verwenden Sie z. B. Code wie den folgenden:  

```xml  
<!-- Block install on Windows 95 -->  
    <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatform"/>  
```  

## <a name="see-also"></a>Siehe auch  
 [\<Befehle >-Element](../deployment/commands-element-bootstrapper.md)   
 [Referenz zum Produkt- und Paketschema](../deployment/product-and-package-schema-reference.md)