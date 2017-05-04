---
title: "Exemplarische Vorgehensweise: Bereitstellen einer Aufgabenlistendefinition f&#252;r Projekte | Microsoft Docs"
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
  - "SharePoint-Entwicklung in Visual Studio, Bereitstellen"
ms.assetid: 18b62016-ed30-4dd1-9dfc-0d7e82c6767f
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Exemplarische Vorgehensweise: Bereitstellen einer Aufgabenlistendefinition f&#252;r Projekte
  In dieser exemplarischen Vorgehensweise wird erläutert, wie [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] verwendet wird, um eine SharePoint\-Liste zu erstellen, anzupassen, zu debuggen und bereitzustellen, um Projektaufgaben zu verfolgen.  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   [Erstellen einer SharePoint-Liste](#CreatingListDef).  
  
-   [Erstellen einer SharePoint-Liste](#CreatingListDef).  
  
-   [Hinzufügen eines Ereignisempfängers](#AddEventRcvr).  
  
-   [Anpassen der Funktion für Projektaufgabenlisten](#CustomizeFeature)  
  
-   [Erstellen und Testen der Projektaufgabenliste](#BuildTest).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Unterstützte Editionen von Microsoft Windows und SharePoint.  Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vs_pro_current_short](../sharepoint/includes/vs-pro-current-short-md.md)] oder eine Edition der Anwendungslebenszyklus\-Verwaltung \(Application Lifecycle Management, ALM\) von Visual Studio.  
  
##  <a name="CreatingListDef"></a> Erstellen einer SharePoint\-Liste  
 Erstellen Sie ein SharePoint\-Listenprojekt und ordnen Sie die Listendefinition mit Aufgaben zu.  
  
#### Um ein SharePoint\-Listenprojekt erstellen  
  
1.  Öffnen Sie das Dialogfeld **Neues Projekt**, erweitern Sie den Knoten **SharePoint**, und wählen Sie den Knoten **2010** aus.  
  
2.  Im Bereich **Vorlagen** wählen Sie die Vorlage **SharePoint 2010\-Projekt** aus, geben Sie dem Projekt den Namen "ProjectTaskList" ein, und wählen Sie dann die Schaltfläche **OK** aus.  
  
     Der **Assistent zum Anpassen von SharePoint** wird angezeigt.  
  
3.  Geben Sie der lokalen SharePoint\-Website, die Sie zum Debuggen verwenden, wählen Sie das Optionsfeld **Als Farmlösung bereitstellen** und wählen Sie dann die Schaltfläche **Fertig stellen** an.  
  
4.  Öffnen Sie das Kontextmenü für das Projekt, und wählen Sie dann **Neues Element**, **Hinzufügen** aus.  
  
5.  Im Bereich **Vorlagen** wählen Sie die Vorlage **Liste** aus, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.  
  
     Der **Assistent zum Anpassen von SharePoint** wird angezeigt.  
  
6.  Im Feld **Welcher Name soll für Ihre Liste angezeigt werden?** geben Sie Projektaufgabenliste ein.  
  
7.  Wählen Sie das Optionsfeld **Nicht\-anpassbare Liste erstellen basierend auf einem bestehenden Listentyp von**, und dann in der Liste, **Aufgaben** auswählen und wählen Sie dann die Schaltfläche **Fertig stellen** aus.  
  
     Die Liste, Funktion und Paket werden im **Projektmappen\-Explorer**.  
  
##  <a name="AddEventRcvr"></a> Hinzufügen eines Ereignisempfängers  
 In der Aufgabenliste können Sie einen Ereignisempfänger hinzufügen, der automatisch das Fälligkeitsdatum und die Beschreibung der Aufgabe.  Im folgenden Verfahren wird der Listeninstanz ein einfacher Ereignishandler als Ereignisempfänger hinzugefügt.  
  
#### So fügen Sie einen Ereignisempfänger hinzu  
  
1.  Öffnen Sie das Kontextmenü für den Projektknoten, und wählen Sie **Hinzufügen** und dann **Neues Element** aus.  
  
2.  In der Liste der SharePoint\-Vorlagen, wählen Sie die Vorlage **Ereignisempfänger** aus, und benennen Sie sie **ProjectTaskListEventReceiver**.  
  
     Der **Assistent zum Anpassen von SharePoint** wird angezeigt.  
  
3.  Auf der Seite **Ereignisempfängereinstellungen auswählen** wählen Sie als Ereignisempfänger Typs in der Liste **Welchen Typ soll der Ereignisempfänger aufweisenListenelementereignisse** aus.  
  
4.  In der Liste **Welche Element soll als Ereignisquelle dienen** wählen Sie **Aufgaben** aus.  
  
5.  In der Liste der zu behandelnden Ereignisse, wählen Sie das Kontrollkästchen neben **Ein Element wurde hinzugefügt.**, und wählen Sie dann die Schaltfläche **Fertig stellen** aus.  
  
     Dem Projekt wird ein neuer Ereignisempfängerknoten mit einer Codedatei mit dem Namen **ProjectTaskListEventReceiver** hinzugefügt.  
  
6.  Fügen Sie der `ItemAdded`\-Methode in der Codedatei **ProjectTaskListEventReceiver** Code hinzu.  Bei jedem Hinzufügen einer neuen Aufgabe werden dieser Aufgabe ein Standardfälligkeitsdatum und eine Beschreibung hinzugefügt.  Das Standardfälligkeitsdatum ist 1. Juli 2009.  
  
     [!code-csharp[SPProjectTaskList#1](../snippets/csharp/VS_Snippets_OfficeSP/spprojecttasklist/cs/projecttasklisteventreceiver/projecttasklisteventreceiver.cs#1)]
     [!code-vb[SPProjectTaskList#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spprojecttasklist/vb/projecttasklisteventreceiver/projecttasklisteventreceiver.vb#1)]  
  
##  <a name="CustomizeFeature"></a> Anpassen der Funktion für Projektaufgabenlisten  
 Wenn Sie eine SharePoint\-Lösung erstellen, erstellt Visual Studio automatisch Funktionen für die Standardprojektelemente.  Sie können die Einstellungen für die Projektaufgabenliste für die SharePoint\-Website mit dem Funktions\-Designer anpassen.  
  
#### So passen Sie die Funktion für Projektaufgabenlisten an  
  
1.  Erweitern Sie im **Projektmappen\-Explorer** den Eintrag **Funktionen**.  
  
2.  Öffnen Sie das Kontextmenü für **Feature1**, und wählen Sie dann **Ansicht\-Designer** aus.  
  
3.  Im Feld **Titel** geben Sie **Funktion für Projektaufgabenlisten** ein.  
  
4.  In der Liste **Bereich** wählen Sie **Web** aus.  
  
5.  Im Fenster **Eigenschaften** geben Sie **1.0.0.0** als Wert für die Eigenschaft **Version** ein.  
  
##  <a name="CustomizePackage"></a> Anpassen des Pakets mit Projektaufgabenlisten  
 Wenn Sie ein SharePoint\-Projekt erstellen, fügt Visual Studio automatisch die Funktionen hinzu, die die Standardprojektelemente für das Paket enthalten.  Sie können die Einstellungen für die Projektaufgabenliste für die SharePoint\-Website mit dem Paket\-Designer anpassen.  
  
#### So passen Sie das Paket mit Projektaufgabenlisten an  
  
1.  In **ProjektmappeExplorer**, öffnen Sie das Kontextmenü für **Paket**, und wählen Sie dann **Ansicht\-Designer** aus.  
  
2.  Im Feld **Name** geben Sie **ProjectTaskListPackage** ein.  
  
3.  Aktivieren Sie das Kontrollkästchen **Webserver zurücksetzen**.  
  
##  <a name="BuildTest"></a> Erstellen und Testen der Projektaufgabenliste  
 Wenn Sie das Projekt ausführen, wird die SharePoint\-Website geöffnet.  Sie müssen jedoch manuell zum Speicherort der Aufgabenliste navigieren.  
  
#### So testen Sie die Projektaufgabenliste  
  
1.  Drücken Sie die F5\-TASTE, um die Projektaufgabenliste zu erstellen und bereitzustellen.  
  
     Die SharePoint\-Website wird geöffnet.  
  
2.  Wählen Sie die Registerkarte **Startseite** aus.  
  
3.  In der linken Randleiste Wählen Sie den Link **Projektaufgabenliste** aus.  
  
     Die Seite Project Task List wird angezeigt.  
  
4.  Auf der Registerkarte **Listentools** wählen Sie die Registerkarte **Elemente** aus.  
  
5.  In Gruppe **Elemente** wählen Sie die Schaltfläche **Neues Element** aus.  
  
6.  Im Textfeld **Titel** geben Sie "Task1" ein.  
  
7.  Wählen Sie die Schaltfläche **Speichern** aus.  
  
     Nach der Aktualisierung der Website wird die Aufgabe **Task1** mit dem Fälligkeitsdatum 01.07.2009 angezeigt.  
  
8.  Wählen Sie **Task1** aus.  
  
     Die detaillierte Ansicht der Aufgabe wird angezeigt, und als Beschreibung wird "This is a critical task" angezeigt.  
  
##  <a name="Deploy"></a> Bereitstellen der Projektaufgabenliste  
 Nachdem Sie die Projektaufgabenliste erstellt und getestet haben, können Sie sie auf dem *lokalen System* oder einem *Remotesystem* bereitstellen.  Das lokale System der Computer, auf dem Sie die Projektmappe erstellen; ein Remotesystem befindet sich auf einem anderen Computer.  
  
#### So stellen Sie die Projektaufgabenliste auf dem lokalen System bereit  
  
1.  Wählen Sie auf der Visual Studio\-Menüleiste wählen Sie **Projektmappe bereitstellen**, **Erstellen** aus.  
  
     Visual Studio verwendet den IIS\-Anwendungspool wieder, zieht alle vorhandenen Versionen der Lösung zurück, kopiert die Lösungspaketdatei \(.wsp\) für SharePoint und aktiviert anschließend die Funktionen.  Sie können die Lösung jetzt in SharePoint verwenden.  Weitere Informationen zur Bereitstellungskonfiguration finden Sie unter [Gewusst wie: Bearbeiten einer SharePoint-Bereitstellungskonfiguration](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).  
  
#### So stellen Sie die Projektaufgabenliste auf einem Remotesystem bereit  
  
1.  Wählen Sie auf der Visual Studio\-Menüleiste wählen Sie **Veröffentlichen**, **Erstellen** aus.  
  
2.  Im Dialogfeld **Veröffentlichen** wählen Sie das Optionsfeld **Im Dateisystem veröffentlichen** aus.  
  
     Sie können den Zielspeicherort im Dialogfeld **Veröffentlichen** ändern, indem Sie die Schaltfläche mit den Auslassungszeichen klicken ![Symbol "Ellipse"](../sharepoint/media/ellipsisicon.png "Symbol "Ellipse"") und dann zu einem anderen Speicherort navigieren.  
  
3.  Wählen Sie die Schaltfläche **Veröffentlichen** aus.  
  
     Eine WSP\-Datei wird für die Projektmappe erstellt.  
  
4.  Kopieren Sie die WSP\-Datei auf das SharePoint\-Remotesystem.  
  
5.  Installieren Sie das Paket mit dem `Add-SPUserSolution`\-Befehl von PowerShell auf der SharePoint\-Remoteinstallation. \(Für Farmlösungen verwenden Sie den Befehl `Add-SPSolution`\).  
  
     Beispielsweise `Add-SPUserSolution C:\MyProjects\ProjectTaskList\ProjectTaskList\bin\Debug\ProjectTaskList.wsp`.  
  
6.  Stellen Sie die Lösung mit Befehl `Install-SPUserSolution` von PowerShell bereit. \(Für Farmlösungen verwenden Sie den Befehl `Install-SPSolution`\).  
  
     Beispielsweise `Install-SPUserSolution –Identity ProjectTaskList.wsp –Site http://NewSiteName`.  
  
     Weitere Informationen zu Remotebereitstellungen finden, und [Projektmappen mit PowerShell in SharePoint 2010 hinzu und Bereitstellen](http://go.microsoft.com/fwlink/?LinkId=217682) Sie [Verwenden von Projektmappen](http://go.microsoft.com/fwlink/?LinkId=217680).  
  
## Nächste Schritte  
 Weitere Informationen zum Anpassen und Bereitstellen von SharePoint\-Lösungen finden Sie in den folgenden Themen:  
  
-   [Exemplarische Vorgehensweise: Erstellen einer Websitespalte, eines Inhaltstyps und einer Liste für SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)  
  
-   [Gewusst wie: Erstellen eines Ereignisempfängers](../sharepoint/how-to-create-an-event-receiver.md)  
  
-   [Windows PowerShell für SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=217684)  
  
## Siehe auch  
 [Verpacken und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  