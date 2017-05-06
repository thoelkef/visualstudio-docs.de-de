---
title: "Verpacken und Bereitstellen von SharePoint-L&#246;sungen"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Bereitstellen [SharePoint-Entwicklung in Visual Studio]"
  - "Packen [SharePoint-Entwicklung in Visual Studio]"
  - "SharePoint-Entwicklung in Visual Studio, Packen und Bereitstellen"
ms.assetid: 39072fa7-9f94-49c0-9a67-cbcce0147e61
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Verpacken und Bereitstellen von SharePoint-L&#246;sungen
  Normalerweise wird eine SharePoint\-Lösung mithilfe einer Lösungspaketdatei \(.wsp\) auf einem SharePoint\-Server bereitgestellt.  Sie können Visual Studio verwenden, um die SharePoint\-Projektelemente in Funktionen zu organisieren und ein Paket zu erstellen, um die SharePoint\-Funktionen bereitzustellen.  
  
 Dieses Thema enthält folgende Informationen:  
  
-   [Erstellen von Funktionen und Paketen](#Creating)  
  
-   [Toolunterstützung für Funktionen und Verpacken](#Tools)  
  
-   [Bereitstellen von SharePoint\-Lösungen](#Deploying)  
  
-   [Bereitstellen von Dateien in SharePoint\-Lösungen](#DeployingFiles)  
  
##  <a name="Creating"></a> Erstellen von Funktionen und Paketen  
 Sie können Visual Studio verwenden, um verwandte SharePoint\-Elemente in eine *Funktion* zu gruppieren.  Eine Funktion für eine Kontaktlistendefinition kann beispielsweise die Listeninstanz und die Listendefinition einschließen.  Zu Bereitstellungszwecken können Sie diese zwei Elemente in einer einzelnen Funktion kombinieren.  Weitere Informationen zu Funktionen, Sie finden. [Baustein: Funktionen](http://go.microsoft.com/fwlink/?LinkID=169183)  
  
 Danach können Sie ein SharePoint\-Lösungspaket \(.wsp\) erstellen, um mehrere Funktionen, Websitedefinitionen, Assemblys und andere Dateien in einem einzelnen Paket zu bündeln, das die Dateien in einem Format speichert, das in SharePoint zum Bereitstellen der Dateien auf dem Server erforderlich ist.  Weitere Informationen finden Sie unter [Baustein: Projektmappen](http://go.microsoft.com/fwlink/?LinkID=169186).  
  
##  <a name="Tools"></a> Toolunterstützung für Funktionen und Verpacken  
 Mit den SharePoint\-Entwicklungstools in Visual Studio können Sie die SharePoint\-Dateien zur einfacheren Bereitstellung schnell in Funktionen und Lösungspakete organisieren.  Die folgenden Tools können zum Konfigurieren des Funktions\- und Lösungspakets verwendet werden.  
  
-   Funktions\-Designer und Paket\-Designer.  
  
-   Paket\-Explorer, ein Toolfenster.  
  
-   Projektmappen\-Explorer.  
  
### Funktions\-Designer und Paket\-Designer  
 Mit dem Funktions\-Designer können Sie Funktionen erstellen, Bereiche festlegen und andere Funktionen als Abhängigkeiten markieren.  Der Designer zeigt auch die endgültige XML\-Datei an, die die einzelnen Funktionen beschreibt.  Weitere Informationen finden Sie unter [Erstellen von SharePoint-Funktionen](../sharepoint/creating-sharepoint-features.md).  
  
 Wenden Sie die Funktion auf eine bestimmte Website oder eine Gruppe von Websites an, indem Sie den *Bereich* im Funktions\-Designer festlegen.  Wenn eine Funktion für eine einzelne Website aktiviert wird, funktioniert diese Funktion nur auf dieser bestimmten Website.  Wenn eine Funktion für eine Websiteauflistung aktiviert wird, gelten die Elemente in der Funktion für die gesamte Websiteauflistung.  Weitere Informationen finden Sie unter [Element\-Bereich](http://go.microsoft.com/fwlink/?LinkID=169189).  
  
 Wenn die Funktion von anderen Funktionen abhängig ist, können Sie eine *Abhängigkeit bei der Funktionsaktivierung* festlegen, um die abhängigen Funktionen zu markieren, bevor Sie die Funktion verfügbar machen.  Durch eine Abhängigkeit bei der Funktionsaktivierung wird überprüft, ob die abhängigen Funktionen bereits in diesem Bereich aktiviert sind.  Weitere Informationen finden Sie unter [Aktivierungs\-Abhängigkeiten und Bereich](http://go.microsoft.com/fwlink/?LinkID=169190).  
  
 Im Paket\-Designer können Sie SharePoint\-Elemente in einem Lösungspaket gruppieren und festlegen, ob der Webserver während der Bereitstellung zurückgesetzt werden soll.  Der Bereitstellungsservertyp wird im Fenster **Eigenschaften** festgelegt.  Der Designer generiert auch die XML\-Datei, die den Paketinhalt beschreibt.  Weitere Informationen finden Sie unter [Erstellen von SharePoint-Lösungspaketen](../sharepoint/creating-sharepoint-solution-packages.md).  
  
 Während der Bereitstellung wird der IIS\-Dienst \(Internet Information Services, Internetinformationsdienste\) beendet, um die Projektmappendateien auf den SharePoint\-Server zu kopieren.  Mit dem Paket\-Designer in Visual Studio können Sie auswählen, ob der Webserver neu gestartet werden soll.  Verwenden Sie das Fenster **Eigenschaften**, um festzulegen, ob die Lösung auf einem Front\-End\-Webserver oder einem Anwendungsserver bereitgestellt wird.  Weitere Informationen finden Sie unter [Projektmappen\-Element \(Projektmappe\)](http://go.microsoft.com/fwlink/?LinkID=169191).  
  
### Paket\-Explorer  
 In Ergänzung zum Funktions\-Designer und zum Paket\-Designer können Sie den Paket\-Explorer verwenden, um die SharePoint\-Dateien in Funktionen und Pakete zu gruppieren.  Außerdem können Sie die hierarchische Ansicht des Pakets, der Funktionen, der SharePoint\-Projektelemente und der Dateien anzeigen.  Der Paket\-Explorer ist ein Toolfenster, mit dem Sie die folgenden Aufgaben durchführen können:  
  
-   Öffnen von SharePoint\-Projektelementen und \-Dateien.  
  
-   Verschieben von SharePoint\-Projektelementen per Drag & Drop von einer Funktion in eine andere.  
  
-   Verschieben von SharePoint\-Projektelementen und \-Funktionen per Drag & Drop von einem Paket in ein anderes.  
  
-   Hinzufügen einer neuen Funktion zu einem Paket.  
  
-   Öffnen einer Funktion oder des Paket\-Designers.  
  
-   Überprüfen von Funktionen und Paketen.  
  
 Die SharePoint\-Entwicklungstools in Visual Studio verfügen über Gültigkeitsprüfungsregeln, mit denen die korrekte Formatierung eines Lösungspakets überprüft werden kann.  Zudem überprüfen die Regeln, ob die WSP\-Lösungsdatei erfolgreich auf einem SharePoint\-Server bereitgestellt und aktiviert werden kann.  Weitere Informationen zum XML\-Schema für Funktionen, Sie finden [Kennzeichnen von Schemas](http://go.microsoft.com/fwlink/?LinkID=169192).  
  
 Sie können dem SharePoint\-Projektsystem benutzerdefinierte Funktions\- und Paketvalidierungsregeln hinzufügen.  Weitere Informationen finden Sie unter [How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).  
  
 Weitere Informationen zum Paket\-Explorer finden Sie unter [Gewusst wie: Hinzufügen und Entfernen von Funktionen und Elementen in einem Paket mit dem Paket-Explorer](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).  
  
### Projektmappen\-Explorer  
 Sie können den Projektmappen\-Explorer verwenden, um zu den Dateien des SharePoint\-Projekts zu navigieren und diese zu öffnen.  Verwenden Sie das Kontextmenü im Projektmappen\-Explorer, um Funktionen, Funktionsereignisempfänger und Funktionsressourcen hinzuzufügen.  Außerdem können Sie Funktions\-Designer und Paket\-Designer öffnen, um die Funktionen und Pakete zur Bereitstellung zu konfigurieren.  
  
##  <a name="Deploying"></a> Bereitstellen von SharePoint\-Lösungen  
 Nachdem Sie die Funktionen und Pakete in Visual Studio angepasst haben, können Sie eine WSP\-Datei erstellen, die auf SharePoint\-Servern bereitgestellt werden soll.  Sie können Visual Studio verwenden, um die WSP\-Datei nur auf dem SharePoint\-Server auf dem Entwicklungscomputer zu debuggen und zu testen.  Weitere Informationen darüber, wie die SharePoint\-Lösungen auf einem Remotewebserver SharePoint\-Server, finden Sie bereitstellen [Bereitstellen einer Projektmappe](http://go.microsoft.com/fwlink/?LinkID=169194).  
  
 Sie können auch die Bereitstellungsschritte auf dem Entwicklungscomputer anpassen.  Weitere Informationen finden Sie unter [Bereitstellen, Veröffentlichen und Aktualisieren von SharePoint-Lösungspaketen](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).  
  
##  <a name="DeployingFiles"></a> Bereitstellen von Dateien in SharePoint\-Lösungen  
 Wenn Sie der SharePoint\-Lösung ein SharePoint\-Projektelement hinzufügen, sind in der Regel alle erforderlichen Dateien enthalten.  Dateien, die kompiliert werden können \(Codedateien\), werden in die Ausgabeassembly der Projektmappe eingebaut.  Sie müssen möglicherweise jedoch nicht kompilierbare Dateien, z. B. XML\-, TXT\- oder Ressourcendateien, zu einem SharePoint\-Projekt hinzufügen.  Diese Dateien werden nicht automatisch in die Projektmappe verpackt.  Fügen Sie die Dateien einem zugeordneten Ordner oder einem SharePoint\-Projektelement hinzu, um sicherzustellen, dass sie verpackt werden.  
  
 Wenn die Projektmappe bereitgestellt wird, werden die den zugeordneten Ordnern hinzugefügten Dateien automatisch in die SharePoint Struktur kopiert.  Einem SharePoint\-Projektelement hinzugefügte Dateien werden an dem Speicherort bereitgestellt, der in der Eigenschaft **Bereitstellungsort** für jede Datei angegeben wird. Der Speicherort wird teilweise auf Grundlage der Eigenschaft **Bereitstellungstyp** festgelegt.  Standardmäßig ist der Eigenschaftswert **Bereitstellungstyp** auf **NoDeployment** festgelegt. Dieser Wert weist darauf hin, dass die Datei nicht mit der Projektmappe bereitgestellt wird.  Sie müssen einen anderen Wert für die Eigenschaft festlegen, um die Datei in das Paket einzuschließen.  
  
 Um beispielsweise einem SharePoint\-Projekt eine XML\-Datei hinzuzufügen, führen Sie eine der folgenden Aktionen aus:  
  
-   Fügen Sie dem Projekt einen Ordner hinzu, der SharePoint "Layouts" zugeordnet ist.  Dadurch wird im **Projektmappen\-Explorer** ein Ordner mit dem Namen **Layouts** erstellt, in dem sich ein Unterordner für das Projekt befindet.  Fügen Sie dem neuen Unterordner die XML\-Datei hinzu.  Standardmäßig wird die Datei im SharePoint\-Dateisystem bereitgestellt unter ..\\TEMPLATE\\LAYOUTS\\*Folder Name*\\ bereitgestellt.  Weitere Informationen zum Hinzufügen von zugeordneten Ordnern finden Sie unter [Gewusst wie: Hinzufügen und Entfernen zugeordneter Ordner](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
-   Fügen Sie dem Ordner eines SharePoint\-Projektelements die XML\-Datei hinzu, und ändern Sie dann die Eigenschaft **Bereitstellungstyp** der XML\-Datei von **NoDeployment** in eine andere Einstellung, z. B. in **RootFile** oder **ElementFile**.  Die entsprechende Einstellung **Bereitstellungstyp** hängt von der Datei und dem Projekt ab.  Weitere Informationen zu den Eigenschafteneinstellungen für **Bereitstellungstyp** finden Sie unter [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md).  
  
 Wenn eine hinzugefügte Datei in der Projektmappe für kein bestimmtes Projekt gilt, können Sie der Projektmappe ein leeres SharePoint Projekt hinzufügen und dann die weiteren Dateien hinzufügen.  Eine andere Alternative zum Bereitstellen von Dateien in SharePoint, besonders zur Inhaltsdatenbank, besteht darin, dem Projekt ein Modul hinzuzufügen und diesem dann die Dateien hinzuzufügen.  Weitere Informationen finden Sie unter [Verwenden von Modulen zum Einfügen von Dateien in die Projektmappe](../sharepoint/using-modules-to-include-files-in-the-solution.md).  
  
## Siehe auch  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [Erstellen und Debuggen von SharePoint-Lösungen](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  