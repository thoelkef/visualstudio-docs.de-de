---
title: Erstellen von Bootstrapperpaketen | Microsoft Docs
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
- deploying applications [Visual Studio], prerequisites
- deploying applications [Visual Studio], custom prerequisites
- prerequisites, custom
- RedistList file
- custom prerequisites
- redistributables list
ms.assetid: ba1a785b-693d-446b-bcae-b88cadee73d1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 794d569504e46627c9387046b381fdb843a7818e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="creating-bootstrapper-packages"></a>Erstellen von Bootstrapperpaketen
Das Setupprogramm ist ein generisches Installationsprogramm, das für die Ermittlung und die Installation von weitervertreibbaren Komponenten wie Windows Installer (MSI-Format) und ausführbaren Programmen konfiguriert werden kann. Das Installationsprogramm wird auch als Bootstrapper bezeichnet. Der Bootstrapper wird mithilfe einer Reihe von XML-Manifesten programmiert, mit denen die Metadaten zur Verwaltung der Komponenteninstallation angegeben werden.  
  
 Der Bootstrapper ermittelt zunächst, ob erforderliche Komponenten bereits installiert sind. Ist dies nicht der Fall, werden vom Bootstrapper die Lizenzverträge angezeigt. Nachdem der Endbenutzer die Lizenzverträge akzeptiert hat, beginnt die Installation der erforderlichen Komponenten. Wurden alle erforderlichen Komponenten ermittelt, wird direkt das Installationsprogramm der Anwendung gestartet.  
  
## <a name="creating-custom-packages"></a>Erstellen von benutzerdefinierten Paketen  
 Sie können die Manifeste mit dem XML-Editor in Visual Studio generieren. Weitere Informationen finden Sie unter [How to: Create a Package Manifest](../deployment/how-to-create-a-package-manifest.md) und [How to: Create a Product Manifest](../deployment/how-to-create-a-product-manifest.md). Ein Beispiel für das Erstellen eines Bootstrapperpakets finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Bootstrappers zum Anzeigen einer Datenschutzeingabeaufforderung](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md).  
  
 Zur Erstellung eines Bootstrapperpakets muss die weitervertreibbare Komponente in Form einer EXE- oder MSI-Datei im Bootstrapper Manifest-Generator angegeben werden. Dann werden vom Bootstrapper Manifest-Generator die folgenden Dateien erstellt:  
  
-   Das Produktmanifest, product.xml, das alle sprachneutralen Metadaten für das Paket enthält. Es enthält Metadaten, die für alle lokalisierten Versionen der verteilbaren Komponente gleich sind.  
  
-   Das Paketmanifest, package.xml, das sprachspezifische Metadaten und in der Regel auch lokalisierte Fehlermeldungen enthält. Eine Komponente benötigt für jede lokalisierte Version dieser Komponente mindestens ein Paketmanifest.  
  
 Nachdem diese Dateien erstellt wurden, platzieren Sie die Produktmanifestdatei in einen entsprechend benannten Ordner für den benutzerdefinierten Bootstrapper. Die Paketmanifestdatei muss in einem Ordner, der dem Gebietsschema entsprechend benannt wurde, abgelegt werden. Wenn die Paketmanifestdatei z. B. für die Neuverteilung in englischer Sprache vorgesehen ist, legen Sie die Datei in einen Ordner mit der Bezeichnung "en" ab. Wiederholen Sie diesen Prozess für jedes Gebietsschema, z. B. "ja" für Japanisch und "de" für Deutsch. Das abschließende benutzerdefinierte Bootstrapperpaket könnte beispielsweise über die folgende Ordnerstruktur verfügen.  
  
 `CustomBootstrapperPackage`  
  
 `product.xml`  
  
 `CustomBootstrapper.msi`  
  
 `de`  
  
 `eula.rtf`  
  
 `package.xml`  
  
 `en`  
  
 `eula.rtf`  
  
 `package.xml`  
  
 `ja`  
  
 `eula.rtf`  
  
 `package.xml`  
  
 Schließlich kopieren Sie die verteilbaren Dateien in den Bootstrapperordner. Weitere Informationen finden Sie unter [How to: Create a Localized Bootstrapper Package](../deployment/how-to-create-a-localized-bootstrapper-package.md).  
  
```  
\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages  
```  
  
 oder  
  
```  
\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages  
```  
  
 Sie können auch den Speicherort des Bootstrapperordners mithilfe des Werts **Pfad** im folgenden Registrierungsschlüssel bestimmen:  
  
```  
HKLM\Software\Microsoft\GenericBootstrapper\11.0  
```  
  
 Auf 64-Bit-Systemen verwenden Sie den folgenden Registrierungsschlüssel:  
  
```  
HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper\11.0  
```  
  
 Jede verteilbare Komponente wird unter dem Paketverzeichnis in einem eigenen Unterordner angezeigt. Das Produktmanifest und die verteilbaren Dateien werden dann in diesem Unterordner abgelegt. Lokalisierte Versionen der Komponente und Paketmanifeste werden in Unterordner eingefügt, die entsprechend dem Kulturnamen benannt sind.  
  
 Nachdem diese Dateien in den Bootstrapperordner kopiert wurden, wird das Bootstrapperpaket in Visual Studio automatisch im Dialogfeld für die erforderlichen Komponenten angezeigt. Wird das benutzerdefinierte Bootstrapperpaket nicht angezeigt, schließen Sie das Dialogfeld für die erforderlichen Komponenten, und öffnen Sie es erneut. Weitere Informationen finden Sie unter [Prerequisites Dialog Box](../ide/reference/prerequisites-dialog-box.md).  
  
 In der folgenden Tabelle werden die Eigenschaften angezeigt, die automatisch vom Bootstrapper eingetragen werden.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|ApplicationName|Der Name der Anwendung.|  
|ProcessorArchitecture|Der Prozessor und die Bits pro Wort für die Plattform, auf die eine ausführbare Datei zielt. Folgende Werte sind gültig:<br /><br /> -Intel<br />-IA64<br />-AMD64|  
|[Version9x](https://msdn.microsoft.com/en-us/library/aa372490\(v=vs.140\).aspx)|Die Versionsnummer für Microsoft Windows 95, Windows 98 oder Windows ME. Die Syntax der Version lautet "Major.Minor.ServicePack".|  
|[VersionNT](https://msdn.microsoft.com/en-us/library/aa372495\(v=vs.140\).xaspx)|Die Versionsnummer für Windows NT, Windows 2000, Windows XP, Windows Vista, Windows Server 2008 oder Windows 7. Die Syntax der Version lautet "Major.Minor.ServicePack".|  
|[VersionMSI](https://msdn.microsoft.com/en-us/library/aa372493\(v=vs.140\).aspx)|Die Version der Windows Installer-Assembly (msi.dll), die während der Installation ausgeführt wird.|  
|[AdminUser](https://msdn.microsoft.com/en-us/library/aa367545\(v=vs.140\).aspx)|Diese Eigenschaft wird festgelegt, wenn der Benutzer über Administratorrechte verfügt. Gültige Werte sind "true" und "false".|  
|InstallMode|Der Installationsmodus gibt an, von welchem Speicherort die Komponente installiert werden muss. Folgende Werte sind gültig:<br /><br /> -HomeSite: Voraussetzungen werden von der Website des Anbieters installiert.<br />-SpecificSite: Voraussetzungen werden von dem Speicherort installiert, die Sie auswählen.<br />-SameSite: Voraussetzungen sind vom gleichen Speicherort wie die Anwendung installiert.|  
  
## <a name="separating-redistributables-from-application-installations"></a>Trennen von weitervertreibbaren Komponenten von Anwendungsinstallationen  
 Sie können die Bereitstellung von verteilbaren Dateien in Setupprojekten auch deaktivieren. Erstellen Sie hierzu im Ordner "RedistList" im Verzeichnis von .NET Framework eine verteilbare Liste:  
  
 `%ProgramFiles%\Microsoft.NET\RedistList`  
  
 Die verteilbare Liste ist eine XML-Datei, die entsprechend dem folgenden Format benannt wird: *Company Name*.*Component Name*.RedistList.xml. Beispiel: Wenn die Komponente "Datawidgets" heißt und von der Firma Acme stammt, nennen Sie die Datei "Acme.DataWidgets.RedistList.xml". Der Inhalt der verteilbaren Liste könnte in etwa so aussehen:  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
<FileList Redist="Acme.DataWidgets" >  
<File AssemblyName="Acme.DataGrid" Version="1.0.0.0" PublicKeyToken="b03f5f7f11d50a3a" Culture="neutral" ProcessorArchitecture="MSIL" InGAC="true" />  
</FileList>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Installieren von erforderlichen Komponenten mit einer ClickOnce-Anwendung](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Voraussetzungen (Dialogfeld)](../ide/reference/prerequisites-dialog-box.md)   
 [Produkt- und Paketschemareferenz](../deployment/product-and-package-schema-reference.md)   
 [Verwenden des Visual Studio 2005-Bootstrappers zum Starten der Installation](http://go.microsoft.com/fwlink/?LinkId=107537)