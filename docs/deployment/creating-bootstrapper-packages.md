---
title: Erstellen von Bootstrapperpaketen
ms.custom: ''
ms.date: 05/02/2018
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
ms.openlocfilehash: d3cc80a6ca29583fdc445b507aeb8f87267459d8
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572724"
---
# <a name="create-bootstrapper-packages"></a>Erstellen von Bootstrapperpaketen
Das Setupprogramm ist ein generisches Installationsprogramm, das für die Ermittlung und die Installation von weitervertreibbaren Komponenten wie Windows Installer (MSI-Format) und ausführbaren Programmen konfiguriert werden kann. Das Installationsprogramm wird auch als Bootstrapper bezeichnet. Der Bootstrapper wird mithilfe einer Reihe von XML-Manifesten programmiert, mit denen die Metadaten zur Verwaltung der Komponenteninstallation angegeben werden.  Jede verteilbare Komponente, oder eine erforderliche Komponente, angezeigt, die der **Voraussetzungen** im Dialogfeld für ClickOnce ist ein Bootstrapperpaket. Bei einem Bootstrapperpaket handelt es sich um eine Gruppe von Verzeichnissen und Dateien, die Manifestdateien enthalten, mit denen beschrieben wird, wie die erforderliche Komponente installiert werden muss. 
  
Der Bootstrapper ermittelt zunächst, ob erforderliche Komponenten bereits installiert sind. Ist dies nicht der Fall, werden vom Bootstrapper die Lizenzverträge angezeigt. Nachdem der Endbenutzer die Lizenzverträge akzeptiert hat, beginnt die Installation der erforderlichen Komponenten. Wurden alle erforderlichen Komponenten ermittelt, wird direkt das Installationsprogramm der Anwendung gestartet.  
  
## <a name="create-custom-bootstrapper-packages"></a>Erstellen Sie benutzerdefinierte Bootstrapperpakete  
Sie können die Manifeste Bootstrapper generieren, indem Sie mit der XML-Editor in Visual Studio. Ein Beispiel zum Erstellen eines Bootstrapperpakets finden Sie unter [Exemplarische Vorgehensweise: erstellen ein benutzerdefiniertes Bootstrappers mit einer datenschutzeingabeaufforderung](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md).  
  
Zum Erstellen eines Bootstrapperpakets Sie zum Erstellen eines Produktmanifests haben und für jede lokalisierte Version einer Komponente, wie gut ein Paketmanifest.
  
* Das Produktmanifest, *product.xml*, alle sprachneutralen Metadaten für das Paket enthält. Es enthält Metadaten, die für alle lokalisierten Versionen der verteilbaren Komponente gleich sind.  Um diese Datei zu erstellen, finden Sie unter [Vorgehensweise: Erstellen eines Produktmanifests](../deployment/how-to-create-a-product-manifest.md).
  
* Das Paketmanifest *"Package.xml"*, enthält sprachspezifische Metadaten; es wird in der Regel lokalisierte Fehlermeldungen enthält. Eine Komponente benötigt für jede lokalisierte Version dieser Komponente mindestens ein Paketmanifest. Um diese Datei zu erstellen, finden Sie unter [Vorgehensweise: Erstellen eines Paketmanifests](../deployment/how-to-create-a-package-manifest.md).
  
Nachdem diese Dateien erstellt wurden, platzieren Sie die Produktmanifestdatei in einen entsprechend benannten Ordner für den benutzerdefinierten Bootstrapper. Die Paketmanifestdatei muss in einem Ordner, der dem Gebietsschema entsprechend benannt wurde, abgelegt werden. Wenn die Paketmanifestdatei z. B. für die Neuverteilung in englischer Sprache vorgesehen ist, legen Sie die Datei in einen Ordner mit der Bezeichnung "en" ab. Wiederholen Sie diesen Prozess für jedes Gebietsschema, z. B. "ja" für Japanisch und "de" für Deutsch. Das abschließende benutzerdefinierte Bootstrapperpaket könnte beispielsweise über die folgende Ordnerstruktur verfügen.  

    ```
    CustomBootstrapperPackage
      product.xml
      CustomBootstrapper.msi
      de
        eula.rtf
        package.xml
      en
        eula.rtf
        package.xml
      ja
        eula.rtf
        package.xml
    ```
  
Kopieren Sie anschließend die verteilbaren Dateien in den Bootstrapperordner. Weitere Informationen finden Sie unter [How to: Create a Localized Bootstrapper Package](../deployment/how-to-create-a-localized-bootstrapper-package.md).
 
    *\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
    
oder  
    
    *\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
  
Sie können auch den Speicherort des Bootstrapperordners mithilfe des Werts **Pfad** im folgenden Registrierungsschlüssel bestimmen:  
  
    *HKLM\Software\Microsoft\GenericBootstrapper\11.0*
  
Verwenden Sie auf 64-Bit-Systemen den folgenden Registrierungsschlüssel:  
  
    *HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper\11.0*
  
Jede verteilbare Komponente wird unter dem Paketverzeichnis in einem eigenen Unterordner angezeigt. Das Produkt Produktmanifest und die verteilbaren Dateien müssen in diesem Unterordner abgelegt werden. Lokalisierte Versionen der Komponente und Paketmanifeste müssen in Unterordnern, die entsprechend dem Kulturnamen benannt abgelegt werden.  
  
Nachdem diese Dateien in den Bootstrapperordner kopiert wurden, wird das Bootstrapperpaket automatisch in Visual Studio **Voraussetzungen** (Dialogfeld). Wenn das benutzerdefinierte Bootstrapperpaket nicht angezeigt wird, schließen und öffnen Sie dann erneut die **Voraussetzungen** (Dialogfeld). Weitere Informationen finden Sie unter [Dialogfeld "Erforderliche Komponenten"](../ide/reference/prerequisites-dialog-box.md).  
  
In der folgenden Tabelle werden die Eigenschaften angezeigt, die automatisch vom Bootstrapper eingetragen werden.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|ApplicationName|Der Name der Anwendung.|  
|ProcessorArchitecture|Der Prozessor und die Bits pro Wort für die Plattform, auf die eine ausführbare Datei zielt. Folgende Werte sind gültig:<br /><br /> -Intel<br />-IA64<br />-AMD64|  
|[Version9x](https://msdn.microsoft.com/en-us/library/aa372490\(v=vs.140\).aspx)|Die Versionsnummer für Microsoft Windows 95, Windows 98 oder Windows ME. Die Syntax der Version lautet "Major.Minor.ServicePack".|  
|[VersionNT](https://msdn.microsoft.com/en-us/library/aa372495\(v=vs.140\).aspx)|Die Versionsnummer für Windows NT, Windows 2000, Windows XP, Windows Vista, Windows Server 2008 oder Windows 7. Die Syntax der Version lautet "Major.Minor.ServicePack".|  
|[VersionMSI](https://msdn.microsoft.com/en-us/library/aa372493\(v=vs.140\).aspx)|Die Version der Windows Installer-Assembly (msi.dll), die während der Installation ausgeführt wird.|  
|[AdminUser](https://msdn.microsoft.com/en-us/library/aa367545\(v=vs.140\).aspx)|Diese Eigenschaft wird festgelegt, wenn der Benutzer über Administratorrechte verfügt. Gültige Werte sind "true" und "false".|  
|InstallMode|Der Installationsmodus gibt an, von welchem Speicherort die Komponente installiert werden muss. Folgende Werte sind gültig:<br /><br /> -HomeSite: Voraussetzungen werden von der Website des Anbieters installiert.<br />-SpecificSite: Voraussetzungen werden von dem Speicherort installiert, die Sie auswählen.<br />-SameSite: Voraussetzungen sind vom gleichen Speicherort wie die Anwendung installiert.|  
  
## <a name="separating-redistributables-from-application-installations"></a>Trennen von weitervertreibbaren Komponenten von Anwendungsinstallationen  
Sie können die Bereitstellung von verteilbaren Dateien in Setupprojekten auch deaktivieren. Erstellen Sie hierzu im Ordner "RedistList" im Verzeichnis von .NET Framework eine verteilbare Liste:  
  
`%ProgramFiles%\Microsoft.NET\RedistList`  
  
Die verteilbare Liste ist eine XML-Datei, die entsprechend dem folgenden Format benannt wird: *Company Name*.*Component Name*.RedistList.xml. Also z. B. wenn die Komponente versucht, die von der Firma Acme Datawidgets aufgerufen wird, verwenden Sie *Namen Acme.DataWidgets.RedistList.xml*. Der Inhalt der verteilbaren Liste könnte in etwa so aussehen:  
  
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
