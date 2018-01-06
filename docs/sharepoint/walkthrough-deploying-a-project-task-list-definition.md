---
title: 'Exemplarische Vorgehensweise: Bereitstellen einer Aufgabenlistendefinition Projekt | Microsoft Docs'
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
helpviewer_keywords: SharePoint development in Visual Studio, deploying
ms.assetid: 18b62016-ed30-4dd1-9dfc-0d7e82c6767f
caps.latest.revision: "34"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 16cccaf9a8639ef2d7213140121b087cd15e72d2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-deploying-a-project-task-list-definition"></a>Exemplarische Vorgehensweise: Bereitstellen einer Aufgabenlistendefinition für Projekte
  In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Sie [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] zum Erstellen, anpassen, Debuggen und Bereitstellen eine SharePoint-Liste zum Nachverfolgen von Projektaufgaben.  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   [Erstellen einer SharePoint-Liste](#CreatingListDef).  
  
-   [Erstellen einer SharePoint-Liste](#CreatingListDef).  
  
-   [Hinzufügen eines Ereignisempfängers](#AddEventRcvr).  
  
-   [Anpassen der Aufgabe-Liste Projektfunktion](#CustomizeFeature).  
  
-   [Erstellen und Testen des Projekts Aufgabenliste](#BuildTest).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Unterstützte Editionen von Microsoft Windows und SharePoint. Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vs_pro_current_short](../sharepoint/includes/vs-pro-current-short-md.md)]oder eine Edition von Visual Studio Application Lifecycle Management (ALM).  
  
##  <a name="CreatingListDef"></a>Erstellen einer SharePoint-Liste  
 Erstellen Sie eine SharePoint-List-Projekt, und ordnen Sie die Listendefinition Aufgaben.  
  
#### <a name="to-create-a-sharepoint-list-project"></a>Zum Erstellen eines SharePoint-Liste-Projekts  
  
1.  Öffnen der **neues Projekt** Dialogfeld erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.  
  
2.  In der **Vorlagen** Bereich, wählen Sie die **SharePoint 2010-Projekt** Vorlage, nennen Sie das Projekt **ProjectTaskList**, und wählen Sie dann die **OK**Schaltfläche.  
  
     Die **Assistent zum Anpassen von SharePoint** angezeigt wird.  
  
3.  Geben Sie die lokale SharePoint-Website, die Sie verwenden, für das Debuggen, wählen Sie die **als farmlösung bereitstellen** Optionsfeld aus, und wählen Sie dann die **Fertig stellen** Schaltfläche.  
  
4.  Öffnen Sie das Kontextmenü für das Projekt, und wählen Sie dann **hinzufügen**, **neues Element**.  
  
5.  In der **Vorlagen** Bereich, wählen Sie die **Liste** Vorlage, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
     Die **Assistent zum Anpassen von SharePoint** angezeigt wird.  
  
6.  In der **welchen Namen möchten Sie für Ihre Liste anzeigen?** geben **Projektaufgabenliste**.  
  
7.  Wählen Sie die **Erstellen einer nicht anpassbaren Liste basierend auf einer vorhandenen Liste** Optionsfeld aus, und wählen Sie dann in der Liste **Aufgaben**, und wählen Sie dann die **Fertig stellen** Schaltfläche.  
  
     Die Liste, Funktion und Paket angezeigt, **Projektmappen-Explorer**.  
  
##  <a name="AddEventRcvr"></a>Hinzufügen eines Ereignisempfängers  
 Sie können in der Aufgabenliste Ereignisempfänger, der den Gesamtbetrag automatisch festlegt hinzufügen Datum und die Beschreibung des Tasks. Das folgende Verfahren werden die Listeninstanz als Ereignisempfänger einen einfachen-Ereignishandler hinzugefügt.  
  
#### <a name="to-add-an-event-receiver"></a>Ereignisempfänger hinzufügen  
  
1.  Öffnen Sie das Kontextmenü für den Projektknoten, wählen Sie **hinzufügen**, und wählen Sie dann **neues Element**.  
  
2.  Wählen Sie in der Liste der SharePoint-Vorlagen, die **Ereignisempfänger** Vorlage, und nennen Sie sie **ProjectTaskListEventReceiver**.  
  
     Die **Assistent zum Anpassen von SharePoint** angezeigt wird.  
  
3.  Auf der **wählen Sie Empfänger Ereigniseinstellungen** Seite **Listenelementereignisse** als Empfänger Ereignistyp in der **Art-Ereignisempfänger verwenden, möchten Sie den** Liste.  
  
4.  In der **welches Element die Ereignisquelle liegen** wählen **Aufgaben**.  
  
5.  In der Liste der Ereignisse behandelt werden soll, aktivieren Sie das Kontrollkästchen neben **ein Element wurde hinzugefügt,**, und wählen Sie dann die **Fertig stellen** Schaltfläche.  
  
     Ein neuen Ereignis-Empfänger-Knoten wird dem Projekt hinzugefügt, während eine Codedatei mit dem Namen **ProjectTaskListEventReceiver**.  
  
6.  Hinzufügen von Code für die `ItemAdded` Methode in der **ProjectTaskListEventReceiver** Codedatei. Jedes Mal wird eine neue Aufgabe hinzugefügt wird, eine standardmäßige Fälligkeitsdatum und eine Beschreibung der Aufgabe hinzugefügt. Die Standardeinstellung aufgrund Datum ist 1. Juli 2009.  
  
     [!code-vb[SPProjectTaskList#1](../sharepoint/codesnippet/VisualBasic/projecttasklist1/projecttasklisteventreceiver/projecttasklisteventreceiver.vb#1)]
     [!code-csharp[SPProjectTaskList#1](../sharepoint/codesnippet/CSharp/projecttasklist/projecttasklisteventreceiver/projecttasklisteventreceiver.cs#1)]  
  
##  <a name="CustomizeFeature"></a>Anpassen der Liste der Projektfunktion-Aufgabe  
 Wenn Sie eine SharePoint-Lösung erstellen, erstellt Visual Studio automatisch Funktionen für die Projektelemente. Sie können die projekteinstellungen für die Liste von Task für die SharePoint-Website mit dem Funktions-Designer anpassen.  
  
#### <a name="to-customize-the-project-task-list-feature"></a>Anpassen der Liste der Projektfunktion-Aufgabe  
  
1.  In **Projektmappen-Explorer**, erweitern Sie **Funktionen**.  
  
2.  Öffnen Sie das Kontextmenü für **Feature1**, und wählen Sie dann **Sicht-Designer**.  
  
3.  In der **Titel** geben **Projektfunktion Tasks-Liste**.  
  
4.  In der **Bereich** wählen **Web**.  
  
5.  In der **Eigenschaften** Fenster, geben Sie **1.0.0.0** als Wert für die **Version** Eigenschaft.  
  
##  <a name="CustomizePackage"></a>Anpassen des Projekts Aufgabe Liste-Pakets  
 Wenn Sie ein SharePoint-Projekt erstellen, fügt Visual Studio automatisch die Funktionen, die die Standardelemente-Projekt auf das Paket enthalten. Sie können die projekteinstellungen für die Liste von Task für die SharePoint-Website mit dem Paket-Designer anpassen.  
  
#### <a name="to-customize-the-project-task-list-package"></a>Zum Anpassen der Liste der Projektpaket-Aufgabe  
  
1.  In **"SolutionExplorer"**, öffnen Sie das Kontextmenü für **Paket**, und wählen Sie dann **Sicht-Designer**.  
  
2.  In der **Namen** geben **ProjectTaskListPackage**.  
  
3.  Wählen Sie die **Webserver zurücksetzen** Kontrollkästchen.  
  
##  <a name="BuildTest"></a>Erstellen und Testen der Projekt-Aufgabenliste  
 Wenn Sie das Projekt ausführen, wird die SharePoint-Website geöffnet. Sie müssen jedoch manuell auf den Speicherort der Aufgabenliste navigieren.  
  
#### <a name="to-test-the-project-task-list"></a>So testen Sie die Project-Aufgabenliste  
  
1.  Wählen Sie zum Erstellen und Bereitstellen Ihrer Aufgabenliste des Projekts die Taste F5.  
  
     Die SharePoint-Website wird geöffnet.  
  
2.  Wählen Sie die **Home** Registerkarte.  
  
3.  Wählen Sie in der linken Randleiste der **Projektaufgabenliste** Link.  
  
     Die Projekt-Aufgabenliste-Seite wird angezeigt.  
  
4.  In der **Listentools** Registerkarte, und wählen Sie die **Elemente** Registerkarte.  
  
5.  In der **Elemente** gruppieren, wählen Sie die **neues Element** Schaltfläche.  
  
6.  In der **Titel** Text geben **Task1**.  
  
7.  Wählen Sie die **speichern** Schaltfläche.  
  
     Nach der Aktualisierung der Website der **Task1** Aufgabe mit einem Fälligkeitsdatum 7/1/2009 angezeigt wird.  
  
8.  Wählen Sie **Task1**.  
  
     Die Detailansicht des Tasks angezeigt, und die Beschreibung zeigt "This is eine wichtige Aufgabe"  
  
##  <a name="Deploy"></a>Die Projektaufgabenliste bereitstellen  
 Nachdem Sie erstellt und die Projektaufgabenliste zu testen, können Sie es zum Bereitstellen der *lokales System* oder ein *Remotesystem*. Das lokale System ist dem gleichen Computer, auf dem Sie die Lösung entwickelt haben, während ein Remotesystem einem anderen Computer ist.  
  
#### <a name="to-deploy-the-project-task-list-to-the-local-system"></a>Die Projektaufgabenliste mit dem lokalen System bereitstellen  
  
1.  Wählen Sie in der Visual Studio-Menüleiste **erstellen**, **Projektmappe bereitstellen**.  
  
     Visual Studio wiederverwendet wird, den IIS-Anwendungspool, alle vorhandenen Versionen der Lösung zurückzieht, kopiert die Lösung-Paketdatei (.wsp) in SharePoint und aktiviert anschließend die Funktionen. Sie können nun die Projektmappe in SharePoint verwenden. Weitere Informationen zur Bereitstellungskonfiguration finden Sie unter [wie: Bearbeiten einer SharePoint-Bereitstellungskonfiguration](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).  
  
#### <a name="to-deploy-the-project-task-list-to-a-remote-system"></a>Die Aufgabenliste des Projekts zu einem Remotesystem bereitstellen  
  
1.  Wählen Sie in der Visual Studio-Menüleiste **erstellen**, **veröffentlichen**.  
  
2.  In der **veröffentlichen** Dialogfeld Wählen Sie die **Veröffentlichen im Dateisystem** Optionsfeld.  
  
     Können Sie den Zielspeicherort im Ändern der **veröffentlichen** Dialogfeld durch Auswählen der Schaltfläche mit den Auslassungspunkten ![Symbol "Ellipse"](../sharepoint/media/ellipsisicon.gif "Symbol "Ellipse"") , und klicken Sie dann an einen anderen Speicherort navigieren.  
  
3.  Wählen Sie die **veröffentlichen** Schaltfläche.  
  
     WSP-Datei für die Projektmappe wird erstellt.  
  
4.  Kopieren Sie die WSP-Datei mit dem SharePoint-Remotesystem.  
  
5.  Verwenden Sie das PowerShell `Add-SPUserSolution` Befehl aus, um das Paket auf die remote-SharePoint-Installation installieren. (Verwenden Sie für farmlösungen, die `Add-SPSolution` Befehl.)  
  
     Beispielsweise `Add-SPUserSolution C:\MyProjects\ProjectTaskList\ProjectTaskList\bin\Debug\ProjectTaskList.wsp`.  
  
6.  Verwenden Sie das PowerShell `Install-SPUserSolution` Befehl aus, um die Lösung bereitzustellen. (Verwenden Sie für farmlösungen, die `Install-SPSolution` Befehl.)  
  
     Beispielsweise `Install-SPUserSolution -Identity ProjectTaskList.wsp -Site http://NewSiteName`.  
  
     Weitere Informationen über die Remotebereitstellung finden Sie unter [Lösungen mithilfe von](http://go.microsoft.com/fwlink/?LinkId=217680) und [hinzufügen und Bereitstellen von Projektmappen mit PowerShell in SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=217682).  
  
## <a name="next-steps"></a>Nächste Schritte  
 Erfahren Sie mehr über das Anpassen und Bereitstellen von SharePoint-Lösungen in den folgenden Themen:  
  
-   [Exemplarische Vorgehensweise: Erstellen einer Websitespalte, eines Inhaltstyps und einer Liste für SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)  
  
-   [Vorgehensweise: Erstellen eines Ereignisempfängers](../sharepoint/how-to-create-an-event-receiver.md)  
  
-   [WindowsPowerShell für SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=217684)  
  
## <a name="see-also"></a>Siehe auch  
 [Verpacken und Bereitstellen von SharePoint-Projektmappen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  