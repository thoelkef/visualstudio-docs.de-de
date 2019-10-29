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
ms.openlocfilehash: 45815e03d887f4d22f2559acf741f612cab34c49
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986206"
---
# <a name="package-and-deploy-sharepoint-solutions"></a>Packen und Bereitstellen von SharePoint-Lösungen
  In der Regel wird eine SharePoint-Lösung auf einem SharePoint-Server bereitgestellt, indem eine Projektmappenpaketdatei (. wsp) verwendet wird. Sie können Visual Studio verwenden, um die SharePoint-Projekt Elemente in Funktionen zu organisieren und ein Paket zum Bereitstellen der SharePoint-Funktionen zu erstellen.

 Dieses Thema enthält folgende Informationen:

- [Erstellen von Features und Paketen](#create-features-and-packages)

- [Unterstützung für Funktionen und Verpackungs Tools](#feature-and-packaging-tool-support)

- [Bereitstellen von SharePoint-Lösungen](#deploy-sharepoint-solutions)

- [Bereitstellen von Dateien in SharePoint-Lösungen](#deploy-files-in-sharepoint-solutions)

## <a name="create-features-and-packages"></a>Erstellen von Features und Paketen
 Sie können Visual Studio verwenden, um verwandte SharePoint-Elemente in einer *Funktion*zu gruppieren. Beispielsweise kann eine Funktion für eine Kontaktlisten Definition die Listen Instanz und die Listen Definition enthalten. Sie können diese beiden Elemente zu Bereitstellungs Zwecken in einer einzigen Funktion kombinieren. Weitere Informationen zu Features finden Sie unter [Baustein: Features](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14)).

 Als nächstes können Sie ein SharePoint-Lösungspaket ( *. wsp*) erstellen, um mehrere Features, Site Definitionen, Assemblys und andere Dateien in einem einzelnen Paket zu bündeln, das die Dateien in einem von SharePoint benötigten Format speichert, um die Dateien auf dem Server bereitzustellen. Weitere Informationen finden Sie unter [Building Block: Solutions](/previous-versions/office/developer/sharepoint-2010/ee537008(v=office.14)).

## <a name="feature-and-packaging-tool-support"></a>Unterstützung für Funktionen und Verpackungs Tools
 Sie können die SharePoint-Entwicklungs Tools in Visual Studio verwenden, um Ihre SharePoint-Dateien schnell in Features und Lösungs Paketen zu organisieren, um die Bereitstellung zu vereinfachen. Sie können die folgenden Tools verwenden, um das Feature und das Lösungspaket zu konfigurieren.

- Funktions-Designer und Paket-Designer.

- Verpackungs-Explorer, ein Tool Fenster.

- Projektmappen-Explorer.

### <a name="feature-designer-and-package-designer"></a>Funktions-Designer und Paket-Designer
 Mithilfe des Funktions-Designers können Sie Features erstellen, Bereiche festlegen und andere Features als Abhängigkeiten markieren. Der Designer zeigt außerdem die endgültige XML-Datei an, in der die einzelnen Features beschrieben werden. Weitere Informationen finden Sie unter [Erstellen von SharePoint-Funktionen](../sharepoint/creating-sharepoint-features.md).

 Wenden Sie die Funktion auf eine bestimmte Website oder Gruppe von Websites an, indem Sie Ihren *Bereich* im Funktions-Designer festlegen. Wenn eine Funktion für eine einzelne Website aktiviert ist, kann die Funktion nur auf dieser speziellen Website verwendet werden. Wenn eine Funktion für eine Website Sammlung aktiviert ist, gelten die Elemente in der Funktion für die gesamte Website Sammlung. Weitere Informationen finden Sie unter [Element Bereich](/previous-versions/office/developer/sharepoint-2010/ms476615(v=office.14)).

 Wenn Ihre Funktion von anderen Features abhängig ist, können Sie eine *Funktions Aktivierungs Abhängigkeit* festlegen, um die abhängigen Features zu markieren, bevor Sie das Feature verfügbar macht. Eine Funktions Aktivierungs Abhängigkeit prüft, ob die abhängigen Funktionen bereits in diesem Bereich aktiviert sind. Weitere Informationen finden Sie unter [Aktivierungs Abhängigkeiten und Bereich](/previous-versions/office/developer/sharepoint-2010/aa543162(v=office.14)).

 Im Paket-Designer können Sie SharePoint-Elemente in einem einzelnen Projektmappenpaket gruppieren und konfigurieren, ob der Webserver während der Bereitstellung zurückgesetzt werden soll. Verwenden Sie zum Festlegen des Bereitstellungs Server Typs das **Eigenschaften** Fenster. Der Designer generiert außerdem die XML-Datei, die den Paket Inhalt beschreibt. Weitere Informationen finden Sie unter [Erstellen von SharePoint-Lösungs Paketen](../sharepoint/creating-sharepoint-solution-packages.md).

 Während der Bereitstellung wird der Internetinformationsdienste (IIS)-Dienst beendet, um die Projektmappendateien auf den SharePoint-Server zu kopieren. Wenn Sie den Paket-Designer in Visual Studio verwenden, können Sie auswählen, ob der Webserver neu gestartet werden soll. Um zu konfigurieren, ob die Lösung auf einem Front-End-Webserver oder einem Anwendungsserver bereitgestellt wird, verwenden Sie das **Eigenschaften** Fenster. Weitere Informationen finden Sie unter [Solution-Element (](/previous-versions/office/developer/sharepoint-2010/ms412929(v=office.14))Projekt Mappe).

### <a name="packaging-explorer"></a>Paket-Explorer
 Um den Funktions-Designer und den Paket-Designer zu ergänzen, können Sie den Paket-Explorer verwenden, um die SharePoint-Dateien in Funktionen und Pakete zu gruppieren. Außerdem können Sie die hierarchische Ansicht des Pakets, der Features, der SharePoint-Projekt Elemente und der Dateien sehen. Der Paket-Explorer ist ein Tool Fenster, das Sie verwenden können, um die folgenden Aufgaben auszuführen:

- Öffnen Sie SharePoint-Projekt Elemente und-Dateien.

- Ziehen Sie SharePoint-Projekt Elemente per Drag & Drop aus einer Funktion in eine andere.

- Ziehen Sie SharePoint-Projekt Elemente und-Funktionen per Drag & Drop aus einem Paket in ein anderes.

- Fügen Sie einem Paket ein neues Feature hinzu.

- Öffnen Sie eine Funktion oder einen Paket-Designer.

- Überprüfen von Features und Paketen.

  Die SharePoint-Entwicklungs Tools in Visual Studio verfügen über Validierungsregeln, um sicherzustellen, dass das Lösungspaket ordnungsgemäß formatiert ist. Außerdem überprüfen die Regeln, ob die *wsp* -Projektmappendatei erfolgreich auf einem SharePoint-Server bereitgestellt und aktiviert werden kann. Weitere Informationen zum XML-Schema für Funktionen finden Sie unter [Funktions Schemas](/previous-versions/office/developer/sharepoint-2010/ms414322(v=office.14)).

  Sie können dem SharePoint-Projekt Systembenutzer definierte Feature-und Paket Validierungsregeln hinzufügen. Weitere Informationen finden Sie unter Gewusst [wie: Erstellen von benutzerdefinierten Funktions-und Paket Validierungsregeln für SharePoint-Lösungen](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

  Weitere Informationen zum Paket-Explorer finden Sie unter Gewusst [wie: Hinzufügen und Entfernen von Features und Elementen in einem Paket mit dem Paket-Explorer](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).

### <a name="solution-explorer"></a>Projektmappen-Explorer
 Sie können Projektmappen-Explorer verwenden, um die Dateien des SharePoint-Projekts zu navigieren und zu öffnen. Verwenden Sie das Kontextmenü in Projektmappen-Explorer, um Features, Funktions Ereignis Empfänger und featureressourcen hinzuzufügen. Außerdem können Sie die Funktions-Designer und Paket-Designer öffnen, um die Features und Pakete für die Bereitstellung zu konfigurieren.

## <a name="deploy-sharepoint-solutions"></a>Bereitstellen von SharePoint-Lösungen
 Nachdem Sie die Features und das Paket in Visual Studio angepasst haben, können Sie eine *wsp* -Datei erstellen, die für SharePoint-Server bereitgestellt werden soll. Sie können Visual Studio verwenden, um das zu Debuggen und zu testen. *wsp* ist nur auf dem SharePoint-Server auf dem Entwicklungs Computer. Weitere Informationen zum Bereitstellen von SharePoint-Lösungen auf einem Remote-SharePoint-Server finden Sie unter Bereitstellen [einer Lösung](/previous-versions/office/developer/sharepoint-2010/aa544500(v=office.14)).

 Sie können auch die Bereitstellungs Schritte auf dem Entwicklungs Computer anpassen. Weitere Informationen finden Sie unter Bereitstellen [, veröffentlichen und Aktualisieren von SharePoint-Lösungs Paketen](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).

## <a name="deploy-files-in-sharepoint-solutions"></a>Bereitstellen von Dateien in SharePoint-Lösungen
 Wenn Sie der SharePoint-Lösung ein SharePoint-Projekt Element hinzufügen, werden in der Regel alle erforderlichen Dateien eingeschlossen. Dateien, die kompiliert werden können (Code Dateien), werden in die Ausgabeassembly der Projekt Mappe integriert. Möglicherweise müssen Sie jedoch auch nicht Kompilier Bare Dateien, z *. b. XML*-, *txt*-oder Ressourcen Dateien, einem SharePoint-Projekt hinzufügen. Diese Dateien werden nicht automatisch in die Projekt Mappe gepackt. Um sicherzustellen, dass Sie verpackt sind, fügen Sie die Dateien entweder einem zugeordneten Ordner oder einem SharePoint-Projekt Element hinzu.

 Dateien, die zugeordneten Ordnern hinzugefügt werden, werden bei der Bereitstellung der Lösung automatisch in die SharePoint-Struktur kopiert. Dateien, die einem SharePoint-Projekt Element hinzugefügt werden, werden an dem Speicherort bereitgestellt, der in der Eigenschaft **Bereitstellungsort** für jede Datei angegeben ist, die teilweise basierend auf der Eigenschaft **Bereitstellungstyp** festgelegt ist. Standardmäßig ist der Wert der Eigenschaft **Bereitstellungstyp** **nodeployment**, was bedeutet, dass die Datei nicht mit der Lösung bereitgestellt wird. Sie müssen einen anderen Wert für die-Eigenschaft festlegen, um die Datei in das Paket aufzunehmen.

 Um z. b. eine *XML* -Datei zu einem SharePoint-Projekt hinzuzufügen, führen Sie eine der folgenden Aktionen aus:

- Fügen Sie dem Projekt einen für den SharePoint-Ordner "Layouts" zugeordneten Ordner hinzu. Dadurch wird in **Projektmappen-Explorer** einem Ordner mit dem Namen **Layouts** erstellt, der einen Unterordner für das Projekt enthält. Fügen Sie die *XML* -Datei dem neuen Unterordner hinzu. Standardmäßig wird die Datei im SharePoint-Dateisystem unter. bereitgestellt.  *\Template\layouts\\\<Ordnernamen >* . Weitere Informationen zum Hinzufügen von zugeordneten Ordnern finden Sie unter Gewusst [wie: Hinzufügen und entfernen](../sharepoint/how-to-add-and-remove-mapped-folders.md)von zugeordneten Ordnern.

- Fügen Sie die *XML* -Datei zum Ordner eines SharePoint-Projekt Elements hinzu, und ändern Sie dann die Eigenschaft **Bereitstellungstyp** der *XML* -Datei von **nodeployment** in eine andere Einstellung, z. b. **RootFile** oder **Element File**. Die geeignete Einstellung für den **Bereitstellungstyp** hängt von der Datei und dem Projekt ab. Weitere Informationen zu den Eigenschaften Einstellungen für den **Bereitstellungstyp** finden Sie unter [entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md).

  Wenn eine hinzugefügte Datei nicht auf ein bestimmtes Projekt in der Projekt Mappe angewendet wird, können Sie der Projekt Mappe ein leeres SharePoint-Projekt hinzufügen und dann die zusätzlichen Dateien hinzufügen. Eine weitere Alternative zum Bereitstellen von Dateien für SharePoint, insbesondere für die Inhalts Datenbank, besteht darin, dem Projekt ein Modul hinzuzufügen und die Dateien dem Modul hinzuzufügen. Weitere Informationen finden Sie unter [Verwenden von Modulen zum Einschließen von Dateien in die](../sharepoint/using-modules-to-include-files-in-the-solution.md)Projekt Mappe.

## <a name="see-also"></a>Siehe auch
- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)
- [Erstellen und Debuggen von SharePoint-Lösungen](../sharepoint/building-and-debugging-sharepoint-solutions.md)
