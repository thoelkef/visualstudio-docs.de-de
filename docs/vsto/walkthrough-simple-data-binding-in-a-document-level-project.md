---
title: 'Exemplarische Vorgehensweise: Einfache Datenbindung in einem Projekt auf Dokumentebene'
ms.date: 02/02/2017
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
ms.openlocfilehash: a9967d830d72355f23173a7dfc6f1a95be073959
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53895492"
---
# <a name="walkthrough-simple-data-binding-in-a-document-level-project"></a>Exemplarische Vorgehensweise: Einfache Datenbindung in einem Projekt auf Dokumentebene
  Diese exemplarische Vorgehensweise veranschaulicht die Grundlagen der Datenbindung in einem Projekt auf Dokumentebene. Ein einzelnes Datenfeld in einer SQL Server-Datenbank ist an einen benannten Bereich in Microsoft Office Excel gebunden. In der exemplarischen Vorgehensweise wird gezeigt, wie Steuerelemente hinzufügen, die Ihnen ermöglichen, führen Sie einen Bildlauf durch alle Datensätze in der Tabelle.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
- Erstellen eine Datenquelle für ein Projekt für Excel.  
  
- Hinzufügen von Steuerelementen zu einem Arbeitsblatt ein.  
  
- Durchführen eines Bildlaufs durch Datenbankdatensätze.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Zugriff auf einen Server mit der Beispieldatenbank Northwind-SQL Server.  
  
-   Berechtigungen zum Lesen und Schreiben in SQL Server-Datenbank.  
  
## <a name="create-a-new-project"></a>Erstellt ein neues Projekt  
 In diesem Schritt erstellen Sie ein Excel-Workbook-Projekt.  
  
### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt  
  
1. Erstellen Sie ein Excel-Workbook-Projekt mit dem Namen **Meine einfache Datenbindung**, mit Visual Basic oder c#. Stellen Sie sicher, dass **ein neues Dokument erstellen** ausgewählt ist. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
   Visual Studio öffnet die neue Excel-Arbeitsmappe im Designer und fügt die **Meine einfache Datenbindung** Projekt **Projektmappen-Explorer**.  
  
## <a name="create-the-data-source"></a>Erstellen der Datenquelle  
 Verwenden das Fenster **Datenquellen** , um dem Projekt ein typisiertes Dataset hinzuzufügen.  
  
### <a name="to-create-the-data-source"></a>So erstellen Sie die Datenquelle  
  
1. Wenn die **Datenquellen** Fenster ist nicht sichtbar ist, zeigen Sie es an, indem in der Menüleiste die Optionen **Ansicht** > **Other Windows**  >   **Datenquellen**.  
  
2. Wählen Sie **Neue Datenquelle hinzufügen** , um den **Assistenten zum Konfigurieren von Datenquellen**zu starten.  
  
3. Wählen Sie **Datenbank** , und klicken Sie dann auf **Weiter**.  
  
4. Wählen Sie eine Datenverbindung zur Northwind-Beispieldatenbank SQL Server, oder fügen Sie eine neue Verbindung mit der **neue Verbindung** Schaltfläche.  
  
5. Nachdem eine Verbindung ausgewählt oder erstellt wurde, klicken Sie auf **Weiter**.  
  
6. Deaktivieren Sie die Option zum Speichern der Verbindung, wenn diese Option ausgewählt ist, und klicken Sie dann auf **Weiter**.  
  
7. Erweitern Sie die **Tabellen** Knoten in der **Datenbankobjekte** Fenster.  
  
8. Aktivieren Sie das Kontrollkästchen neben den **Kunden** Tabelle.  
  
9. Klicken Sie auf **Fertig stellen**.  
  
   Der Assistent fügt die **Kunden** Tabelle, auf die **Datenquellen** Fenster. Es auch ein typisiertes Dataset dem Projekt hinzugefügt, die in angezeigt wird **Projektmappen-Explorer**.  
  
## <a name="add-controls-to-the-worksheet"></a>Hinzufügen von Steuerelementen zum Arbeitsblatt  
 In dieser exemplarischen Vorgehensweise benötigen Sie zwei benannte Bereiche und vier Schaltflächen auf das erste Arbeitsblatt ein. Fügen Sie zunächst die beiden benannten Bereiche aus der **Datenquellen** Fenster, damit diese automatisch an die Datenquelle gebunden werden. Fügen Sie die Schaltflächen aus der **Toolbox**.  
  
### <a name="to-add-two-named-ranges"></a>Hinzufügen von zwei benannte Bereiche  
  
1.  Überprüfen Sie, ob die *Meine einfache Daten Binding.xlsx* Arbeitsmappe geöffnet, in der Visual Studio-Designer ist mit **Sheet1** angezeigt.  
  
2.  Öffnen der **Datenquellen** Fenster, und erweitern Sie die **Kunden** Knoten.  
  
3.  Wählen Sie die **CompanyName** Spalte, und klicken Sie dann auf den Dropdown-Pfeil, der angezeigt wird.  
  
4.  Wählen Sie **NamedRange** in der Dropdown-Liste, und ziehen Sie dann die **CompanyName** Spalte Zelle **A1**.  
  
     Ein <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement mit dem Namen `companyNameNamedRange` ist in der Zelle erstellt **A1**. Zur gleichen Zeit eine <xref:System.Windows.Forms.BindingSource> mit dem Namen `customersBindingSource`, ein Tabellenadapter und eine <xref:System.Data.DataSet> Instanz werden dem Projekt hinzugefügt. Das Steuerelement gebunden ist, um die <xref:System.Windows.Forms.BindingSource>, das wiederum gebunden ist die <xref:System.Data.DataSet> Instanz.  
  
5.  Wählen Sie die **"CustomerID"** -Spalte in der **Datenquellen** Fenster, und klicken Sie dann auf den Dropdown-Pfeil, der angezeigt wird.  
  
6.  Klicken Sie auf **NamedRange** in der Dropdown-Liste, und ziehen Sie dann die **"CustomerID"** Spalte Zelle **B1**.  
  
7.  Eine andere <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement mit dem Namen `customerIDNamedRange` ist in der Zelle erstellt **B1**, und Binden an die <xref:System.Windows.Forms.BindingSource>.  
  
### <a name="to-add-four-buttons"></a>Vier Schaltflächen hinzufügen  
  
1. Aus der **Standardsteuerelementen** Registerkarte die **Toolbox**, Hinzufügen einer <xref:System.Windows.Forms.Button> -Steuerelement zur Zelle **A3** des Arbeitsblatts.  
  
    Diese Schaltfläche den Namen `Button1`.  
  
2. Fügen Sie drei weitere Schaltflächen für die folgenden Zellen in der angegebenen Reihenfolge, sodass die Namen sind, siehe:  
  
   |Zelle|(Name)|  
   |----------|--------------|  
   |B3|Button2|  
   |C3|Button3|  
   |D3|Button4|  
  
   Der nächste Schritt ist, fügen Text auf Schaltflächen, und fügen in C#-Ereignishandler.  
  
## <a name="initialize-the-controls"></a>Initialisieren Sie die Steuerelemente  
 Legen Sie den Text der Schaltfläche, und fügen Sie Ereignishandler während der <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> Ereignis.  
  
### <a name="to-initialize-the-controls"></a>Um die Steuerelemente zu initialisieren.  
  
1. In **Projektmappen-Explorer**, mit der rechten Maustaste **Sheet1.vb** oder **Sheet1.cs**, und klicken Sie dann auf **Ansichtscode** im Kontextmenü auf.  
  
2. Fügen Sie den folgenden Code der `Sheet1_Startup` Methode, um den Text für jede Schaltfläche festzulegen.  
  
    [!code-csharp[Trin_VstcoreDataExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#2)]
    [!code-vb[Trin_VstcoreDataExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#2)]  
  
3. Nur für c#, fügen Ereignishandler für die Schaltfläche mit den click-Ereignisse, die `Sheet1_Startup` Methode.  
  
    [!code-csharp[Trin_VstcoreDataExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#3)]  
  
   Fügen Sie jetzt Code für die Behandlung der <xref:System.Windows.Forms.Control.Click> Ereignisse der Schaltflächen, damit der Benutzer durch die Datensätze navigieren kann.  
  
## <a name="add-code-to-enable-scrolling-through-the-records"></a>Hinzufügen von Code zum Aktivieren des Bildlaufs durch die Datensätze  
 Fügen Sie Code in die <xref:System.Windows.Forms.Control.Click> -Ereignishandler der einzelnen Schaltflächen zum Navigieren durch die Datensätze.  
  
### <a name="to-move-to-the-first-record"></a>Um auf den ersten Eintrag verschieben  
  
1.  Hinzufügen eines ereignishandlers für das <xref:System.Windows.Forms.Control.Click> Ereignis die `Button1` Schaltfläche aus, und fügen Sie den folgenden Code hinzu, verschieben Sie auf den ersten Eintrag hinzu:  
  
     [!code-csharp[Trin_VstcoreDataExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreDataExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#4)]  
  
### <a name="to-move-to-the-previous-record"></a>Um zum vorherigen Datensatz zu verschieben.  
  
1.  Hinzufügen eines ereignishandlers für das <xref:System.Windows.Forms.Control.Click> Ereignis die `Button2` Schaltfläche, und fügen Sie den folgenden Code, um die Position zurück zu navigieren:  
  
     [!code-csharp[Trin_VstcoreDataExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreDataExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#5)]  
  
### <a name="to-move-to-the-next-record"></a>Um zum nächsten Datensatz zu verschieben.  
  
1.  Hinzufügen eines ereignishandlers für das <xref:System.Windows.Forms.Control.Click> Ereignis die `Button3` Schaltfläche, und fügen Sie den folgenden Code zum fahren Sie fort, der die Position von einem:  
  
     [!code-csharp[Trin_VstcoreDataExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreDataExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#6)]  
  
### <a name="to-move-to-the-last-record"></a>Bis zum letzten Datensatz verschieben  
  
1.  Hinzufügen eines ereignishandlers für das <xref:System.Windows.Forms.Control.Click> Ereignis die `Button4` Schaltfläche, und fügen Sie den folgenden Code zum bis zum letzten Datensatz verschoben:  
  
     [!code-csharp[Trin_VstcoreDataExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreDataExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#7)]  
  
## <a name="test-the-application"></a>Testen der Anwendung  
 Jetzt können Sie testen, die Arbeitsmappe, um sicherzustellen, dass Sie durch die Datensätze in der Datenbank durchsuchen können.  
  
### <a name="to-test-your-workbook"></a>So testen Sie die Arbeitsmappe  
  
1.  Drücken Sie **F5** um Ihr Projekt auszuführen.  
  
2.  Vergewissern Sie sich, dass der erste Datensatz in Zellen angezeigt **A1** und **B1**.  
  
3.  Klicken Sie auf die **>** (`Button3`) und bestätigen Sie, dass es sich bei der nächste Datensatz in Zelle angezeigt wird **A1** und **B1**.  
  
4.  Klicken Sie auf die anderen Bildlaufschaltflächen, um sicherzustellen, dass der Datensatz geändert wird, wie erwartet.  
  
## <a name="next-steps"></a>Nächste Schritte  
 In dieser exemplarischen Vorgehensweise wird gezeigt, die Grundlagen der Bindung eines benannten Bereichs auf ein Feld in einer Datenbank. Die folgenden Aufgaben könnten sich daran anschließen:  
  
-   Daten zwischengespeichert, so dass sie offline verwendet werden kann. Weitere Informationen finden Sie unter [Vorgehensweise: Zwischenspeichern von Daten für die Verwendung, offline ist oder auf einem Server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   Binden von Zellen an mehrere Spalten in einer Tabelle statt auf ein Feld. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Komplexe Datenbindung in einem Projekt auf Dokumentebene](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md).  
  
-   Verwenden einer <xref:System.Windows.Forms.BindingNavigator> Steuerelement durch die Datensätze scrollen. Weitere Informationen finden Sie unter [Vorgehensweise: Datennavigation mithilfe des Windows Forms BindingNavigator-Steuerelements](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).  
  
## <a name="see-also"></a>Siehe auch  
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Daten in Office-Projektmappen](../vsto/data-in-office-solutions.md)   
 [Exemplarische Vorgehensweise: Komplexe Datenbindung in einem Projekt auf Dokumentebene](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)  
