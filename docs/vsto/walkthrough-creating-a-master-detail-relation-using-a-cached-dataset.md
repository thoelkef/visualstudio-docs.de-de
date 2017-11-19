---
title: 'Exemplarische Vorgehensweise: Erstellen einer Master-Detail-Beziehung mithilfe eines zwischengespeicherten Datasets | Microsoft Docs'
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
- master-detail tables [Office development in Visual Studio], walkthroughs
- data caching [Office development in Visual Studio], Master/Detail Relation
ms.assetid: 419f4e07-c67f-4fc9-973a-bc794f349ac3
caps.latest.revision: "41"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b392b4de0288478c73fba8cecd88be1f701cd5ae
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-master-detail-relation-using-a-cached-dataset"></a>Exemplarische Vorgehensweise: Erstellen einer Master-Detail-Beziehung mithilfe eines zwischengespeicherten Datasets
  Diese exemplarische Vorgehensweise veranschaulicht das Erstellen einer Master/Detail-Beziehungs in einem Arbeitsblatt und das Zwischenspeichern der Daten, damit die Projektmappe offline verwendet werden kann.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Bei dieser exemplarischen Vorgehensweise lernen Sie Folgendes:  
  
-   Hinzufügen von Steuerelementen zu einem Arbeitsblatt.  
  
-   Richten Sie ein Dataset in einem Arbeitsblatt zwischengespeichert werden soll.  
  
-   Fügen Sie Code zum Durchführen eines Bildlaufs durch die Datensätze zu aktivieren.  
  
-   Testen des Projekts.  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Zugriff auf die Beispieldatenbank Northwind-SQL Server. Die Datenbank möglich auf dem Entwicklungscomputer oder auf einem Server.  
  
-   Berechtigungen zum Lesen und Schreiben in SQL Server-Datenbank.  
  
## <a name="creating-a-new-project"></a>Erstellen eines neuen Projekts  
 In diesem Schritt erstellen Sie ein Excel-Arbeitsmappenprojekt.  
  
#### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt  
  
1.  Erstellen Sie ein Excel-Arbeitsmappenprojekt mit dem Namen **Meine Master / Detail-**, mit Visual Basic oder c#. Stellen Sie sicher, dass **erstellen Sie ein neues Dokument** ausgewählt ist. Weitere Informationen finden Sie unter [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Visual Studio öffnet die neue Excel-Arbeitsmappe im Designer und fügt die **Meine Master / Detail-** Projekt **Projektmappen-Explorer**.  
  
## <a name="creating-the-data-source"></a>Erstellen der Datenquelle  
 Verwenden das Fenster **Datenquellen** , um dem Projekt ein typisiertes Dataset hinzuzufügen.  
  
#### <a name="to-create-the-data-source"></a>So erstellen Sie die Datenquelle  
  
1.  Wenn das Fenster **Datenquellen** nicht sichtbar ist, zeigen Sie es an, indem Sie in der Menüleiste **Ansicht**, **Weitere Fenster**und **Datenquellen**wählen.  
  
2.  Wählen Sie **Neue Datenquelle hinzufügen** , um den **Assistenten zum Konfigurieren von Datenquellen**zu starten.  
  
3.  Wählen Sie **Datenbank** , und klicken Sie dann auf **Weiter**.  
  
4.  Wählen Sie eine Datenverbindung zur Northwind-Beispieldatenbank SQL Server, oder fügen Sie eine neue Verbindung mit der **neue Verbindung** Schaltfläche.  
  
5.  Nach dem auswählen oder erstellen eine Verbindung, klicken Sie auf **Weiter**.  
  
6.  Deaktivieren Sie die Option aus, um die Verbindung zu speichern, wenn diese Option ausgewählt ist, und klicken Sie dann auf **Weiter**.  
  
7.  Erweitern Sie die **Tabellen** Knoten in der **-Datenbankobjekte** Fenster.  
  
8.  Wählen Sie die **Aufträge** Tabelle und die **Bestelldetails** Tabelle.  
  
9. Klicken Sie auf **Fertig stellen**.  
  
 Der Assistent fügt die beiden Tabellen die **Datenquellen** Fenster. Es auch ein typisiertes Dataset dem Projekt hinzugefügt, die in angezeigt wird **Projektmappen-Explorer**.  
  
## <a name="adding-controls-to-the-worksheet"></a>Hinzufügen von Steuerelementen zum Arbeitsblatt  
 In diesem Schritt fügen Sie einen benannten Bereich, ein Listenobjekt und zwei Schaltflächen auf das erste Arbeitsblatt hinzu. Fügen Sie zunächst den benannten Bereich und das Listenobjekt aus der **Datenquellen** Fenster, damit sie automatisch an die Datenquelle gebunden sind. Als Nächstes fügen Sie die Schaltflächen über der **Toolbox**.  
  
#### <a name="to-add-a-named-range-and-a-list-object"></a>So fügen Sie einen benannten Bereich und ein Listenobjekt hinzu  
  
1.  Überprüfen Sie, ob die **Meine Master-Detail.xlsx** Arbeitsmappe geöffnet, in der Visual Studio-Designer ist mit **"Sheet1"** angezeigt.  
  
2.  Öffnen der **Datenquellen** Fenster, und erweitern Sie die **Aufträge** Knoten.  
  
3.  Wählen Sie die **OrderID** Spalte, und klicken Sie dann auf den Dropdown Pfeil, der angezeigt wird.  
  
4.  Klicken Sie auf **NamedRange** in der Dropdownliste aus, und ziehen Sie dann die **OrderID** Spalte Zelle **A2**.  
  
     Ein <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement namens `OrderIDNamedRange` ist in der Zelle erstellt **A2**. Zur gleichen Zeit eine <xref:System.Windows.Forms.BindingSource> mit dem Namen `OrdersBindingSource`, Tabellenadapters, und ein <xref:System.Data.DataSet> Instanz werden dem Projekt hinzugefügt. Das Steuerelement gebunden ist die <xref:System.Windows.Forms.BindingSource>, das wiederum gebunden ist, um die <xref:System.Data.DataSet> Instanz.  
  
5.  Führen Sie einen Bildlauf nach unten nach den Spalten, die unter der **Aufträge** Tabelle. Wird am unteren Rand der Liste der **Order Details** Tabelle; ist hier, da es ein untergeordnetes Element eines ist die **Aufträge** Tabelle. Wählen Sie diese Option **Bestelldetails** Tabelle, nicht auf das Projekt, das auf der gleichen Ebene wie ist die **Aufträge** Tabelle, und klicken Sie dann auf den Dropdown Pfeil, der angezeigt wird.  
  
6.  Klicken Sie auf **ListObject** in der Dropdownliste aus, und ziehen Sie dann die **OrderDetails** Tabelle Zelle **A6**.  
  
7.  Ein <xref:Microsoft.Office.Tools.Excel.ListObject> Steuerelement namens **Order_DetailsListObject** ist in der Zelle erstellt **A6**, und das Binden der <xref:System.Windows.Forms.BindingSource>.  
  
#### <a name="to-add-two-buttons"></a>So fügen Sie zwei Schaltflächen hinzu  
  
1.  Aus der **Standardsteuerelementen** auf der Registerkarte die **Toolbox**, Hinzufügen einer <xref:System.Windows.Forms.Button> -Steuerelement zur Zelle **A3** des Arbeitsblatts.  
  
     Diese Schaltfläche den Namen `Button1`.  
  
2.  Fügen Sie einen anderen <xref:System.Windows.Forms.Button> -Steuerelement zur Zelle **B3** des Arbeitsblatts.  
  
     Diese Schaltfläche den Namen `Button2`.  
  
 Als Nächstes, markieren Sie das Dataset im Dokument zwischengespeichert werden soll.  
  
## <a name="caching-the-dataset"></a>Das Dataset zwischenspeichern  
 Markieren Sie das Dataset im Dokument zwischengespeichert werden soll, indem Sie das Dataset machen, öffentliche und Festlegen der **CacheInDocument** Eigenschaft.  
  
#### <a name="to-cache-the-dataset"></a>Das Dataset Zwischenspeichern  
  
1.  Wählen Sie **NorthwindDataSet** auf der Komponentenleiste.  
  
2.  In der **Eigenschaften** Ändern der **Modifizierer** Eigenschaft **öffentlichen**.  
  
     Datasets müssen öffentlich sein, bevor das Zwischenspeichern aktiviert ist.  
  
3.  Ändern der **CacheInDocument** Eigenschaft **"true"**.  
  
 Der nächste Schritt besteht, die Schaltflächen Text hinzu, und fügen Sie im C#-Code, um den Ereignishandler zu verknüpfen.  
  
## <a name="initializing-the-controls"></a>Initialisieren der Steuerelemente  
 Legen Sie den Text der Schaltfläche, und fügen Sie Ereignishandler während der <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> Ereignis.  
  
#### <a name="to-initialize-the-data-and-the-controls"></a>So initialisieren Sie die Daten und die Steuerelemente  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste **Sheet1.vb** oder **Sheet1.cs**, und klicken Sie dann auf **Code anzeigen** im Kontextmenü.  
  
2.  Fügen Sie folgenden Code, der `Sheet1_Startup` Methode, um den Text für die Schaltflächen einzurichten.  
  
     [!code-vb[Trin_VstcoreDataExcel#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#15)]
     [!code-csharp[Trin_VstcoreDataExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#15)]  
  
3.  Nur c# fügen Ereignishandler für die Schaltfläche click-Ereignisse, die `Sheet1_Startup` Methode.  
  
     [!code-csharp[Trin_VstcoreDataExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#16)]  
  
## <a name="adding-code-to-enable-scrolling-through-the-records"></a>Hinzufügen von Code zum Durchführen eines Bildlaufs durch die Datensätze aktivieren  
 Hinzufügen von Code für die <xref:System.Windows.Forms.Control.Click> -Ereignishandler der einzelnen Schaltflächen, um durch die Datensätze zu verschieben.  
  
#### <a name="to-scroll-through-the-records"></a>So führen Sie einen Bildlauf durch die Datensätze durch  
  
1.  Fügen Sie einen Ereignishandler für das <xref:System.Windows.Forms.Control.Click> -Ereignis `Button1`, und fügen Sie den folgenden Code hinzu, durch die Datensätze rückwärts verschieben:  
  
     [!code-vb[Trin_VstcoreDataExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#17)]
     [!code-csharp[Trin_VstcoreDataExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#17)]  
  
2.  Fügen Sie einen Ereignishandler für das <xref:System.Windows.Forms.Control.Click> -Ereignis `Button2`, und fügen Sie den folgenden Code hinzu, durch die Datensätze zu gelangen:  
  
     [!code-vb[Trin_VstcoreDataExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#18)]
     [!code-csharp[Trin_VstcoreDataExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#18)]  
  
## <a name="testing-the-application"></a>Testen der Anwendung  
 Jetzt können Sie die Arbeitsmappe aus, um sicherzustellen, dass die Daten wie erwartet angezeigt wird und die Projektmappe offline verwendet werden können, testen.  
  
#### <a name="to-test-the-data-caching"></a>So testen Sie das Zwischenspeichern von Daten  
  
1.  Drücken Sie **F5**.  
  
2.  Stellen Sie sicher, dass der benannte Bereich und das Listenobjekt mit Daten aus der Datenquelle gefüllt werden.  
  
3.  Blättern Sie durch einige der Einträge, indem Sie auf die Schaltflächen.  
  
4.  Speichern Sie die Arbeitsmappe, und schließen Sie dann die Arbeitsmappe und die Visual Studio.  
  
5.  Deaktivieren Sie die Verbindung mit der Datenbank. Ziehen Sie das Netzwerkkabel von Ihrem Computer, wenn die Datenbank auf einem Server befindet, oder beenden Sie den SQL Server-Dienst aus, wenn die Datenbank auf dem Entwicklungscomputer befindet.  
  
6.  Öffnen Sie Excel, und öffnen Sie **Meine Master-Detail.xlsx** aus dem Verzeichnis \bin (\My Master-Detail\bin in Visual Basic oder C#-\My Master-Detail\bin\debug).  
  
7.  Blättern Sie durch einige der Einträge Sie feststellen, ob das Arbeitsblatt wird normal ausgeführt, wenn der getrennt.  
  
8.  Verbindung mit der Datenbank wiederherstellen. Verbinden Sie den Computer mit dem Netzwerk erneut, wenn die Datenbank auf einem Server befindet, oder starten Sie SQL Server-Dienst aus, wenn die Datenbank auf dem Entwicklungscomputer befindet.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Diese exemplarische Vorgehensweise veranschaulicht die Grundlagen erstellen eine Master/Detail-datenbeziehung in einem Arbeitsblatt und ein Dataset Zwischenspeichern. Die folgenden Aufgaben könnten sich daran anschließen:  
  
-   Die Lösung bereit. Weitere Informationen finden Sie unter [Bereitstellen einer Office-Lösung](../vsto/deploying-an-office-solution.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Daten in Office-Projektmappen](../vsto/data-in-office-solutions.md)   
 [Zwischenspeichern von Daten](../vsto/caching-data.md)   
 [Übersicht über Hostelemente und Hoststeuerelemente](../vsto/host-items-and-host-controls-overview.md)  
  
  