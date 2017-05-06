---
title: "Exemplarische Vorgehensweise: Komplexe Datenbindung in Projekten auf Dokumentebene"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Komplexe Daten [Office-Entwicklung in Visual Studio]"
  - "Daten [Office-Entwicklung in Visual Studio], Binden von Daten"
  - "Datenbindung [Office-Entwicklung in Visual Studio], Mehrere Spalten"
  - "Datenbindung in mehreren Spalten [Office-Entwicklung in Visual Studio]"
ms.assetid: 32ffad3d-fba4-476a-99b8-ef440434f4e1
caps.latest.revision: 50
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 49
---
# Exemplarische Vorgehensweise: Komplexe Datenbindung in Projekten auf Dokumentebene
  Diese exemplarische Vorgehensweise veranschaulicht die Grundlagen der komplexen Datenbindung in einem Projekt auf Dokumentebene.  In einem Microsoft Office Excel\-Arbeitsblatt können mehrere Zellen an Felder der SQL Server\-Datenbank **Northwind** gebunden werden.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Hinzufügen einer Datenquelle zum Arbeitsmappenprojekt  
  
-   Hinzufügen datengebundener Steuerelemente zu einem Arbeitsblatt  
  
-   Speichern von Datenänderungen in der Datenbank  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Zugriff auf einen Server mit der SQL Server\-Beispieldatenbank **Northwind**.  
  
-   Lese\- und Schreibberechtigungen für die SQL Server\-Datenbank.  
  
## Erstellen eines neuen Projekts  
 Zunächst müssen Sie ein Excel\-Arbeitsmappenprojekt erstellen.  
  
#### So erstellen Sie ein neues Projekt  
  
1.  Erstellen Sie ein Excel\-Arbeitsmappenprojekt mit dem Namen **My Complex Data Binding**.  Wählen Sie im Assistenten **Neues Dokument erstellen** aus.  
  
     Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio öffnet die neue Excel\-Arbeitsmappe im Designer und fügt dem **Projektmappen\-Explorer** das Projekt "My Complex Data Binding" hinzu.  
  
## Erstellen der Datenquelle  
 Verwenden Sie das **Datenquellenfenster**, um dem Projekt ein typisiertes Dataset hinzuzufügen.  
  
#### So erstellen Sie die Datenquelle  
  
1.  Wenn das **Datenquellen** nicht sichtbar ist, zeigen Sie sie durch, auf der Menüleiste auf und **Ansicht** auswählen, **Weitere Fenster**, **Datenquellen**.  
  
2.  Wählen Sie **Neue Datenquelle hinzufügen**, um **Assistent zum Konfigurieren von Datenquellen** zu starten.  
  
3.  Wählen Sie **Datenbank** aus, und klicken Sie auf **Weiter**.  
  
4.  Wählen Sie eine Datenverbindung zur Northwind SQL Server\-Beispieldatenbank aus, oder fügen Sie mithilfe der Schaltfläche **Neue Verbindung** eine neue Verbindung hinzu.  
  
5.  Klicken Sie nach dem Auswählen oder Erstellen einer Verbindung auf **Weiter**.  
  
6.  Deaktivieren Sie ggf. die Option zum Speichern der Verbindung, und klicken Sie dann auf **Weiter**.  
  
7.  Erweitern Sie im Fenster **Datenbankobjekte** den Knoten **Tabellen**.  
  
8.  Aktivieren Sie das Kontrollkästchen neben der Tabelle **Employees**.  
  
9. Klicken Sie auf **Fertig stellen**.  
  
 Der Assistent fügt dem **Datenquellen** die Tabelle **Employees** hinzu.  Außerdem wird dem Projekt ein typisiertes Dataset hinzugefügt, das im **Projektmappen\-Explorer** sichtbar ist.  
  
## Hinzufügen von Steuerelementen zum Arbeitsblatt  
 Beim Öffnen einer Arbeitsmappe wird darin die Tabelle **Employees** angezeigt.  Benutzer können auch die Daten ändern und anschließend die Änderungen durch Klicken auf eine Schaltfläche in der Datenbank speichern.  
  
 Soll die Arbeitsmappe automatisch an die Tabelle gebunden werden, kann der Arbeitsmappe im Fenster **Datenquellen** ein <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelement hinzugefügt werden.  Fügen Sie aus der **Toolbox** ein <xref:System.Windows.Forms.Button>\-Steuerelement hinzu, um dem Benutzer das Speichern von Änderungen zu ermöglichen.  
  
#### So fügen Sie ein Listenobjekt hinzu  
  
1.  Überprüfen Sie, ob die **My Complex Data Binding.xlsx** Arbeitsmappe im Visual Studio\-Designer geöffnet ist, mit **Blatt1** angezeigt.  
  
2.  Öffnen Sie das Fenster **Datenquellen**, und wählen Sie den Knoten **Employees** aus.  
  
3.  Klicken Sie auf den Dropdownpfeil, der angezeigt wird.  
  
4.  Wählen Sie in der Dropdownliste **ListObject** aus.  
  
5.  Ziehen Sie die Tabelle **Employees** zur Zelle **A6**.  
  
     Ein <xref:Microsoft.Office.Tools.Excel.ListObject>\-Steuerelement mit Namen `EmployeesListObject` wird in der Zelle **A6** erstellt.  Gleichzeitig werden dem Projekt eine <xref:System.Windows.Forms.BindingSource> mit Namen `EmployeesBindingSource`, ein Tabellenadapter und eine <xref:System.Data.DataSet>\-Instanz hinzugefügt.  Das Steuerelement ist an die <xref:System.Windows.Forms.BindingSource> gebunden, die wiederum an die <xref:System.Data.DataSet>\-Instanz gebunden ist.  
  
#### So fügen Sie eine Schaltfläche hinzu  
  
1.  Klicken Sie in der **Toolbox** auf die Registerkarte **Allgemeine Steuerelemente**, und fügen Sie von dort aus der Zelle **A4** des Arbeitsblatts ein <xref:System.Windows.Forms.Button>\-Steuerelement hinzu.  
  
 Der nächste Schritt besteht darin, der Schaltfläche Text hinzuzufügen, wenn das Arbeitsblatt geöffnet wird.  
  
## Initialisieren des Steuerelements  
 Fügen Sie der Schaltfläche den Text im <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>\-Ereignishandler hinzu.  
  
#### So initialisieren Sie das Steuerelement  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf **Sheet1.vb** oder **Sheet1.cs**, und klicken Sie dann im Kontextmenü auf **Code anzeigen**.  
  
2.  Fügen Sie der `Sheet1_Startup`\-Methode den folgenden Code hinzu, um den Text für b`utton` festzulegen.  
  
     [!code-csharp[Trin_VstcoreDataExcel#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet3.cs#8)]
     [!code-vb[Trin_VstcoreDataExcel#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet3.vb#8)]  
  
3.  Nur in C\#: Fügen Sie einen Ereignishandler für das <xref:System.Windows.Forms.Control.Click>\-Ereignis zur `Sheet1_Startup`\-Methode hinzu.  
  
     [!code-csharp[Trin_VstcoreDataExcel#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet3.cs#9)]  
  
 Fügen Sie nun Code hinzu, um das <xref:System.Windows.Forms.Control.Click>\-Ereignis der Schaltfläche zu behandeln.  
  
## Speichern von Änderungen in der Datenbank  
 Alle vorgenommenen Datenänderungen sind nur im lokalen Dataset vorhanden, solange sie nicht explizit in der Datenbank gespeichert werden.  
  
#### So speichern Sie Änderungen in der Datenbank  
  
1.  Fügen Sie für das <xref:System.Windows.Forms.Control.Click>\-Ereignis von b`utton` einen Ereignishandler hinzu. Um alle am Dataset vorgenommenen Änderungen in die Datenbank zu übernehmen, fügen Sie folgenden Code hinzu.  
  
     [!code-csharp[Trin_VstcoreDataExcel#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet3.cs#10)]
     [!code-vb[Trin_VstcoreDataExcel#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet3.vb#10)]  
  
## Testen der Anwendung  
 Sie können die Arbeitsmappe jetzt testen, um zu überprüfen, ob die Daten wie erwartet angezeigt werden und Sie die Daten im Listenobjekt bearbeiten können.  
  
#### So testen Sie die Datenbindung  
  
-   Drücken Sie F5.  
  
     Stellen Sie sicher, dass das Listenobjekt beim Öffnen der Arbeitsmappe mit Daten aus der Tabelle **Employees** gefüllt wird.  
  
#### So ändern Sie Daten  
  
1.  Klicken Sie auf die Zelle **B7**, die den Namen **Davolio** enthalten sollte.  
  
2.  Geben Sie den Namen Anderson ein, und drücken Sie die EINGABETASTE.  
  
#### So ändern Sie einen Spaltenheader  
  
1.  Klicken Sie auf die Zelle, die den Spaltenheader **LastName** enthält.  
  
2.  Geben Sie "Last Name" mit einem Leerzeichen zwischen den beiden Wörtern ein, und drücken Sie die EINGABETASTE.  
  
#### So speichern Sie Daten  
  
1.  Klicken Sie im Arbeitsblatt auf **Speichern**.  
  
2.  Beenden Sie Excel.  Klicken Sie auf **Nein**, wenn Sie zum Speichern der vorgenommenen Änderungen aufgefordert werden.  
  
3.  Drücken Sie F5, um das Projekt erneut auszuführen.  
  
     Das Listenobjekt wird mit Daten aus der Tabelle **Employees** aufgefüllt.  
  
4.  Beachten Sie, dass in Zelle **B7** immer noch der Name "Anderson" steht. Dabei handelt es sich um die Datenänderung, die Sie vorgenommen haben und die jetzt in der Datenbank gespeichert ist.  Der Spaltenheader **LastName** hat wieder seine ursprüngliche Schreibweise ohne Leerzeichen angenommen, weil der Spaltenheader nicht an die Datenbank gebunden ist, und Sie die im Arbeitsblatt vorgenommenen Änderungen nicht abgespeichert haben.  
  
#### So fügen Sie neue Zeilen hinzu  
  
1.  Wählen Sie im Listenobjekt eine Zelle aus.  
  
     Am unteren Rand der Liste wird eine neue Reihe mit einem Sternchen \(**\***\) in der ersten Zelle angezeigt.  
  
2.  Fügen Sie der leeren Zeile folgende Informationen hinzu:  
  
    |EmployeeID|LastName|FirstName|Titel|  
    |----------------|--------------|---------------|-----------|  
    |10|Ito|Shu|Sales Manager|  
  
#### So löschen Sie Zeilen  
  
-   Klicken Sie mit der rechten Maustaste ganz links auf der Arbeitsmappe auf die Nummer 16 \(Zeile 16\), und klicken Sie anschließend auf **Löschen**.  
  
#### So sortieren Sie die Zeilen in der Liste  
  
1.  Wählen Sie in der Liste eine Zelle aus.  
  
     Pfeilschaltflächen werden in den einzelnen Spaltenheadern angezeigt.  
  
2.  Klicken Sie im Spaltenheader **Last Name** auf die Pfeilschaltfläche.  
  
3.  Klicken Sie auf **Aufsteigend sortieren**.  
  
     Die Zeilen werden alphabetisch nach Nachnamen sortiert.  
  
#### So filtern Sie Informationen  
  
1.  Wählen Sie in der Liste eine Zelle aus.  
  
2.  Klicken Sie im Spaltenheader **Title** auf die Pfeilschaltfläche.  
  
3.  Klicken Sie auf **Sales Representative**.  
  
     Die Liste zeigt nur die Zeilen an, bei denen in der Spalte **Title** der Eintrag **Sales Representative** steht.  
  
4.  Klicken Sie im Spaltenheader **Title** erneut auf die Pfeilschaltfläche.  
  
5.  Klicken Sie auf **\(All\)**.  
  
     Der Filter wird entfernt, und es werden alle Zeilen angezeigt.  
  
## Nächste Schritte  
 In dieser exemplarischen Vorgehensweise werden die Grundlagen für das Binden einer Tabelle in einer Datenbank an ein Listenobjekt veranschaulicht.  Die folgenden Aufgaben könnten sich daran anschließen:  
  
-   Zwischenspeichern der Daten, damit diese offline verwendet werden können.  Weitere Informationen hierzu finden Sie unter [Gewusst wie: Zwischenspeichern von Daten zur Offlineverwendung oder zur Verwendung auf einem Server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   Bereitstellen der Projektmappe.  Weitere Informationen finden Sie unter [Bereitstellen einer Office-Projektmappe](../vsto/deploying-an-office-solution.md).  
  
-   Erstellen einer Master\/Detail\-Beziehung zwischen einem Feld und einer Tabelle.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Master&#47;Detail-Beziehung mithilfe eines zwischengespeicherten Datasets](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md).  
  
## Siehe auch  
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Daten in Office-Lösungen](../vsto/data-in-office-solutions.md)   
 [Exemplarische Vorgehensweise: Einfache Datenbindung in Projekten auf Dokumentebene](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)  
  
  