---
title: 'Exemplarische Vorgehensweise: Importieren ein Wiederverwendbaren Workflows aus SharePoint-Designer in Visual Studio | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
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
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 05428f2e702643b88415663249e9f29a9f7d46bc
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio"></a>Exemplarische Vorgehensweise: Importieren eines wiederverwendbaren Workflows aus SharePoint-Designer in Visual Studio
  Diese exemplarische Vorgehensweise veranschaulicht, wie zum Importieren eines wiederverwendbaren Workflows aus SharePoint Designer 2010 in erstellt ein [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint-Workflowprojekt.  
  
 Im SharePoint-Designer erstellten Workflows oder *deklarativer Workflows*, bestehen aus [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Anweisungen anstelle von Code. SharePoint Designer 2010 gibt es *wiederverwendbare Workflows*, welche sind portable, deklarativen Workflows, die von anderen Listen in SharePoint-Websites verwendet werden können.  
  
 In erstellte Workflows [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)], z. B. sequenzielle und Zustandsautomatworkflows, heißen *code Workflows*. Codeworkflows bestehen aus XML-Dateien und Codemodule, die in denen Benutzer das Verhalten des Workflows anpassen können.  
  
 Visual Studio können Sie zum Importieren von wiederverwendbaren Workflows, die in SharePoint Designer 2010 erstellt und zum von Codeworkflows für die Verwendung in Ihrer SharePoint-Websites zu konvertieren.  
  
 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:  
  
-   Erstellen einen einfachen, wiederverwendbaren Workflow in SharePoint Designer.  
  
-   Export des wiederverwendbaren SharePoint Designer-Workflows in SharePoint in der WSP-Datei.  
  
-   Importieren von WSP-Datei in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mit dem Projekt Wiederverwendbaren Workflow importieren.  
  
-   Ändern des Workflows durch Hinzufügen von Code.  
  
-   Verwenden den importierten Workflow in einer SharePoint-Website.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Unterstützte Editionen von [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] und SharePoint. Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
-   Microsoft [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] SharePoint Designer 2010.  
  
## <a name="create-target-sharepoint-subsites"></a>Ziel SharePoint Unterwebsites erstellen  
 Zunächst erstellen Sie zwei neue SharePoint-Unterwebsites: eine zum Hosten von wiederverwendbaren Workflows aus SharePoint-Designer, ein weiteres zum Hosten der konvertierten Workflows.  
  
#### <a name="to-create-sharepoint-subsites"></a>Zum Erstellen von SharePoint-Unterwebsites  
  
1.  Wählen Sie in SharePoint Designer 2010 in der Menüleiste **Datei**, **neue leere Website**.  
  
2.  In der **neue leere Website** (Dialogfeld), navigieren Sie zu einer SharePoint-Website möchten Sie den Workflow erstellen, oder verwenden Sie den Wert der http://*SystemName*/ und wählen Sie dann die **OK** Schaltfläche ".  
  
     Auf der Startseite angezeigt wird.  
  
3.  In der **Unterwebsites** Abschnitt der **neu** Schaltfläche.  
  
4.  In der **neu** Dialogfeld Wählen Sie **SharePoint-Vorlagen** aus der Liste im linken Bereich, und wählen Sie **Teamwebsite** aus der Liste im rechten Bereich.  
  
5.  In der **Geben Sie den Speicherort der Website** Feld, ersetzen Sie das Wort **Unterwebsite** in der URL durch **SPD1**, und wählen Sie dann die **OK** Schaltfläche.  
  
     Dadurch wird die neue Unterwebsite im SharePoint-Designer geöffnet. Schließen Sie diese Instanz des SharePoint-Designers, und wechseln Sie zurück zur ersten Instanz (Standort der obersten Ebene).  
  
6.  Wiederholen Sie die Schritte 3 bis 5, um die zweite Unterwebsite diesmal das Wort ersetzen erstellen **Unterwebsite** in der [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] mit **SPD2**.  
  
## <a name="create-a-sharepoint-designer-reusable-workflow"></a>Erstellen eines Wiederverwendbaren Workflows aus SharePoint-Designer  
 Da SharePoint nicht wieder verwendbaren Workflows enthält, die Sie für dieses Beispiel verwenden können, erstellen Sie eine. Wenn ein Benutzer eine neue Aufgabe in der Aufgabenliste eingibt, die einen bestimmten Titel verfügt, wird die Aufgabe in diesem einfachen Workflow für diesen Benutzer zugewiesen.  
  
#### <a name="to-create-a-sharepoint-designer-reusable-workflow"></a>Zum Erstellen eines wiederverwendbaren Workflows aus SharePoint-Designer  
  
1.  In der **Unterwebsites** Abschnitt der **SPD1** Website ändern.  
  
2.  Wählen Sie auf dem Menüband der **Wiederverwendbaren Workflow** Schaltfläche.  
  
     Das Erstellen eines Wiederverwendbaren Workflows-Assistent wird angezeigt.  
  
3.  In der **Namen** geben **SPD Aufgabenworkflow**.  
  
4.  In der **Inhaltstyp** wählen **Aufgabe**, und wählen Sie dann die **OK** Schaltfläche.  
  
     Der Workflow wird in der SharePoint Designer-Workflow-Designer geöffnet.  
  
5.  Klicken Sie im Workflow-Designer, wählen Sie Schritt 1, und wählen Sie dann im Menüband die **Bedingung** Schaltfläche.  
  
6.  Wählen Sie in der Liste der Bedingungen, **Wenn aktuelle des Arbeitsaufgabenfelds Wert**.  
  
     Dieser Schritt fügt eine Bedingung mit dem Namen **Feld Wert gleich**.  
  
7.  In der **Feld Wert gleich** Bedingung, und wählen Sie die **Feld** Link.  
  
8.  Wählen Sie in der Werteliste **Titel**.  
  
9. In der **Feld Wert gleich** Bedingung, und wählen Sie die **Wert** Link.  
  
10. Geben Sie im Feld **neue Aufgabe**.  
  
     Liest die bedingungsanweisung jetzt **Wenn aktuelle: Titel des Elements gleich neue Aufgabe**.  
  
11. Wählen Sie die Zeile unter der bedingungsanweisung, und wählen Sie dann im Menüband die **Aktion** Schaltfläche.  
  
12. Wählen Sie in der Liste der Aktionen, **Set-Feld im aktuellen Element**.  
  
13. In der **Set-Feld Wert** Aktion, wählen Sie die **Feld** verknüpfen, und wählen Sie dann in der Liste **zugewiesene**.  
  
14. In der **Set-Feld Wert** Aktion, wählen Sie die **Wert** verknüpfen, und wählen Sie dann in der Liste der vorhandenen Benutzer und Gruppen, **Benutzer, der das Element erstellt**.  
  
15. Wählen Sie die **hinzufügen** aus, und klicken Sie dann die **OK** Schaltfläche.  
  
     Liest die Action-Anweisung jetzt **festgelegt zugewiesen an zum aktuellen Element: CreatedBy**.  
  
## <a name="save-and-deploy-the-reusable-workflow"></a>Speichern und Bereitstellen von Wiederverwendbaren Workflows  
 Da [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] können nur die WSP-Dateien importieren, müssen Sie die wiederverwendbaren Workflow als WSP-Datei speichern und für SharePoint bereitgestellt werden, vor dem Importieren ihn in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
> [!IMPORTANT]  
>  Wenn Sie einen Laufzeitfehler des folgenden Verfahrens erhalten, müssen Sie das Verfahren auf einem System ausführen, die auf der SharePoint-Website zugreifen.  
  
#### <a name="to-save-and-deploy-the-reusable-workflow"></a>Speichern und Bereitstellen von wiederverwendbaren Workflows  
  
1.  Klicken Sie oben auf der SharePoint-Designer wählen Sie die **speichern** Schaltfläche, um den Fortschritt zu speichern, und wählen Sie dann die **veröffentlichen** Schaltfläche, um den Workflow zum Bereitstellen der **SPD1** SharePoint-Website .  
  
2.  Wählen Sie im Navigationsbereich die **Workflows** Objekt.  
  
3.  Klicken Sie unter **Wiederverwendbaren Workflow**, wählen Sie **SPD Aufgabenworkflow**.  
  
4.  Wählen Sie auf dem Menüband der **als Vorlage speichern** Schaltfläche, um den Workflow als WSP-Datei zu speichern.  
  
5.  Öffnen der **SPD1** SharePoint-Website in einem Browser, um die WSP-Datei in SharePoint anzuzeigen.  
  
6.  Wählen Sie in der Schnellstartleiste der **Bibliotheken** Link.  
  
7.  In der **Dokumentbibliotheken** Abschnitt der **Site Anlagen** Link.  
  
     Die **SPD Aufgabenworkflow** Datei wird mit den anderen Standort Ressourcen aufgeführt.  
  
8.  Wählen Sie in der Liste der Dateien den Namen der Datei  
  
9. In der **Dateidownload** Dialogfeld Wählen Sie die **speichern** Schaltfläche, um die WSP-Datei auf dem lokalen System zu speichern.  
  
## <a name="import-the-wsp-file-into-visual-studio"></a>Importieren Sie die WSP-Datei in Visual Studio  
 Importieren Sie die WSP-Datei in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mit einem Projekt Wiederverwendbaren Workflow importieren. Dieses Projekt konvertiert den Workflow aus einer wiederverwendbaren deklarativen Workflow in einem Code-Workflow. Nachdem der Workflow konvertiert wurde, werden Sie Code verwenden, um dessen Verhalten zu ändern.  
  
#### <a name="to-import-a-workflow-from-a-wsp-file-and-modify-it"></a>Um einen Workflow aus einer WSP-Datei importieren und ändern es  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], wählen Sie in der Menüleiste **Datei**, **neu**, **Projekt**.  
  
2.  In der **neues Projekt** Dialogfeld erweitern Sie die **SharePoint** Knoten unter einem **Visual C#-** oder **Visual Basic**, und wählen Sie dann die **2010** Knoten.  
  
3.  In der **Vorlagen** Bereich, wählen Sie die **Wiederverwendbaren SharePoint 2010-Workflow importieren** Vorlage, lassen Sie den Namen des Projekts als **WorkflowImportProject1**, und wählen Sie dann die **OK** Schaltfläche.  
  
     Der Assistent zum Anpassen von SharePoint wird angezeigt.  
  
4.  Auf der **Geben Sie die Website und die Sicherheit für das Debuggen** geben die [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] für den zweiten SharePoint-Unterwebsite, die Sie zuvor erstellt haben: http://*Systemname*  /SPD2.  
  
5.  In der **was der Vertrauensebene für diese SharePoint-Lösung ist?** Abschnitt der **als farmlösung bereitstellen** Optionsfeld aus, und wählen Sie dann die **Weiter** Schaltfläche.  
  
     Weitere Informationen zu sandkastenlösungen im Vergleich zu farmlösungen, finden Sie unter [Überlegungen zu Sandkastenlösungen](../sharepoint/sandboxed-solution-considerations.md).  
  
6.  In der **Geben Sie die Projektquelle der neuen** Seite, navigieren Sie zum Speicherort auf dem System, in dem Sie zuvor die WSP-Datei gespeichert, öffnen Sie die Datei und wählen Sie dann die **Weiter** Schaltfläche.  
  
    > [!NOTE]  
    >  Wählen Sie die **Fertig stellen** Schaltfläche, um alle verfügbaren Elemente in der WSP-Datei zu importieren.  
  
     Dies zeigt eine Liste der verfügbaren zum Importieren von wiederverwendbaren Workflows aus.  
  
7.  In der **Elemente auswählen, um importieren** wählen Sie die **SPD Aufgabenworkflow** Workflow, und wählen Sie dann die **Fertig stellen** Schaltfläche.  
  
     Nachdem der Importvorgang abgeschlossen ist, ein Projekt mit dem Namen **WorkflowImportProject1** wird erstellt, mit einem Workflow mit dem Namen **SPD_Workflow_TestFT**. In diesem Ordner wird der Workflow-Definitionsdatei "Elements.xml" und die Workflow-Designer-Datei (.xoml). Der Designer enthält zwei Dateien: die Rules-Datei (Rules) und der Code-Behind-Datei (.cs oder .vb, je nach Programmiersprache des Projekts).  
  
8.  In **Projektmappen-Explorer**, löschen Sie die **andere importierte Dateien** Ordner.  
  
9. Löschen Sie in der Datei "Elements.xml" `InstantiationURL="_layouts/IniErkflIP.sspx"`.  
  
10. In **Projektmappen-Explorer**, wählen Sie **WorkflowImportProject1**, und anschließend auf der Menüleiste die Optionen **Projekt**, **als Startprojekt festlegen** an Legen Sie **WorkflowImportProject1** als Startelement.  
  
     Die Liste wird sofort, wenn Sie das Debuggen des Projekts angezeigt.  
  
11. Da die **Wiederverwendbaren SharePoint 2010-Workflow importieren** Vorlage nicht die Zuordnung Eigenschaftswerte für den importierten Workflow importieren, müssen Sie sie eingeben. Gehen Sie dazu wie folgt vor:  
  
    1.  In **Projektmappen-Explorer**, wählen Sie die **SPD_Workflow_TestFT** Knoten.  
  
    2.  Schaltfläche mit den Auslassungszeichen (![ASP.NET Mobile-Designer Ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile-Designer Ellipse")) Schaltfläche neben mindestens einer der Listeneigenschaften, z. B. die **Zielliste** Eigenschaft.  
  
    3.  Füllen Sie die fehlenden Werte in der Assistent zum Anpassen von SharePoint, und wählen Sie dann die **Fertig stellen** Schaltfläche.  
  
12. Wählen Sie die XOML-Datei, und anschließend auf der Menüleiste die Optionen **Ansicht**, **Designer** importierten Workflow im Workflow-Designer anzeigen.  
  
13. In der **Windows Workflow v3. 0** Knoten der **Toolbox**, führen Sie einen der folgenden Schritte aus:  
  
    -   Öffnen Sie das Kontextmenü für die **Code** Aktivität, und wählen Sie dann **Kopie**. Öffnen Sie im Workflow-Designer das Kontextmenü für die Zeile unter der **SequenceActivity1 ab** Aktivität, und wählen Sie dann **einfügen**.  
  
    -   Ziehen Sie die **Code** Aktivität aus der **Toolbox** dem Workflow-Designer, und verbinden Sie ihn mit der Zeile unter der **SequenceActivity1 ab** Aktivität.  
  
     Dadurch wird eine Aktivität in den Workflowdesigner mit dem Namen **CodeActivity1**. In dieser Aktivität fügen Sie eine Codeaktion, die in der Liste der Ankündigungen eine Ankündigung erstellt, wenn der Benutzer den Workflow startet.  
  
14. Führen Sie einen der folgenden Schritte aus:  
  
    -   Doppelklicken Sie auf **CodeActivity1** einen Ereignishandler zu generieren und den Code anzuzeigen.  
  
    -   In der **Eigenschaften** Fenster für **CodeActivity1**, legen Sie den Wert von der **ExecuteCode** Eigenschaft **CodeActivity_ExecuteCode**.  
  
15. Fügen Sie die folgenden unter den vorhandenen **mit** oder **Importe** Anweisungen:  
  
     [!code-csharp[SP_SPDWFImport#1](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#1)]
     [!code-vb[SP_SPDWFImport#1](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#1)]  
  
16. Ersetzen Sie `codeActivity1_ExecuteCode` durch Folgendes:  
  
     [!code-csharp[SP_SPDWFImport#2](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#2)]
     [!code-vb[SP_SPDWFImport#2](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#2)]  
  
## <a name="deploy-the-project-and-associate-the-workflow"></a>Bereitstellen Sie des Projekts, und ordnen Sie den Workflow  
 Als Nächstes konvertiert WorkflowImportProject1 ausführen auf einer SharePoint-Website bereitstellen, und ordnen Sie den Workflow mit der Liste der Aufgaben zum Anzeigen und testen das geänderte Workflow.  
  
#### <a name="to-deploy-the-project-and-associate-the-workflow"></a>Zum Bereitstellen des Projekts, und ordnen Sie den workflow  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], wählen Sie die Taste F5, um auszuführen und das konvertierte Workflowprojekt bereitzustellen.  
  
2.  Wählen Sie in der Schnellstartleiste der **Aufgaben** Link, um die Aufgabenliste anzuzeigen.  
  
3.  Auf der **Listentools** Registerkarte, und wählen Sie die **Elemente** aus, und klicken Sie dann die **neues Element** Schaltfläche.  
  
     Die **Aufgaben - neues Element** Dialogfeld wird geöffnet.  
  
4.  In der **Titel** geben **neue Aufgabe**, und wählen Sie dann die **speichern** Schaltfläche.  
  
5.  Auf der **Listentools** Registerkarte, und wählen Sie die **Liste** aus, und klicken Sie dann die **Listeneinstellungen** Schaltfläche.  
  
     Die **Listeneinstellungen** Seite wird angezeigt.  
  
6.  In der **Berechtigungen und Verwaltung** Abschnitt der **Workfloweinstellungen** Link.  
  
     Die **Workfloweinstellungen** Seite wird angezeigt.  
  
7.  Wählen Sie die **Hinzufügen eines Workflows** Link.  
  
8.  In der **Workflow** wählen **WorkflowImportProject1 - SPD Workflow Test**.  
  
9. In der **Namen** geben **SPD Workflow Test**, und wählen Sie dann die **OK** Schaltfläche.  
  
10. Wählen Sie in der Schnellstartleiste der **Aufgaben** Liste.  
  
11. Wählen Sie den Pfeil neben **neue Aufgabe**, und wählen Sie dann in der Liste **Workflows**.  
  
12. In der **Starten eines neuen Workflows** Abschnitt, und wählen Sie den Link, um **SPD Workflow Test**, und wählen Sie dann die **starten** Schaltfläche, um den Workflow zu initiieren.  
  
    > [!NOTE]  
    >  Alternativ Sie können automatisch einen Workflow mit einer Liste Zuordnen von dem Workflow-Assistenten ausführen und zum Festlegen des Workflows automatisch zuordnen.  
  
     Beachten Sie, dass zwei Aktionen, die vom Workflow ausgeführt werden: Ihr Name wird angezeigt, in der Aufgabe **zugewiesen an** Spalte und eine Ankündigung angezeigt wird, der **Ankündigungen** Liste.  
  
## <a name="see-also"></a>Siehe auch  
 [Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md)   
 [Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  