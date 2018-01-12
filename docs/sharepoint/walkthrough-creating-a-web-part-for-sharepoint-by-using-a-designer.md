---
title: "Exemplarische Vorgehensweise: Erstellen eines Webparts für SharePoint mithilfe eines Designers | Microsoft Docs"
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
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 28be854f01234783ff9873753eb88ca92bc192d6
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer"></a>Exemplarische Vorgehensweise: Erstellen eines Webparts für SharePoint mithilfe eines Designers
  Wenn Sie Webparts für eine SharePoint-Website erstellen, können Benutzer Inhalt, Darstellung und Verhalten der Seiten auf dieser Website direkt mithilfe eines Browsers ändern. Diese exemplarische Vorgehensweise veranschaulicht das Erstellen eines Webparts visuell mithilfe der SharePoint **visuelles Webpart** -Projektvorlage in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Das erstellte Webpart zeigt eine monatliche Kalenderansicht und ein Kontrollkästchen für jede Kalenderliste auf der Website an. Die Benutzer können angeben, welche Kalenderlisten in die monatliche Kalenderansicht eingeschlossen werden, indem sie die Kontrollkästchen aktivieren.  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Erstellen eines Webparts mit der **visuelles Webpart** -Projektvorlage.  
  
-   Entwerfen des Webparts mit dem Visual Web Developer-Designer in Visual Studio  
  
-   Hinzufügen von Code, um die Ereignisse der Steuerelemente des Webparts zu behandeln  
  
-   Testen des Webparts in SharePoint  
  
    > [!NOTE]  
    >  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt, als in den folgenden Anweisungen aufgeführt werden. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren der Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   Unterstützte Editionen von Windows und SharePoint. Finden Sie unter [Anforderungen für die Entwicklung von SharePoint-Lösungen](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)] oder höher  
  
## <a name="creating-a-web-part-project"></a>Erstellen eines Webpartprojekts  
 Erstellen Sie zunächst ein Webpartprojekts mithilfe der **visuelles Webpart** -Projektvorlage.  
  
#### <a name="to-create-a-visual-web-part-project"></a>So erstellen Sie ein Projekt vom Typ Visuelles Webpart  
  
1.  Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mithilfe der **als Administrator ausführen** Option.  
  
2.  Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt**aus.  
  
     Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
3.  In der **neues Projekt** im Dialogfeld unter entweder **Visual C#-** oder **Visual Basic**, erweitern Sie **Office/SharePoint**, und wählen Sie dann die  **SharePoint-Lösungen** Kategorie.  
  
4.  Wählen Sie in der Liste der Vorlagen, die **SharePoint 2013 - visuelles Webpart** Vorlage, und wählen Sie dann die **OK** Schaltfläche.  
  
     Die **Assistent zum Anpassen von SharePoint** angezeigt wird. Mit diesem Assistenten können Sie die Website, die Sie zum Debuggen des Projekts verwenden, sowie die Vertrauensebene der Projektmappe angeben.  
  
5.  In der **neuerungen die Vertrauensebene für diese SharePoint-Lösung?** Abschnitt der **als farmlösung bereitstellen** Optionsfeld.  
  
6.  Wählen Sie die **Fertig stellen** Schaltfläche, um die standardmäßige lokale SharePoint-Website zu übernehmen.  
  
## <a name="designing-the-web-part"></a>Entwerfen des Webparts  
 Entwerfen des Webparts durch Hinzufügen von Steuerelementen aus dem **Toolbox** auf die Oberfläche des Visual Web Developer-Designer.  
  
#### <a name="to-design-the-layout-of-the-web-part"></a>So entwerfen Sie das Layout für das Webpart  
  
1.  Wählen Sie in Visual Web Developer-Designer, der **Entwurf** Registerkarte ", um zur Entwurfsansicht zu wechseln.  
  
2.  Klicken Sie in der Menüleiste auf **Ansicht**, **Toolbox**.  
  
3.  In der **Standard** Knoten der **Toolbox**, wählen Sie die **CheckBoxList** steuern, und führen Sie einen der folgenden Schritte aus:  
  
    -   Öffnen Sie das Kontextmenü für die **CheckBoxList** steuern, wählen Sie **Kopie**, öffnen Sie das Kontextmenü für die erste Zeile im Designer, und wählen Sie dann **einfügen**.  
  
    -   Ziehen Sie die **CheckBoxList** -Steuerelement aus der **Toolbox**, und verbinden Sie das Steuerelement mit der ersten Zeile im Designer.  
  
4.  Wiederholen Sie den vorherigen Schritt, aber verschieben Sie eine Schaltfläche in die nächste Zeile des Designers.  
  
5.  Wählen Sie im Designer die **Button1** Schaltfläche.  
  
6.  Wählen Sie in der Menüleiste **Ansicht**, **Fenster "Eigenschaften"**.  
  
     Die **Eigenschaften** Fenster wird geöffnet.  
  
7.  In der **Text** Geben Sie die Eigenschaft der Schaltfläche **Update**.  
  
## <a name="handling-the-events-of-controls-on-the-web-part"></a>Behandeln der Ereignisse von Steuerelementen des Webparts  
 Fügen Sie Code hinzu, der es dem Benutzer ermöglicht, der Masterkalenderansicht Kalender hinzuzufügen.  
  
#### <a name="to-handle-events-of-controls-on-the-web-part"></a>So behandeln Sie Ereignisse der Steuerelemente des Webparts  
  
1.  Führen Sie einen der folgenden Schritte aus:  
  
    -   Doppelklicken Sie im Designer auf die **Update** Schaltfläche.  
  
    -   In der **Eigenschaften** Fenster für die **Update** Schaltfläche der **Ereignisse** Schaltfläche. In der **klicken Sie auf** -Eigenschaft, geben Sie **Button1_Click**, und wählen Sie dann die EINGABETASTE.  
  
     Die Benutzersteuerelement-Codedatei wird im Code-Editor geöffnet, und der `Button1_Click`-Ereignishandler wird angezeigt. Später fügen Sie diesem Ereignishandler Code.  
  
2.  Fügen Sie am Anfang der Benutzersteuerelement-Codedatei die folgenden Anweisungen hinzu.  
  
     [!code-vb[SP_VisualWebPart#1](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_VisualWebPart#1](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]  
  
3.  Fügen Sie der `VisualWebPart1`-Klasse folgende Codezeile hinzu. In diesem Code wird ein monatliches Kalenderansichtssteuerelement deklariert.  
  
     [!code-vb[SP_VisualWebPart#2](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#2)]
     [!code-csharp[SP_VisualWebPart#2](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#2)]  
  
4.  Ersetzen Sie die `Page_Load`-Methode der `VisualWebPart1`-Klasse durch folgenden Code. Mit diesem Code werden die folgenden Aufgaben ausgeführt:  
  
    -   Fügt dem Benutzersteuerelement eine monatliche Kalenderansicht hinzu.  
  
    -   Fügt ein Kontrollkästchen für jede Kalenderliste der Website hinzu.  
  
    -   Gibt eine Vorlage für jeden Typ von Element an, das in der Kalenderansicht angezeigt wird.  
  
     [!code-vb[SP_VisualWebPart#3](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#3)]
     [!code-csharp[SP_VisualWebPart#3](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#3)]  
  
5.  Ersetzen Sie die `Button1_Click`-Methode der `VisualWebPart1`-Klasse durch folgenden Code. Mit diesem Code werden der Masterkalenderansicht Elemente aus jedem ausgewählten Kalender hinzugefügt.  
  
     [!code-vb[SP_VisualWebPart#4](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#4)]
     [!code-csharp[SP_VisualWebPart#4](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#4)]  
  
## <a name="testing-the-web-part"></a>Testen des Webparts  
 Wenn Sie das Projekt ausführen, wird die SharePoint-Website geöffnet. Das Webpart wird automatisch dem Webpartkatalog in SharePoint hinzugefügt. Um dieses Projekt zu testen, müssen Sie die folgenden Aufgaben ausführen:  
  
-   Fügen Sie jeder von zwei separaten Kalenderlisten ein Ereignis hinzu.  
  
-   Fügen Sie das Webpart einer Webpartseite hinzu.  
  
-   Geben Sie die Listen an, die in die monatliche Kalenderansicht eingeschlossen werden sollen.  
  
#### <a name="to-add-events-to-calendar-lists-on-the-site"></a>So fügen Sie Kalenderlisten der Website Ereignisse hinzu  
  
1.  In Visual Studio drücken Sie die Taste F5.  
  
     Die SharePoint-Website wird geöffnet, und die [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] -Schnellstartleiste wird auf der Seite angezeigt.  
  
2.  Auf der Schnellstartleiste unter **listet**, wählen Sie die **Kalender** Link.  
  
     Die **Kalender** Seite wird angezeigt.  
  
     Wenn Sie kein Link "Kalender" auf der Schnellstartleiste angezeigt wird, wählen Sie die **Websiteinhalte** Link. Die Seite "Websiteinhalte" angezeigt ein **Kalender** Element, erstellen Sie einen.  
  
3.  Klicken Sie auf der Seite "Kalender" Wählen Sie ein Tag aus, und wählen Sie dann die **hinzufügen** Link in der ausgewählten Tag um ein Ereignis hinzuzufügen.  
  
4.  In der **Titel** geben **Ereignis im Standardkalender**, und wählen Sie dann die **speichern** Schaltfläche.  
  
5.  Wählen Sie die **Websiteinhalte** verknüpfen, und wählen Sie dann die **app hinzufügen** Kachel.  
  
6.  Auf der **erstellen** Seite, und wählen Sie die **Kalender** geben, benennen Sie den Kalender, und wählen Sie dann die **erstellen** Schaltfläche.  
  
7.  Dem neuen Kalender ein Ereignis hinzugefügt haben, benennen Sie das Ereignis **Ereignis im benutzerdefinierten Kalender**, und wählen Sie dann die **speichern** Schaltfläche.  
  
#### <a name="to-add-the-web-part-to-a-web-part-page"></a>So fügen Sie das Webpart einer Webpartseite hinzu  
  
1.  Auf der **Websiteinhalte** Seite öffnen die **Websiteseiten** Ordner.  
  
2.  Wählen Sie auf dem Menüband der **Dateien** Registerkarte Öffnen der **neues Dokument** im Menü, und wählen Sie dann die **Webpartseite** Befehl.  
  
3.  Auf der **neue Webpartseite** Seite, nennen Sie die Seite **SampleWebPartPage.aspx**, und wählen Sie dann die **erstellen** Schaltfläche.  
  
     Die Webpartseite wird angezeigt.  
  
4.  Wählen Sie im oberen Bereich der Webpartseite, die **einfügen** Registerkarte, und wählen Sie dann die **Webpart** Schaltfläche.  
  
5.  Wählen Sie die **benutzerdefinierte** Ordner, wählen Sie die **VisualWebPart1** -Webpart, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
     Das Webpart wird auf der Seite angezeigt. Die folgenden Steuerelemente werden für das Webpart angezeigt:  
  
    -   Eine monatliche Kalenderansicht.  
  
    -   Ein **Update** Schaltfläche.  
  
    -   Ein **Kalender** Kontrollkästchen.  
  
    -   Ein **benutzerdefinierter Kalender** Kontrollkästchen.  
  
#### <a name="to-specify-lists-to-include-in-the-monthly-calendar-view"></a>So geben Sie die Listen an, die in die monatliche Kalenderansicht eingeschlossen werden sollen  
  
1.  Geben Sie im Webpart Kalender, die Sie verwenden möchten, in die monatliche Kalenderansicht einschließen, und wählen Sie dann die **Update** Schaltfläche.  
  
     Die Ereignisse aus allen angegebenen Kalendern werden in der monatlichen Kalenderansicht angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Webparts für SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Vorgehensweise: Erstellen eines SharePoint-Webparts](../sharepoint/how-to-create-a-sharepoint-web-part.md)   
 [Vorgehensweise: erstellen ein SharePoint-Webparts mithilfe eines Designers](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [Exemplarische Vorgehensweise: Erstellen eines Webparts für SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)  
  
  