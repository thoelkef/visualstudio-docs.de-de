---
title: "Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Websiteworkflowaktivit&#228;t"
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
  - "Benutzerdefinierte Workflowaktivitäten [SharePoint-Entwicklung in Visual Studio]"
  - "SharePoint-Entwicklung in Visual Studio, Benutzerdefinierte Workflowaktivitäten"
  - "SharePoint-Entwicklung in Visual Studio, Websiteworkflows"
  - "Websiteworkflows [SharePoint-Entwicklung in Visual Studio]"
  - "Workflowaktivitäten [SharePoint-Entwicklung in Visual Studio]"
ms.assetid: 8219a779-c27b-4186-92c9-5bda03328aa9
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Websiteworkflowaktivit&#228;t
  In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie mit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] eine benutzerdefinierte Aktivität für einen Workflow auf Websiteebene erstellt wird. \(Workflows auf Websiteebene gelten für die gesamte Website und nicht nur für eine Liste der Website.\) Die benutzerdefinierte Aktivität erstellt eine Sicherungskopie der Ankündigungsliste, in die dann der Inhalt der Ankündigungsliste kopiert wird.  
  
 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:  
  
-   Erstellen eines Workflows auf Websiteebene.  
  
-   Erstellen einer benutzerdefinierten Workflowaktivität.  
  
-   Erstellen und Löschen einer SharePoint\-Liste.  
  
-   Kopieren von Elementen aus einer Liste in eine andere.  
  
-   Anzeigen einer Liste auf der Schnellstartleiste.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Unterstützte Editionen von [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] und SharePoint.  Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## Erstellen eines benutzerdefinierten Websiteworkflow\-Aktivitätsprojekts  
 Erstellen Sie zunächst ein Projekt, um die benutzerdefinierte Workflowaktivität zu speichern und zu testen.  
  
#### So erstellen Sie ein benutzerdefiniertes Websiteworkflow\-Aktivitätsprojekt  
  
1.  Klicken Sie auf der Menüleiste **Neu**, **Projekt**, **Datei**, um das Dialogfeld **Neues Projekt** anzuzeigen.  
  
2.  Erweitern Sie den Knoten **SharePoint** entweder unter **Visual C\#** oder **Visual Basic**, und wählen Sie den Knoten **2010** aus.  
  
3.  Im Bereich **Vorlagen** wählen Sie die Vorlage **SharePoint 2010\-Projekt** aus.  
  
4.  Im Feld **Name** geben Sie AnnouncementBackup ein und wählen Sie dann die Schaltfläche **OK** aus.  
  
     Der **Assistent zum Anpassen von SharePoint** wird angezeigt.  
  
5.  Auf der Seite **Site und Sicherheitsebene für Debugging angeben** wählen Sie das Optionsfeld **Als Farmlösung bereitstellen** aus, und wählen Sie die Schaltfläche **Fertig stellen**, um die Vertrauensebenen\- und Standardsite zu übernehmen.  
  
     In diesem Schritt wird die Vertrauensebene für die Lösung als Farmlösung festgelegt, wobei es sich um die einzige verfügbare Option für Workflowprojekte handelt.  
  
6.  Wählen Sie im **Projektmappen\-Explorer** den Projektknoten, und klicken Sie auf der Menüleiste, **Projekt** auswählen, **Neues Element hinzufügen** aus.  
  
7.  Entweder unter **Visual C\#** oder den Knoten **Visual BasicSharePoint**, und wählen Sie den Knoten **2010** aus.  
  
8.  Im Bereich **Vorlagen** wählen Sie die Vorlage **Sequenzieller Workflow \(nur Farmlösung\)** aus, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.  
  
     Der **Assistent zum Anpassen von SharePoint** wird angezeigt.  
  
9. Auf der Seite **Workflownamen für das Debugging angeben** übernehmen Sie den Standardnamen \(AnnouncementBackup \- Workflow1\).  Ändern Sie den Workflowvorlagentyp in **Siteworkflow**, und wählen Sie die Schaltfläche **Weiter** aus.  
  
10. Wählen Sie die Schaltfläche **Fertig stellen**, um die verbleibenden Standardeinstellungen zu akzeptieren.  
  
## Hinzufügen einer benutzerdefinierten Workflowaktivitätsklasse  
 Fügen Sie dem Projekt danach eine Klasse hinzu, die den Code für die benutzerdefinierte Workflowaktivität enthalten soll.  
  
#### So fügen Sie eine benutzerdefinierte Workflowaktivitätsklasse hinzu  
  
1.  Wählen Sie in der Menüleiste **Neues Element hinzufügen**, **Projekt**, um das Dialogfeld **Neues Element hinzufügen** anzuzeigen.  
  
2.  In der Strukturansicht **Installierte Vorlagen** wählen Sie den Knoten **Code**, und wählen Sie dann die Vorlage **Klasse** in der Liste der Projektelementvorlagen aus.  Verwenden Sie den Standardnamen Class1.  Wählen Sie die Schaltfläche **Hinzufügen** aus.  
  
3.  Ersetzen Sie den gesamten Code in Class1 durch den folgenden Code:  
  
     [!code-csharp[SP_AnnBackup#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_annbackup/cs/class1.cs#1)]
     [!code-vb[SP_AnnBackup#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_annbackup/vb/class1.vb#1)]  
  
4.  Speichern Sie das Projekt, und wählen dann, auf der Menüleiste, wählen Sie **Projektmappe erstellen**, **Erstellen** aus.  
  
     Class1 wird als benutzerdefinierte Aktion in **Werkzeugkasten** auf der Registerkarte **AnnouncementBackup\-Komponenten**.  
  
## Hinzufügen der benutzerdefinierten Aktivität zum Websiteworkflow  
 Fügen Sie dem Workflow danach eine Aktivität hinzu, die den benutzerdefinierten Code enthalten soll.  
  
#### So fügen Sie dem Websiteworkflow eine benutzerdefinierte Aktivität hinzu  
  
1.  Öffnen Sie Workflow1 im Workflow\-Designer in der Entwurfsansicht.  
  
2.  Ziehen Sie Class1 von **Werkzeugkasten**, sodass die Aktivität unter der `onWorkflowActivated1` angezeigt wird, oder öffnen Sie das Kontextmenü für Class1, wählen Sie **Kopieren** aus, öffnen Sie das Kontextmenü für die Zeile unter der Aktivität `onWorkflowActivated1`, und wählen Sie dann **Einfügen** aus.  
  
3.  Speichern Sie das Projekt.  
  
## Testen der benutzerdefinierten Websiteworkflowaktivität  
 Führen Sie danach das Projekt aus, und starten Sie den Websiteworkflow.  Die benutzerdefinierte Aktivität erstellt eine Sicherungskopie der Ankündigungsliste, in die dann der Inhalt der aktuellen Ankündigungsliste kopiert wird.  Der Code überprüft vor dem Erstellen einer Sicherungsliste auch, ob bereits eine vorhanden ist.  Wenn bereits eine Sicherungsliste vorhanden ist, wird diese gelöscht.  Im Code wird außerdem auf der Schnellstartleiste der SharePoint\-Website ein Link zur neuen Liste hinzugefügt.  
  
#### So testen Sie die benutzerdefinierte Websiteworkflowaktivität  
  
1.  Drücken Sie die F5\-TASTE, um das Projekt auszuführen und in SharePoint bereitzustellen.  
  
2.  Klicken Sie auf der Schnellstartleiste wählen Sie den Link **Listen**, um alle Listen anzuzeigen, die in der SharePoint\-Website verfügbaren.  Beachten Sie, dass für Ankündigungen nur eine Liste mit dem Namen **Ankündigungen** vorhanden ist.  
  
3.  Am oberen Rand der SharePoint\-Webseite Wählen Sie den Link **Website\-Workflows** aus.  
  
4.  Mit dem Start eines neuen Workflowabschnitt, wählen Sie den Link **AnnouncementBackup – Workflow1** aus.  Hiermit wird der Websiteworkflow gestartet und der Code in der benutzerdefinierten Aktion ausgeführt.  
  
5.  Klicken Sie auf der Schnellstartleiste auf den Link **Ankündigungssicherung** aus.  Beachten Sie, dass alle in der Liste **Ankündigungen** enthaltenen Ankündigungen in diese neue Liste kopiert wurden.  
  
## Siehe auch  
 [Gewusst wie: Erstellen eines Ereignisempfängers](../sharepoint/how-to-create-an-event-receiver.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  