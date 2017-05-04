---
title: "Exemplarische Vorgehensweise: Aktualisieren der Steuerelemente in einer Multifunktionsleiste zur Laufzeit | Microsoft Docs"
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
  - "Steuerelemente [Office-Entwicklung in Visual Studio], Menüband"
  - "Dynamische Menüs [Office-Entwicklung in Visual Studio]"
  - "Menüband [Office-Entwicklung in Visual Studio], Steuerelemente"
  - "Menüband [Office-Entwicklung in Visual Studio], Dynamisches Menü"
  - "Menüband [Office-Entwicklung in Visual Studio], Aktualisieren"
  - "Aktualisieren von Multifunktionsleisten-Steuerelementen"
ms.assetid: ed80790f-3f95-47e4-8a41-872588a8ca07
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# Exemplarische Vorgehensweise: Aktualisieren der Steuerelemente in einer Multifunktionsleiste zur Laufzeit
  Diese exemplarische Vorgehensweise veranschaulicht das Verwenden des Menüband\-Objektmodells zum Aktualisieren der Steuerelemente auf einem Menüband, nachdem das Menüband in die Office\-Anwendung geladen wurde.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 Das Beispiel ruft Daten aus der Beispieldatenbank "Northwind" ab, um ein Kombinationsfeld und ein Menü in Microsoft Office Outlook mit Daten aufzufüllen.  Elemente, die Sie in diesen Steuerelementen auswählen, füllen Felder wie z. B. **An** und **Betreff** in einer E\-Mail\-Nachricht automatisch mit Daten auf.  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Erstellen eines neuen Outlook VSTO\-Add\-In\-Projekts.  
  
-   Entwerfen einer benutzerdefinierten Menübandgruppe.  
  
-   Hinzufügen der benutzerdefinierten Gruppe zu einer integrierten Registerkarte.  
  
-   Aktualisieren von Steuerelementen auf dem Menüband zur Laufzeit.  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten.  Diese Elemente sind von der jeweiligen Visual Studio\-Version und den verwendeten Einstellungen abhängig.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Outlook  
  
## Erstellen eines neuen Outlook VSTO\-Add\-In\-Projekts  
 Erstellen Sie zunächst ein neues Outlook VSTO\-Add\-In\-Projekt.  
  
#### So erstellen Sie ein neues Outlook VSTO\-Add\-In\-Projekt  
  
1.  Erstellen Sie in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ein Outlook VSTO\-Add\-In\-Projekt mit dem Namen "Ribbon\_Update\_At\_Runtime".  
  
2.  Wählen Sie im Dialogfeld **Neues Projekt** die Option **Projektmappenverzeichnis erstellen**.  
  
3.  Speichern Sie das Projekt im Standardprojektverzeichnis.  
  
     Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
## Entwerfen einer benutzerdefinierten Menübandgruppe  
 Das Menüband für dieses Beispiel wird angezeigt, wenn ein Benutzer eine neue E\-Mail\-Nachricht verfasst.  Um eine benutzerdefinierte Gruppe für das Menüband zu erstellen, fügen Sie dem Projekt zuerst Sie ein Menübandelement hinzu, und entwerfen Sie dann die Gruppe im Menüband\-Designer.  Diese benutzerdefinierte Gruppe unterstützt Sie beim Generieren von Nachverfolgungs\-Mail\-Nachrichten, indem Namen und Auftragsverläufe aus einer Datenbank abgerufen werden.  
  
#### So entwerfen Sie eine benutzerdefinierte Gruppe  
  
1.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
2.  Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option **Menüband \(Visueller Designer\)** aus.  
  
3.  Ändern Sie den Namen des neuen Menübands in **CustomerRibbon**, und klicken Sie dann auf **Hinzufügen**.  
  
     Die Datei **CustomerRibbon.cs** oder **CustomerRibbon.vb** wird im Menüband\-Designer geöffnet. Sie beinhaltet eine Standardregisterkarte und eine Gruppe.  
  
4.  Klicken Sie auf den Menüband\-Designer, um diese auszuwählen.  
  
5.  Klicken Sie im Fenster**Eigenschaften** auf den Dropdownpfeil neben der Eigenschaft **RibbonType**, und klicken Sie dann auf **Microsoft.Outlook.Mail.Compose**.  
  
     Auf diese Weise wird das Menüband angezeigt, wenn der Benutzer eine neue E\-Mail\-Nachricht in Outlook verfasst.  
  
6.  Klicken Sie auf den Menüband\-Designer auf **Group1**, um diese auszuwählen.  
  
7.  Legen Sie im Fenster **Eigenschaften** die Eigenschaft **Name** auf den Wert "Kundenbestellungen" fest.  
  
8.  Ziehen Sie aus der Registerkarte **Steuerelemente für Office\-Menübänder**  der **Toolbox** ein **ComboBox**\-Element in die Gruppe **Kundenbestellungen**.  
  
9. Klicken Sie auf **ComboBox1**, um diese Option auszuwählen.  
  
10. Legen Sie im Fenster **Eigenschaften** die Eigenschaft **Label** auf "Kunden" fest.  
  
11. Ziehen Sie aus der Registerkarte **Steuerelemente für Office\-Menübänder**  der **Toolbox** ein **Menü**\-Element in die Gruppe **Kundenbestellungen**.  
  
12. Legen Sie im Fenster **Eigenschaften** die Eigenschaft **Label** auf "Gekauftes Produkt" fest.  
  
13. Legen Sie **Dynamisch** auf **true** fest.  
  
     Auf diese Weise können Schaltflächen für das Menü während der Laufzeit hinzugefügt und entfernt werden, nachdem das Menüband in die Office\-Anwendung geladen wurde.  
  
## Hinzufügen der benutzerdefinierten Gruppe zu einer integrierten Registerkarte  
 Eine integrierte Registerkarte ist eine Registerkarte, die sich bereits auf dem Menüband einer Outlook Explorer\- oder Inspector\-Anwendung befindet.  In diesem Verfahren fügen Sie die benutzerdefinierte Gruppe einer integrierten Registerkarte hinzu und geben dann die Position der benutzerdefinierten Gruppe auf der Registerkarte an.  
  
#### So fügen Sie die benutzerdefinierte Gruppe einer integrierten Registerkarte hinzu  
  
1.  Klicken Sie auf die Registerkarte **TabAddins \(integriert\)**, um diese auszuwählen.  
  
2.  Erweitern Sie im Fenster **Eigenschaften** die Eigenschaft **ControlId**, und legen Sie dann **OfficeId** auf "TabNewMailMessage" fest.  
  
     Auf diese Weise wird die Gruppe **Kundenbestellungen** der Registerkarte **Nachrichten** des Menübands hinzugefügt, die in einer neuen E\-Mail\-Nachricht angezeigt wird.  
  
3.  Klicken Sie auf Gruppe **Kundenbestellungen**, um diese auszuwählen.  
  
4.  Erweitern Sie im Fenster **Eigenschaften** die Eigenschaft **Position**, klicken Sie auf den Dropdownpfeil neben der Eigenschaft **PositionType**, und klicken Sie dann auf **BeforeOfficeId**.  
  
5.  Legen Sie die Eigenschaft **OfficeId** auf "GroupClipboard" fest.  
  
     Dies positioniert die Gruppe **Kundenbestellungen** vor der Gruppe **Zwischenablage** der Registerkarte **Nachrichten**.  
  
## Erstellen der Datenquelle  
 Verwenden das Fenster **Datenquellen**, um dem Projekt ein typisiertes Dataset hinzuzufügen.  
  
#### So erstellen Sie die Datenquelle  
  
1.  Klicken Sie im Menü **Daten** auf **Neue Datenquelle hinzufügen**.  
  
     Der **Assistent zum Konfigurieren von Datenquellen** wird gestartet.  
  
2.  Wählen Sie **Datenbank** aus, und klicken Sie dann auf **Weiter**.  
  
3.  Wählen Sie **Dataset** aus, und klicken Sie dann auf **Weiter**.  
  
4.  Wählen Sie eine Datenverbindung mit der Microsoft SQL Server Compact 4.0\-Beispieldatenbank "Northwind" aus, oder fügen Sie eine neue Verbindung mithilfe der Schaltfläche **Neue Verbindung** hinzu.  
  
5.  Nachdem eine Verbindung ausgewählt oder erstellt wurde, klicken Sie auf **Weiter**.  
  
6.  Klicken Sie auf **Weiter**, um die Verbindungszeichenfolge zu speichern.  
  
7.  Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen**.  
  
8.  Aktivieren Sie das Kontrollkästchen neben jeder der folgenden Tabellen:  
  
    1.  **Kunden**  
  
    2.  **Auftragsdetails**  
  
    3.  **Aufträge**  
  
    4.  **Produkte**  
  
9. Klicken Sie auf **Fertig stellen**.  
  
## Aktualisieren von Steuerelementen in der benutzerdefinierten Gruppe zur Laufzeit  
 Verwenden Sie Menüband\-Objektmodell, um die folgenden Aufgaben auszuführen:  
  
-   Hinzufügen von Kundennamen zum Kombinationsfeld **Kunden**.  
  
-   Hinzufügen von Menüs und Schaltflächen\-Steuerelementen zum Menü **Gekaufte Produkte**, das Bestellungen und Produkte darstellt.  
  
-   Auffüllen der Felder To, Subject und Body neuer E\-Mail\-Nachrichten mithilfe von Daten aus dem Kombinationsfeld **Kunden** und dem Menü **Gekaufte Produkte**.  
  
#### So aktualisieren Sie Steuerelemente in der benutzerdefinierten Gruppe mithilfe des Menüband\-Objektmodells  
  
1.  Klicken Sie im Menü **Projekt** auf **Verweis hinzufügen**.  
  
2.  Klicken Sie im Dialogfeld **Verweis hinzufügen** auf die Registerkarte **.NET**, wählen Sie die Assembly **System.Data.Linq** aus, und klicken Sie dann auf **OK**.  
  
     Diese Assembly enthält Klassen für die Verwendung von LINQ \(Language\-Integrated Queries\).  Sie verwenden LINQ zum Auffüllen der Steuerelemente in der benutzerdefinierten Gruppe mit Daten aus der Datenbank "Northwind".  
  
3.  Klicken Sie im **Projektmappen\-Explorer** auf **CustomerRibbon.cs** oder **CustomerRibbon.vb**, um die Datei auszuwählen.  
  
4.  Klicken Sie im Menü **Ansicht** auf **Code**.  
  
     Die Menüband\-Codedatei wird im Code\-Editor geöffnet.  
  
5.  Fügen Sie am Anfang der Menüband\-Codedatei die folgenden Anweisungen hinzu.  Diese Anweisungen ermöglichen den einfachen Zugriff auf LINQ\-Namespaces und den Namespace der primären Interopassembly \(PIA\) von Outlook.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#1)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#1)]  
  
6.  Fügen Sie den folgenden Code in der Klasse "CustomerRibbon" hinzu.  Dieser Code deklariert die Datentabelle und die Tabellenadapter, die Sie zum Speichern von Informationen aus den Kunden\-, Bestellungen\-, Bestelldetails\- und Produkttabellen der Datenbank "Northwind" verwenden.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#2)]  
  
7.  Fügen Sie der Klasse `CustomerRibbon` den folgenden Codeblock hinzu.  Dieser Code fügt drei Hilfsmethoden hinzu, die zur Laufzeit Steuerelemente für das Menüband erstellen.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#3)]  
  
8.  Ersetzen Sie die `CustomerRibbon_Load`\-Ereignishandlermethode durch den folgenden Code.  Dieser Code verwendet eine LINQ\-Abfrage, um die folgenden Aufgaben auszuführen:  
  
    -   Auffüllen des Kombinationsfelds **Kunden** mithilfe der ID und dem Namen von 20 Kunden in der Datenbank "Northwind".  
  
    -   Aufrufen der Hilfsmethode `PopulateSalesOrderInfo`.  Diese Methode aktualisiert das Menü **ProductsPurchased** mit Bestellnummern, die den zurzeit ausgewählten Kunden betreffen.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#4)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#4)]  
  
9. Fügen Sie der `CustomerRibbon`\-Klasse folgenden Code hinzu.  Dieser Code verwendet LINQ\-Abfragen, um die folgenden Aufgaben auszuführen:  
  
    -   Hinzufügen eines Untermenüs zum Menü **ProductsPurchased** für jede Bestellung, die sich auf den ausgewählten Kunden bezieht.  
  
    -   Hinzufügen von Schaltflächen zu jedem Untermenü für die Produkte, die sich auf die Bestellung beziehen.  
  
    -   Hinzufügen von Ereignishandlern zu jeder Schaltfläche.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#6)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#6)]  
  
10. Doppelklicken Sie im **Projektmappen\-Explorer** auf die Menüband\-Codedatei.  
  
     Der Menüband\-Designer wird geöffnet.  
  
11. Doppelklicken Sie im Menüband\-Designer auf das Kombinationsfeld **Kunden**.  
  
     Die Menüband\-Codedatei wird im Code\-Editor geöffnet, und der `ComboBox1_TextChanged`\-Ereignishandler wird angezeigt.  
  
12. Ersetzen Sie den `ComboBox1_TextChanged`\-Ereignishandler durch den folgenden Code.  Mit diesem Code werden die folgenden Aufgaben ausgeführt:  
  
    -   Aufrufen der Hilfsmethode `PopulateSalesOrderInfo`.  Diese Methode aktualisiert das Menü **Gekaufte Produkte** mit Bestellungen, die den zurzeit ausgewählten Kunden betreffen.  
  
    -   Aufrufen der Hilfsmethode `PopulateMailItem` und Übergeben des aktuellen Texts, der den Namen des ausgewählten Kunden darstellt.  Diese Methode füllt die Felder To, Subject und Body neuer E\-Mail\-Nachrichten mit Daten auf.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#5)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#5)]  
  
13. Hinzufügen des folgenden Click\-Ereignishandlers zur Klasse `CustomerRibbon`.  Dieser Code fügt den Namen ausgewählter Produkte dem Feld Body neuer E\-Mail\-Nachrichten hinzu.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#8)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#8)]  
  
14. Fügen Sie der `CustomerRibbon`\-Klasse folgenden Code hinzu.  Mit diesem Code werden die folgenden Aufgaben ausgeführt:  
  
    -   Auffüllen der Zeile To neuer E\-Mail\-Nachrichten mithilfe der E\-Mail\-Adresse des aktuell ausgewählten Kunden.  
  
    -   Hinzufügen von Text zu den Feldern Subject und Body neuer E\-Mail\-Nachrichten.  
  
     [!code-csharp[Trin_Ribbon_Update_At_Runtime#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/CS/CustomerRibbon.cs#7)]
     [!code-vb[Trin_Ribbon_Update_At_Runtime#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Update_At_Runtime/VB/CustomerRibbon.vb#7)]  
  
## Testen der Steuerelemente in der benutzerdefinierten Gruppe  
 Wenn Sie ein neues E\-Mail\-Formular in Outlook öffnen, wird eine benutzerdefinierte Gruppe mit dem Namen **Kundenbestellungen** auf der Registerkarte **Nachrichten** des Menübands angezeigt.  
  
 Wählen Sie zum Erstellen einer Nachverfolgungs\-E\-Mail\-Nachricht für Kunden einen Kunden aus, und wählen Sie dann die vom Kunden erworbenen Produkte aus.  Die Steuerelemente in der Gruppe **Kundenbestellungen** werden zur Laufzeit mit Daten aus der Datenbank "Northwind" aktualisiert.  
  
#### So testen Sie die Steuerelemente in der benutzerdefinierten Gruppe  
  
1.  Drücken Sie F5, um das Projekt auszuführen.  
  
     Outlook wird gestartet.  
  
2.  Zeigen Sie in Outlook im Menü **Datei** auf **Neu**, und klicken Sie dann auf **E\-Mail\-Nachricht**.  
  
     Die folgenden Aktionen werden ausgeführt:  
  
    -   Eine neues Inspektor\-Fenster für E\-Mail\-Nachrichten wird angezeigt.  
  
    -   Auf der Registerkarte **Nachricht** des Menübands wird die Gruppe **Kundenbestellungen** vor der Gruppe **Zwischenablage** angezeigt.  
  
    -   Das Kombinationsfeld **Kunden** in der Gruppe wird mit den Namen der Kunden in der Datenbank "Northwind" aktualisiert.  
  
3.  Wählen Sie auf der Registerkarte **Nachricht** des Menübands in der Gruppe **Kundenbestellungen** einen Kunden aus dem Kombinationsfeld **Kunden** aus.  
  
     Die folgenden Aktionen werden ausgeführt:  
  
    -   Das Menü **Gekaufte Produkte** wird so aktualisiert, dass jede Bestellung für den ausgewählten Kunden angezeigt wird.  
  
    -   Jedes Bestellungsuntermenü wird so aktualisiert, dass die in der betreffenden Bestellung gekauften Produkte angezeigt werden.  
  
    -   Die E\-Mail\-Adresse des ausgewählten Kunden wird der Zeile **An** der E\-Mail\-Nachricht hinzugefügt, und der Betreff und der Nachrichtentext der E\-Mail\-Nachricht werden mit Text aufgefüllt.  
  
4.  Klicken Sie auf das Menü **Gekaufte Produkte**, zeigen Sie auf eine beliebige Bestellung, und klicken Sie dann auf ein Produkt aus der Bestellung.  
  
     Der Produktname wird dem Nachrichtentext der E\-Mail\-Nachricht hinzugefügt.  
  
## Nächste Schritte  
 Weitere Informationen zum Anpassen der Office\-Benutzeroberfläche finden Sie in diesen Themen:  
  
-   Fügen Sie jeder Anpassung auf Dokumentebene kontextbasierte Benutzeroberfläche hinzu.  Weitere Informationen zu Aktionsbereichen finden Sie unter [Aktionsbereichsübersicht](../vsto/actions-pane-overview.md).  
  
-   Erweitern Sie ein standardmäßiges oder benutzerdefiniertes Microsoft Office Outlook\-Formular.  Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Entwerfen eines Outlook-Formularbereichs](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
-   Hinzufügen eines benutzerdefinierten Aufgabenbereichs zu Outlook.  Weitere Informationen finden Sie unter [Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md).  
  
## Siehe auch  
 [Zugreifen auf die Multifunktionsleiste zur Laufzeit](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Übersicht über die Multifunktionsleiste](../vsto/ribbon-overview.md)   
 [Language\-Integrated Query \(LINQ\)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)   
 [Gewusst wie: Erste Schritte beim Anpassen der Multifunktionsleiste](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Multifunktionsleisten-Designer](../vsto/ribbon-designer.md)   
 [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit dem Multifunktionsleisten-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Multifunktionsleisten-Objektmodellübersicht](../vsto/ribbon-object-model-overview.md)   
 [Anpassen einer Multifunktionsleiste in Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Gewusst wie: Ändern der Position einer Registerkarte im Menüband](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Gewusst wie: Anpassen einer integrierten Registerkarte](../vsto/how-to-customize-a-built-in-tab.md)   
 [Gewusst wie: Hinzufügen von Steuerelementen zur Backstage-Ansicht](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Gewusst wie: Exportieren einer Multifunktionsleiste aus dem Multifunktionsleisten-Designer in Multifunktionsleisten-XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Gewusst wie: Anzeigen von Add-In-Benutzeroberflächenfehlern](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  