---
title: 'Exemplarische Vorgehensweise: Erstellen eine benutzerdefinierten Websiteworkflowaktivität | Microsoft-Dokumentation'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, custom workflow activities
- site workflows [SharePoint development in Visual Studio]
- workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, site workflows
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f717345689de9be640e03e9c7d81726a57d494b0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63008328"
---
# <a name="walkthrough-create-a-custom-site-workflow-activity"></a>Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Websiteworkflowaktivität
  In dieser exemplarischen Vorgehensweise veranschaulicht, wie eine benutzerdefinierte Aktivität für eine Website-Ebene mit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. (Workflowdokumentbibliothek auf Siteebene Workflows gelten für die gesamte Website, nicht nur eine Liste auf der Website.) Die benutzerdefinierte Aktivität wird eine Liste der Ankündigungen-Sicherung erstellt und kopiert dann den Inhalt dieser Liste hinein.

 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:

- Erstellen einen Workflow auf.

- Erstellen einer benutzerdefinierten Workflowaktivität.

- Erstellen und löschen eine SharePoint-Liste.

- Kopieren von Elementen aus einer Liste in eine andere.

- Zeigt eine Liste auf der Schnellstartleiste.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Vorraussetzungen
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:

- Unterstützte Editionen von [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] und SharePoint.

- Visual Studio.

## <a name="create-a-site-workflow-custom-activity-project"></a>Erstellen eines Projekts benutzerdefinierte Aktivität für workflow
 Erstellen Sie zunächst ein Projekt zum Speichern und testen die benutzerdefinierte Workflow-Aktivität.

#### <a name="to-create-a-site-workflow-custom-activity-project"></a>Erstellen ein Projekts benutzerdefinierte Aktivität für workflow

1. Wählen Sie auf der Menüleiste **Datei** > **neu** > **Projekt** zum Anzeigen der **neues Projekt** Dialogfeld.

2. Erweitern Sie die **SharePoint** Knoten entweder **Visual C#-** oder **Visual Basic**, und wählen Sie dann die **2010** Knoten.

3. In der **Vorlagen** Bereich, wählen Sie die **SharePoint 2010-Projekt** Vorlage.

4. In der **Namen** geben **AnnouncementBackup**, und wählen Sie dann die **OK** Schaltfläche.

     Die **SharePoint Customization Wizard** angezeigt wird.

5. Auf der **Geben Sie die Website und Sicherheitsebene für debugging** Seite die **als farmlösung bereitstellen** Optionsfeld aus, und wählen Sie dann die **Fertig stellen** Schaltfläche zum Akzeptieren der Trust-Ebene und Standard-Website.

     In diesem Schritt wird die Vertrauensebene für die Lösung als Farm-Lösung, die einzig verfügbare Option für Workflowprojekte.

6. In **Projektmappen-Explorer**, wählen Sie den Projektknoten und anschließend auf der Menüleiste die Optionen **Projekt** > **neues Element hinzufügen**.

7. Entweder unter **Visual C#-** oder **Visual Basic**, erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.

8. In der **Vorlagen** Bereich Wählen Sie die **sequenzieller Workflow (nur Farmlösung)** Vorlage, und wählen Sie dann die **hinzufügen** Schaltfläche.

     Die **SharePoint Customization Wizard** angezeigt wird.

9. Auf der **Geben Sie den Workflownamen für das Debuggen** Seite aus, übernehmen Sie den Standardnamen (AnnouncementBackup - Workflow1). Ändern Sie den Typ des Workflow-Vorlage zum **Siteworkflow**, und wählen Sie dann die **Weiter** Schaltfläche.

10. Wählen Sie die **Fertig stellen** Schaltfläche, um die restlichen Standardeinstellungen akzeptieren.

## <a name="add-a-custom-workflow-activity-class"></a>Fügen Sie eine benutzerdefinierten Workflow Activity-Klasse
 Als Nächstes fügen Sie eine Klasse, um das Projekt, um den Code für die benutzerdefinierte Workflow-Aktivität enthält.

#### <a name="to-add-a-custom-workflow-activity-class"></a>Hinzufügen eine benutzerdefinierten Workflow Activity-Klasse

1. Wählen Sie auf der Menüleiste **Projekt** > **neues Element hinzufügen** zum Anzeigen der **neues Element hinzufügen** Dialogfeld.

2. In der **installierte Vorlagen** Strukturansicht, und wählen Sie die **Code** Knoten, und wählen Sie dann die **Klasse** Vorlage in der Liste von Projektelementvorlagen. Verwenden Sie den Standardnamen Class1. Wählen Sie die Schaltfläche **Hinzufügen** aus.

3. Ersetzen Sie sämtlichen Code in Class1 durch Folgendes:

     [!code-csharp[SP_AnnBackup#1](../sharepoint/codesnippet/CSharp/announcementbackup/class1.cs#1)]
     [!code-vb[SP_AnnBackup#1](../sharepoint/codesnippet/VisualBasic/announcementbackupvb/class1.vb#1)]

4. Speichern Sie das Projekt, und anschließend auf der Menüleiste die Optionen **erstellen** > **Projektmappe**.

     Class1 angezeigt wird, als benutzerdefinierte Aktion in der **Toolbox** auf die **AnnouncementBackup Komponenten** Registerkarte.

## <a name="add-the-custom-activity-to-the-site-workflow"></a>Fügen Sie die benutzerdefinierte Aktivität auf der Website-workflow
 Fügen Sie eine Aktivität zum Workflow, um den benutzerdefinierten Code enthalten.

#### <a name="to-add-a-custom-activity-to-the-site-workflow"></a>Zum Hinzufügen einer benutzerdefinierten Aktivität auf der Website-workflow

1. Öffnen Sie Workflow1 im Workflow-Designer in der Entwurfsansicht.

2. Ziehen Sie die Class1 aus der **Toolbox** , damit es unter angezeigt wird der `onWorkflowActivated1` wählen Sie die Aktivität, oder Sie öffnen das Kontextmenü für Class1, **kopieren**, öffnen das Kontextmenü für die Zeile unter der `onWorkflowActivated1` Aktivität, und wählen Sie dann **einfügen**.

3. Speichern Sie das Projekt.

## <a name="test-the-site-workflow-custom-activity"></a>Testen der benutzerdefinierten Websiteworkflowaktivität
 Als Nächstes führen Sie das Projekt, und starten Sie den Websiteworkflow. Die benutzerdefinierte Aktivität erstellt eine Sicherungsliste von Ankündigungen und kopiert den Inhalt aus der Liste der Ankündigungen für das aktuelle hinein. Der Code überprüft auch, ob eine Liste der Sicherungen, die bereits vor dem Erstellen einer vorhanden ist. Wenn eine Sicherungsliste bereits vorhanden ist, wird sie gelöscht. Der Code fügt auch einen Link in die neue Liste auf der Schnellstartleiste der SharePoint-Website.

#### <a name="to-test-the-site-workflow-custom-activity"></a>So testen Sie die benutzerdefinierten Websiteworkflowaktivität

1. Wählen Sie die **F5** Taste, um das Projekt ausführen und in SharePoint bereitzustellen.

2. Wählen Sie auf der Schnellstartleiste der **listet** Link, um alle Listen anzuzeigen, die in der SharePoint-Website verfügbar sind. Beachten Sie, dass es nur eine Liste mit dem Namen Ankündigungen **Ankündigungen**.

3. Wählen Sie am oberen Rand der SharePoint-Website, die **Websiteworkflows** Link.

4. Wählen Sie den Anfang einer neuen Workflow-Bereich, der **AnnouncementBackup - Workflow1** Link. Dies startet den Websiteworkflow und führt den Code in die benutzerdefinierte Aktion.

5. Wählen Sie auf der Schnellstartleiste der **Ankündigungen Sicherung** Link. Beachten Sie, dass alle Ankündigungen, die in befinden die **Ankündigungen** Liste in diese neue Liste kopiert wurden.

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Erstellen eines Ereignisempfängers](../sharepoint/how-to-create-an-event-receiver.md)
- [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)
