---
title: 'Exemplarische Vorgehensweise: Bereitstellen einer Aufgabenlistendefinition für Projekt | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3df4f161eddc5d10b77887b99d93be2204821c24
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826623"
---
# <a name="walkthrough-deploy-a-project-task-list-definition"></a>Exemplarische Vorgehensweise: Bereitstellen einer Aufgabenlistendefinition für Projekt

In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie mit [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] zum Erstellen, anpassen, Debuggen und Bereitstellen eine SharePoint-Liste zum Nachverfolgen von Projektaufgaben.

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Vorraussetzungen

- Unterstützte Editionen von Microsoft Windows und SharePoint.

- Visual Studio 2017 oder Azure DevOps-Dienste.

## <a name="create-a-sharepoint-list"></a>Erstellen Sie eine SharePoint-Liste

Erstellen Sie ein Projekt der SharePoint-Liste, und ordnen Sie die Listendefinition Aufgaben.

1. Öffnen der **neues Projekt** Dialogfeld erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.

2. In der **Vorlagen** Bereich, wählen Sie die **SharePoint 2010-Projekt** Vorlage, nennen Sie das Projekt **ProjectTaskList**, und wählen Sie dann die **OK**Schaltfläche.

     Die **SharePoint Customization Wizard** angezeigt wird.

3. Geben Sie der lokalen SharePoint-Website, die Sie verwenden, für das Debuggen, wählen Sie die **als farmlösung bereitstellen** Optionsfeld aus, und wählen Sie dann die **Fertig stellen** Schaltfläche.

4. Öffnen Sie das Kontextmenü für das Projekt, und wählen Sie dann **hinzufügen** > **neues Element**.

5. In der **Vorlagen** Bereich Wählen Sie die **Liste** Vorlage, und wählen Sie dann die **hinzufügen** Schaltfläche.

     Die **SharePoint Customization Wizard** angezeigt wird.

6. In der **welchen Namen möchten Sie für der Liste angezeigt werden soll?** geben **Projektaufgabenliste**.

7. Wählen Sie die **erstellen Sie eine nicht anpassbare Liste basierend auf einem bestehenden Listentyp der** Optionsfeld aus, und klicken Sie dann in der Liste wählen **Aufgaben**, und wählen Sie dann die **Fertig stellen** Schaltfläche.

     Die Liste, Funktion und Paket angezeigt, **Projektmappen-Explorer**.

## <a name="add-an-event-receiver"></a>Hinzufügen eines Ereignisempfängers

In der Aufgabenliste können Sie einen Ereignisempfänger, die den Gesamtbetrag automatisch legt hinzufügen Datum und die Beschreibung des Tasks. Das folgende Verfahren werden die Listeninstanz als einen Ereignisempfänger einen einfacher Ereignishandler hinzugefügt.

1. Öffnen Sie das Kontextmenü für den Projektknoten, und wählen **hinzufügen**, und wählen Sie dann **neues Element**.

2. Wählen Sie in der Liste der SharePoint-Vorlagen, die **Ereignisempfänger** Vorlage, und nennen Sie sie **ProjectTaskListEventReceiver**.

     Die **SharePoint Customization Wizard** angezeigt wird.

3. Auf der **Ereignisempfängereinstellungen auswählen** Seite **Listenelementereignisse** als Empfänger Ereignistyp in der **Art der Ereignisempfänger möchten Sie** Liste.

4. In der **welche Artikel befinden sollte, die Ereignisquelle** wählen **Aufgaben**.

5. In der Liste der Ereignisse behandelt werden soll, aktivieren Sie das Kontrollkästchen neben **ein Element wurde hinzugefügt**, und wählen Sie dann die **Fertig stellen** Schaltfläche.

     Ein neuer Event Receiver-Knoten wird dem Projekt hinzugefügt, während eine Codedatei mit dem Namen **ProjectTaskListEventReceiver**.

6. Fügen Sie Code in die `ItemAdded` -Methode in der die **ProjectTaskListEventReceiver** Codedatei. Jedes Mal wird eine neue Aufgabe hinzugefügt wird, eine standardmäßige Fälligkeitsdatum und eine Beschreibung der Aufgabe hinzugefügt. Der Standardwert aufgrund Datum der 1. Juli 2009 ist.

     [!code-vb[SPProjectTaskList#1](../sharepoint/codesnippet/VisualBasic/projecttasklist1/projecttasklisteventreceiver/projecttasklisteventreceiver.vb#1)]
     [!code-csharp[SPProjectTaskList#1](../sharepoint/codesnippet/CSharp/projecttasklist/projecttasklisteventreceiver/projecttasklisteventreceiver.cs#1)]

## <a name="customize-the-project-task-list-feature"></a>Das Feature für den Task Listen von Projekt anpassen

Wenn Sie eine SharePoint-Lösung erstellen, erstellt Visual Studio automatisch Funktionen für den standardmäßigen Projektelemente. Sie können die projekteinstellungen für die Liste von Task für die SharePoint-Website mithilfe von Funktions-Designer anpassen.

1. In **Projektmappen-Explorer**, erweitern Sie **Features**.

2. Öffnen Sie das Kontextmenü für **Feature1**, und wählen Sie dann **Ansicht-Designer**.

3. In der **Titel** geben **Projektfeature Tasks-Liste**.

4. In der **Bereich** wählen **Web**.

5. In der **Eigenschaften** Fenster eingeben **1.0.0.0** als Wert für die **Version** Eigenschaft.

## <a name="customize-the-project-task-list-package"></a>Passen Sie das Projekt umgebungsaufgabenlisten-Paket

Wenn Sie ein SharePoint-Projekt erstellen, fügt Visual Studio automatisch die Funktionen, die die Standard-Projektelemente, auf das Paket enthalten. Sie können die projekteinstellungen für die Liste von Task für die SharePoint-Website anpassen, mit der Paket-Designer.

1. In **SolutionExplorer**, öffnen Sie das Kontextmenü für **Paket**, und wählen Sie dann **Ansicht-Designer**.

2. In der **Namen** geben **ProjectTaskListPackage**.

3. Wählen Sie die **Webserver zurücksetzen** Kontrollkästchen.

## <a name="build-and-test-the-project-task-list"></a>Erstellen Sie und Testen Sie die Projekt-Aufgabenliste

Wenn Sie das Projekt ausführen, wird die SharePoint-Website geöffnet. Sie müssen jedoch manuell auf den Speicherort der Aufgabenliste navigieren.

1. Wählen Sie die **F5** Schlüssel zum Erstellen und Bereitstellen Ihrer Projekt-Aufgabenliste.

     Die SharePoint-Website wird geöffnet.

2. Wählen Sie die **Startseite** Registerkarte.

3. Wählen Sie in der linken Randleiste die **Projektaufgabenliste** Link.

     Die Projekt-Aufgabenliste-Seite wird angezeigt.

4. In der **Listentools** Registerkarte die **Elemente** Registerkarte.

5. In der **Elemente** Gruppe der **neues Element** Schaltfläche.

6. In der **Titel** Text geben **Task1**.

7. Wählen Sie die **speichern** Schaltfläche.

     Nach der Aktualisierung des Standorts die **Task1** Aufgabe mit Fälligkeit von 7/1/2009 angezeigt wird.

8. Wählen Sie **Task1**.

     In der Detailansicht der Aufgabe angezeigt wird, und die Beschreibung zeigt "Dies ist eine wichtige Aufgabe."

## <a name="deploy-the-project-task-list"></a>Die Projektaufgabenliste bereitstellen

Nachdem Sie erstellt und die Projektaufgabenliste zu testen, können Sie es zum Bereitstellen der *lokales System* oder *Remotesystem*. Das lokale System ist dem gleichen Computer, auf dem Sie die Projektmappe, aus, während ein Remotesystem einen anderen Computer ist.

### <a name="to-deploy-the-project-task-list-to-the-local-system"></a>Die Projekt-Aufgabenliste auf das lokale System bereitstellen.

Wählen Sie in der Visual Studio-Menüleiste **erstellen** > **Projektmappe bereitstellen**.

Visual Studio der IIS-Anwendungspool wird wiederverwendet, alle vorhandenen Versionen der Lösung zieht, kopiert das Lösungspaket (*.wsp*)-Datei in SharePoint, und klicken Sie dann die Funktionen werden aktiviert. Sie können jetzt die Lösung in SharePoint verwenden. Weitere Informationen zur Bereitstellungskonfiguration finden Sie unter [Vorgehensweise: Bearbeiten einer SharePoint-Bereitstellungskonfiguration](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).

### <a name="to-deploy-the-project-task-list-to-a-remote-system"></a>Die Projekt-Aufgabenliste auf einem Remotesystem bereitstellen

1. Wählen Sie in der Visual Studio-Menüleiste **erstellen** > **veröffentlichen**.

2. In der **veröffentlichen** Dialogfeld auf die **im Dateisystem veröffentlichen** Optionsfeld aus.

     Sie können auch am Zielspeicherort im Ändern der **veröffentlichen** Dialogfeld durch Auswählen der Schaltfläche mit den Auslassungspunkten ![Symbol "Ellipse"](../sharepoint/media/ellipsisicon.gif "Symbol \"Ellipse\"") , und klicken Sie dann an einen anderen Speicherort navigieren.

3. Wählen Sie die **veröffentlichen** Schaltfläche.

     Ein *.wsp* Datei für die Projektmappe erstellt wird.

4. Kopieren der *.wsp* Datei in das remote SharePoint-System.

5. Verwenden Sie das PowerShell `Add-SPUserSolution` Befehl aus, um das Paket auf die remote-SharePoint-Installation installieren. (Verwenden Sie für die farmlösungen, die `Add-SPSolution` Befehl.)

     Beispielsweise `Add-SPUserSolution C:\MyProjects\ProjectTaskList\ProjectTaskList\bin\Debug\ProjectTaskList.wsp`.

6. Verwenden Sie das PowerShell `Install-SPUserSolution` Befehl aus, um die Lösung bereitzustellen. (Verwenden Sie für die farmlösungen, die `Install-SPSolution` Befehl.)

     Beispielsweise `Install-SPUserSolution -Identity ProjectTaskList.wsp -Site http://NewSiteName`.

     Weitere Informationen zur Remotebereitstellung finden Sie unter [Lösungen mithilfe von](http://go.microsoft.com/fwlink/?LinkId=217680) und [hinzufügen und Bereitstellen von Lösungen mithilfe von PowerShell in SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=217682).

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Anpassen und Bereitstellen von SharePoint-Lösungen in den folgenden Themen:

- [Exemplarische Vorgehensweise: Erstellen einer Websitespalte, den Inhaltstyp und die Liste für SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)

- [Vorgehensweise: Erstellen eines Ereignisempfängers](../sharepoint/how-to-create-an-event-receiver.md)

- [Windows PowerShell für SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=217684)

## <a name="see-also"></a>Siehe auch
[Packen und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
