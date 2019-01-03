---
title: 'Exemplarische Vorgehensweise: Erstellen Sie eine master-Detail-Beziehung mithilfe eines zwischengespeicherten Datasets'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- master-detail tables [Office development in Visual Studio], walkthroughs
- data caching [Office development in Visual Studio], Master/Detail Relation
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c75ee922694e80b5ba70e4743d397cdf465169e8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53823648"
---
# <a name="walkthrough-create-a-master-detail-relation-using-a-cached-dataset"></a>Exemplarische Vorgehensweise: Erstellen Sie eine master-Detail-Beziehung mithilfe eines zwischengespeicherten Datasets
  In dieser exemplarischen Vorgehensweise veranschaulicht das Erstellen einer Master/Detail-Beziehung in einem Arbeitsblatt und Zwischenspeichern von Daten, damit die Projektmappe offline verwendet werden kann.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Bei dieser exemplarischen Vorgehensweise lernen Sie Folgendes:  
  
-   Hinzufügen von Steuerelementen zu einem Arbeitsblatt.  
  
-   Richten Sie ein Dataset aus, um in einem Arbeitsblatt zwischengespeichert werden.  
  
-   Hinzufügen von Code zum Durchführen eines Bildlaufs durch die Datensätze zu aktivieren.  
  
-   Testen Sie das Projekt ein.  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Zugriff auf die Northwind-SQL Server-Beispieldatenbank. Die Datenbank möglich auf Ihrem Entwicklungscomputer oder auf einem Server.  
  
-   Berechtigungen zum Lesen und Schreiben in SQL Server-Datenbank.  
  
## <a name="create-a-new-project"></a>Erstellt ein neues Projekt  
 In diesem Schritt erstellen Sie ein Excel-Workbook-Projekt.  
  
### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt  
  
1. Erstellen Sie ein Excel-Workbook-Projekt mit dem Namen **My Master-Detail**, mit Visual Basic oder c#. Stellen Sie sicher, dass **ein neues Dokument erstellen** ausgewählt ist. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
   Visual Studio öffnet die neue Excel-Arbeitsmappe im Designer und fügt die **My Master-Detail** Projekt **Projektmappen-Explorer**.  
  
## <a name="create-the-data-source"></a>Erstellen der Datenquelle  
 Verwenden das Fenster **Datenquellen** , um dem Projekt ein typisiertes Dataset hinzuzufügen.  
  
### <a name="to-create-the-data-source"></a>So erstellen Sie die Datenquelle  
  
1. Wenn die **Datenquellen** Fenster ist nicht sichtbar ist, zeigen Sie es an, indem in der Menüleiste die Optionen **Ansicht** > **Other Windows**  >   **Datenquellen**.  
  
2. Wählen Sie **Neue Datenquelle hinzufügen** , um den **Assistenten zum Konfigurieren von Datenquellen**zu starten.  
  
3. Wählen Sie **Datenbank** , und klicken Sie dann auf **Weiter**.  
  
4. Wählen Sie eine Datenverbindung zur Northwind-Beispieldatenbank SQL Server, oder fügen Sie eine neue Verbindung mit der **neue Verbindung** Schaltfläche.  
  
5. Nach dem auswählen oder erstellen eine Verbindung, klicken Sie auf **Weiter**.  
  
6. Deaktivieren Sie die Option zum Speichern der Verbindung, wenn diese Option ausgewählt ist, und klicken Sie dann auf **Weiter**.  
  
7. Erweitern Sie die **Tabellen** Knoten in der **Datenbankobjekte** Fenster.  
  
8. Wählen Sie die **Bestellungen** Tabelle und die **Bestelldetails** Tabelle.  
  
9. Klicken Sie auf **Fertig stellen**.  
  
   Der Assistent fügt die beiden Tabellen aus, um die **Datenquellen** Fenster. Es auch ein typisiertes Dataset dem Projekt hinzugefügt, die in angezeigt wird **Projektmappen-Explorer**.  
  
## <a name="add-controls-to-the-worksheet"></a>Hinzufügen von Steuerelementen zum Arbeitsblatt  
 In diesem Schritt fügen Sie einen benannten Bereich, ein List-Objekt und zwei Schaltflächen, das erste Arbeitsblatt hinzu. Fügen Sie zunächst den benannten Bereich und das List-Objekt, aus der **Datenquellen** Fenster, damit diese automatisch an die Datenquelle gebunden werden. Fügen Sie die Schaltflächen aus der **Toolbox**.  
  
### <a name="to-add-a-named-range-and-a-list-object"></a>Zum Hinzufügen eines benannten Bereichs und ein List-Objekt  
  
1.  Überprüfen Sie, ob die **Meine Master-Detail.xlsx** Arbeitsmappe geöffnet, in der Visual Studio-Designer ist mit **Sheet1** angezeigt.  
  
2.  Öffnen der **Datenquellen** Fenster, und erweitern Sie die **Bestellungen** Knoten.  
  
3.  Wählen Sie die **"OrderID"** Spalte, und klicken Sie dann auf den Dropdown-Pfeil, der angezeigt wird.  
  
4.  Klicken Sie auf **NamedRange** in der Dropdown-Liste, und ziehen Sie dann die **"OrderID"** Spalte Zelle **A2**.  
  
     Ein <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement mit dem Namen `OrderIDNamedRange` ist in der Zelle erstellt **A2**. Zur gleichen Zeit eine <xref:System.Windows.Forms.BindingSource> mit dem Namen `OrdersBindingSource`, ein Tabellenadapter und eine <xref:System.Data.DataSet> Instanz werden dem Projekt hinzugefügt. Das Steuerelement gebunden ist, um die <xref:System.Windows.Forms.BindingSource>, das wiederum gebunden ist die <xref:System.Data.DataSet> Instanz.  
  
5.  Scrollen Sie nach unten, über die Spalten, die unter der **Bestellungen** Tabelle. Wird am unteren Rand der Liste der **Order Details** Tabelle; es ist hier, da es sich um ein untergeordnetes Element des ist der **Bestellungen** Tabelle. Wählen Sie diese **Bestelldetails** -Tabelle nicht zu derjenigen, die auf der gleichen Ebene wie die **Bestellungen** Tabelle, und klicken Sie dann auf den Dropdown-Pfeil, der angezeigt wird.  
  
6.  Klicken Sie auf **ListObject** in der Dropdown-Liste, und ziehen Sie dann die **OrderDetails** Tabelle in Zelle **A6**.  
  
7.  Ein <xref:Microsoft.Office.Tools.Excel.ListObject> Steuerelement mit dem Namen **Order_DetailsListObject** ist in der Zelle erstellt **A6**, und Binden an die <xref:System.Windows.Forms.BindingSource>.  
  
### <a name="to-add-two-buttons"></a>Zwei Schaltflächen hinzufügen  
  
1. Aus der **Standardsteuerelementen** Registerkarte die **Toolbox**, Hinzufügen einer <xref:System.Windows.Forms.Button> -Steuerelement zur Zelle **A3** des Arbeitsblatts.  
  
    Diese Schaltfläche den Namen `Button1`.  
  
2. Fügen Sie ein weiteres <xref:System.Windows.Forms.Button> -Steuerelement zur Zelle **B3** des Arbeitsblatts.  
  
    Diese Schaltfläche den Namen `Button2`.  
  
   Markieren Sie als Nächstes das Dataset im Dokument zwischengespeichert werden.  
  
## <a name="cache-the-dataset"></a>Die Zwischenspeicherung des Datasets  
 Markieren Sie das Dataset im Dokument zwischengespeichert werden, indem öffentlich zu machen das Dataset und das Festlegen der **CacheInDocument** Eigenschaft.  
  
### <a name="to-cache-the-dataset"></a>Das Dataset zwischengespeichert  
  
1. Wählen Sie **NorthwindDataSet** auf der Komponentenleiste.  
  
2. In der **Eigenschaften** Ändern der **Modifizierer** Eigenschaft **öffentliche**.  
  
    Datasets müssen öffentlich sein, bevor Sie das Zwischenspeichern aktiviert ist.  
  
3. Ändern der **CacheInDocument** Eigenschaft **"true"**.  
  
   Der nächste Schritt ist zum Hinzufügen von Text auf Schaltflächen, und fügen Sie im C#-Code, um die Ereignishandler einzubinden.  
  
## <a name="initialize-the-controls"></a>Initialisieren Sie die Steuerelemente  
 Legen Sie den Text der Schaltfläche, und fügen Sie Ereignishandler während der <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> Ereignis.  
  
### <a name="to-initialize-the-data-and-the-controls"></a>So initialisieren Sie die Daten und die Steuerelemente  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste **Sheet1.vb** oder **Sheet1.cs**, und klicken Sie dann auf **Ansichtscode** im Kontextmenü auf.  
  
2.  Fügen Sie den folgenden Code der `Sheet1_Startup` Methode, um den Text für die Schaltflächen festzulegen.  
  
     [!code-vb[Trin_VstcoreDataExcel#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#15)]
     [!code-csharp[Trin_VstcoreDataExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#15)]  
  
3.  Nur für c#, fügen Ereignishandler für die Schaltfläche mit den click-Ereignisse, die `Sheet1_Startup` Methode.  
  
     [!code-csharp[Trin_VstcoreDataExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#16)]  
  
## <a name="add-code-to-enable-scrolling-through-the-records"></a>Hinzufügen von Code zum Aktivieren des Bildlaufs durch die Datensätze  
 Fügen Sie Code in die <xref:System.Windows.Forms.Control.Click> -Ereignishandler der einzelnen Schaltflächen zum Navigieren durch die Datensätze.  
  
### <a name="to-scroll-through-the-records"></a>So führen Sie einen Bildlauf durch die Datensätze durch  
  
1.  Hinzufügen eines ereignishandlers für das <xref:System.Windows.Forms.Control.Click> Ereignis `Button1`, und fügen Sie den folgenden Code, durch die Datensätze zurückzugehen hinzu:  
  
     [!code-vb[Trin_VstcoreDataExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#17)]
     [!code-csharp[Trin_VstcoreDataExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#17)]  
  
2.  Hinzufügen eines ereignishandlers für das <xref:System.Windows.Forms.Control.Click> Ereignis `Button2`, und fügen Sie den folgenden Code hinzu, durch die Datensätze fahren Sie fort:  
  
     [!code-vb[Trin_VstcoreDataExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#18)]
     [!code-csharp[Trin_VstcoreDataExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#18)]  
  
## <a name="test-the-application"></a>Testen der Anwendung  
 Jetzt können Sie die Arbeitsmappe aus, um sicherzustellen, dass die Daten wie erwartet angezeigt wird und Sie die Lösung offline verwenden zu können, testen.  
  
### <a name="to-test-the-data-caching"></a>So testen Sie das Zwischenspeichern von Daten  
  
1.  Drücken Sie **F5**.  
  
2.  Stellen Sie sicher, dass es sich bei den benannten Bereich und das List-Objekt mit Daten aus der Datenquelle gefüllt werden.  
  
3.  Scrollen Sie durch einige der Einträge, indem Sie auf die Schaltflächen.  
  
4.  Speichern Sie die Arbeitsmappe, und schließen Sie die Arbeitsmappe und die Visual Studio.  
  
5.  Deaktivieren Sie die Verbindung mit der Datenbank. Trennen Sie das Netzwerkkabel von Ihrem Computer aus, wenn die Datenbank auf einem Server befindet, oder beenden Sie den SQL Server-Dienst aus, wenn die Datenbank auf dem Entwicklungscomputer gespeichert ist.  
  
6.  Öffnen Sie Excel, und öffnen Sie **Meine Master-Detail.xlsx** aus der *\bin* Verzeichnis (*\My Master-Detail\bin* in Visual Basic oder *\My Master-Detail\bin\ Debuggen von* in c#).  
  
7.  Scrollen Sie durch einige der Einträge zu erkennen, dass das Arbeitsblatt normal ausgeführt wird, die Verbindung getrennt.  
  
8.  Verbindung mit der Datenbank. Verbinden Sie den Computer mit dem Netzwerk wieder, wenn die Datenbank auf einem Server befindet, oder starten Sie den SQL Server-Dienst aus, wenn die Datenbank auf dem Entwicklungscomputer gespeichert ist.  
  
## <a name="next-steps"></a>Nächste Schritte  
 In dieser exemplarischen Vorgehensweise wird gezeigt, die Grundlagen von erstellen eine Master-/detailbeziehung Daten in einem Arbeitsblatt und das Zwischenspeichern eines Datasets. Die folgenden Aufgaben könnten sich daran anschließen:  
  
-   Die Lösung bereit. Weitere Informationen finden Sie unter [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Daten in Office-Projektmappen](../vsto/data-in-office-solutions.md)   
 [Zwischenspeichern von Daten](../vsto/caching-data.md)   
 [Hostelemente und Host-Steuerelementen (Übersicht)](../vsto/host-items-and-host-controls-overview.md)  
