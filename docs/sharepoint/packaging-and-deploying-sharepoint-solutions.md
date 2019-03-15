---
title: Verpacken und Bereitstellen von SharePoint-Lösungen | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- packaging [SharePoint development in Visual Studio]
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, packaging and deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 297fefddd45b080af236da0b4fe53649e7d630cf
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57867563"
---
# <a name="package-and-deploy-sharepoint-solutions"></a>Packen und Bereitstellen von SharePoint-Lösungen
  In der Regel wird eine SharePoint-Lösung auf einem SharePoint Server mithilfe einer Lösung-Paketdatei (.wsp) bereitgestellt. Sie können Visual Studio verwenden, um Ihre SharePoint-Projektelemente in Features zu organisieren und zum Erstellen eines Pakets zum Bereitstellen Ihrer SharePoint-Funktionen.

 Dieses Thema enthält folgende Informationen:

-   [Erstellen von Funktionen und Pakete](#create-features-and-packages)

-   [Feature und toolunterstützung für die paketerstellung](#feature-and-packaging-tool-support)

-   [Bereitstellen von SharePoint-Lösungen](#deploy-sharepoint-solutions)

-   [Bereitstellen von Dateien in SharePoint-Lösungen](#deploy-files-in-sharepoint-solutions)

## <a name="create-features-and-packages"></a>Erstellen von Funktionen und Pakete
 Sie können Visual Studio verwenden, zum Gruppieren von verwandten SharePoint-Elemente in einem *Feature*. Eine Funktion für die Definition eines Contacts-Liste gehören z. B. die Listeninstanz und die Listendefinition. Sie können diese beiden Elemente in einer einzelnen Funktion für die Bereitstellung kombinieren. Weitere Informationen zu Funktionen finden Sie unter [Baustein: Features](http://go.microsoft.com/fwlink/?LinkID=169183).

 Anschließend erstellen Sie eine SharePoint-Lösungspaket (*.wsp*) um mehrere Funktionen zu bündeln, site-Definitionen, Assemblys und andere Dateien in einem einzigen Paket, das die Dateien in einem Format, die von SharePoint benötigt werden, um die bereitzustellen, speichert der Server. Weitere Informationen finden Sie unter [Baustein: Lösungen](http://go.microsoft.com/fwlink/?LinkID=169186).

## <a name="feature-and-packaging-tool-support"></a>Feature und toolunterstützung für die paketerstellung
 Die SharePoint-Entwicklungstools können in Visual Studio Sie um die SharePoint-Dateien schnell in die Features und Lösungspakete für einfachere Bereitstellung zu organisieren. Sie können die folgenden Tools verwenden, so konfigurieren Sie die Lösung und Feature-Paket.

-   Funktions-Designer und Paket-Designer.

-   Paket-Explorer ein Toolfenster.

-   Projektmappen-Explorer.

### <a name="feature-designer-and-package-designer"></a>Funktions-Designer und die Paket-designer
 Sie können Funktionen erstellen, Bereiche festlegen und markieren andere Funktionen als Abhängigkeiten mithilfe von Funktions-Designer. Der Designer zeigt auch die endgültige XML-Datei, die jede Funktion beschreibt. Weitere Informationen finden Sie unter [erstellen SharePoint-Funktionen](../sharepoint/creating-sharepoint-features.md).

 Wenden Sie die Funktion eine bestimmte Website oder eine Gruppe von Websites durch Festlegen seiner *Bereich* im Funktions-Designer. Wenn eine Funktion für eine einzelne Website aktiviert ist, funktioniert diese Funktion nur in dieser bestimmten Website. Wenn eine Funktion für eine Websitesammlung aktiviert ist, wenden die Elemente in der Funktion für die gesamte Websitesammlung an. Weitere Informationen finden Sie unter [Gültigkeitsbereich Elements](http://go.microsoft.com/fwlink/?LinkID=169189).

 Wenn das Feature auf andere Funktionen verwendet werden soll, legen Sie eine *Funktion die aktivierungsabhängigkeit* um die abhängigen Funktionen zu markieren, bevor Sie das Feature zur Verfügung zu stellen. Eine funktionsaktivierungsabhängigkeit wird überprüft, ob die abhängigen Features bereits in diesem Bereich aktiviert werden. Weitere Informationen finden Sie unter [Aktivierungsabhängigkeiten und Bereich](http://go.microsoft.com/fwlink/?LinkID=169190).

 In der Paket-Designer können Sie SharePoint-Elemente in einem Lösungspaket gruppieren und festlegen, ob der Webserver während der Bereitstellung zurückgesetzt. Um den Bereitstellungstyp für den Server festzulegen, verwenden die **Eigenschaften** Fenster. Der Designer generiert außerdem die XML-Datei, die den Inhalt des Pakets beschreibt. Weitere Informationen finden Sie unter [erstellen SharePoint-Lösungspakete](../sharepoint/creating-sharepoint-solution-packages.md).

 Während der Bereitstellung ist der Internet Information Services (IIS)-Dienst beendet, um die Projektmappendateien auf dem SharePoint-Server zu kopieren. Mithilfe der Paket-Designer in Visual Studio können Sie auswählen, ob der Webserver neu gestartet werden soll. Verwenden Sie zum Konfigurieren, wenn die Lösung auf einem Front-End-Webserver oder Anwendungsserver bereitgestellt wird, die **Eigenschaften** Fenster. Weitere Informationen finden Sie unter [Solution-Element (Lösung)](http://go.microsoft.com/fwlink/?LinkID=169191).

### <a name="packaging-explorer"></a>Paket-Explorer
 Um die Funktions-Designer und die Paket-Designer zu ergänzen, können Sie die Paket-Explorer, um die SharePoint-Dateien in Funktionen und Pakete zu gruppieren. Darüber hinaus sehen Sie die hierarchische Ansicht des Pakets, der Funktionen, SharePoint-Projekts und der Dateien. Die Paket-Explorer ist ein Toolfenster, die Sie verwenden können, um die folgenden Aufgaben ausführen:

- Öffnen Sie die SharePoint-Projektelemente und Dateien.

- Ziehen Sie und legen Sie der SharePoint-Projektelemente aus einer Funktion in eine andere ab.

- Ziehen und Ablegen von SharePoint-Projektelemente und-Funktionen aus einem Paket in einen anderen.

- Fügen Sie ein neues Feature in ein Paket hinzu.

- Öffnen Sie einen Feature oder Paket-Designer.

- Überprüfen Sie Funktionen und Pakete.

  Die SharePoint-Entwicklungstools in Visual Studio haben die Validierungsregeln, um sicherzustellen, dass das Lösungspaket richtig formatiert ist. Darüber hinaus die Regeln zu überprüfen, die die *.wsp* Projektmappendatei erfolgreich bereitgestellt und auf einem SharePoint-Server aktiviert. Weitere Informationen zum XML-Schema für Funktionen, finden Sie unter [Feature Schemas](http://go.microsoft.com/fwlink/?LinkID=169192).

  Sie können SharePoint-Projektsystem benutzerdefinierten Funktions- und Paketvalidierungsregeln hinzufügen. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen, benutzerdefinierte Funktions- und Paketvalidierungsregeln für SharePoint-Lösungen](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

  Weitere Informationen zu den Paket-Explorer, finden Sie unter [Vorgehensweise: Hinzufügen und Entfernen von Funktionen und Elementen in einem Paket mithilfe der Paket-Explorer](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).

### <a name="solution-explorer"></a>Projektmappen-Explorer
 Sie können die Projektmappen-Explorer navigieren, und öffnen Sie die Dateien des SharePoint-Projekts verwenden. Verwenden Sie das Kontextmenü im Projektmappen-Explorer zum Hinzufügen von Features, Funktionsereignisempfänger und Funktionsressourcen. Darüber hinaus können Sie die Funktions-Designer und die Paket-Designer, um die Funktionen und Pakete für die Bereitstellung konfigurieren öffnen.

## <a name="deploy-sharepoint-solutions"></a>Bereitstellen von SharePoint-Lösungen
 Nachdem Sie die Features und das Paket in Visual Studio anpassen, können Sie erstellen eine *.wsp* Datei, die auf SharePoint-Servern bereitzustellen. Sie können Visual Studio zum Debuggen und Testen der. *Wsp* nur auf dem SharePoint-Server, auf dem Entwicklungscomputer. Weitere Informationen dazu, wie Sie die SharePoint-Lösungen auf einem remote-SharePoint-Server bereitstellen, finden Sie unter [Bereitstellen einer Lösung](http://go.microsoft.com/fwlink/?LinkID=169194).

 Sie können auch die Bereitstellungsschritte auf dem Entwicklungscomputer anpassen. Weitere Informationen finden Sie unter [bereitstellen, veröffentlichen und Aktualisieren von SharePoint-Lösungspakete](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).

## <a name="deploy-files-in-sharepoint-solutions"></a>Bereitstellen von Dateien in SharePoint-Lösungen
 In der Regel, wenn Sie die SharePoint-Lösung ein SharePoint-Projektelement hinzufügen, alle erforderlichen Dateien enthalten sind. Dateien, die möglich kompiliert (Codedateien) in der Ausgabeassembly der Lösung integriert sind. Allerdings auch möglicherweise nicht kompilierbar Dateien, z. B. hinzufügen *XML*, *.txt*, oder Ressourcendateien zu einer SharePoint-Projekt. Diese Dateien werden nicht automatisch in Ihrer Projektmappe gepackt. Um sicherzustellen, dass sie verpackt werden, hinzufügen entweder die Dateien auf einen zugeordneten Ordner oder eine SharePoint-Projektelement.

 Dateien, zugeordnete Ordner hinzugefügt wurden, werden automatisch in der SharePoint-Struktur kopiert, wenn die Lösung bereitgestellt wird. Dateien, die zu einem SharePoint-Projektelement hinzugefügt werden bereitgestellt, zu dem Speicherort, die im angegebenen die **Speicherort für die Bereitstellung** -Eigenschaft für jede Datei, die teilweise festgelegt wird, basierend auf den **Bereitstellungstyp** Eigenschaft. In der Standardeinstellung die **Bereitstellungstyp** Eigenschaftswert ist **NoDeployment**, was bedeutet, dass die Datei nicht mit der Lösung bereitgestellt wird. Sie müssen einen anderen Wert für die Eigenschaft, die die Datei im Paket enthalten festlegen.

 Beispielsweise, um das Hinzufügen einer *XML* -Datei in einem SharePoint-Projekt, eine der folgenden Aktionen ausführen:

- Fügen Sie Ihrem Projekt eine "Layouts" zugeordneten SharePoint-Ordner hinzu. Dieser Vorgang erstellt im **Projektmappen-Explorer** einen Ordner namens **Layouts** , bei dem einen Unterordner des Projekts. Hinzufügen der *XML* Datei in den neuen Unterordner. Standardmäßig wird die Datei im SharePoint-Dateisystem unter bereitgestellt *... \TEMPLATE\LAYOUTS\\\<Ordnername >*. Informationen dazu, wie Sie zugeordneter Ordner hinzufügen, finden Sie unter [Vorgehensweise: Hinzufügen und entfernen zugeordneter Ordner](../sharepoint/how-to-add-and-remove-mapped-folders.md).

- Hinzufügen der *XML* Datei in den Ordner eines SharePoint-Projektelements, und ändern Sie die **Bereitstellungstyp** Eigenschaft der *XML* Datei **NoDeployment**  , z. B. eine andere Einstellung **RootFile** oder **ElementFile**. Die entsprechende **Bereitstellungstyp** Einstellung hängt von der Datei und das Projekt. Weitere Informationen zu den **Bereitstellungstyp** eigenschafteneinstellungen, finden Sie unter [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md).

  Wenn eine hinzugefügte Datei zu keinem bestimmten Projekt in der Projektmappe nicht anwendbar ist, können Sie ein leeres SharePoint-Projekt der Projektmappe hinzufügen und anschließend die zusätzlichen Dateien hinzugefügt. Eine weitere Alternative für die Bereitstellung von Dateien in SharePoint, besonders in der Inhaltsdatenbank ist auf das Projekt ein Modul hinzu, und klicken Sie dann die Dateien an das Modul hinzufügen. Weitere Informationen finden Sie unter [Verwenden von Modulen zum Einfügen von Dateien in der Projektmappe](../sharepoint/using-modules-to-include-files-in-the-solution.md).

## <a name="see-also"></a>Siehe auch
- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)
- [Erstellen und Debuggen von SharePoint-Lösungen](../sharepoint/building-and-debugging-sharepoint-solutions.md)
