---
title: "Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Websiteworkflowaktivität | Microsoft Docs"
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
- custom workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, custom workflow activities
- site workflows [SharePoint development in Visual Studio]
- workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, site workflows
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: b723635b1baecfec4bddb2339414d57803c76d5d
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-create-a-custom-site-workflow-activity"></a>Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Websiteworkflowaktivität
  In dieser exemplarischen Vorgehensweise veranschaulicht, wie eine benutzerdefinierte Aktivität für einen Workflow Siteebene mit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. (Siteebene Workflows vornehmen, um den gesamten Standort, nicht nur eine Liste auf der Website.) Die benutzerdefinierte Aktivität erstellt eine Sicherungskopie Ankündigungen und klicken Sie dann den Inhalt der Ankündigungen hinein kopiert.  
  
 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:  
  
-   Erstellen eines Workflows für die Website-Ebene an.  
  
-   Erstellen einer benutzerdefinierten Workflowaktivität.  
  
-   Erstellen und Löschen einer SharePoint-Liste.  
  
-   Kopieren von Elementen aus einer Liste in eine andere.  
  
-   Anzeigen einer Liste auf der Schnellstartleiste.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Unterstützte Editionen von [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] und SharePoint. Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## <a name="creating-a-site-workflow-custom-activity-project"></a>Erstellen eine benutzerdefinierte Workflow-Aktivitätsprojekt  
 Erstellen Sie zunächst ein Projekt zum Speichern und testen die benutzerdefinierte Workflow-Aktivität.  
  
#### <a name="to-create-a-site-workflow-custom-activity-project"></a>So erstellen eine benutzerdefinierte Workflow-Aktivitätsprojekt  
  
1.  Wählen Sie in der Menüleiste **Datei**, **neu**, **Projekt** zum Anzeigen der **neues Projekt** (Dialogfeld).  
  
2.  Erweitern Sie die **SharePoint** Knoten unter einem **Visual C#-** oder **Visual Basic**, und wählen Sie dann die **2010** Knoten.  
  
3.  In der **Vorlagen** Bereich, wählen Sie die **SharePoint 2010-Projekt** Vorlage.  
  
4.  In der **Namen** geben **AnnouncementBackup**, und wählen Sie dann die **OK** Schaltfläche.  
  
     Die **Assistent zum Anpassen von SharePoint** angezeigt wird.  
  
5.  Auf der **Geben Sie die Website und die Sicherheit für das Debuggen** Seite der **als farmlösung bereitstellen** Optionsfeld aus, und wählen Sie dann die **Fertig stellen** Schaltfläche zum Akzeptieren der Vertrauensstellung Ebene und Standard-Website.  
  
     In diesem Schritt wird die Vertrauensebene für die Projektmappe als farmlösung, die einzig verfügbare Option für Workflowprojekte.  
  
6.  In **Projektmappen-Explorer**, wählen Sie den Projektknoten, und wählen Sie dann auf der Menüleiste **Projekt**, **neues Element hinzufügen**.  
  
7.  Unter einem **Visual C#-** oder **Visual Basic**, erweitern Sie die **SharePoint** Knoten, und wählen Sie dann die **2010** Knoten.  
  
8.  In der **Vorlagen** Bereich, wählen Sie die **sequenzieller Workflow (nur Farmlösung)** Vorlage, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
     Die **Assistent zum Anpassen von SharePoint** angezeigt wird.  
  
9. Auf der **Geben Sie den Workflownamen für das Debuggen** Seite, übernehmen Sie den Standardnamen (AnnouncementBackup - Workflow1). Ändern Sie den Typ des Workflow-Vorlage zu **Website-Workflow**, und wählen Sie dann die **Weiter** Schaltfläche.  
  
10. Wählen Sie die **Fertig stellen** Schaltfläche, um die restlichen Standardeinstellungen zu übernehmen.  
  
## <a name="adding-a-custom-workflow-activity-class"></a>Hinzufügen einer benutzerdefinierten Workflow Activity-Klasse  
 Als Nächstes fügen Sie eine Klasse, um das Projekt enthält den Code für die benutzerdefinierte Workflow-Aktivität.  
  
#### <a name="to-add-a-custom-workflow-activity-class"></a>So fügen Sie einen benutzerdefinierten Workflow Activity-Klasse hinzu  
  
1.  Wählen Sie in der Menüleiste **Projekt**, **neues Element hinzufügen** zum Anzeigen der **neues Element hinzufügen** (Dialogfeld).  
  
2.  In der **installierte Vorlagen** Strukturansicht, und wählen Sie die **Code** Knoten, und wählen Sie dann die **Klasse** Vorlage in der Liste der Projektelementvorlagen. Verwenden Sie den Standardnamen Class1. Wählen Sie die Schaltfläche **Hinzufügen** aus.  
  
3.  Ersetzen Sie alle des Codes in Class1 durch Folgendes:  
  
     [!code-csharp[SP_AnnBackup#1](../sharepoint/codesnippet/CSharp/announcementbackup/class1.cs#1)]
     [!code-vb[SP_AnnBackup#1](../sharepoint/codesnippet/VisualBasic/announcementbackupvb/class1.vb#1)]  
  
4.  Speichern Sie das Projekt, und wählen Sie dann auf der Menüleiste **erstellen**, **Projektmappe**.  
  
     Class1 angezeigt wird, wie eine benutzerdefinierte Aktion in der **Toolbox** auf die **AnnouncementBackup Komponenten** Registerkarte.  
  
## <a name="adding-the-custom-activity-to-the-site-workflow"></a>Die benutzerdefinierte Aktivität hinzufügen auf der Website-Workflow  
 Fügen Sie eine Aktivität des Workflows der benutzerdefinierten Code enthalten.  
  
#### <a name="to-add-a-custom-activity-to-the-site-workflow"></a>Hinzufügen eine benutzerdefinierte Aktivität zu der Website-Workflow  
  
1.  Öffnen Sie Workflow1 im Workflow-Designer in der Entwurfsansicht.  
  
2.  Ziehen Sie die Class1 aus der **Toolbox** , damit es unter angezeigt wird der `onWorkflowActivated1` Aktivität, oder Sie öffnen das Kontextmenü für Class1, wählen Sie **Kopie**, öffnen Sie das Kontextmenü für die Zeile unter der `onWorkflowActivated1` Aktivität, und wählen Sie dann **einfügen**.  
  
3.  Speichern Sie das Projekt.  
  
## <a name="testing-the-site-workflow-custom-activity"></a>Testen der benutzerdefinierten Websiteworkflowaktivität  
 Als Nächstes führen Sie das Projekt, und starten Sie den Websiteworkflow. Die benutzerdefinierte Aktivität erstellt eine Sicherungsliste von Ankündigungen und kopiert den Inhalt aus der Liste der Ankündigungen für das aktuelle hinein. Der Code überprüft auch, ob eine Sicherungsliste vor dem Erstellen einer bereits vorhanden ist. Wenn bereits eine Sicherungsliste vorhanden ist, wird er gelöscht. Der Code fügt auch einen Link in die neue Liste auf der Schnellstartleiste der SharePoint-Website.  
  
#### <a name="to-test-the-site-workflow-custom-activity"></a>So testen Sie die benutzerdefinierten Websiteworkflowaktivität  
  
1.  Wählen Sie die Taste F5, um führen Sie das Projekt und in SharePoint bereitzustellen.  
  
2.  Wählen Sie in der Schnellstartleiste der **listet** Link, um alle Listen anzuzeigen, die in der SharePoint-Website verfügbar sind. Beachten Sie, dass es nur eine Liste für Ankündigungen, die mit dem Namen **Ankündigungen**.  
  
3.  Wählen Sie am oberen Rand der SharePoint-Webseite, die **Websiteworkflows** Link.  
  
4.  Wählen Sie aus dem Start eine neue Workflow-Bereich, der **AnnouncementBackup - Workflow1** Link. Dies startet den Workflow, Standort und führt den Code in der benutzerdefinierten Aktion.  
  
5.  Wählen Sie in der Schnellstartleiste der **Ankündigungen Sicherung** Link. Beachten Sie, dass alle die Ankündigungen, die in enthaltenen der **Ankündigungen** Liste auf dieses neue Liste kopiert wurden.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Erstellen eines Ereignisempfängers](../sharepoint/how-to-create-an-event-receiver.md)   
 [Entwickeln von SharePoint-Projektmappen](../sharepoint/developing-sharepoint-solutions.md)  
  
  