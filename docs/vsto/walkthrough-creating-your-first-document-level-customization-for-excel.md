---
title: 'Exemplarische Vorgehensweise: Erstellen Sie Ihrer ersten Anpassung auf Dokumentebene, für Excel'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, creating your first project
- Excel [Office development in Visual Studio], creating your first project
- document-level customizations [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 70e82a8b126f5292cd8efe1420c59af90ca59c3d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53955317"
---
# <a name="walkthrough-create-your-first-document-level-customization-for-excel"></a>Exemplarische Vorgehensweise: Erstellen Sie Ihrer ersten Anpassung auf Dokumentebene, für Excel
  Diese exemplarische Vorgehensweise bietet eine Einführung zum Erstellen einer Anpassung auf Dokumentebene für Microsoft Office Excel. Die Features, die Sie in dieser Art von Projektmappe erstellen, sind nur verfügbar, wenn eine bestimmte Arbeitsmappe geöffnet ist. Sie können eine Anpassung auf Dokumentebene nicht verwenden, um anwendungsweite Änderungen vorzunehmen, z. B., um eine neue Registerkarte des Menübands anzuzeigen, wenn eine Arbeitsmappe geöffnet ist.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
- Erstellen eines Excel-Arbeitsmappenprojekts.  
  
- Hinzufügen von Text zu einem Arbeitsblatt, das im Visual Studio-Designer gehostet wird.  
  
- Schreiben von Code, der das Excel-Objektmodell zum Hinzufügen von Text zum angepassten Arbeitsblatt verwendet, wenn dieses geöffnet wird.  
  
- Erstellen Sie das Projekt, und führen Sie es aus, um es zu testen.  
  
- Bereinigen des abgeschlossenen Projekts zum Entfernen nicht benötigter Builddateien und Sicherheitseinstellungen vom Entwicklungscomputer.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="create-the-project"></a>Erstellen eines Projekts  
  
### <a name="to-create-a-new-excel-workbook-project-in-visual-studio"></a>So erstellen Sie ein neues Excel-Arbeitsmappenprojekt in Visual Studio  
  
1. Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2. Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
3. Erweitern Sie im Vorlagenbereich **Visual C#** oder **Visual Basic**und dann **Office/SharePoint**.  
  
4. Wählen Sie unter dem erweiterten Knoten **Office/SharePoint** den Knoten **Office-Add-Ins** aus.  
  
5. Wählen Sie in der Liste der Projektvorlagen ein Excel-VSTO-Add-In-Projekt aus.  
  
6. In der **Namen** geben **FirstWorkbookCustomization**.  
  
7. Klicken Sie auf **OK**.  
  
    Der **Projekt-Assistent aus Visual Studio Tools for Office** wird geöffnet.  
  
8. Wählen Sie **ein neues Dokument erstellen**, und klicken Sie auf **OK**.  
  
   - [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] erstellt die **FirstWorkbookCustomization** Projekt, und fügt Sie dem Projekt die folgenden Dateien.  
  
   - *FirstWorkbookCustomization*.xlsx – Stellt die Excel-Arbeitsmappe im Projekt dar. Enthält alle Arbeitsblätter und Diagramme.  
  
   - Tabelle1 (*vb* Datei für Visual Basic oder *cs* Datei für Visual c#) – ein Arbeitsblatt, das die Entwurfsoberfläche und den Code für das erste Arbeitsblatt in der Arbeitsmappe bereitstellt. Weitere Informationen finden Sie unter [Arbeitsblatt-Hostelement](../vsto/worksheet-host-item.md).  
  
   - Tabelle2 (*vb* Datei für Visual Basic oder *cs* Datei für Visual c#) – ein Arbeitsblatt, das die Entwurfsoberfläche und den Code für das zweite Arbeitsblatt in der Arbeitsmappe bereitstellt.  
  
   - Sheet3 (*vb* Datei für Visual Basic oder *cs* Datei für Visual c#) – ein Arbeitsblatt, das die Entwurfsoberfläche und den Code für das dritte Arbeitsblatt in der Arbeitsmappe bereitstellt.  
  
   - ThisWorkbook (*vb* Datei für Visual Basic oder *cs* Datei für Visual c#) – enthält die Entwurfsoberfläche und den Code für Anpassungen auf Arbeitsmappenebene. Weitere Informationen finden Sie unter [Arbeitsmappenhostelement](../vsto/workbook-host-item.md).  
  
     Die Codedatei "Sheet1" wird automatisch im Designer geöffnet.  
  
## <a name="close-and-reopen-worksheets-in-the-designer"></a>Schließen und Öffnen von Arbeitsblättern im designer  
 Wenn Sie eine Arbeitsmappe oder ein Arbeitsblatt absichtlich oder versehentlich im Designer schließen, während Sie das Projekt entwickeln, können Sie sie bzw. es erneut öffnen.  
  
### <a name="to-close-and-reopen-a-worksheet-in-the-designer"></a>So schließen Sie ein Arbeitsblatt im Designer und öffnen es erneut  
  
1.  Schließen Sie die Arbeitsmappe, indem Sie auf die **schließen** Schaltfläche (X) für das Designer-Fenster.  
  
2.  In **Projektmappen-Explorer**, mit der rechten Maustaste die **Sheet1** Codedatei, und klicken Sie auf **Ansicht-Designer**.  
  
     \- oder –  
  
     In **Projektmappen-Explorer**, doppelklicken Sie auf die **Sheet1** Codedatei.  
  
## <a name="add-text-to-a-worksheet-in-the-designer"></a>Hinzufügen von Text in einem Arbeitsblatt im designer  
 Sie können die Benutzeroberfläche (User Interface, UI) Ihrer Anpassung gestalten, indem Sie das im Designer geöffnete Arbeitsblatt ändern. Beispielsweise können Sie Zellen Text hinzufügen, Formeln anwenden oder Excel-Steuerelemente hinzufügen. Weitere Informationen zur Verwendung des Designers finden Sie unter [Office-Projekten in Visual Studio-Umgebung](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
### <a name="to-add-text-to-a-worksheet-by-using-the-designer"></a>So fügen Sie einem Arbeitsblatt mithilfe des Designers Text hinzu  
  
1.  Wählen Sie in das Arbeitsblatt, das im Designer geöffnet ist, Zelle **A1**, und geben Sie dann den folgenden Text.  
  
     **Dieser Text wurde mithilfe des Designers hinzugefügt.**  
  
> [!WARNING]  
>  Wenn Sie diese Textzeile der Zelle hinzufügen **A2**, wird Sie von anderem Code in diesem Beispiel überschrieben.  
  
## <a name="add-text-to-a-worksheet-programmatically"></a>Fügen Sie Text in einem Arbeitsblatt programmgesteuert hinzu  
 Als Nächstes fügen Sie der Codedatei "Sheet1" Code hinzu. Der neue Code verwendet das Excel-Objektmodell, um der Arbeitsmappe eine zweite Textzeile hinzuzufügen. Standardmäßig enthält die Codedatei "Sheet1" den folgenden generierten Code:  
  
-   Eine partielle Definition der `Sheet1`-Klasse, die das Programmiermodell des Arbeitsblatts darstellt und den Zugriff auf das Excel-Objektmodell bereitstellt. Weitere Informationen [Arbeitsblatt-Hostelement](../vsto/worksheet-host-item.md) und [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md). Der Rest der `Sheet1` -Klasse ist in einer ausgeblendeten Codedatei definiert, die nicht geändert werden darf.  
  
-   Die Ereignishandler `Sheet1_Startup` und `Sheet1_Shutdown` . Diese Ereignishandler werden aufgerufen, wenn Ihre Anpassung von Excel geladen und entladen wird. Verwenden Sie diese Ereignishandler zum Initialisieren der Anpassung, wenn sie geladen wird, und zum Bereinigen der von der Anpassung verwendeten Ressourcen, wenn sie entladen wird. Weitere Informationen finden Sie unter [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md).  
  
### <a name="to-add-a-second-line-of-text-to-the-worksheet-by-using-code"></a>So fügen Sie dem Arbeitsblatt mithilfe von Code eine zweite Textzeile hinzu  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste **Sheet1**, und klicken Sie dann auf **Ansichtscode**.  
  
     Die Codedatei wird in Visual Studio geöffnet.  
  
2.  Ersetzen Sie den `Sheet1_Startup`-Ereignishandler durch den folgenden Code. Beim Öffnen von "Sheet1" wird dem Arbeitsblatt durch diesen Code eine zweite Textzeile hinzugefügt.  
  
     [!code-csharp[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/CSharp/Trin_ExcelWorkbookTutorial/Sheet1.cs#1)]
     [!code-vb[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ExcelWorkbookTutorial/Sheet1.vb#1)]  
  
## <a name="test-the-project"></a>Testen Sie das Projekt  
  
### <a name="to-test-your-workbook"></a>So testen Sie die Arbeitsmappe  
  
1.  Drücken Sie **F5** , um das Projekt zu erstellen und auszuführen.  
  
     Wenn Sie das Projekt erstellen, wird der Code in eine Assembly kompiliert, die der Arbeitsmappe zugeordnet ist. Visual Studio legt eine Kopie der Arbeitsmappe und der Assembly im Buildausgabeordner für das Projekt ab und konfiguriert die Sicherheitseinstellungen auf dem Entwicklungscomputer, damit die Anpassung ausgeführt werden kann. Weitere Informationen finden Sie unter [erstellen Office-Projektmappen](../vsto/building-office-solutions.md).  
  
2.  Vergewissern Sie sich, dass der folgende Text in der Arbeitsmappe angezeigt wird.  
  
     **Dieser Text wurde mithilfe des Designers hinzugefügt.**  
  
     **Dieser Text wurde per Code hinzugefügt.**  
  
3.  Schließen Sie die Arbeitsmappe.  
  
## <a name="clean-up-the-project"></a>Bereinigen Sie das Projekt  
 Wenn Sie die Entwicklung eines Projekts abgeschlossen haben, sollten Sie die Dateien im Buildausgabeordner und die Sicherheitseinstellungen entfernen, die durch den Buildvorgang erstellt wurden.  
  
### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>So bereinigen Sie das abgeschlossene Projekt auf dem Entwicklungscomputer  
  
1.  Klicken Sie in Visual Studio im Menü **Build** auf **Projektmappe bereinigen**.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Da Sie nun eine grundlegende Anpassung auf Dokumentebene für Excel erstellt haben, können Sie mehr über die Entwicklung von Anpassungen in den folgenden Themen erfahren:  
  
-   Allgemeine Programmieraufgaben, die Sie in Anpassungen auf Dokumentebene ausführen können: [Programmieren von Anpassungen auf Dokumentebene](../vsto/programming-document-level-customizations.md).  
  
-   Programmieraufgaben, die für Anpassungen auf Dokumentebene für Excel spezifisch sind: [Excel-Projektmappen](../vsto/excel-solutions.md).  
  
-   Verwenden das Objektmodell von Excel: [Übersicht über Excel-Objektmodell](../vsto/excel-object-model-overview.md).  
  
-   Anpassen der Benutzeroberfläche von Excel, z. B. durch Hinzufügen einer benutzerdefinierten Registerkarte zum Menüband oder durch Erstellen eines eigenen Aktionsbereichs: [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).  
  
-   Mithilfe von erweiterten Excel-Objekten, die von Office-Entwicklungstools in Visual Studio bereitgestellten Aufgaben, die mit dem Excel-Objektmodell (z. B. Hosten verwalteter Steuerelemente für Dokumente und binden Excel-Steuerelementen an Daten mithilfe der Windows-Formulare nicht möglich sind -Datenbindungsmodell verwendet): [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md).  
  
-   Erstellen und Debuggen von Anpassungen auf Dokumentebene für Excel: [Erstellen von Office-Projektmappen](../vsto/building-office-solutions.md).  
  
-   Bereitstellen von Anpassungen auf Dokumentebene für Excel: [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Excel-Projektmappen](../vsto/excel-solutions.md)   
 [Programmieren von Anpassungen auf Dokumentebene](../vsto/programming-document-level-customizations.md)   
 [Übersicht über Excel-Objektmodell](../vsto/excel-object-model-overview.md)   
 [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)   
 [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md)   
 [Erstellen von Office-Projektmappen](../vsto/building-office-solutions.md)   
 [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)   
 [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md)  
