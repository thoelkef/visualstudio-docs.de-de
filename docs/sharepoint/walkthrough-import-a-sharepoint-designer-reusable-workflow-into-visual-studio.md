---
title: 'Exemplarische Vorgehensweise: Importieren ein Wiederverwendbaren Workflows aus SharePoint Designer in Visual Studio | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.WSPImport.ImportWF
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing reusable workflows
- reusable workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2269beef06f7ca43556c2c00493ac8d7cb1c4ad5
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2018
ms.locfileid: "37118983"
---
# <a name="walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio"></a>Exemplarische Vorgehensweise: Importieren eines wiederverwendbaren Workflows aus SharePoint Designer in Visual Studio
  In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie zum Importieren eines wiederverwendbaren Workflows in SharePoint Designer 2010 in erstellt eine [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint-Workflowprojekt.  
  
 In SharePoint Designer erstellte Workflows oder *deklarativer Workflows*, bestehen aus [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] -Anweisungen anstelle von Code. SharePoint Designer 2010 führt *wiederverwendbare Workflows*, welche sind portable, deklarativen Workflows, die von anderen Listen in SharePoint-Websites verwendet werden können.  
  
 In erstellte Workflows [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)], z. B. sequenzielle und Zustandsautomatworkflows, heißen *code Workflows*. Codeworkflows bestehen aus XML-Dateien und Codemodule, die in denen Benutzern das Verhalten des Workflows angepasst werden können.  
  
 Visual Studio ermöglicht Ihnen das Importieren von wiederverwendbaren Workflows in SharePoint Designer 2010 erstellt und in Codeworkflows zur Verwendung in Ihrer SharePoint-Websites konvertieren.  
  
 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:  
  
-   Erstellen eine einfache, wiederverwendbare Workflows in SharePoint Designer.  
  
-   Die wiederverwendbaren Workflows aus SharePoint Designer zum Exportieren einer *.wsp* Datei in SharePoint.  
  
-   Importieren der *.wsp* in Datei [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mit dem Projekt Wiederverwendbaren Workflow importieren.  
  
-   Ändern den Workflow durch Hinzufügen von Code.  
  
-   Verwenden den importierten Workflow in einer SharePoint-Website ein.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Unterstützte Editionen von [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] und SharePoint. Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
-   Microsoft [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] SharePoint Designer 2010.  
  
## <a name="create-target-sharepoint-subsites"></a>Ziel-SharePoint-Unterwebsites erstellen
 Erstellen Sie zunächst zwei neue SharePoint-Unterwebsites: einer der wiederverwendbaren Workflows aus SharePoint Designer, ein weiteres zum Hosten der konvertierte Workflows zu hosten.  
  
#### <a name="to-create-sharepoint-subsites"></a>Zum Erstellen von SharePoint Unterwebsites  
  
1.  Wählen Sie auf der Menüleiste in SharePoint Designer 2010 **Datei** > **neue leere Website**.  
  
2.  In der **neue leere Website** (Dialogfeld), navigieren Sie zu einer SharePoint-Website, in dem Sie den Workflow erstellen oder verwenden Sie den Wert http:// möchten*SystemName*/ und wählen Sie dann die **OK** Schaltfläche ".  
  
     Die Startseite wird angezeigt.  
  
3.  In der **Unterwebsites** Abschnitt der **neu** Schaltfläche.  
  
4.  In der **neu** Dialogfeld wählen **SharePoint-Vorlagen** aus der Liste im linken Bereich, und wählen Sie **Teamwebsite** aus der Liste im rechten Bereich.  
  
5.  In der **Geben Sie den Speicherort der Website** ersetzen die Word **Unterwebsite** in der URL durch **SPD1**, und wählen Sie dann die **OK** Schaltfläche.  
  
     Die neue Unterwebsite in SharePoint Designer wird geöffnet. Schließen Sie diese Instanz von SharePoint Designer, und wechseln Sie zurück zur ersten Instanz (Standort der obersten Ebene).  
  
6.  Wiederholen Sie die Schritte 3 bis 5, um die zweite Unterwebsite ein, und Ersetzen Sie dabei das Wort erstellen **Unterwebsite** in die [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] mit **SPD2**.  
  
## <a name="create-a-sharepoint-designer-reusable-workflow"></a>Erstellen eines wiederverwendbaren Workflows aus SharePoint Designer
 Da SharePoint nicht wiederverwendbare Workflows enthalten, die Sie in diesem Beispiel verwenden können, erstellen Sie eine. Wenn ein Benutzer eine neue Aufgabe in der Aufgabenliste eingibt, die einen bestimmten Titel hat, ist die Aufgabe in diesem einfachen Workflow für diesen Benutzer zugewiesen.  
  
#### <a name="to-create-a-sharepoint-designer-reusable-workflow"></a>Erstellen ein wiederverwendbares Workflows aus SharePoint Designer
  
1.  In der **Unterwebsites** Abschnitt der **SPD1** Website ändern.  
  
2.  Wählen Sie auf dem Menüband der **wieder verwendbaren Workflow** Schaltfläche.  
  
     Das Erstellen eines Wiederverwendbaren Workflows-Assistent wird angezeigt.  
  
3.  In der **Namen** geben **SPD Task Workflow**.  
  
4.  In der **Inhaltstyp** wählen **Aufgabe**, und wählen Sie dann die **OK** Schaltfläche.  
  
     Der Workflow wird in der SharePoint Designer-Workflow-Designer geöffnet.  
  
5.  Wählen Sie Schritt 1 im Workflow-Designer, und wählen Sie dann im Menüband der **Bedingung** Schaltfläche.  
  
6.  Wählen Sie in der Liste der Bedingungen, **Wenn aktuelle Elementfeld gleich Wert ist**.  
  
     Dieser Schritt fügt eine Bedingung mit dem Namen **Feld Wert gleich**.  
  
7.  In der **Feld Wert gleich** Bedingung, und wählen Sie die **Feld** Link.  
  
8.  Wählen Sie in der Liste der Werte, **Titel**.  
  
9. In der **Feld Wert gleich** Bedingung, und wählen Sie die **Wert** Link.  
  
10. Geben Sie die im **neue Aufgabe**.  
  
     Liest die bedingungsanweisung jetzt **Wenn Current Item: Title entspricht die neue Aufgabe**.  
  
11. Wählen Sie die Zeile unter der bedingungsanweisung aus, und wählen Sie dann im Menüband der **Aktion** Schaltfläche.  
  
12. Wählen Sie in der Liste der Aktionen, **Set-Feld im aktuellen Element**.  
  
13. In der **Set-Feld Wert** Aktion wählen Sie die **Feld** verknüpfen, und wählen Sie in der Liste dann **zugewiesen**.  
  
14. In der **Set-Feld Wert** Aktion wählen Sie die **Wert** verknüpfen, und wählen Sie dann in der Liste der vorhandenen Benutzer und Gruppen, **Benutzer, der das Element erstellt**.  
  
15. Wählen Sie die **hinzufügen** Schaltfläche, und wählen Sie dann die **OK** Schaltfläche.  
  
     Jetzt die Action-Anweisung liest **festgelegt zugewiesen an zum aktuellen Element: CreatedBy**.  
  
## <a name="save-and-deploy-the-reusable-workflow"></a>Speichern und Bereitstellen von wiederverwendbaren workflow
 Da [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] können nur importieren *.wsp* -Dateien, müssen Sie den wieder verwendbaren Workflow als speichern eine *.wsp* Datei, und vor dem Import in für SharePoint bereitstellen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
> [!IMPORTANT]  
>  Wenn Sie einen Laufzeitfehler, die den folgenden Schritten erhalten haben, müssen Sie das Verfahren auf einem System ausführen, die zur SharePoint-Website zugreifen.  
  
#### <a name="to-save-and-deploy-the-reusable-workflow"></a>Speichern und den wiederverwendbaren Workflow bereit  
  
1.  Wählen Sie am Anfang von SharePoint Designer, der **speichern** Schaltfläche, um Ihre Arbeit zu speichern, und wählen Sie dann die **veröffentlichen** für die Bereitstellung von Workflows, der die **SPD1** SharePoint-Website .  
  
2.  Wählen Sie im Navigationsbereich die **Workflows** Objekt.  
  
3.  Klicken Sie unter **wieder verwendbaren Workflow**, wählen Sie **SPD Task Workflow**.  
  
4.  Wählen Sie auf dem Menüband der **als Vorlage speichern** aus, um den Workflow als speichern eine *.wsp* Datei.  
  
5.  Öffnen der **SPD1** SharePoint-Website in einem Browser zum Anzeigen der *.wsp* -Datei in SharePoint.  
  
6.  Wählen Sie auf der Schnellstartleiste der **Bibliotheken** Link.  
  
7.  In der **Dokumentbibliotheken** Abschnitt der **Websiteobjekten** Link.  
  
     Die **SPD Task Workflow** Datei wird zusammen mit anderen Websiteobjekten aufgeführt.  
  
8.  Wählen Sie in der Liste der Dateien den Namen der Datei  
  
9. In der **Dateidownload** Dialogfeld wählen die **speichern** Schaltfläche zum Speichern der *.wsp* Datei auf Ihrem lokalen System.  
  
## <a name="import-the-wsp-file-into-visual-studio"></a>Die WSP-Datei in Visual Studio importieren
 Importieren der *.wsp* in Datei [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mit einem Projekt Wiederverwendbaren Workflow importieren. Dieses Projekt konvertiert den Workflow aus einer wiederverwendbaren deklarativen Workflow in einem Code-Workflow. Nachdem der Workflow konvertiert wurde, werden Sie Code verwenden, um dessen Verhalten zu ändern.  
  
#### <a name="to-import-a-workflow-from-a-wsp-file-and-modify-it"></a>Um einen Workflow aus einer WSP-Datei importieren, und ändern Sie Sie  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], wählen Sie auf der Menüleiste **Datei** > **neu** > **Projekt**.  
  
2.  In der **neues Projekt** Dialogfeld erweitern Sie die **SharePoint** Knoten entweder **Visual C#-** oder **Visual Basic**, und wählen Sie dann die **2010** Knoten.  
  
3.  In der **Vorlagen** Bereich Wählen Sie die **Wiederverwendbaren SharePoint 2010-Workflow importieren** Vorlage, lassen Sie den Namen des Projekts als **WorkflowImportProject1**, und wählen Sie dann die **OK** Schaltfläche.  
  
     SharePoint Customization Wizard angezeigt wird.  
  
4.  Auf der **Geben Sie die Website und Sicherheitsebene für debugging** geben die [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] für den zweiten SharePoint-Unterwebsite, die Sie zuvor erstellt haben: http://*Systemname*  /SPD2.  
  
5.  In der **was der Vertrauensebene für diese SharePoint-Lösung ist?** Abschnitt der **als farmlösung bereitstellen** Optionsfeld aus, und wählen Sie dann die **Weiter** Schaltfläche.  
  
     Weitere Informationen zu sandkastenlösungen im Vergleich zu farmlösungen, finden Sie unter [Überlegungen zu sandkastenlösungen](../sharepoint/sandboxed-solution-considerations.md).  
  
6.  In der **neue Projektquelle angeben** Seite, navigieren Sie zum Speicherort auf dem System, in dem Sie zuvor gespeichert haben, die *.wsp* Datei, öffnen Sie die Datei, und wählen Sie dann die **Weiter** Schaltfläche ".  
  
    > [!NOTE]  
    >  Wählen Sie die **Fertig stellen** Schaltfläche, um alle verfügbaren Elemente im Importieren der *.wsp* Datei.  
  
     Dies zeigt eine Liste der verfügbaren für das Importieren von wiederverwendbaren Workflows aus.  
  
7.  In der **zu importierende Elemente auswählen** wählen die **SPD Task Workflow** Workflow, und wählen Sie dann die **Fertig stellen** Schaltfläche.  
  
     Nachdem der Importvorgang abgeschlossen ist, ein Projekt mit dem Namen **WorkflowImportProject1** wird erstellt, enthält einen Workflow namens **SPD_Workflow_TestFT**. In diesem Ordner wird die Workflowdefinitionsdatei *"Elements.xml"* und die Workflow-Designer-Datei (*xoml*). Der Designer enthält zwei Dateien: die Datei "Rules" (.rules) und der Code-Behind-Datei (entweder *cs* oder *vb*, je nach Programmiersprache Ihres Projekts).  
  
8.  In **Projektmappen-Explorer**, löschen Sie die **andere importierte Dateien** Ordner.  
  
9. In der *"Elements.xml"* , löschen Sie `InstantiationURL="_layouts/IniErkflIP.sspx"`.  
  
10. In **Projektmappen-Explorer**, wählen Sie **WorkflowImportProject1**, und anschließend auf der Menüleiste die Optionen **Projekt** > **als Startprojekt festlegen**  festzulegende **WorkflowImportProject1** als Startelement.  
  
     Die Liste wird sofort, wenn Sie das Debuggen des Projekts angezeigt.  
  
11. Da die **Wiederverwendbaren SharePoint 2010-Workflow importieren** Vorlage nicht die Zuordnung-Eigenschaftswerte für den importierten Workflow importieren, müssen Sie sie eingeben. Gehen Sie dazu wie folgt vor:  
  
    1.  In **Projektmappen-Explorer**, wählen Sie die **SPD_Workflow_TestFT** Knoten.  
  
    2.  Wählen Sie die Auslassungspunkte (![ASP.NET Mobile-Designer Ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile-Designer Ellipse")) Schaltfläche neben der Listeneigenschaften an, wie z. B. die **Zielliste** Eigenschaft.  
  
    3.  Geben Sie die fehlenden Werte in den SharePoint Customization Wizard, und wählen Sie dann die **Fertig stellen** Schaltfläche.  
  
12. Wählen Sie die XOML-Datei, und anschließend auf der Menüleiste die Optionen **Ansicht** > **Designer** um die importierten Workflow im Workflow-Designer anzuzeigen.  
  
13. In der **Windows Workflow v3. 0** Knoten die **Toolbox**, führen Sie eine der folgenden Schritte aus:  
  
    -   Öffnen Sie das Kontextmenü für die **Code** -Aktivität, und wählen Sie dann **Kopie**. Öffnen Sie im Workflowdesigner das Kontextmenü für die Zeile unter der **SequenceActivity1 ab** -Aktivität, und wählen Sie dann **einfügen**.  
  
    -   Ziehen Sie die **Code** Aktivität aus der **Toolbox** zum Workflow-Designer, und verbinden Sie es mit der Zeile unter der **SequenceActivity1 ab** Aktivität.  
  
     Hiermit wird eine Aktivität zum Workflow-Designer mit dem Namen **CodeActivity1**. In dieser Aktivität fügen Sie eine Aktion, die eine Ankündigung in der Liste der Ankündigungen erstellt werden, wenn der Benutzer den Workflow startet.  
  
14. Führen Sie einen der folgenden Schritte aus:  
  
    -   Doppelklicken Sie auf **CodeActivity1** generieren einen Ereignishandler, und zeigen Sie den Code.  
  
    -   In der **Eigenschaften** Fenster für **CodeActivity1**, legen Sie den Wert von der **ExecuteCode** Eigenschaft **CodeActivity_ExecuteCode**.  
  
15. Fügen Sie die folgenden unter den vorhandenen **mit** oder **Importe** Anweisungen:  
  
     [!code-csharp[SP_SPDWFImport#1](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#1)]
     [!code-vb[SP_SPDWFImport#1](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#1)]  
  
16. Ersetzen Sie dies `codeActivity1_ExecuteCode` durch Folgendes:  
  
     [!code-csharp[SP_SPDWFImport#2](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#2)]
     [!code-vb[SP_SPDWFImport#2](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#2)]  
  
## <a name="deploy-the-project-and-associate-the-workflow"></a>Bereitstellen Sie des Projekts, und ordnen Sie den workflow
 Als Nächstes konvertiert WorkflowImportProject1 ausführen auf einer SharePoint-Website bereitstellen, und ordnen Sie dann den Workflow der Aufgabenliste anzeigen und testen das geänderte Workflow.  
  
#### <a name="to-deploy-the-project-and-associate-the-workflow"></a>Bereitstellen des Projekts, und ordnen Sie den workflow  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], wählen Sie die **F5** Schlüssel ausführen und das konvertierte Workflow-Projekt bereitstellen.  
  
2.  Wählen Sie auf der Schnellstartleiste der **Aufgaben** Link, um die Aufgabenliste anzuzeigen.  
  
3.  Auf der **Listentools** Registerkarte die **Elemente** Schaltfläche, und wählen Sie dann die **neues Element** Schaltfläche.  
  
     Die **Aufgaben - neues Element** Dialogfeld wird geöffnet.  
  
4.  In der **Titel** geben **neue Aufgabe**, und wählen Sie dann die **speichern** Schaltfläche.  
  
5.  Auf der **Listentools** Registerkarte die **Liste** Schaltfläche, und wählen Sie dann die **Listeneinstellungen** Schaltfläche.  
  
     Die **Listeneinstellungen** Seite wird angezeigt.  
  
6.  In der **Berechtigungen und Verwaltung** Abschnitt der **Workfloweinstellungen** Link.  
  
     Die **Workfloweinstellungen** Seite wird angezeigt.  
  
7.  Wählen Sie die **fügen Sie einen Workflow** Link.  
  
8.  In der **Workflow** wählen **WorkflowImportProject1 - SPD Workflow Test**.  
  
9. In der **Namen** geben **SPD Workflow Test**, und wählen Sie dann die **OK** Schaltfläche.  
  
10. Wählen Sie in der Schnellstartleiste der **Aufgaben** Liste.  
  
11. Wählen Sie den Pfeil neben **neue Aufgabe**, und wählen Sie in der Liste dann **Workflows**.  
  
12. In der **Starten eines neuen Workflows** Abschnitt, und wählen Sie den Link, um **SPD Workflow Test**, und wählen Sie dann die **starten** Schaltfläche, um den Workflow zu initiieren.  
  
    > [!NOTE]  
    >  Alternativ Sie können automatisch einen Workflow mit einer Liste eine Zuordnung von den workfloweinstellungs-Assistenten ausführen und Festlegen des Workflows automatisch zuordnen.  
  
     Beachten Sie, dass zwei Aktionen, die vom Workflow ausgeführt werden: Ihr Name wird in der Aufgabe **zugewiesen an** Spalte und eine Ankündigung angezeigt wird, der **Ankündigungen** Liste.  
  
## <a name="see-also"></a>Siehe auch
 [Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)   
 [Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
