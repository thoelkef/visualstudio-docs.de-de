---
title: 'Exemplarische Vorgehensweise: Einfache Datenbindung in einem Projekt auf Dokumentebene | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding [Office development in Visual Studio], worksheet cell to Database field
- worksheets [Office development in Visual Studio], binding worksheet cell to Database field
- Database field [Office development in Visual Studio]
- data [Office development in Visual Studio], binding data
- simple data binding [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 939d45246ea36f4227a0b914210cb0470b325c20
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-simple-data-binding-in-a-document-level-project"></a>Exemplarische Vorgehensweise: Einfache Datenbindung in Projekten auf Dokumentebene
  Diese exemplarische Vorgehensweise veranschaulicht die Grundlagen der Datenbindung in einem Projekt auf Dokumentebene. Ein einzelnes Datenfeld in einer SQL Server-Datenbank, die an einen benannten Bereich in Microsoft Office Excel gebunden ist. Die exemplarischen Vorgehensweise wird gezeigt, wie Steuerelemente hinzufügen, die Sie durch alle Datensätze in der Tabelle einen Bildlauf durchführen können.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Erstellen eine Datenquelle für ein Excel-Projekt.  
  
-   Hinzufügen von Steuerelementen zu einem Arbeitsblatt ein.  
  
-   Durchführen eines Bildlaufs durch Datenbankdatensätze.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Zugriff auf einen Server mit der Beispieldatenbank Northwind-SQL Server.  
  
-   Berechtigungen zum Lesen und Schreiben in SQL Server-Datenbank.  
  
## <a name="creating-a-new-project"></a>Erstellen eines neuen Projekts  
 In diesem Schritt erstellen Sie ein Excel-Arbeitsmappenprojekt.  
  
#### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt  
  
1.  Erstellen Sie ein Excel-Arbeitsmappenprojekt mit dem Namen **Meine einfache Datenbindung**, Visual Basic oder c# verwenden. Stellen Sie sicher, dass **erstellen Sie ein neues Dokument** ausgewählt ist. Weitere Informationen finden Sie unter [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Visual Studio öffnet die neue Excel-Arbeitsmappe im Designer und fügt die **Meine einfache Datenbindung** Projekt **Projektmappen-Explorer**.  
  
## <a name="creating-the-data-source"></a>Erstellen der Datenquelle  
 Verwenden das Fenster **Datenquellen** , um dem Projekt ein typisiertes Dataset hinzuzufügen.  
  
#### <a name="to-create-the-data-source"></a>So erstellen Sie die Datenquelle  
  
1.  Wenn das Fenster **Datenquellen** nicht sichtbar ist, zeigen Sie es an, indem Sie in der Menüleiste **Ansicht**, **Weitere Fenster**und **Datenquellen**wählen.  
  
2.  Wählen Sie **Neue Datenquelle hinzufügen** , um den **Assistenten zum Konfigurieren von Datenquellen**zu starten.  
  
3.  Wählen Sie **Datenbank** , und klicken Sie dann auf **Weiter**.  
  
4.  Wählen Sie eine Datenverbindung zur Northwind-Beispieldatenbank SQL Server, oder fügen Sie eine neue Verbindung unter Verwendung der **neue Verbindung** Schaltfläche.  
  
5.  Nachdem eine Verbindung ausgewählt oder erstellt wurde, klicken Sie auf **Weiter**.  
  
6.  Deaktivieren Sie die Option aus, um die Verbindung zu speichern, wenn diese Option ausgewählt ist, und klicken Sie dann auf **Weiter**.  
  
7.  Erweitern Sie die **Tabellen** Knoten in der **-Datenbankobjekte** Fenster.  
  
8.  Aktivieren Sie das Kontrollkästchen neben den **Kunden** Tabelle.  
  
9. Klicken Sie auf **Fertig stellen**.  
  
 Fügt der Assistent die **Kunden** Tabelle, auf die **Datenquellen** Fenster. Es auch ein typisiertes Dataset dem Projekt hinzugefügt, die in angezeigt wird **Projektmappen-Explorer**.  
  
## <a name="adding-controls-to-the-worksheet"></a>Hinzufügen von Steuerelementen zum Arbeitsblatt  
 In dieser exemplarischen Vorgehensweise benötigen Sie zwei benannte Bereiche und vier Schaltflächen auf das erste Arbeitsblatt. Fügen Sie zunächst die beiden benannten Bereiche aus der **Datenquellen** Fenster, damit sie automatisch an die Datenquelle gebunden sind. Als Nächstes fügen Sie die Schaltflächen über der **Toolbox**.  
  
#### <a name="to-add-two-named-ranges"></a>So fügen Sie zwei benannte Bereiche hinzu  
  
1.  Überprüfen Sie, ob die **Meine einfache Daten Binding.xlsx** Arbeitsmappe geöffnet, in der Visual Studio-Designer ist mit **"Sheet1"** angezeigt.  
  
2.  Öffnen der **Datenquellen** Fenster, und erweitern Sie die **Kunden** Knoten.  
  
3.  Wählen Sie die **CompanyName** Spalte, und klicken Sie dann auf den Dropdown Pfeil, der angezeigt wird.  
  
4.  Wählen Sie **NamedRange** in der Dropdownliste aus, und ziehen Sie dann die **CompanyName** Spalte Zelle **A1**.  
  
     Ein <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement namens `companyNameNamedRange` ist in der Zelle erstellt **A1**. Zur gleichen Zeit eine <xref:System.Windows.Forms.BindingSource> mit dem Namen `customersBindingSource`, Tabellenadapters, und ein <xref:System.Data.DataSet> Instanz werden dem Projekt hinzugefügt. Das Steuerelement gebunden ist die <xref:System.Windows.Forms.BindingSource>, das wiederum gebunden ist, um die <xref:System.Data.DataSet> Instanz.  
  
5.  Wählen Sie die **CustomerID** Spalte in der **Datenquellen** Fenster, und klicken Sie dann auf den Dropdown Pfeil, der angezeigt wird.  
  
6.  Klicken Sie auf **NamedRange** in der Dropdownliste aus, und ziehen Sie dann die **CustomerID** Spalte Zelle **B1**.  
  
7.  Eine andere <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement namens `customerIDNamedRange` ist in der Zelle erstellt **B1**, und das Binden der <xref:System.Windows.Forms.BindingSource>.  
  
#### <a name="to-add-four-buttons"></a>So fügen Sie die vier Schaltflächen hinzu  
  
1.  Aus der **Standardsteuerelementen** auf der Registerkarte die **Toolbox**, Hinzufügen einer <xref:System.Windows.Forms.Button> -Steuerelement zur Zelle **A3** des Arbeitsblatts.  
  
     Diese Schaltfläche den Namen `Button1`.  
  
2.  Fügen Sie drei weitere Schaltflächen für die folgenden Zellen in dieser Reihenfolge, sodass die Namen werden wie gezeigt:  
  
    |Zelle|(Name)|  
    |----------|--------------|  
    |B3|Button2|  
    |C3|Button3|  
    |D3|Button4|  
  
 Der nächste Schritt besteht, die Schaltflächen Text hinzu, und fügen Sie in C#-Ereignishandler hinzu.  
  
## <a name="initializing-the-controls"></a>Initialisieren der Steuerelemente  
 Legen Sie den Text der Schaltfläche, und fügen Sie Ereignishandler während der <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> Ereignis.  
  
#### <a name="to-initialize-the-controls"></a>Um die Steuerelemente zu initialisieren.  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste **Sheet1.vb** oder **Sheet1.cs**, und klicken Sie dann auf **Code anzeigen** im Kontextmenü.  
  
2.  Fügen Sie folgenden Code, der `Sheet1_Startup` Methode, um den Text für jede Schaltfläche festzulegen.  
  
     [!code-csharp[Trin_VstcoreDataExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreDataExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#2)]  
  
3.  Nur c# fügen Ereignishandler für die Schaltfläche click-Ereignisse, die `Sheet1_Startup` Methode.  
  
     [!code-csharp[Trin_VstcoreDataExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#3)]  
  
 Nun fügen Sie Code zum Behandeln der <xref:System.Windows.Forms.Control.Click> Ereignisse der Schaltflächen, damit der Benutzer durch die Datensätze navigieren kann.  
  
## <a name="adding-code-to-enable-scrolling-through-the-records"></a>Hinzufügen von Code zum Durchführen eines Bildlaufs durch die Datensätze aktivieren  
 Hinzufügen von Code für die <xref:System.Windows.Forms.Control.Click> -Ereignishandler der einzelnen Schaltflächen, um durch die Datensätze zu verschieben.  
  
#### <a name="to-move-to-the-first-record"></a>So verschieben Sie in den ersten Datensatz  
  
1.  Fügen Sie einen Ereignishandler für das <xref:System.Windows.Forms.Control.Click> -Ereignis für die `Button1` Schaltfläche, und fügen Sie den folgenden Code hinzu, auf den ersten Eintrag zu verschieben:  
  
     [!code-csharp[Trin_VstcoreDataExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreDataExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#4)]  
  
#### <a name="to-move-to-the-previous-record"></a>So verschieben Sie in den vorherigen Datensatz  
  
1.  Fügen Sie einen Ereignishandler für das <xref:System.Windows.Forms.Control.Click> -Ereignis für die `Button2` Schaltfläche, und fügen Sie den folgenden Code aus, um die Position wieder um eins zu verschieben:  
  
     [!code-csharp[Trin_VstcoreDataExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreDataExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#5)]  
  
#### <a name="to-move-to-the-next-record"></a>So verschieben Sie in den nächsten Datensatz  
  
1.  Fügen Sie einen Ereignishandler für die <xref:System.Windows.Forms.Control.Click> -Ereignis für die `Button3` Schaltfläche, und fügen Sie den folgenden Code aus, um die Position von einem fortzufahren:  
  
     [!code-csharp[Trin_VstcoreDataExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreDataExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#6)]  
  
#### <a name="to-move-to-the-last-record"></a>Bis zum letzten Datensatz wechseln  
  
1.  Fügen Sie einen Ereignishandler für das <xref:System.Windows.Forms.Control.Click> -Ereignis für die `Button4` Schaltfläche, und fügen Sie den folgenden Code aus, um bis zum letzten Datensatz zu verschieben:  
  
     [!code-csharp[Trin_VstcoreDataExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreDataExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#7)]  
  
## <a name="testing-the-application"></a>Testen der Anwendung  
 Sie können jetzt Testen Ihrer Arbeitsmappe, um sicherzustellen, dass Sie die Datensätze in der Datenbank durchsuchen können.  
  
#### <a name="to-test-your-workbook"></a>So testen Sie die Arbeitsmappe  
  
1.  Drücken Sie F5, um das Projekt auszuführen.  
  
2.  Vergewissern Sie sich, dass der erste Datensatz in Zellen angezeigt **A1** und **B1**.  
  
3.  Klicken Sie auf die **>** (`Button3`) Schaltfläche, und vergewissern Sie sich, dass der nächste Datensatz in der Zelle angezeigt wird **A1** und **B1**.  
  
4.  Klicken Sie auf die anderen Navigationsschaltflächen, um sicherzustellen, dass der Datensatz geändert wird, wie erwartet.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Diese exemplarische Vorgehensweise veranschaulicht die Grundlagen der Bindung eines benannten Bereichs an ein Feld in einer Datenbank. Die folgenden Aufgaben könnten sich daran anschließen:  
  
-   Die Daten zwischengespeichert werden, damit es offline verwendet werden kann. Weitere Informationen finden Sie unter [Vorgehensweise: Zwischenspeichern von Daten für Offline verwenden oder auf einem Server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   Binden von Zellen an mehrere Spalten in einer Tabelle anstelle von an ein Feld. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: komplexe Datenbindung in einem Projekt auf Dokumentebene](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md).  
  
-   Verwenden einer <xref:System.Windows.Forms.BindingNavigator> Steuerelement, durch die Datensätze scrollen. Weitere Informationen finden Sie unter [wie: Navigieren Sie Daten mit BindingNavigator-Steuerelement in Windows Forms](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).  
  
## <a name="see-also"></a>Siehe auch  
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Daten in Office-Projektmappen](../vsto/data-in-office-solutions.md)   
 [Exemplarische Vorgehensweise: Komplexe Datenbindung in einem Projekt auf Dokumentebene](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)  
  
  