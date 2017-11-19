---
title: 'Exemplarische Vorgehensweise: Komplexe Datenbindung in einem Projekt auf Dokumentebene | Microsoft Docs'
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
- data [Office development in Visual Studio], binding data
- complex data [Office development in Visual Studio]
- multiple column data binding [Office development in Visual Studio]
- data binding [Office development in Visual Studio], multiple columns
ms.assetid: 32ffad3d-fba4-476a-99b8-ef440434f4e1
caps.latest.revision: "50"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: dff7896b24508891a62ad3a0760880ed6a68a65a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-complex-data-binding-in-a-document-level-project"></a>Exemplarische Vorgehensweise: Komplexe Datenbindung in Projekten auf Dokumentebene
  Diese exemplarische Vorgehensweise veranschaulicht die Grundlagen der komplexe Datenbindung in einem Projekt auf Dokumentebene. Sie können mehrere Zellen in einem Microsoft Office Excel-Arbeitsblatt an Felder in der Northwind-SQL Server-Datenbank binden.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Eine Datenquelle hinzufügen zum Arbeitsmappenprojekt.  
  
-   Hinzufügen von datengebundenen Steuerelementen zu einem Arbeitsblatt.  
  
-   Speichern von datenänderungen in der Datenbank.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Zugriff auf einen Server mit der Beispieldatenbank Northwind-SQL Server.  
  
-   Berechtigungen zum Lesen und Schreiben in SQL Server-Datenbank.  
  
## <a name="creating-a-new-project"></a>Erstellen eines neuen Projekts  
 Der erste Schritt besteht darin ein Excel-Arbeitsmappenprojekt erstellen.  
  
#### <a name="to-create-a-new-project"></a>So erstellen Sie ein neues Projekt  
  
1.  Erstellen Sie ein Excel-Arbeitsmappenprojekt mit dem Namen **Meine komplexe Datenbindung**. Wählen Sie im Assistenten **erstellen Sie ein neues Dokument**.  
  
     Weitere Informationen finden Sie unter [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio öffnet die neue Excel-Arbeitsmappe im Designer und fügt die **Meine komplexe Datenbindung** Projekt **Projektmappen-Explorer**.  
  
## <a name="creating-the-data-source"></a>Erstellen der Datenquelle  
 Verwenden das Fenster **Datenquellen** , um dem Projekt ein typisiertes Dataset hinzuzufügen.  
  
#### <a name="to-create-the-data-source"></a>So erstellen Sie die Datenquelle  
  
1.  Wenn das Fenster **Datenquellen** nicht sichtbar ist, zeigen Sie es an, indem Sie in der Menüleiste **Ansicht**, **Weitere Fenster**und **Datenquellen**wählen.  
  
2.  Wählen Sie **Neue Datenquelle hinzufügen** , um den **Assistenten zum Konfigurieren von Datenquellen**zu starten.  
  
3.  Wählen Sie **Datenbank** , und klicken Sie dann auf **Weiter**.  
  
4.  Wählen Sie eine Datenverbindung zur Northwind-Beispieldatenbank SQL Server, oder fügen Sie eine neue Verbindung mit der **neue Verbindung** Schaltfläche.  
  
5.  Nachdem eine Verbindung ausgewählt oder erstellt wurde, klicken Sie auf **Weiter**.  
  
6.  Deaktivieren Sie die Option aus, um die Verbindung zu speichern, wenn diese Option ausgewählt ist, und klicken Sie dann auf **Weiter**.  
  
7.  Erweitern Sie die **Tabellen** Knoten in der **-Datenbankobjekte** Fenster.  
  
8.  Aktivieren Sie das Kontrollkästchen neben den **Mitarbeiter** Tabelle.  
  
9. Klicken Sie auf **Fertig stellen**.  
  
 Fügt der Assistent die **Mitarbeiter** Tabelle, auf die **Datenquellen** Fenster. Es auch ein typisiertes Dataset dem Projekt hinzugefügt, die in angezeigt wird **Projektmappen-Explorer**.  
  
## <a name="adding-controls-to-the-worksheet"></a>Hinzufügen von Steuerelementen zum Arbeitsblatt  
 Ein Arbeitsblatt zeigt die **Mitarbeiter** Tabelle, wenn die Arbeitsmappe geöffnet ist. Benutzer werden in der Lage, nehmen Änderungen an den Daten und speichern Sie diese Änderungen dann wieder in der Datenbank, durch Klicken auf eine Schaltfläche.  
  
 Um das Arbeitsblatt automatisch an die Tabelle zu binden, fügen Sie eine <xref:Microsoft.Office.Tools.Excel.ListObject> -Steuerelement auf das Arbeitsblatt aus der **Datenquellen** Fenster. Um die Benutzer die Option zum Speichern der Änderungen zu gewähren, fügen einen <xref:System.Windows.Forms.Button> -Steuerelement aus der **Toolbox**.  
  
#### <a name="to-add-a-list-object"></a>So fügen Sie ein Listenobjekt hinzu  
  
1.  Überprüfen Sie, ob die **Meine komplexe Daten Binding.xlsx** Arbeitsmappe geöffnet, in der Visual Studio-Designer ist mit **"Sheet1"** angezeigt.  
  
2.  Öffnen der **Datenquellen** und wählen Sie die **Mitarbeiter** Knoten.  
  
3.  Klicken Sie auf den Dropdown Pfeil, der angezeigt wird.  
  
4.  Wählen Sie **ListObject** in der Dropdown-Liste.  
  
5.  Ziehen Sie die **Mitarbeiter** Tabelle Zelle **A6**.  
  
     Ein <xref:Microsoft.Office.Tools.Excel.ListObject> Steuerelement namens `EmployeesListObject` ist in der Zelle erstellt **A6**. Zur gleichen Zeit eine <xref:System.Windows.Forms.BindingSource> mit dem Namen `EmployeesBindingSource`, Tabellenadapters, und ein <xref:System.Data.DataSet> Instanz werden dem Projekt hinzugefügt. Das Steuerelement gebunden ist die <xref:System.Windows.Forms.BindingSource>, das wiederum gebunden ist, um die <xref:System.Data.DataSet> Instanz.  
  
#### <a name="to-add-a-button"></a>So fügen Sie eine Schaltfläche hinzu  
  
1.  Aus der **Standardsteuerelementen** auf der Registerkarte die **Toolbox**, Hinzufügen einer <xref:System.Windows.Forms.Button> -Steuerelement zur Zelle **A4** des Arbeitsblatts.  
  
 Der nächste Schritt ist die Schaltfläche Text hinzugefügt, wenn das Arbeitsblatt geöffnet.  
  
## <a name="initializing-the-control"></a>Initialisieren des Steuerelements  
 Hinzufügen von Text der Schaltfläche in der <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> -Ereignishandler.  
  
#### <a name="to-initialize-the-control"></a>Um das Steuerelement zu initialisieren.  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste **Sheet1.vb** oder **Sheet1.cs**, und klicken Sie dann auf **Code anzeigen** im Kontextmenü.  
  
2.  Fügen Sie folgenden Code zu der `Sheet1_Startup` Methode, um den Text für den b einzurichten`utton`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#8)]
     [!code-vb[Trin_VstcoreDataExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#8)]  
  
3.  Nur für c#, fügen Sie einen Ereignishandler für das <xref:System.Windows.Forms.Control.Click> Ereignis, um die `Sheet1_Startup` Methode.  
  
     [!code-csharp[Trin_VstcoreDataExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#9)]  
  
 Nun fügen Sie Code zum Behandeln der <xref:System.Windows.Forms.Control.Click> -Ereignis der Schaltfläche.  
  
## <a name="saving-changes-to-the-database"></a>Speichern von Änderungen an der Datenbank  
 Alle Änderungen vorgenommen wurden die Daten sind nur im lokalen Dataset vorhanden, bis sie explizit wieder in der Datenbank gespeichert werden.  
  
#### <a name="to-save-changes-to-the-database"></a>Um Änderungen an der Datenbank speichern  
  
1.  Fügen Sie einen Ereignishandler für das <xref:System.Windows.Forms.Control.Click> der b-Ereignis`utton`, und fügen Sie folgenden Code aus, um alle Änderungen zu speichern, die im Dataset wieder in der Datenbank vorgenommen wurden.  
  
     [!code-csharp[Trin_VstcoreDataExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#10)]
     [!code-vb[Trin_VstcoreDataExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#10)]  
  
## <a name="testing-the-application"></a>Testen der Anwendung  
 Sie können jetzt Testen Ihrer Arbeitsmappe, um sicherzustellen, dass die Daten wie erwartet angezeigt wird und Sie die Daten im Listenobjekt bearbeiten können.  
  
#### <a name="to-test-the-data-binding"></a>So testen Sie die Datenbindung  
  
-   Drücken Sie F5.  
  
     Stellen Sie sicher, dass das Listenobjekt mit Daten aus, wenn die Arbeitsmappe geöffnet wird gefüllt ist, die **Mitarbeiter** Tabelle.  
  
#### <a name="to-modify-data"></a>Zum Ändern von Daten  
  
1.  Klicken Sie auf die Zelle **B7**, die den Namen enthalten **Davolio**.  
  
2.  Geben Sie den Namen **Anderson**, und drücken Sie dann die EINGABETASTE.  
  
#### <a name="to-modify-a-column-header"></a>So ändern Sie einen Spaltenheader  
  
1.  Klicken Sie auf die Zelle mit den Spaltenüberschrift **LastName**.  
  
2.  Typ **Nachname**, z. B. ein Leerzeichen zwischen den beiden Wörtern, und drücken Sie dann die EINGABETASTE.  
  
#### <a name="to-save-data"></a>Zum Speichern von Daten  
  
1.  Klicken Sie auf **speichern** auf das Arbeitsblatt.  
  
2.  Beenden Sie Excel. Klicken Sie auf **keine** Aufforderung die vorgenommenen Änderungen zu speichern.  
  
3.  Drücken Sie F5, um das Projekt erneut auszuführen.  
  
     Das Listenobjekt mit Daten gefüllt wird die **Mitarbeiter** Tabelle.  
  
4.  Beachten Sie, dass der Name in Zelle **B7** ist immer noch **Anderson**, also die Daten ändern, dass Sie vorgenommen und wieder in der Datenbank gespeichert. Den Spaltenüberschrift **LastName** zurück in ihr ursprüngliches Format ohne Leerzeichen geändert hat, da den Spaltenüberschrift nicht an die Datenbank gebunden ist und Sie nicht die Änderungen in das Arbeitsblatt speichern.  
  
#### <a name="to-add-new-rows"></a>So fügen Sie neue Zeilen hinzu  
  
1.  Wählen Sie eine Zelle innerhalb der List-Objekts.  
  
     Wird eine neue Zeile am unteren Rand der Liste mit einem Sternchen (**\***) in der ersten Zelle der neuen Zeile.  
  
2.  Fügen Sie die folgenden Informationen in die leere Zeile hinzu.  
  
    |EmployeeID|LastName|FirstName|Titel|  
    |----------------|--------------|---------------|-----------|  
    |10|Zischka|ERwin|Vertriebsleiter|  
  
#### <a name="to-delete-rows"></a>Löschen von Zeilen  
  
-   Mit der rechten Maustaste in der Zahl 16 (Zeile 16) auf die äußerst linke Seite des Arbeitsblatts, und klicken Sie dann auf **löschen**.  
  
#### <a name="to-sort-the-rows-in-the-list"></a>Um die Zeilen in der Liste zu sortieren.  
  
1.  Wählen Sie eine Zelle in der Liste.  
  
     Pfeilschaltflächen werden in jeder Kopfzeile der Spalte angezeigt.  
  
2.  Klicken Sie auf den Pfeil in der **Nachname** Spaltenüberschrift.  
  
3.  Klicken Sie auf **Aufsteigend sortieren**.  
  
     Die Zeilen sind alphabetisch nach Nachnamen sortiert.  
  
#### <a name="to-filter-information"></a>Informationen zu filtern  
  
1.  Wählen Sie eine Zelle in der Liste.  
  
2.  Klicken Sie auf den Pfeil in der **Titel** Spaltenüberschrift.  
  
3.  Klicken Sie auf **Vertriebsmitarbeiter**.  
  
     Die Liste zeigt nur die Zeilen, die über **Vertriebsmitarbeiter** in der **Titel** Spalte.  
  
4.  Klicken Sie auf den Pfeil in der **Titel** Spaltenüberschrift erneut aus.  
  
5.  Klicken Sie auf **(alle)**.  
  
     Der Filter wird entfernt, und alle Zeilen angezeigt.  
  
## <a name="next-steps"></a>Nächste Schritte  
 In dieser exemplarischen Vorgehensweise veranschaulicht die Grundlagen des Bindens von einer Tabellenstatus in einer Datenbank an ein Listenobjekt. Die folgenden Aufgaben könnten sich daran anschließen:  
  
-   Die Daten zwischengespeichert werden, damit es offline verwendet werden kann. Weitere Informationen finden Sie unter [Vorgehensweise: Zwischenspeichern von Daten für Offline verwenden oder auf einem Server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   Die Lösung bereit. Weitere Informationen finden Sie unter [Bereitstellen einer Office-Lösung](../vsto/deploying-an-office-solution.md).  
  
-   Erstellen einer Master/Detail-Beziehungs zwischen einem Feld und eine Tabelle an. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Master Detail-Beziehung mithilfe eines zwischengespeicherten Datasets](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Daten in Office-Projektmappen](../vsto/data-in-office-solutions.md)   
 [Exemplarische Vorgehensweise: Einfache Datenbindung in einem Projekt auf Dokumentebene](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)  
  
  