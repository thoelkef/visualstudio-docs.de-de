---
title: "Verpacken und Bereitstellen von SharePoint-Lösungen | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- packaging [SharePoint development in Visual Studio]
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, packaging and deploying
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: e25d0829305f414712590296b6121d62583736a2
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="packaging-and-deploying-sharepoint-solutions"></a>Verpacken und Bereitstellen von SharePoint-Lösungen
  In der Regel ist eine SharePoint-Lösung mithilfe einer Lösung-Paketdatei (.wsp) auf einer SharePoint-Server bereitgestellt. Sie können Visual Studio verwenden, um die SharePoint-Projektelemente in Funktionen zu organisieren und erstellen Sie ein Paket zum Bereitstellen von SharePoint-Funktionen.  
  
 Dieses Thema enthält folgende Informationen:  
  
-   [Erstellen von Funktionen und Pakete](#Creating)  
  
-   [Funktions- und Verpacken Toolsupport](#Tools)  
  
-   [Bereitstellen von SharePoint-Lösungen](#Deploying)  
  
-   [Bereitstellen von Dateien in SharePoint-Lösungen](#DeployingFiles)  
  
##  <a name="Creating"></a>Erstellen von Funktionen und Pakete  
 Sie können Visual Studio verwenden, zum Gruppieren von verwandten SharePoint-Elemente in einem *Feature*. Eine Funktion für eine Listendefinition Kontakte gehören z. B. die Listeninstanz und die Listendefinition. Sie können diese beiden Elemente in eine einzelne Funktion für die Bereitstellung kombinieren. Weitere Informationen zu Funktionen finden Sie unter [Baustein: Funktionen](http://go.microsoft.com/fwlink/?LinkID=169183).  
  
 Als Nächstes können Sie eine SharePoint-Lösungspaket (.wsp) um mehrere Funktionen, Websitedefinitionen, Assemblys und andere Dateien in einem einzelnen Paket zu bündeln erstellen, dem die Dateien, in einem Format, das von SharePoint benötigt gespeichert, um die Dateien auf dem Server bereitstellen. Weitere Informationen finden Sie unter [Baustein: Lösungen](http://go.microsoft.com/fwlink/?LinkID=169186).  
  
##  <a name="Tools"></a>Funktions- und Verpacken Toolsupport  
 Die SharePoint-Entwicklungstools können in Visual Studio Sie um die SharePoint-Dateien schnell in Funktionen und Lösungspakete für die Bereitstellung einfacher zu organisieren. Sie können die folgenden Tools verwenden, so konfigurieren Sie das Paket Funktions- und Lösung.  
  
-   Funktions-Designer und Paket-Designer.  
  
-   Paket-Explorer, ein Toolfenster.  
  
-   Projektmappen-Explorer.  
  
### <a name="feature-designer-and-package-designer"></a>Funktions-Designer und Paket-Designer  
 Sie können Funktionen erstellen, Bereiche festlegen und andere Funktionen wie Abhängigkeiten zu markieren, mit dem Funktions-Designer. Der Designer zeigt auch die endgültige XML-Datei, die einzelnen Funktionen beschreibt. Weitere Informationen finden Sie unter [Erstellen von SharePoint-Funktionen](../sharepoint/creating-sharepoint-features.md).  
  
 Wenden Sie die Funktion auf eine bestimmte Website oder eine Gruppe von Websites durch Festlegen seiner *Bereich* im Funktions-Designer. Wenn eine Funktion für eine einzelne Website aktiviert ist, funktioniert die Funktion nur in dieser bestimmten Website. Wenn eine Funktion für eine Websitesammlung aktiviert ist, gelten die Elemente in der Funktion für die gesamte Websitesammlung. Weitere Informationen finden Sie unter [Gültigkeitsbereich Elements](http://go.microsoft.com/fwlink/?LinkID=169189).  
  
 Wenn Ihr Feature von anderen Features abhängig ist, legen Sie eine *feature Aktivierung Abhängigkeit* um die abhängigen Funktionen zu markieren, bevor Ihr Feature verfügbar gemacht. Eine Aktivierung funktionsabhängigkeit wird überprüft, ob die abhängigen Funktionen bereits in diesem Gültigkeitsbereich aktiviert werden. Weitere Informationen finden Sie unter [Aktivierung Abhängigkeiten und Bereich](http://go.microsoft.com/fwlink/?LinkID=169190).  
  
 Im Paket-Designer können Sie SharePoint-Elemente in einem Lösungspaket gruppieren und konfigurieren Sie, ob der Webserver während der Bereitstellung zurückgesetzt. Verwenden Sie zum Festlegen der Bereitstellungsservertyp der **Eigenschaften** Fenster. Der Designer generiert auch die XML-Datei, die den Paketinhalt beschreibt. Weitere Informationen finden Sie unter [Erstellen von SharePoint-Lösungspakete](../sharepoint/creating-sharepoint-solution-packages.md).  
  
 Während der Bereitstellung wird der Internetinformationsdienste (Internet Information Services, IIS)-Dienst beendet, um die Projektmappendateien an den SharePoint-Server zu kopieren. Mithilfe der Paket-Designer in Visual Studio können Sie auswählen, ob der Webserver neu gestartet werden soll. So konfigurieren, wenn die Projektmappe auf einem Front-End-Webserver oder einem Anwendungsserver bereitgestellt wurde, verwenden Sie die **Eigenschaften** Fenster. Weitere Informationen finden Sie unter [Lösungselement (Lösung)](http://go.microsoft.com/fwlink/?LinkID=169191).  
  
### <a name="packaging-explorer"></a>Paket-Explorer  
 Um der Funktion und Paket-Designer zu ergänzen, können Sie dem Paket-Explorer, um die SharePoint-Dateien zu Funktionen und Pakete zu gruppieren. Darüber hinaus sehen Sie die hierarchische Ansicht des Pakets, der Funktionen, SharePoint-Projekts Objekte und Dateien. Die Paket-Explorer ist ein Toolfenster, die Sie verwenden können, um die folgenden Aufgaben ausführen:  
  
-   Öffnen Sie die SharePoint-Projektelemente und Dateien.  
  
-   Drag & drop von SharePoint-Projektelemente aus einer Funktion in eine andere.  
  
-   Drag & drop von SharePoint-Projektelemente und-Funktionen aus einem Paket in einen anderen.  
  
-   Fügen Sie eine neue Funktion zu einem Paket hinzu.  
  
-   Einen Feature oder Paket-Designer zu öffnen.  
  
-   Überprüfen Sie die Funktionen und Pakete.  
  
 Die SharePoint-Entwicklungstools in Visual Studio haben Validierungsregeln, um sicherzustellen, dass das Lösungspaket, richtig formatiert ist. Darüber hinaus überprüfen die Regeln an, dass die WSP-Projektmappendatei erfolgreich bereitgestellt und auf einem SharePoint-Server aktiviert. Weitere Informationen zu XML-Schema für Features, finden Sie unter [Feature Schemas](http://go.microsoft.com/fwlink/?LinkID=169192).  
  
 Mit dem SharePoint-Projektsystem können Sie benutzerdefinierte Feature- und Paketvalidierungsregeln hinzufügen. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von benutzerdefinierten Funktions- und Paketvalidierungsregeln für SharePoint-Lösungen](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).  
  
 Weitere Informationen zu dem Paket-Explorer, finden Sie unter [wie: Hinzufügen und Entfernen von Funktionen und Elementen in einem Paket mit dem Paket-Explorer](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).  
  
### <a name="solution-explorer"></a>Projektmappen-Explorer  
 Sie können Projektmappen-Explorer navigieren, und öffnen Sie die Dateien des SharePoint-Projekts. Verwenden Sie das Kontextmenü im Projektmappen-Explorer, zum Hinzufügen von Features, Funktionsereignisempfänger und Funktionsressourcen. Darüber hinaus können Sie Informationen zum Konfigurieren der Funktionen und Pakete für die Bereitstellung Funktions-Designer und Paket-Designer öffnen.  
  
##  <a name="Deploying"></a>Bereitstellen von SharePoint-Lösungen  
 Nachdem Sie die Funktionen und Pakete in Visual Studio angepasst haben, können Sie die WSP-Datei zur Bereitstellung auf SharePoint-Servern erstellen. Sie können Visual Studio verwenden, Debuggen und testen die WSP-Datei nur auf dem SharePoint-Server, auf dem Entwicklungscomputer. Weitere Informationen zum Bereitstellen von SharePoint-Lösungen zu einem remote-SharePoint-Server finden Sie unter [Bereitstellen einer Lösung](http://go.microsoft.com/fwlink/?LinkID=169194).  
  
 Sie können auch die Schritten zur Bereitstellung auf dem Entwicklungscomputer anpassen. Weitere Informationen finden Sie unter [bereitstellen, veröffentlichen und Aktualisieren von SharePoint-Lösungspakete](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).  
  
##  <a name="DeployingFiles"></a>Bereitstellen von Dateien in SharePoint-Lösungen  
 In der Regel, wenn Sie die SharePoint-Lösung ein SharePoint-Projektelement hinzugefügt haben, alle erforderlichen Dateien enthalten sind. Dateien, die möglich kompiliert (Codedateien) sind in der Ausgabeassembly der Lösung integriert. Allerdings müssen Sie auch nicht kompilierbare Dateien, z. B. XML, TXT oder Ressourcendateien, einem SharePoint-Projekt hinzufügen. Diese Dateien werden nicht automatisch in der Projektmappe gepackt. Um sicherzustellen, dass sie gepackt werden, hinzufügen entweder die Dateien in einen zugeordneten Ordner oder einer SharePoint-Projektelement.  
  
 Dateien, zugeordnete Ordner hinzugefügt werden automatisch in der SharePoint-Struktur kopiert, wenn die Lösung bereitgestellt wird. Dateien in einer SharePoint-Projektelement hinzugefügt, die im angegebenen Speicherort bereitgestellt werden die **Bereitstellungsspeicherort** Eigenschaft für jede Datei, die teilweise festgelegt ist, basierend auf der **Bereitstellungstyp** Eigenschaft. Wird standardmäßig die **Bereitstellungstyp** Eigenschaftswert ist **NoDeployment**, was bedeutet, dass die Datei nicht mit der Lösung bereitgestellt wird. Sie müssen einen anderen Wert für die Eigenschaft, die Datei im Paket enthalten festlegen.  
  
 Beispielsweise um eine XML-Datei auf einem SharePoint-Projekt hinzuzufügen, führen Sie eine der folgenden Aktionen:  
  
-   Fügen Sie eine "Layouts" zugeordneten SharePoint-Ordner zu Ihrem Projekt hinzu. Dieser Vorgang erstellt im **Projektmappen-Explorer** einen Ordner namens **Layouts** , die verfügt über einen Unterordner für das Projekt. Fügen Sie die XML-Datei in die neue Unterordner hinzu. Standardmäßig wird die Datei im Dateisystem SharePoint unter bereitgestellt... \TEMPLATE\LAYOUTS\\*Ordnername*\\. Informationen zum zugeordneten Ordner hinzuzufügen, finden Sie unter [wie: Hinzufügen und Entfernen von zugeordneten Ordner](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
-   Der Ordner von einer SharePoint-Projektelement der XML-Datei hinzu, und ändern Sie dann die **Bereitstellungstyp** Eigenschaft der XML-Datei aus **NoDeployment** , z. B. eine andere Einstellung **RootFile** oder **ElementFile**. Die entsprechende **Bereitstellungstyp** Einstellung hängt von der Datei und das Projekt. Weitere Informationen zu den **Bereitstellungstyp** eigenschafteneinstellungen, finden Sie unter [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md).  
  
 Wenn eine hinzugefügte Datei nicht zu einem bestimmten Projekt in der Lösung gilt, können Sie ein leeres SharePoint-Projekt zur Projektmappe hinzufügen und dann die zusätzlichen Dateien hinzuzufügen. Eine Alternative zum Bereitstellen von Dateien in SharePoint, insbesondere in der Inhaltsdatenbank ist ein Modul zum Projekt hinzufügen und dann die Dateien an das Modul hinzufügen. Weitere Informationen finden Sie unter [mithilfe von Modulen zum Einschließen von Dateien in der Projektmappe](../sharepoint/using-modules-to-include-files-in-the-solution.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)   
 [Erstellen und Debuggen von SharePoint-Projektmappen](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  