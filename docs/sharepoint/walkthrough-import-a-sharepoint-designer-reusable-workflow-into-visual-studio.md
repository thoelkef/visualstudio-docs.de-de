---
title: "Exemplarische Vorgehensweise: Importieren eines wiederverwendbaren Workflows aus SharePoint-Designer in Visual Studio"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.WSPImport.ImportWF"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint-Entwicklung in Visual Studio, Importieren von wiederverwendbaren Workflows"
  - "Wiederverwendbare Workflows [SharePoint-Entwicklung in Visual Studio]"
ms.assetid: a6550615-4433-4aba-8bdf-0fcbf8dbcf97
caps.latest.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# Exemplarische Vorgehensweise: Importieren eines wiederverwendbaren Workflows aus SharePoint-Designer in Visual Studio
  In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie ein wiederverwendbarer, im SharePoint\-Designer 2010 erstellter Workflow in ein [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\-SharePoint\-Workflowprojekt importiert wird.  
  
 Im SharePoint\-Designer erstellte Workflows oder *deklarative Workflows* bestehen nicht aus Code, sondern aus [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]\-Anweisungen.  Der SharePoint\-Designer 2010 führt *wiederverwendbare Workflows* ein, die portable, deklarative Workflows sind, die von anderen Listen in SharePoint\-Websites verwendet werden können.  
  
 Mithilfe der Workflows, die in [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)], wie sequenzielle und Zustandsautomatworkflows erstellt werden, werden als Codeworkflows bezeichnet.  Codeworkflows bestehen aus XML\-Dateien und Codemodulen, in denen Benutzer das Verhalten des Workflows anpassen können.  
  
 Visual Studio ermöglicht es Ihnen, die wiederverwendbare Workflows zu importieren, die in SharePoint Designer 2010 und sie mit den zur Verwendung in den SharePoint\-Websites in Codeworkflows konvertieren erstellt werden.  
  
 Diese exemplarische Vorgehensweise enthält die folgenden Aufgaben:  
  
-   Erstellen eines einfachen, wiederverwendbaren Workflows im SharePoint\-Designer.  
  
-   Exportieren des wiederverwendbaren Workflows aus SharePoint Designer in eine WSP\-Datei und nach SharePoint.  
  
-   Importieren der WSP\-Datei in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mit dem Projekttyp Wiederverwendbaren Workflow importieren.  
  
-   Ändern des Workflows durch Hinzufügen von Code.  
  
-   Verwenden des importierten Workflows in einer SharePoint\-Website.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Unterstützte Editionen von [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] und SharePoint.  Weitere Informationen finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
-   Microsoft [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] SharePoint\-Designer 2010.  
  
## Erstellen von SharePoint\-Zielunterwebsites  
 Zunächst erstellen Sie zwei neue SharePoint\-Unterwebsites: eine zum Hosten der wiederverwendbaren Workflows des SharePoint\-Designers und eine zum Hosten der konvertierten Workflows.  
  
#### So erstellen Sie SharePoint\-Unterwebsites  
  
1.  In SharePoint Designer 2010 auf der Menüleiste, wählen Sie **Neue leere Website**, **Datei** aus.  
  
2.  Im Dialogfeld **Neue leere Website** wechseln Sie zu einer SharePoint\-Website, in der den Workflow erstellen möchten, oder verwenden Sie den Wert http:\/\/*SystemName*\/und wählen Sie dann die Schaltfläche **OK** aus.  
  
     Die Homepage wird angezeigt.  
  
3.  Im Abschnitt **Unterwebsites** wählen Sie die Schaltfläche **Neu** aus.  
  
4.  Im Dialogfeld **Neu** wählen Sie aus der Liste im linken Bereich, **SharePoint\-Vorlagen** aus und wählen aus der Liste im rechten Bereich **Teamwebsite** aus.  
  
5.  Im Feld **Geben Sie den Standort der Website an** ersetzen Sie das Wort **Unterwebsite** in der URL durch SPD1, und wählen Sie dann die Schaltfläche **OK** aus.  
  
     Hiermit wird die neue Unterwebsite im SharePoint\-Designer geöffnet.  Schließen Sie diese Instanz des SharePoint\-Designers, und wechseln Sie wieder zur ersten Instanz \(der Website der obersten Ebene\).  
  
6.  Wiederholen Sie die Schritte 3 bis 5, um die zweite Unterwebsite zu erstellen. Ersetzen Sie diesmal das Wort **Unterwebsite** in [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] durch "SPD2".  
  
## Erstellen eines wiederverwendbaren SharePoint\-Designerworkflows  
 Da SharePoint keine wiederverwendbaren Workflows einschließt, die Sie für dieses Beispiel verwenden können, erstellen Sie einen.  Wenn in diesem einfachen Workflow ein Benutzer eine neue Aufgabe mit einem bestimmten Titel in der Aufgabenliste eingibt,wird diesem Benutzer die Aufgabe zugewiesen.  
  
#### So erstellen Sie einen wiederverwendbaren SharePoint\-Designerworkflow  
  
1.  Im Abschnitt **Unterwebsites** wählen Sie die Website **SPD1**, um sie zu ändern.  
  
2.  Klicken Sie im Menüband auf die Schaltfläche **Wieder verwendbarer Workflow** aus.  
  
     Der Assistent zum Erstellen von wiederverwendbaren Workflows wird angezeigt.  
  
3.  Im Feld **Name** Geben Sie Namen "SPD Task Workflow" in ein.  
  
4.  In der Liste **Inhaltstyp** wählen Sie **Aufgabe** und wählen Sie dann die Schaltfläche **OK** aus.  
  
     Der Workflow wird im SharePoint\-Workflowdesigner geöffnet.  
  
5.  im Workflow\-Designer wählen Sie Schritt 1 und dann, auf dem Menüband, die Schaltfläche **Bedingung** aus.  
  
6.  In der Liste der Bedingungen, wählen Sie **Wenn das aktuelle Elementfeld gleich Wert ist** aus.  
  
     Dieser Schritt fügt eine Bedingung hinzu, mit dem Namen **Wenn Feld gleich Wert**.  
  
7.  Zustand In **Wenn Feld gleich Wert** wählen Sie den Link **Feld** aus.  
  
8.  In der Liste der Werte, wählen Sie **Titel** aus.  
  
9. Zustand In **Wenn Feld gleich Wert** wählen Sie den Link **Wert** aus.  
  
10. Geben Sie im Feld New task ein.  
  
     Die Bedingungsanweisung lautet jetzt **Aktuelles Element:Wenn Titel gleich New task**.  
  
11. Wählen Sie die Zeile unter der Bedingungsanweisung, und dann, auf dem Menüband aus, wählen Sie die Schaltfläche **Aktion** aus.  
  
12. In der Liste der Aktionen, wählen Sie **Feld im aktuellen Element festlegen** aus.  
  
13. In der Aktion **Feld auf Wert festlegen** Wählen Sie den Link **Feld**, und dann in der Liste, **Zugewiesen zu** aus.  
  
14. In der Aktion **Feld auf Wert festlegen** Wählen Sie den Link **Wert**, und dann in der Liste der vorhandenen Benutzer und Gruppen aus, wählen **Der Benutzer, der die Arbeitsaufgabe erstellt hat** aus.  
  
15. Wählen Sie die Schaltfläche **Hinzufügen** und dann die Schaltfläche **OK** aus.  
  
     Die Aktionsanweisung lautet jetzt **Festlegen von Zugwiesen auf Aktuelles Element:CreatedBy**.  
  
## Speichern und Bereitstellen des wiederverwendbaren Workflows  
 Da [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nur WSP\-Dateien importieren kann, müssen Sie den wiederverwendbaren Workflow als WSP\-Datei speichern und in SharePoint bereitstellen, bevor sie ihn in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] importieren können.  
  
> [!IMPORTANT]  
>  Wenn beim Ausführen der folgenden Prozedur ein Laufzeitfehler auftritt, müssen Sie die Prozedur auf einem System ausführen, das über Zugriff auf die SharePoint\-Website verfügt.  
  
#### So speichern und stellen Sie den wiederverwendbaren Workflow bereit  
  
1.  Am oberen Rand des SharePoint\-Designers wählen Sie die Schaltfläche **Speichern**, um den Status zu speichern, und dann die Schaltfläche **Veröffentlichen**, um den Workflow auf der SharePoint\-Website **SPD1** bereitzustellen.  
  
2.  im Navigationsbereich wählen Sie das Objekt **Workflows** aus.  
  
3.  Wählen Sie unter **Wieder verwendbarer WorkflowSPD Task Workflow** aus.  
  
4.  Klicken Sie im Menüband verwenden Sie die Schaltfläche **Als Vorlage speichern**, um den Workflow als WSP\-Datei zu speichern.  
  
5.  Öffnen Sie die SharePoint\-Website **SPD1** in einem Browser, um die WSP\-Datei in SharePoint anzuzeigen.  
  
6.  Klicken Sie auf der Schnellstartleiste auf den Link **Bibliotheken** aus.  
  
7.  Im Abschnitt **Dokumentbibliotheken** Wählen Sie den Link **Websiteobjekte** aus.  
  
     Die Datei **SPD\-Aufgabenworkflow** wird zusammen mit anderen Websiteobjekten aufgeführt.  
  
8.  In der Liste von Dateien, wählen Sie den Namen der Datei aus  
  
9. Im Dialogfeld **Dateidownload** wählen Sie die Schaltfläche **Speichern**, um die WSP\-Datei auf dem lokalen System zu speichern.  
  
## Importieren der WSP\-Datei in Visual Studio  
 Importieren Sie die WSP\-Datei mit dem Projekt Wiederverwendbaren Workflow importieren in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Dieses Projekt konvertiert den Workflow von einem wiederverwendbaren, deklarativen Workflow in einen Codeworkflow.  Nachdem der Workflow konvertiert wurde, verwenden Sie Code, um sein Verhalten zu ändern.  
  
#### So importieren Sie einen Workflow aus einer WSP\-Datei und ändern diesen  
  
1.  Klicken Sie in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] auf der Menüleiste, wählen Sie **Neu**, **Projekt**, **Datei** aus.  
  
2.  Im Dialogfeld **Neues Projekt** erweitern Sie den Knoten **SharePoint** entweder unter **Visual C\#** oder **Visual Basic**, und wählen Sie den Knoten **2010** aus.  
  
3.  Im Bereich **Vorlagen** wählen Sie die Vorlage **Wiederverwendbaren SharePoint 2010\-Workflow importieren** aus, übernehmen Sie den Namen **WorkflowImportProject1** des Projekts, und wählen Sie dann die Schaltfläche **OK** aus.  
  
     Der Assistent zum Anpassen von SharePoint wird angezeigt.  
  
4.  Auf der Seite **Site und Sicherheitsebene für Debugging angeben** geben Sie [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] für die zweite SharePoint\-Unterwebsite ein, die Sie zuvor erstellt haben: http:\/\/*system name*\/SPD2.  
  
5.  Im Abschnitt **Wie lautet die Vertrauensebene für diese SharePoint\-Lösung?** wählen Sie das Optionsfeld **Als Farmlösung bereitstellen**, und wählen Sie dann die Schaltfläche **Weiter** aus.  
  
     Weitere Informationen über Sandkastenlösungen im Vergleich zu Farmlösungen finden Sie in [Überlegungen zu Sandkastenlösungen](../sharepoint/sandboxed-solution-considerations.md).  
  
6.  Auf der Seite **Neue Projektquelle angeben** navigieren Sie zum Speicherort im System, an dem Sie zuvor die WSP\-Datei gespeichert haben, öffnen die Datei auswählen und dann die Schaltfläche **Weiter**.  
  
    > [!NOTE]  
    >  Wählen Sie die Schaltfläche **Fertig stellen**, um alle verfügbaren Elemente in der WSP\-Datei zu importieren.  
  
     Dadurch wird eine Liste wiederverwendbarer Workflows angezeigt, die zum Importieren verfügbar sind.  
  
7.  Im Feld **Zu importierende Elemente auswählen** wählen Sie den Workflow **SPD Task Workflow** aus, und wählen Sie dann die Schaltfläche **Fertig stellen** aus.  
  
     Nach Abschluss des Importvorgangs wird ein Projekt mit dem Namen **WorkflowImportProject1** erstellt, das einen Workflow **SPD\_Workflow\_TestFT** enthält.  Dieser Ordner enthält die Definitionsdatei "Elements.xml" des Workflows und die Workflow\-Designerdatei \(.xoml\).  Der Designer enthält zwei Dateien: die Regeldatei \(.rules\) und die Code\-Behind\-Datei \(entweder .cs oder .vb, abhängig von der Programmiersprache des Projekts\).  
  
8.  Löschen Sie im **Projektmappen\-Explorer** den Ordner **Andere importierte Dateien**.  
  
9. In der Datei "Elements.xml" löschen Sie `InstantiationURL="_layouts/IniErkflIP.sspx"`.  
  
10. Wählen Sie im **Projektmappen\-Explorer**, und klicken Sie auf der Menüleiste, **Projekt** auswählen, **Als Startprojekt festlegen**, um als Startelement **WorkflowImportProject1** festzulegen **WorkflowImportProject1** aus.  
  
     Dadurch wird die Liste direkt angezeigt, wenn Sie das Projekt debuggen.  
  
11. Da die Vorlage **Wiederverwendbaren SharePoint 2010\-Workflow importieren** keine Zuordnungseigenschaftswerte für den importierten Workflow importiert werden, müssen Sie sie eingeben.  Gehen Sie dazu wie folgt vor:  
  
    1.  Wählen Sie im **Projektmappen\-Explorer** den Knoten **SPD\_Workflow\_TestFT** aus.  
  
    2.  Wählen Sie die Schaltfläche mit den Auslassungszeichen \(![Auslassungszeichen im ASP.NET Mobile-Designer](../sharepoint/media/mwellipsis.png "Auslassungszeichen im ASP.NET Mobile-Designer")\) neben einer der Listet Eigenschaften, z der Eigenschaft **Zielliste** aus.  
  
    3.  Füllen Sie die fehlenden Werte im Assistenten zum Anpassen von SharePoint aus, und wählen Sie dann die Schaltfläche **Fertig stellen** aus.  
  
12. Wählen Sie die .xoml\-Datei, und dann, auf der Menüleiste aus, wählen Sie **Designer**, **Ansicht**, um den importierten Workflow im Workflow\-Designer anzuzeigen.  
  
13. Im Knoten **Windows Workflow v3.0Werkzeugkasten**, führen Sie einen der folgenden Schritte aus:  
  
    -   Öffnen Sie das Kontextmenü für **Code** die Aktivität, und wählen Sie dann **Kopieren** aus.  im Workflow\-Designer öffnen Sie das Kontextmenü für die Zeile unter der Aktivität **SequenceActivity1**, und wählen Sie dann **Einfügen** aus.  
  
    -   Ziehen Sie die Aktivität **Code** von **Werkzeugkasten** zum Workflow\-Designer, und schließen Sie sie an die Zeile unter der Aktivität **SequenceActivity1** angezeigt.  
  
     Hiermit wird dem Workflow\-Designer eine Aktivität mit dem Namen **CodeActivity1** hinzugefügt.  In dieser Aktivität fügen Sie eine Codeaktion hinzu, die in der Ankündigungsliste eine Ankündigung erstellt, wenn der Benutzer den Workflow startet.  
  
14. Führen Sie einen der folgenden Schritte aus:  
  
    -   Doppelklicken Sie auf **CodeActivity1**, um einen Ereignishandler zu generieren und den Code anzuzeigen.  
  
    -   Im Fenster **Eigenschaften** für **CodeActivity1**, legen Sie den Wert der Eigenschaft **ExecuteCode** auf **codeActivity\_ExecuteCode** fest.  
  
15. Fügen Sie unter den vorhandenen **using**\- oder **Imports**\- Anweisungen Folgendes hinzu:  
  
     [!code-csharp[SP_SPDWFImport#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_spdwfimport/cs/workflows/spd_task_workflowft/spd task workflow.xoml.cs#1)]
     [!code-vb[SP_SPDWFImport#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_spdwfimport/vb/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#1)]  
  
16. Ersetzen Sie `codeActivity1_ExecuteCode` durch Folgendes:  
  
     [!code-csharp[SP_SPDWFImport#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_spdwfimport/cs/workflows/spd_task_workflowft/spd task workflow.xoml.cs#2)]
     [!code-vb[SP_SPDWFImport#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_spdwfimport/vb/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#2)]  
  
## Bereitstellen des Projekts und Zuordnen des Workflows  
 Führen Sie nun WorkflowImportProject1 zum Bereitstellen auf einer SharePoint\-Website aus, und ordnen Sie den Workflow anschließend der Aufgabenliste zu, um den geänderten, konvertierten Workflow anzuzeigen und zu testen.  
  
#### So stellen Sie das Projekt bereit und ordnen den Workflow zu  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] verwenden Sie die F5\-TASTE, um das konvertierte Workflowprojekt auszuführen und bereitzustellen.  
  
2.  Klicken Sie auf der Schnellstartleiste wählen Sie den Link **Aufgaben**, um die Aufgabenliste anzuzeigen.  
  
3.  Auf der Registerkarte **Listentools** wählen Sie die Schaltfläche **Elemente**, und wählen Sie dann die Schaltfläche **Neues Element** aus.  
  
     Das Dialogfeld **Aufgaben \- Neues Element** wird geöffnet.  
  
4.  Im Feld **Titel** geben Sie neuen Aufgabe ein, und wählen Sie dann die Schaltfläche **Speichern** aus.  
  
5.  Auf der Registerkarte **Listentools** wählen Sie die Schaltfläche **Liste**, und wählen Sie dann die Schaltfläche **Listeneinstellungen** aus.  
  
     Die Seite **Listeneinstellungen** wird.  
  
6.  Im Abschnitt **Berechtigungen und Verwaltung** Wählen Sie den Link **Workfloweinstellungen** aus.  
  
     Die Seite **Workfloweinstellungen** wird.  
  
7.  Wählen Sie den Link **Workflow hinzufügen** aus.  
  
8.  In der Liste **Workflow** wählen Sie **WorkflowImportProject1 \- SPD Workflow Test** aus.  
  
9. Im Feld **Name** Geben Sie Namen " SPD Workflow Test ein, und wählen Sie dann die Schaltfläche **OK** aus.  
  
10. In der Schnellstartleiste wählen Sie die Liste **Aufgaben** aus.  
  
11. Wählen Sie den Pfeil neben **Neue Aufgabe**, und dann, in der Liste aus, wählen Sie **Workflows** aus.  
  
12. Im Abschnitt **Neuen Workflow starten** Wählen Sie den Link für **SPD Workflow Test**, und wählen Sie die Schaltfläche **Starten**, um den Workflow zu initiieren.  
  
    > [!NOTE]  
    >  Alternativ kann ein Workflow automatisch einer Liste zugeordnet werden, indem Sie den Workfloweinstellungs\-Assistenten ausführen und den Workflow auf automatische Zuordnung festlegen.  
  
     Beachten Sie, dass der Workflow zwei Aktionen ausführt: Ihr Name wird in der Spalte **Zugewiesen an** der Aufgabe angezeigt, und in der Liste **Ankündigungen** wird eine Ankündigung angezeigt.  
  
## Siehe auch  
 [Importieren von Elementen aus einer vorhandenen SharePoint-Website](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [Erstellen von wiederverwendbaren Steuerelementen für Webparts oder Anwendungsseiten](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  