---
title: "Exemplarische Vorgehensweise: Importieren von Elementen aus einer vorhandenen SharePoint-Website | Microsoft Docs"
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
  - "Importieren von Elementen [SharePoint-Entwicklung in Visual Studio]"
  - "SharePoint-Entwicklung in Visual Studio, Importieren von Elementen"
ms.assetid: faac3309-88d7-4fb2-8392-feda07fc00e5
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Exemplarische Vorgehensweise: Importieren von Elementen aus einer vorhandenen SharePoint-Website
  In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Elemente aus einer vorhandenen SharePoint\-Website in ein [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-SharePoint Projekt importiert werden.  
  
 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:  
  
-   Anpassen einer SharePoint\-Website durch Hinzufügen einer benutzerdefinierten Websitespalte \(wird auch als *Feld* bezeichnet\).  
  
-   Exportieren einer SharePoint\-Website in eine WSP\-Datei.  
  
-   Importieren der WSP\-Datei in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-SharePoint mit dem Projekt zum Importieren von WSP.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Unterstützte Editionen von [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] und SharePoint.  Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## Anpassen einer SharePoint\-Website  
 Für dieses Beispiel erstellen Sie eine SharePoint\-Unterwebsite und passen diese an, indem Sie eine neue Websitespalte hinzufügen und eine weitere Unterwebsite zur späteren Verwendung erstellen.  Später exportieren Sie die erste Unterwebsite in eine WSP\-Datei und importieren dann die benutzerdefinierte Websitespalte in die zweite Unterwebsite, indem Sie das Projekt zum Importieren von WSP verwenden.  
  
#### So erstellen Sie eine SharePoint\-Website und passen diese an  
  
1.  Öffnen Sie eine SharePoint\-Website in einem Webbrowser, z http:\/\/*system name*\/SitePages\/Home.aspx.  
  
2.  Erstellen Sie eine Unterwebsite der SharePoint\-Hauptsite, indem Sie das Menü **Websiteaktionen** öffnen und dann **Neuer Standort** auswählen.  
  
3.  Im Dialogfeld **Erstellen** der Website wählen Sie den Typ **Leere Website** aus.  
  
4.  Im Feld **Titel** geben Sie " Site Column Test 1 "; ein Geben Sie im Feld **URL\-Name** columntest1 ein; Übernehmen Sie die Standardwerte für die anderen Einstellungen; und dann die Schaltfläche **Erstellen** aus.  
  
5.  Nachdem die Website erstellt wurde, navigieren Sie im Browser wieder zur Hauptsite, http:\/\/*system name*\/SitePages\/Home.aspx.  
  
6.  Außerdem erstellen Sie eine leere Unterwebsite der SharePoint\-Hauptsite, indem Sie das Menü **Websiteaktionen** öffnen auswählen, **Neuer Standort**, und dann den Typ **Leere Website** auswählen.  
  
7.  Im Feld **Titel** geben Sie " Site Column Test 2 "; ein Geben Sie im Feld **URL\-Name** columntest2 ein; Übernehmen Sie die Standardwerte für die anderen Einstellungen; und dann die Schaltfläche **Erstellen** aus.  
  
8.  Navigieren Sie zurück zur ersten Unterwebsite, http:\/\/*SystemName*\/columntest1\/default.aspx.  
  
9. Klicken Sie im Menü **Websiteaktionen** wählen **Websiteeinstellungen**, um die Seite Websiteeinstellungen anzuzeigen.  
  
10. Im Abschnitt **Galerien** Wählen Sie den Link **Websitespalten** aus.  
  
11. Im oberen Bereich der Seite **Websitespaltenkatalog** wählen Sie die Schaltfläche **Erstellen** aus.  
  
12. Im Feld **Spaltenname** geben Sie "Test Column" ein, halten Sie die anderen Standardwerte, und wählen Sie dann die Schaltfläche **OK** aus.  
  
13. Die Spalte **Testspalte** wird unter den benutzerdefinierten Spalten, im Websitespaltenkatalog vorangehen.  
  
## Exportieren der SharePoint\-Website  
 Rufen Sie danach eine SharePoint\-Setupdatei \(.wsp\) ab, die die SharePoint\-Elemente und Elemente enthält, die Sie in das [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-SharePoint\-Projekt importieren möchten.  Wenn noch keine WSP\-Datei vorhanden ist, müssen Sie eine aus einer vorhandenen SharePoint\-Website erstellen.  In diesem Beispiel exportieren Sie die SharePoint\-Standardsite in eine WSP\-Datei.  
  
> [!IMPORTANT]  
>  Wenn beim Ausführen der folgenden Prozedur ein Laufzeitfehler auftritt, müssen Sie die Prozedur auf einem System ausführen, das über Zugriff auf die SharePoint\-Website verfügt.  
  
#### So exportieren Sie eine vorhandene SharePoint\-Website  
  
1.  In der SharePoint\-Website wählen Sie auf der Registerkarte **WebsiteaktionenWebsiteeinstellungen**, um die Seite Websiteeinstellungen anzuzeigen.  
  
2.  Im Abschnitt **Websiteaktionen** der Site\-Einstellungen blättern Sie, wählen Sie den Link **Website als Vorlage speichern** aus.  
  
3.  Geben Sie im Feld **Dateiname** den Namen "ExampleSite" ein, und geben Sie im Feld **Vorlagenname** den Namen "Example Site" ein.  
  
4.  Lassen Sie in diesem Beispiel das Kontrollkästchen **Inhalte einschließen** deaktiviert.  
  
     Wenn Sie dieses Kontrollkästchen aktivieren, speichert [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] alle Listen und Dokumentbibliotheken und deren Inhalte in der WSP\-Datei.  Obwohl dies in einigen Fällen nützlich ist, ist es für dieses Beispiel nicht erforderlich.  
  
5.  Wenn der Vorgang erfolgreich abgeschlossen ist, wählen Sie den Link **Lösungskatalog**, um die WSP\-Datei anzuzeigen.  
  
     Um die Lösungskatalogseite später anzuzeigen, öffnen Sie das Menü **Websiteaktionen**, wählen Sie **Websiteeinstellungen** aus, wählen Sie den Link **Zu Websiteeinstellungen der obersten Ebene wechseln** im Abschnitt **Websitesammlungsverwaltung**, und dann den Link **Projektmappen** im Abschnitt **Galerien** aus.  
  
6.  im Lösungskatalog auf den Link **ExampleSite** aus.  
  
7.  Im Dialogfeld **Dateidownload** wählen Sie die Schaltfläche **Speichern**, um die Datei im lokalen System standardmäßig im Downloadordner zu speichern.  
  
## Importieren der WSP\-Datei  
 Jetzt importieren Sie die WSP\-Datei, die ein Element enthält, das Sie wiederverwenden möchten \(die benutzerdefinierte Websitespalte Test Column\), um darauf zuzugreifen.  
  
#### So importieren Sie eine WSP\-Datei  
  
1.  Klicken Sie in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] auf der Menüleiste, wählen Sie **Neu**, **Projekt**, **Datei**, um das Dialogfeld **Neues Projekt** anzuzeigen.  Wenn die IDE festgelegt ist, um Visual Basic\-Entwicklungseinstellungen, in der Menüleiste zu verwenden, wählen Sie **Neues Projekt**, **Datei** aus.  
  
2.  Erweitern Sie den Knoten **SharePoint** entweder unter **Visual C\#** oder **Visual Basic**, und wählen Sie den Knoten **2010** aus.  
  
3.  Wählen Sie die Vorlage **SharePoint 2010\-Lösungspaket importieren** im Bereich **Vorlagen** aus, übernehmen Sie den Namen WspImportProject1 des Projekts, und wählen Sie dann die Schaltfläche **OK** aus.  
  
     Der **Assistent zum Anpassen von SharePoint** wird angezeigt.  
  
4.  Auf der Seite **Site und Sicherheitsebene für Debugging angeben** geben Sie [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] für die zweite SharePoint\-Unterwebsite ein, die Sie zuvor erstellt haben.  fügen Sie das neue benutzerdefinierte Feldelement, http:\/\/*system name*\/columntest2, Dieser Unterwebsite hinzu.  
  
5.  Übernehmen Sie im Abschnitt **Wie lautet die Vertrauensebene für diese SharePoint\-Lösung?** die Auswahl **Als Sandkastenlösung bereitstellen**.  
  
6.  Auf der Seite **Neue Projektquelle angeben** navigieren Sie zum Speicherort im System, an dem Sie zuvor die WSP\-Datei gespeichert haben und dann die Schaltfläche **Weiter** auswählen.  
  
    > [!NOTE]  
    >  Wenn Sie die Schaltfläche **Fertig stellen** auf dieser Seite auswählen, werden alle verfügbaren Elemente in der WSP\-Datei importiert.  
  
7.  Im Feld **Zu importierende Elemente auswählen** löschen Sie alle Kontrollkästchen in der Liste mit Ausnahme von **Testspalte**, und wählen Sie die Schaltfläche **Fertig stellen** aus.  
  
     Da die Liste viele Elemente enthält, können Sie die STRG\+A\-TASTEN die Möglichkeit, alle Elemente in der Liste auszuwählen, wählen die LEERTASTE\-TASTE, um alle Kontrollkästchen zu löschen und dann nur das Kontrollkästchen neben dem Element **Testspalte** aus.  
  
     Nachdem der Importvorgang beendet wurde, wird ein neues Projekt mit dem Namen **WspImportProject1** erstellt, das einen Ordner mit dem Namen **Felder** enthält.  In diesem Ordner befinden sich die benutzerdefinierte Websitespalte **Test Column** sowie deren Definitionsdatei Elements.xml.  
  
## Bereitstellen des Projekts  
 Stellen Sie abschließend **WspImportProject1** auf der zweiten SharePoint\-Unterwebsite bereit, die Sie zuvor erstellt haben, um die benutzerdefinierte Websitespalte anzuzeigen.  
  
#### So stellen Sie das Projekt bereit  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] verwenden Sie die F5\-TASTE, um das WSP\-Importprojekt bereitzustellen und auszuführen.  
  
2.  Auf der SharePoint\-Website öffnen Sie das Menü **Websiteaktionen**, und wählen Sie dann **Websiteeinstellungen**, um die Seite Websiteeinstellungen anzuzeigen.  
  
3.  Im Abschnitt **Galerien** Wählen Sie den Link **Websitespalten** aus.  
  
4.  Führen Sie einen Bildlauf nach unten zum Abschnitt **Benutzerdefinierte Spalten** durch.  
  
     Beachten Sie, dass die benutzerdefinierte Websitespalte, die Sie aus der ersten SharePoint\-Website importiert haben, in der Liste angezeigt wird.  
  
## Siehe auch  
 [Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  