---
title: "Exemplarische Vorgehensweise: Automatisieren einer Anwendung über einen benutzerdefinierten Aufgabenbereich | Microsoft Docs"
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
helpviewer_keywords:
- task panes [Office development in Visual Studio], PowerPoint
- PowerPoint [Office development in Visual Studio], custom task panes
- automating Office applications
- custom task panes [Office development in Visual Studio], automating applications
- custom task panes [Office development in Visual Studio], PowerPoint
- task panes [Office development in Visual Studio], automating applications
ms.assetid: 77be5ab5-e330-4564-87ec-9cba564ba8f9
caps.latest.revision: "37"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c08f04af21e42761b9b9c7e1a760e71fe79d025a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-automating-an-application-from-a-custom-task-pane"></a>Exemplarische Vorgehensweise: Automatisieren einer Anwendung über einen benutzerdefinierten Aufgabenbereich
  In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie ein benutzerdefinierter Aufgabenbereich erstellt wird, der PowerPoint automatisiert. Der benutzerdefinierte Aufgabenbereich fügt Daten in eine Folie ein, wenn der Benutzer auf ein <xref:System.Windows.Forms.MonthCalendar> -Steuerelement im benutzerdefinierten Aufgabenbereich klickt.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Obwohl in dieser exemplarischen Vorgehensweise speziell PowerPoint verwendet wird, gelten die Konzepte in dieser exemplarischen Vorgehensweise für alle oben aufgelisteten Anwendungen.  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Entwerfen der Benutzeroberfläche des benutzerdefinierten Aufgabenbereichs  
  
-   Automatisieren von PowerPoint über den benutzerdefinierten Aufgabenbereich  
  
-   Anzeigen des benutzerdefinierten Aufgabenbereichs in PowerPoint  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft PowerPoint 2010 oder [!INCLUDE[PowerPoint_15_short](../vsto/includes/powerpoint-15-short-md.md)].  
  
## <a name="creating-the-add-in-project"></a>Erstellen des Add-In-Projekts  
 Im ersten Schritt erstellen Sie ein VSTO-Add-In-Projekt für PowerPoint.  
  
#### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt  
  
1.  Erstellen Sie mithilfe der PowerPoint-Add-In-Projektvorlage ein PowerPoint-VSTO-Add-In-Projekt mit dem Namen **MyAddIn**. Weitere Informationen finden Sie unter [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] öffnet die Codedatei **ThisAddIn.cs** oder **ThisAddIn.vb** und fügt dem **Projektmappen-Explorer** das **MyAddIn**-Projekt hinzu.  
  
## <a name="designing-the-user-interface-of-the-custom-task-pane"></a>Entwerfen der Benutzeroberfläche des benutzerdefinierten Aufgabenbereichs  
 Es gibt keinen visuellen Designer für benutzerdefinierte Aufgabenbereiche, Sie können aber dennoch ein Benutzersteuerelement mit dem gewünschten Layout entwerfen. Im weiteren Verlauf dieser exemplarischen Vorgehensweise fügen Sie dem benutzerdefinierten Aufgabenbereich das Benutzersteuerelement hinzu.  
  
#### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>So entwerfen Sie die Benutzeroberfläche des benutzerdefinierten Aufgabenbereichs  
  
1.  Klicken Sie im Menü **Projekt** auf **Benutzersteuerelement hinzufügen**.  
  
2.  Ändern Sie im Dialogfeld **Neues Element hinzufügen** den Namen des Benutzersteuerelements in **MyUserControl**, und klicken Sie auf **Hinzufügen**.  
  
     Das Benutzersteuerelement wird im Designer geöffnet.  
  
3.  Ziehen Sie von der Registerkarte **Allgemeine Steuerelemente** der **Toolbox**ein **MonthCalendar** -Steuerelement auf das Benutzersteuerelement.  
  
     Wenn der Umfang des **MonthCalendar** -Steuerelements größer als die Entwurfsoberfläche des Benutzersteuerelements ist, passen Sie die Größe des Benutzersteuerelements an das **MonthCalendar** -Steuerelement an.  
  
## <a name="automating-powerpoint-from-the-custom-task-pane"></a>Automatisieren von PowerPoint über den benutzerdefinierten Aufgabenbereich  
 Mit dem VSTO-Add-In soll in der ersten Folie der aktiven Präsentation ein ausgewähltes Datum eingefügt werden. Verwenden Sie das <xref:System.Windows.Forms.MonthCalendar.DateChanged> -Ereignis des Steuerelements, um das ausgewählte Datum bei jeder Änderung des Datums hinzuzufügen.  
  
#### <a name="to-automate-powerpoint-from-the-custom-task-pane"></a>So automatisieren Sie PowerPoint über den benutzerdefinierten Aufgabenbereich  
  
1.  Doppelklicken Sie im Designer auf das <xref:System.Windows.Forms.MonthCalendar> -Steuerelement.  
  
     Die Datei **MyUserControl.cs** oder **MyUserControl.vb** wird geöffnet, und ein Ereignishandler für das <xref:System.Windows.Forms.MonthCalendar.DateChanged> -Ereignis wird erstellt.  
  
2.  Fügen Sie am Anfang der Datei folgenden Code hinzu. Mit diesem Code werden Aliase für den <xref:Microsoft.Office.Core> -Namespace und den <xref:Microsoft.Office.Interop.PowerPoint> -Namespace erstellt.  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#1](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#1)]
     [!code-vb[Trin_TaskPaneMonthCalendar#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#1)]  
  
3.  Fügen Sie der `MyUserControl` -Klasse folgenden Code hinzu. Durch diesen Code wird ein <xref:Microsoft.Office.Interop.PowerPoint.Shape> -Objekt als Member von `MyUserControl`deklariert. Im nächsten Schritt verwenden Sie diese <xref:Microsoft.Office.Interop.PowerPoint.Shape> , um einer Folie in der aktiven Präsentation ein Textfeld hinzuzufügen.  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#2](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#2)]
     [!code-vb[Trin_TaskPaneMonthCalendar#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#2)]  
  
4.  Ersetzen Sie den `monthCalendar1_DateChanged` -Ereignishandler durch den folgenden Code. Mit diesem Code wird in die erste Folie in der aktiven Präsentation ein Textfeld eingefügt, in das anschließend das aktuell ausgewählte Datum eingefügt wird. Im Code wird mithilfe des `Globals.ThisAddIn` -Objekts auf das PowerPoint-Objektmodell zugegriffen.  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#3](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#3)]
     [!code-vb[Trin_TaskPaneMonthCalendar#3](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#3)]  
  
5.  Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf das **MyAddIn** -Projekt, und klicken Sie dann auf **Erstellen**. Vergewissern Sie sich, dass das Projekt ohne Fehler erstellt wurde.  
  
## <a name="displaying-the-custom-task-pane"></a>Anzeigen des benutzerdefinierten Aufgabenbereichs  
 Um den benutzerdefinierten Aufgabenbereich beim Starten des VSTO-Add-Ins anzuzeigen, fügen Sie dem Aufgabenbereich das Benutzersteuerelement im <xref:Microsoft.Office.Tools.AddIn.Startup> -Ereignishandler des VSTO-Add-Ins hinzu.  
  
#### <a name="to-display-the-custom-task-pane"></a>So zeigen Sie den benutzerdefinierten Aufgabenbereich an  
  
1.  Erweitern Sie **PowerPoint**im **Projektmappen-Explorer**.  
  
2.  Klicken Sie mit der rechten Maustaste auf **ThisAddIn.cs** oder **ThisAddIn.vb** , und klicken Sie auf **Code anzeigen**.  
  
3.  Fügen Sie der `ThisAddIn` -Klasse folgenden Code hinzu. Dieser Code deklariert Instanzen von `MyUserControl` und <xref:Microsoft.Office.Tools.CustomTaskPane> als Member der `ThisAddIn` -Klasse.  
  
     [!code-vb[Trin_TaskPaneMonthCalendar#4](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/ThisAddIn.vb#4)]
     [!code-csharp[Trin_TaskPaneMonthCalendar#4](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/ThisAddIn.cs#4)]  
  
4.  Ersetzen Sie den `ThisAddIn_Startup` -Ereignishandler durch den folgenden Code. Durch diesen Code wird ein neuer <xref:Microsoft.Office.Tools.CustomTaskPane> erstellt, indem der `MyUserControl` -Auflistung das `CustomTaskPanes` -Objekt hinzugefügt wird. Durch den Code wird auch der Aufgabenbereich angezeigt.  
  
     [!code-vb[Trin_TaskPaneMonthCalendar#5](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/ThisAddIn.vb#5)]
     [!code-csharp[Trin_TaskPaneMonthCalendar#5](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/ThisAddIn.cs#5)]  
  
## <a name="testing-the-add-in"></a>Testen des Add-Ins  
 Wenn Sie das Projekt ausführen, wird PowerPoint geöffnet, und das VSTO-Add-In zeigt den benutzerdefinierten Aufgabenbereich an. Klicken Sie auf das <xref:System.Windows.Forms.MonthCalendar> -Steuerelement, um den Code zu testen.  
  
#### <a name="to-test-your-vsto-add-in"></a>So testen Sie Ihr VSTO-Add-In  
  
1.  Drücken Sie F5, um das Projekt auszuführen.  
  
2.  Vergewissern Sie sich, dass der benutzerdefinierte Aufgabenbereich sichtbar ist.  
  
3.  Klicken Sie im <xref:System.Windows.Forms.MonthCalendar> -Steuerelement des Aufgabenbereichs auf ein Datum.  
  
     Das Datum wird in die erste Folie der aktiven Präsentation eingefügt.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Weitere Informationen über das Erstellen von benutzerdefinierten Aufgabenbereichen finden Sie in diesen Themen:  
  
-   Erstellen eines benutzerdefinierten Aufgabenbereichs in einem VSTO-Add-In für eine andere Anwendung. Weitere Informationen zu den Anwendungen, die benutzerdefinierte Aufgabenbereiche unterstützen, finden Sie unter [benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md).  
  
-   Erstellen einer Menübandschaltfläche, mit der ein benutzerdefinierter Aufgabenbereich ausgeblendet oder angezeigt werden kann. Weitere Informationen finden Sie unter [Walkthrough: Synchronizing a Custom Task Pane with a Ribbon Button](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).  
  
-   Erstellen eines benutzerdefinierten Aufgabenbereichs für jede E-Mail-Nachricht, die in Outlook geöffnet wird. Weitere Informationen finden Sie unter [Walkthrough: Displaying Custom Task Panes with E-Mail Messages in Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md)   
 [Vorgehensweise: Hinzufügen ein benutzerdefinierten Aufgabenbereichs zu einer Anwendung](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Exemplarische Vorgehensweise: Synchronisieren eines benutzerdefinierten Aufgabenbereichs mit einer Menübandschaltfläche](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)   
 [Exemplarische Vorgehensweise: Anzeigen von benutzerdefinierten Aufgabenbereichen in E-Mails in Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)  
  
  