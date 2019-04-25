---
title: 'Exemplarische Vorgehensweise: Komplexe Datenbindung in einem Projekt auf Dokumentebene'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], binding data
- complex data [Office development in Visual Studio]
- multiple column data binding [Office development in Visual Studio]
- data binding [Office development in Visual Studio], multiple columns
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: aabd45871e55fd22b9b9e35597555fd13b15d6eb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60052531"
---
# <a name="walkthrough-complex-data-binding-in-a-document-level-project"></a>Exemplarische Vorgehensweise: Komplexe Datenbindung in einem Projekt auf Dokumentebene
  Diese exemplarische Vorgehensweise veranschaulicht die Grundlagen der komplexe Datenbindung in einem Projekt auf Dokumentebene. Sie können mehrere Zellen in einem Microsoft Office Excel-Arbeitsblatt an Felder in der Northwind-SQL Server-Datenbank binden.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Hinzufügen einer Datenquelle zu Ihrem Arbeitsmappenprojekt an.

- Hinzufügen von datengebundenen Steuerelementen zu einem Arbeitsblatt.

- Speichern von datenänderungen in der Datenbank.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Vorraussetzungen
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Zugriff auf einen Server mit der Beispieldatenbank Northwind-SQL Server.

- Berechtigungen zum Lesen und Schreiben in SQL Server-Datenbank.

## <a name="create-a-new-project"></a>Erstellt ein neues Projekt
 Der erste Schritt ist ein Excel-Workbook-Projekt zu erstellen.

### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt

1. Erstellen Sie ein Excel-Workbook-Projekt mit dem Namen **Meine komplexe Datenbindung**. Wählen Sie im Assistenten **ein neues Dokument erstellen**.

     Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio öffnet die neue Excel-Arbeitsmappe im Designer und fügt die **Meine komplexe Datenbindung** Projekt **Projektmappen-Explorer**.

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

8. Aktivieren Sie das Kontrollkästchen neben den **Mitarbeiter** Tabelle.

9. Klicken Sie auf **Fertig stellen**.

   Der Assistent fügt die **Mitarbeiter** Tabelle, auf die **Datenquellen** Fenster. Es auch ein typisiertes Dataset dem Projekt hinzugefügt, die in angezeigt wird **Projektmappen-Explorer**.

## <a name="add-controls-to-the-worksheet"></a>Hinzufügen von Steuerelementen zum Arbeitsblatt
 Ein Arbeitsblatt zeigt die **Mitarbeiter** Tabelle, wenn die Arbeitsmappe geöffnet wird. Benutzer werden Änderungen an den Daten vornehmen und speichern Sie diese Änderungen in der Datenbank durch Klicken auf eine Schaltfläche.

 Um das Arbeitsblatt automatisch in die Tabelle zu binden, können Sie Hinzufügen einer <xref:Microsoft.Office.Tools.Excel.ListObject> Steuerelement in das Arbeitsblatt aus der **Datenquellen** Fenster. Um die Benutzer die Option zum Speichern von Änderungen gewähren, fügen einen <xref:System.Windows.Forms.Button> -Steuerelement aus der **Toolbox**.

#### <a name="to-add-a-list-object"></a>Ein List-Objekt hinzufügen

1. Überprüfen Sie, ob die **Meine komplexe Daten Binding.xlsx** Arbeitsmappe geöffnet, in der Visual Studio-Designer ist mit **Sheet1** angezeigt.

2. Öffnen der **Datenquellen** Fenster, und wählen die **Mitarbeiter** Knoten.

3. Klicken Sie auf den Dropdown-Pfeil, der angezeigt wird.

4. Wählen Sie **ListObject** in der Dropdown-Liste.

5. Ziehen Sie die **Mitarbeiter** Tabelle in Zelle **A6**.

     Ein <xref:Microsoft.Office.Tools.Excel.ListObject> Steuerelement mit dem Namen `EmployeesListObject` ist in der Zelle erstellt **A6**. Zur gleichen Zeit eine <xref:System.Windows.Forms.BindingSource> mit dem Namen `EmployeesBindingSource`, ein Tabellenadapter und eine <xref:System.Data.DataSet> Instanz werden dem Projekt hinzugefügt. Das Steuerelement gebunden ist, um die <xref:System.Windows.Forms.BindingSource>, das wiederum gebunden ist die <xref:System.Data.DataSet> Instanz.

### <a name="to-add-a-button"></a>Hinzufügen eine Schaltfläche

1. Aus der **Standardsteuerelementen** Registerkarte die **Toolbox**, Hinzufügen einer <xref:System.Windows.Forms.Button> -Steuerelement zur Zelle **A4** des Arbeitsblatts.

   Der nächste Schritt ist zum Hinzufügen von Text auf die Schaltfläche, wenn das Arbeitsblatt geöffnet wird.

## <a name="initialize-the-control"></a>Das Steuerelement initialisiert
 Hinzufügen von Text auf die Schaltfläche in der <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> -Ereignishandler.

### <a name="to-initialize-the-control"></a>Um das Steuerelement zu initialisieren.

1. In **Projektmappen-Explorer**, mit der rechten Maustaste **Sheet1.vb** oder **Sheet1.cs**, und klicken Sie dann auf **Ansichtscode** im Kontextmenü auf.

2. Fügen Sie den folgenden Code der `Sheet1_Startup` Methode, um den Text für den b festzulegen`utton`.

    [!code-csharp[Trin_VstcoreDataExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#8)]
    [!code-vb[Trin_VstcoreDataExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#8)]

3. Nur für c#, fügen Sie einen Ereignishandler für die <xref:System.Windows.Forms.Control.Click> Ereignis, um die `Sheet1_Startup` Methode.

    [!code-csharp[Trin_VstcoreDataExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#9)]

   Fügen Sie jetzt Code für die Behandlung der <xref:System.Windows.Forms.Control.Click> -Ereignis der Schaltfläche.

## <a name="save-changes-to-the-database"></a>Speichern Sie Änderungen an der Datenbank
 Alle Änderungen vorgenommen wurden die Daten sind nur im lokalen Dataset vorhanden, bis sie explizit wieder in der Datenbank gespeichert werden.

### <a name="to-save-changes-to-the-database"></a>Um Änderungen an der Datenbank speichern

1. Hinzufügen eines ereignishandlers für das <xref:System.Windows.Forms.Control.Click> Ereignis die `button`, und fügen Sie den folgenden Code, um alle Änderungen zu speichern, die im Dataset in der Datenbank vorgenommen wurden.

     [!code-csharp[Trin_VstcoreDataExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#10)]
     [!code-vb[Trin_VstcoreDataExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#10)]

## <a name="test-the-application"></a>Testen der Anwendung
 Jetzt können Sie testen, die Arbeitsmappe, um sicherzustellen, dass die Daten wie erwartet angezeigt wird und Sie die Daten in der Liste bearbeiten können.

### <a name="to-test-the-data-binding"></a>Um die Datenbindung zu testen.

- Drücken Sie **F5**.

     Stellen Sie sicher, dass das List-Objekt mit Daten aus, wenn die Arbeitsmappe geöffnet wird ausgefüllt ist, die **Mitarbeiter** Tabelle.

### <a name="to-modify-data"></a>Zum Ändern von Daten

1. Klicken Sie auf die Zelle **B7**, die den Namen enthalten **Davolio**.

2. Geben Sie den Namen **Anderson**, und drücken Sie dann die **EINGABETASTE**.

### <a name="to-modify-a-column-header"></a>So ändern Sie eine Spaltenüberschrift

1. Klicken Sie auf die Zelle, die den Spaltenkopf enthält **"LastName"**.

2. Typ **Nachname**, mit einem Leerzeichen zwischen den beiden Wörtern, und drücken Sie dann die **EINGABETASTE**.

### <a name="to-save-data"></a>Zum Speichern von Daten

1. Klicken Sie auf **speichern** auf dem Arbeitsblatt.

2. Beenden Sie Excel. Klicken Sie auf **keine** bei der Aufforderung zum Speichern der Änderungen Sie vorgenommen haben.

3. Drücken Sie **F5** auf das Projekt erneut ausgeführt.

     Das List-Objekt mit Daten gefüllt der **Mitarbeiter** Tabelle.

4. Beachten Sie, dass der Name in Zelle **B7** ist immer noch **Anderson**, d.h. die Daten zu ändern, dass Sie bereits erstellt und in der Datenbank gespeichert. Die Kopfzeile der Spalte **"LastName"** hat die an ihrer ursprünglichen Form ohne Leerzeichen, geändert werden, da die Kopfzeile der Spalte nicht auf die Datenbank gebunden ist und Sie nicht die Änderungen in das Arbeitsblatt speichern.

### <a name="to-add-new-rows"></a>Zum Hinzufügen von neuer Zeilen

1. Wählen Sie eine Zelle innerhalb des List-Objekts.

    Es wird eine neue Zeile am unteren Rand der Liste mit einem Sternchen (**\\***) in der ersten Zelle der neuen Zeile.

2. Fügen Sie die folgenden Informationen in der leeren Zeile.

   |EmployeeID|LastName|FirstName|Titel|
   |----------------|--------------|---------------|-----------|
   |10|Fest|Shu|Vertriebsleiter|

### <a name="to-delete-rows"></a>Zum Löschen von Zeilen

- Mit der rechten Maustaste in den Wert 16 (Zeile 16) auf der linken Seite des Arbeitsblatts, und klicken Sie dann auf **löschen**.

### <a name="to-sort-the-rows-in-the-list"></a>Um die Zeilen in der Liste sortieren

1. Wählen Sie eine Zelle in der Liste.

     Pfeilschaltflächen werden in jeder Kopfzeile der Spalte angezeigt.

2. Klicken Sie auf den Pfeil in der **Nachname** Spaltenüberschrift.

3. Klicken Sie auf **Aufsteigend sortieren**.

     Die Zeilen sind alphabetisch nach Nachnamen sortiert.

### <a name="to-filter-information"></a>Um Informationen zu filtern

1. Wählen Sie eine Zelle in der Liste.

2. Klicken Sie auf den Pfeil in der **Titel** Spaltenüberschrift.

3. Klicken Sie auf **Vertriebsmitarbeiter**.

     Die Liste enthält nur die Zeilen, die **Vertriebsmitarbeiter** in die **Titel** Spalte.

4. Klicken Sie auf den Pfeil in der **Titel** erneut die Kopfzeile der Spalte.

5. Klicken Sie auf **(alle)**.

     Der Filter wird entfernt, und alle Zeilen angezeigt werden.

## <a name="next-steps"></a>Nächste Schritte
 In dieser exemplarischen Vorgehensweise wird gezeigt, die Grundlagen des Bindens einer Tabelle in einer Datenbank an ein Listenobjekt. Die folgenden Aufgaben könnten sich daran anschließen:

- Daten zwischengespeichert, so dass sie offline verwendet werden kann. Weitere Informationen finden Sie unter [Vorgehensweise: Zwischenspeichern von Daten für die Verwendung, offline ist oder auf einem Server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- Die Lösung bereit. Weitere Informationen finden Sie unter [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md).

- Erstellen Sie eine Master/Detail-Beziehung zwischen einem Feld und eine Tabelle an. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen Sie eine master-Detail-Beziehung mithilfe eines zwischengespeicherten Datasets](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md).

## <a name="see-also"></a>Siehe auch
- [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Daten in Office-Projektmappen](../vsto/data-in-office-solutions.md)
- [Exemplarische Vorgehensweise: Einfache Datenbindung in einem Projekt auf Dokumentebene](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
