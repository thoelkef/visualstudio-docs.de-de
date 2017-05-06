---
title: "Exemplarische Vorgehensweise: Einfache Datenbindung in Projekten auf Dokumentebene"
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
  - "Daten [Office-Entwicklung in Visual Studio], Binden von Daten"
  - "Datenbindung [Office-Entwicklung in Visual Studio], Arbeitsblattzelle an ein Datenbankfeld"
  - "Datenbankfeld [Office-Entwicklung in Visual Studio]"
  - "Einfache Datenbindung [Office-Entwicklung in Visual Studio]"
  - "Arbeitsblätter [Office-Entwicklung in Visual Studio], Binden einer Arbeitsblattzelle an ein Datenbankfeld"
ms.assetid: 6b8fd638-af13-4ea1-b1c0-2763e2d8ae23
caps.latest.revision: 58
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 57
---
# Exemplarische Vorgehensweise: Einfache Datenbindung in Projekten auf Dokumentebene
  Diese exemplarische Vorgehensweise veranschaulicht die Grundlagen der Datenbindung in einem Projekt auf Dokumentebene.  Ein einzelnes Datenfeld in einer SQL Server\-Datenbank wird an einen benannten Bereich in Microsoft Office Excel gebunden.  Die exemplarische Vorgehensweise erklärt auch das Hinzufügen von Steuerelementen, mit denen Sie einen Bildlauf durch alle Datensätze in der Tabelle durchführen können.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Erstellen einer Datenquelle für ein Excel\-Projekt.  
  
-   Hinzufügen von Steuerelementen zu einem Arbeitsblatt  
  
-   Durchführen von Bildläufen durch Datenbankdatensätze.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] oder [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Zugriff auf einen Server mit der SQL Server\-Beispieldatenbank **Northwind**.  
  
-   Lese\- und Schreibberechtigungen für die SQL Server\-Datenbank.  
  
## Erstellen eines neuen Projekts  
 In diesem Schritt wird ein Excel\-Arbeitsmappenprojekt erstellt.  
  
#### So erstellen Sie ein neues Projekt  
  
1.  Erstellen Sie mit Visual Basic oder C\# ein Excel\-Arbeitsmappenprojekt mit dem Namen **My Simple Data Binding**.  Stellen Sie sicher, dass **Neues Dokument erstellen** ausgewählt ist.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Visual Studio öffnet die neue Excel\-Arbeitsmappe im Designer und fügt dem **Projektmappen\-Explorer** das Projekt "My Simple Data Binding" hinzu.  
  
## Erstellen der Datenquelle  
 Verwenden Sie das **Datenquellenfenster**, um dem Projekt ein typisiertes Dataset hinzuzufügen.  
  
#### So erstellen Sie die Datenquelle  
  
1.  Wenn das **Datenquellen** nicht sichtbar ist, zeigen Sie sie durch, auf der Menüleiste auf und **Ansicht** auswählen, **Weitere Fenster**, **Datenquellen**.  
  
2.  Wählen Sie **Neue Datenquelle hinzufügen**, um **Assistent zum Konfigurieren von Datenquellen** zu starten.  
  
3.  Wählen Sie **Datenbank** aus, und klicken Sie auf **Weiter**.  
  
4.  Wählen Sie eine Datenverbindung zur SQL Server\-Beispieldatenbank Northwind aus, oder fügen Sie mithilfe der Schaltfläche **Neue Verbindung** eine neue Verbindung hinzu.  
  
5.  Klicken Sie nach dem Auswählen oder Erstellen einer Verbindung auf **Weiter**.  
  
6.  Deaktivieren Sie ggf. die Option zum Speichern der Verbindung, und klicken Sie dann auf **Weiter**.  
  
7.  Erweitern Sie im Fenster **Datenbankobjekte** den Knoten **Tabellen**.  
  
8.  Aktivieren Sie das Kontrollkästchen neben der Tabelle **Customers**.  
  
9. Klicken Sie auf **Fertig stellen**.  
  
 Der Assistent fügt dem **Datenquellenfenster** die Tabelle **Customers** hinzu.  Außerdem wird dem Projekt ein typisiertes Dataset hinzugefügt, das im **Projektmappen\-Explorer** sichtbar ist.  
  
## Hinzufügen von Steuerelementen zum Arbeitsblatt  
 Diese exemplarische Vorgehensweise setzt zwei benannte Bereiche und vier Schaltflächen auf dem ersten Arbeitsblatt voraus.  Fügen Sie zuerst die beiden benannten Bereiche aus dem **Datenquellenfenster** hinzu, damit diese automatisch an die Datenquelle gebunden werden.  Fügen Sie dann die Schaltflächen aus der **Toolbox** hinzu.  
  
#### So fügen Sie zwei benannte Bereiche hinzu  
  
1.  Überprüfen Sie, ob die **My Simple Data Binding.xlsx** Arbeitsmappe im Visual Studio\-Designer geöffnet ist, mit **Blatt1** angezeigt.  
  
2.  Öffnen Sie das **Datenquellenfenster**, und erweitern Sie den Knoten **Customers**.  
  
3.  Wählen Sie die Spalte **CompanyName**, und klicken Sie anschließend auf den angezeigten Dropdownpfeil.  
  
4.  Klicken Sie in der Dropdownliste auf **NamedRange**, und ziehen Sie die Spalte **CompanyName** auf die Zelle **A1**.  
  
     Ein <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement mit dem Namen `companyNameNamedRange` wird in der Zelle **A1** erstellt.  Gleichzeitig werden dem Projekt eine <xref:System.Windows.Forms.BindingSource> mit dem Namen `customersBindingSource`, ein Tabellenadapter und eine <xref:System.Data.DataSet>\-Instanz hinzugefügt.  Das Steuerelement ist an die <xref:System.Windows.Forms.BindingSource> gebunden, die wiederum an die <xref:System.Data.DataSet>\-Instanz gebunden ist.  
  
5.  Wählen Sie im **Datenquellenfenster** die Spalte **CustomerID**, und klicken Sie anschließend auf den angezeigten Dropdownpfeil.  
  
6.  Klicken Sie in der Dropdownliste auf **NamedRange**, und ziehen Sie die Spalte **CustomerID** auf die Zelle **B1**.  
  
7.  Es wird ein weiteres, mit `customerIDNamedRange` benanntes <xref:Microsoft.Office.Tools.Excel.NamedRange>\-Steuerelement in der Zelle **B1** erstellt und an die <xref:System.Windows.Forms.BindingSource> gebunden.  
  
#### So fügen Sie vier Schaltflächen hinzu  
  
1.  Klicken Sie in der **Toolbox** auf die Registerkarte **Allgemeine Steuerelemente**, und fügen Sie von dort ein <xref:System.Windows.Forms.Button>\-Steuerelement zur Zelle **A3** des Arbeitsblattes hinzu.  
  
     Diese Schaltfläche erhält den Namen `Button1`.  
  
2.  Fügen Sie den folgenden Zellen je eine weitere Schaltfläche hinzu. Die Namen der Schaltflächen lauten dann:  
  
    |Zelle|\(Name\)|  
    |-----------|--------------|  
    |B3|Button2|  
    |C3|Button3|  
    |D3|Button4|  
  
 Der nächste Schritt besteht darin, den Schaltflächen Text hinzuzufügen und in C\# Ereignishandler hinzuzufügen.  
  
## Initialisieren der Steuerelemente  
 Legen Sie den Schaltflächentext fest, und fügen Sie dem <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>\-Ereignis Ereignishandler hinzu.  
  
#### So initialisieren Sie die Steuerelemente  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf **Sheet1.vb** oder **Sheet1.cs**, und klicken Sie dann im Kontextmenü auf **Code anzeigen**.  
  
2.  Fügen Sie der `Sheet1_Startup`\-Methode den folgenden Code hinzu, um den Text für die einzelnen Schaltflächen festzulegen.  
  
     [!code-csharp[Trin_VstcoreDataExcel#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreDataExcel#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#2)]  
  
3.  Nur in C\#: Fügen Sie der `Sheet1_Startup`\-Methode Ereignishandler für die Klickereignisse der Schaltflächen hinzu.  
  
     [!code-csharp[Trin_VstcoreDataExcel#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#3)]  
  
 Fügen Sie nun Code für die Behandlung der <xref:System.Windows.Forms.Control.Click>\-Ereignisse der Schaltflächen hinzu, damit der Benutzer durch die Datensätze blättern kann.  
  
## Hinzufügen von Code, um das Durchführen des Bildlaufs durch die Datensätze zu ermöglichen  
 Fügen Sie den <xref:System.Windows.Forms.Control.Click>\-Ereignishandlern der einzelnen Schaltflächen Code hinzu, um durch die Datensätze zu navigieren.  
  
#### So navigieren Sie zum ersten Datensatz  
  
1.  Fügen Sie dem <xref:System.Windows.Forms.Control.Click>\-Ereignis der `Button1`\-Schaltfläche einen Ereignishandler mit folgendem Code hinzu, um zum ersten Datensatz zu navigieren:  
  
     [!code-csharp[Trin_VstcoreDataExcel#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreDataExcel#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#4)]  
  
#### So navigieren Sie zum vorherigen Datensatz  
  
1.  Fügen Sie dem <xref:System.Windows.Forms.Control.Click>\-Ereignis der `Button2`\-Schaltfläche einen Ereignishandler mit folgendem Code hinzu, um zur vorherigen Position zu navigieren:  
  
     [!code-csharp[Trin_VstcoreDataExcel#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreDataExcel#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#5)]  
  
#### So navigieren Sie zum nächsten Datensatz  
  
1.  Fügen Sie dem <xref:System.Windows.Forms.Control.Click>\-Ereignis der `Button3`\-Schaltfläche einen Ereignishandler mit folgendem Code hinzu, um zur nächsten Position zu navigieren:  
  
     [!code-csharp[Trin_VstcoreDataExcel#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreDataExcel#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#6)]  
  
#### So navigieren Sie zum letzten Datensatz  
  
1.  Fügen Sie dem <xref:System.Windows.Forms.Control.Click>\-Ereignis der `Button4`\-Schaltfläche einen Ereignishandler mit folgendem Code hinzu, um zum letzten Datensatz zu navigieren:  
  
     [!code-csharp[Trin_VstcoreDataExcel#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreDataExcel#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#7)]  
  
## Testen der Anwendung  
 Nun können Sie die Arbeitsmappe testen, um sicherzustellen, dass das Blättern durch die Datensätze der Datenbank möglich ist.  
  
#### So testen Sie die Arbeitsmappe  
  
1.  Drücken Sie F5, um das Projekt auszuführen.  
  
2.  Bestätigen Sie, dass der erste Datensatz in den Zellen **A1** und **B1** angezeigt wird.  
  
3.  Klicken Sie auf die Schaltfläche **\>** \(`Button3`\), und prüfen Sie, ob in den Zellen **A1** und **B1** der nächste Datensatz angezeigt wird.  
  
4.  Klicken Sie auf die anderen Navigationsschaltflächen, um zu prüfen, ob sich der Datensatz wie erwartet ändert.  
  
## Nächste Schritte  
 Diese exemplarische Vorgehensweise erläutert die Grundlagen des Bindens eines benannten Bereichs an ein Datenbankfeld.  Die folgenden Aufgaben könnten sich daran anschließen:  
  
-   Zwischenspeichern der Daten, damit diese offline verwendet werden können.  Weitere Informationen hierzu finden Sie unter [Gewusst wie: Zwischenspeichern von Daten zur Offlineverwendung oder zur Verwendung auf einem Server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   Binden von Zellen an mehrere Spalten in einer Tabelle, anstatt nur an ein Feld.  Weitere Informationen hierzu finden Sie unter [Exemplarische Vorgehensweise: Komplexe Datenbindung in Projekten auf Dokumentebene](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md).  
  
-   Verwenden eines <xref:System.Windows.Forms.BindingNavigator>\-Steuerelements, um einen Bildlauf durch die Datensätze durchzuführen.  Weitere Informationen finden Sie unter [Gewusst wie: Datennavigation mithilfe des DataNavigator-Steuerelements in Windows Forms](http://msdn.microsoft.com/library/0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb).  
  
## Siehe auch  
 [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Daten in Office-Lösungen](../vsto/data-in-office-solutions.md)   
 [Exemplarische Vorgehensweise: Komplexe Datenbindung in Projekten auf Dokumentebene](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)  
  
  