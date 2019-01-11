---
title: 'Exemplarische Vorgehensweise: Erstellen der ersten Anpassung der auf Dokumentebene für Word'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, creating your first project
- Word [Office development in Visual Studio], creating your first project
- document-level customizations [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8aff32bbbbc396651079d16449e9746760c4541e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53856424"
---
# <a name="walkthrough-create-your-first-document-level-customization-for-word"></a>Exemplarische Vorgehensweise: Erstellen der ersten Anpassung der auf Dokumentebene für Word
  Diese exemplarische Vorgehensweise bietet eine Einführung zum Erstellen einer Anpassung auf Dokumentebene für Microsoft Office Word. Die Features, die Sie in dieser Art von Lösung erstellen, sind nur verfügbar, wenn ein bestimmtes Dokument geöffnet ist. Sie können eine Anpassung auf Dokumentebene nicht verwenden, um anwendungsweite Änderungen (z. B. eine neue Registerkarte des Menübands anzuzeigen, wenn ein Dokument geöffnet ist) vorzunehmen.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
- Erstellen eines Word-Dokumentprojekts.  
  
- Hinzufügen von Text zu dem Dokument, das in Visual Studio-Designer gehostet wird.  
  
- Schreiben von Code, der das Word-Objektmodell zum Hinzufügen von Text zum angepassten Dokument verwendet, wenn dieses geöffnet wird.  
  
- Erstellen Sie das Projekt, und führen Sie es aus, um es zu testen.  
  
- Bereinigen des Projekts zum Entfernen nicht benötigter Builddateien und Sicherheitseinstellungen vom Entwicklungscomputer.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## <a name="create-the-project"></a>Erstellen eines Projekts  
  
### <a name="to-create-a-new-word-document-project-in-visual-studio"></a>So erstellen Sie ein neues Word-Dokumentprojekt in Visual Studio  
  
1.  Starten Sie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
3.  Erweitern Sie im Vorlagenbereich **Visual C#** oder **Visual Basic**und dann **Office/SharePoint**.  
  
4.  Wählen Sie unter dem erweiterten Knoten **Office/SharePoint** den Knoten **Office-Add-Ins** aus.  
  
5.  Wählen Sie in der Liste der Projektvorlagen ein Word VSTO-Dokumentprojekt aus.  
  
6.  In der **Namen** geben **FirstDocumentCustomization**.  
  
7.  Klicken Sie auf **OK**.  
  
     Der **Projekt-Assistent aus Visual Studio Tools for Office** wird geöffnet.  
  
8.  Wählen Sie **ein neues Dokument erstellen**, und klicken Sie auf **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] erstellt die **FirstDocumentCustomization** und fügt die **FirstDocumentCustomization** Dokument und der Codedatei "ThisDocument" dem Projekt. Die **FirstDocumentCustomization** Dokument wird automatisch im Designer geöffnet.  
  
## <a name="close-and-reopen-the-document-in-the-designer"></a>Schließen Sie und öffnen Sie das Dokument im designer  
 Wenn Sie das Dokument absichtlich oder versehentlich im Designer schließen, während Sie das Projekt entwickeln, können Sie es erneut öffnen.  
  
### <a name="to-close-and-reopen-the-document-in-the-designer"></a>So schließen Sie das Dokument im Designer und öffnen es erneut  
  
1.  Schließen Sie das Dokument, indem Sie auf die **schließen** Schaltfläche (X) für das Designer-Fenster.  
  
2.  In **Projektmappen-Explorer**, mit der rechten Maustaste die **ThisDocument** Codedatei, und klicken Sie auf **Ansicht-Designer**.  
  
     \- oder –  
  
     In **Projektmappen-Explorer**, doppelklicken Sie auf die **ThisDocument** Codedatei.  
  
## <a name="add-text-to-the-document-in-the-designer"></a>Hinzufügen von Text zum Dokument im designer  
 Sie können die Benutzeroberfläche (User Interface, UI) Ihrer Anpassung gestalten, indem Sie das im Designer geöffnete Dokument ändern. Sie können z. B. Text, Tabellen oder Word-Steuerelemente hinzufügen. Weitere Informationen zur Verwendung des Designers finden Sie unter [Office-Projekten in Visual Studio-Umgebung](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
### <a name="to-add-text-to-your-document-by-using-the-designer"></a>So fügen Sie Ihrem Dokument mithilfe des Designers Text hinzu  
  
1.  Geben Sie den folgenden Text in das Dokument ein, das im Designer geöffnet ist.  
  
     **Dieser Text wurde mithilfe des Designers hinzugefügt.**  
  
## <a name="add-text-to-the-document-programmatically"></a>Fügen Sie Text zum Dokument programmgesteuert hinzu  
 Fügen Sie der Codedatei "ThisDocument " nun Code hinzu. Der neue Code verwendet das Word-Objektmodell, um dem Dokument einen zweiten Textabsatz hinzuzufügen. Standardmäßig enthält die Codedatei "ThisDocument " den folgenden generierten Code:  
  
-   Eine partielle Definition der Klasse `ThisDocument`, die das Programmiermodell des Dokuments darstellt und den Zugriff auf das Word-Objektmodell bereitstellt. Weitere Informationen finden Sie unter [Dokumenthostelement](../vsto/document-host-item.md) und [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md). Der Rest der `ThisDocument` -Klasse ist in einer ausgeblendeten Codedatei definiert, die nicht geändert werden darf.  
  
-   Die `ThisDocument_Startup`- und `ThisDocument_Shutdown`-Ereignishandler. Diese Ereignishandler werden aufgerufen, wenn das Dokument geöffnet und geschlossen wird. Verwenden Sie diese Ereignishandler, um Ihre Anpassung zu initialisieren, wenn das Dokument geöffnet wird, sowie zum Bereinigen von Ressourcen, die von Ihrer Anpassung verwendet werden, wenn das Dokument geschlossen wird. Weitere Informationen finden Sie unter [Ereignisse in Office-Projekten](../vsto/events-in-office-projects.md).  
  
### <a name="to-add-a-second-paragraph-of-text-to-the-document-by-using-code"></a>So fügen Sie dem Dokument mithilfe von Code einen zweiten Textabsatz hinzu  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste **ThisDocument**, und klicken Sie dann auf **Ansichtscode**.  
  
     Die Codedatei wird in Visual Studio geöffnet.  
  
2.  Ersetzen Sie den `ThisDocument_Startup` -Ereignishandler durch den folgenden Code. Beim Öffnen des Dokuments fügt dieser Code dem Dokument einen zweiten Textabsatz hinzu.  
  
     [!code-vb[Trin_WordDocumentTutorial#1](../vsto/codesnippet/VisualBasic/FirstDocumentCustomization/ThisDocument.vb#1)]
     [!code-csharp[Trin_WordDocumentTutorial#1](../vsto/codesnippet/CSharp/FirstDocumentCustomization/ThisDocument.cs#1)]  
  
    > [!NOTE]  
    >  Dieser Code verwendet den Indexwert 1 in der Eigenschaft <xref:Microsoft.Office.Tools.Word.Document.Paragraphs%2A>, um auf den ersten Absatz zuzugreifen. Obwohl Visual Basic und Visual C# auf Null basierende Arrays verwenden, ist die untere Arraygrenze der meisten Auflistungen im Word-Objektmodell 1. Weitere Informationen finden Sie unter [schreiben Sie Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md).  
  
## <a name="test-the-project"></a>Testen Sie das Projekt  
  
### <a name="to-test-your-document"></a>So testen Sie das Dokument  
  
1.  Drücken Sie **F5** , um das Projekt zu erstellen und auszuführen.  
  
     Wenn Sie das Projekt erstellen, wird der Code in eine Assembly kompiliert, die dem Dokument zugeordnet ist. Visual Studio legt eine Kopie des Dokuments und der Assembly im Buildausgabeordner für das Projekt ab und konfiguriert die Sicherheitseinstellungen auf dem Entwicklungscomputer, damit die Anpassung ausgeführt werden kann. Weitere Informationen finden Sie unter [erstellen Office-Projektmappen](../vsto/building-office-solutions.md).  
  
2.  Vergewissern Sie sich im Dokument, dass der folgende Text angezeigt wird.  
  
     **Dieser Text wurde mithilfe des Designers hinzugefügt.**  
  
     **Dieser Text wurde per Code hinzugefügt.**  
  
3.  Schließen Sie das Dokument.  
  
## <a name="clean-up-the-project"></a>Bereinigen Sie das Projekt  
 Wenn Sie die Entwicklung eines Projekts abgeschlossen haben, sollten Sie die Dateien im Buildausgabeordner und die Sicherheitseinstellungen entfernen, die durch den Buildvorgang erstellt wurden.  
  
### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>So bereinigen Sie das abgeschlossene Projekt auf dem Entwicklungscomputer  
  
1.  Klicken Sie in Visual Studio im Menü **Build** auf **Projektmappe bereinigen**.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Da Sie nun eine grundlegende Anpassung auf Dokumentebene für Word erstellt haben, können Sie mehr über die Entwicklung von Anpassungen in den folgenden Themen erfahren:  
  
-   Allgemeine Programmieraufgaben, die Sie in Anpassungen auf Dokumentebene ausführen können: [Programmieren von Anpassungen auf Dokumentebene](../vsto/programming-document-level-customizations.md).  
  
-   Programmieraufgaben, die für Anpassungen auf Dokumentebene für Word spezifisch sind: [Word-Projektmappen](../vsto/word-solutions.md).  
  
-   Verwenden das Objektmodell von Word: [Word-Objektmodell-Übersicht](../vsto/word-object-model-overview.md).  
  
-   Anpassen der Benutzeroberfläche von Word, z. B. durch Hinzufügen einer benutzerdefinierten Registerkarte zum Menüband oder durch Erstellen eines eigenen Aktionsbereichs: [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).  
  
-   Verwenden erweiterter Word-Objekte, die von Office-Projektmappen in Visual Studio bereitgestellten Aufgaben, die mit dem Word-Objektmodell (z. B. Hosten verwalteter Steuerelemente für Dokumente und Binden von Word-Steuerelemente an Daten mithilfe der Windows Forms-Daten nicht möglich sind Bindung-Modell): [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md).  
  
-   Erstellen und Debuggen von Anpassungen auf Dokumentebene für Word: [Erstellen von Office-Projektmappen](../vsto/building-office-solutions.md).  
  
-   Bereitstellen von Anpassungen auf Dokumentebene für Word: [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Word-Projektmappen](../vsto/word-solutions.md)   
 [Programmieren von Anpassungen auf Dokumentebene](../vsto/programming-document-level-customizations.md)   
 [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md)   
 [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)   
 [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md)   
 [Erstellen von Office-Projektmappen](../vsto/building-office-solutions.md)   
 [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)   
 [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md)  
