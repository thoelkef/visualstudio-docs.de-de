---
title: "Exemplarische Vorgehensweise: Speichern von Daten mit den TableAdapter-DBDirect-Methoden | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Daten [Visual Studio], Speichern"
  - "Daten [Visual Studio], TableAdapter"
  - "Speichern von Daten, Exemplarische Vorgehensweisen"
  - "TableAdapters, Exemplarische Vorgehensweisen"
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
caps.latest.revision: 14
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Exemplarische Vorgehensweise: Speichern von Daten mit den TableAdapter-DBDirect-Methoden
Diese exemplarische Vorgehensweise enthält detaillierte Anweisungen für das Ausführen von SQL\-Anweisungen direkt an einer Datenbank mithilfe von DBDirect\-Methoden eines TableAdapters.  Die DBDirect\-Methoden eines TableAdapters bieten ein sehr gutes Maß an Kontrolle über Änderungen an der Datenbank.  Damit können sie spezifische SQL\-Anweisung und gespeicherter Prozeduren ausführen, indem Sie einzelne `Insert`\-, `Update`\- und `Delete`\-Methoden aufrufen, ganz nach Bedarf der Anwendung \(im Gegensatz zur überladenen `Update`\-Methode, die die Anweisungen UPDATE, INSERT und DELETE in einem Aufruf ausführt\).  
  
 Bei dieser exemplarischen Vorgehensweise lernen Sie Folgendes:  
  
-   Erstellen Sie eine neue **Windows\-Anwendung**.  
  
-   Erstellen und Konfigurieren eines Datasets mit dem [Assistent zum Konfigurieren von Datenquellen](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Wählen Sie das Steuerelement aus, das für das Formular erstellt werden soll, wenn Elemente aus dem **Datenquellenfenster** gezogen werden.  Weitere Informationen finden Sie unter [Festlegen des Steuerelements, das beim Ziehen aus dem Datenquellenfenster erstellt werden soll](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Erstellen eines datengebundenen Formulars durch Ziehen von Elementen aus dem **Datenquellenfenster** auf das Formular.  
  
-   Hinzufügen von Methoden für den direkten Zugriff auf die Datenbank und das Durchführen von Einfügungen, Aktualisierung und Löschungen direkt an der Datenbank.  
  
## Vorbereitungsmaßnahmen  
 Für die Durchführung dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:  
  
-   Zugriff auf die Beispieldatenbank Northwind.  Weitere Informationen finden Sie unter [Gewusst wie: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
## Erstellen einer Windows\-Anwendung  
 Im ersten Schritt wird eine **Windows\-Anwendung** erstellt.  
  
#### So erstellen Sie ein neues Windows\-Projekt  
  
1.  Erstellen Sie in Visual Studio im Menü **Datei** ein neues **Projekt**.  
  
2.  Geben Sie dem Projekt den Namen TableAdapterDbDirectMethodsWalkthrough.  
  
3.  Wählen Sie **Windows\-Anwendung** aus, und klicken Sie auf **OK**.  Weitere Informationen finden Sie unter [Clientanwendungen](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Das Projekt **TableAdapterDbDirectMethodsWalkthrough** wird erstellt und zum **Projektmappen\-Explorer** hinzugefügt.  
  
## Erstellen einer Datenquelle aus einer Datenbank  
 Dieser Schritt verwendet den **Assistenten zum Konfigurieren von Datenquellen** auf Grundlage der `Region`\-Tabelle in der Beispieldatenbank Northwind.  Sie benötigen Zugriff auf die Beispieldatenbank Northwind, um die Verbindung herstellen zu können.  Informationen zum Einrichten der Beispieldatenbank Northwind finden Sie unter [Gewusst wie: Installieren von Beispieldatenbanken](../data-tools/how-to-install-sample-databases.md).  
  
#### So erstellen Sie die Datenquelle  
  
1.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.  
  
2.  Wählen Sie im **Datenquellenfenster** die Option **Neue Datenquelle hinzufügen** aus, um den **Assistenten zum Konfigurieren von Datenquellen** zu starten.  
  
3.  Wählen Sie auf der Seite **Datenquellentyp auswählen** die Option **Datenbank** aus, und klicken Sie auf **Weiter**.  
  
4.  Führen Sie auf der Seite **Wählen Sie Ihre Datenverbindung** einen der folgenden Schritte aus:  
  
    -   Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank "Northwind" verfügbar ist, wählen Sie diese aus.  
  
         \- oder \-  
  
    -   Wählen Sie **Neue Verbindung**, um das Dialogfeld **Verbindung hinzufügen\/ändern** zu öffnen.  
  
5.  Falls die Datenbank ein Kennwort erfordern sollte, aktivieren Sie die Option für die Einbeziehung vertraulicher Daten, und klicken Sie dann auf **Weiter**.  
  
6.  Klicken Sie auf der Seite **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern** auf **Weiter**.  
  
7.  Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen**.  
  
8.  Wählen Sie die `Region`\-Tabelle und klicken Sie anschließend auf **Fertig stellen**.  
  
     **NorthwindDataSet** wird dem Projekt hinzugefügt. Die Tabelle `Region` wird im **Datenquellenfenster** angezeigt.  
  
## Hinzufügen von Steuerelementen zum Formular für das Anzeigen der Daten  
 Erstellen Sie die datengebundenen Steuerelemente, indem Sie Elemente aus dem **Datenquellenfenster** auf das Formular ziehen.  
  
#### So erstellen Sie datengebundene Steuerelemente auf dem Windows Form  
  
-   Ziehen Sie den Hauptknoten **Region** aus dem **Datenquellenfenster** auf das Formular.  
  
     Auf dem Formular wird ein <xref:System.Windows.Forms.DataGridView>\-Steuerelement und ein Toolstrip \(<xref:System.Windows.Forms.BindingNavigator>\) für die Navigation in den Datensätzen angezeigt.  Es wird eine [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [RegionTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> sowie eine <xref:System.Windows.Forms.BindingNavigator> auf der Komponentenleiste angezeigt.  
  
#### Hinzufügen von Schaltflächen, die die einzelnen TableAdapter DbDirect\-Methoden aufruft  
  
1.  Ziehen Sie drei <xref:System.Windows.Forms.Button>\-Steuerelemente von der **Symbolleiste** auf **Form1** \(unter **RegionDataGridView**\).  
  
2.  Legen Sie die folgenden Eigenschaften für **Name** und **Text** auf jeder Schaltfläche fest.  
  
    |Name|Text|  
    |----------|----------|  
    |`InsertButton`|Insert|  
    |`UpdateButton`|Aktualisieren|  
    |`DeleteButton`|Löschen|  
  
#### Hinzufügen von Code für das Einfügen neuer Datensätze in die Datenbank  
  
1.  Doppelklicken Sie **InsertButton**, sodass ein Ereignishandler für Click\-Ereignis erstellt wird und öffnen Sie das Formular im Code\-Editor.  
  
2.  Ersetzen Sie den Ereignishandler `InsertButton_Click`durch den folgenden Code:  
  
     [!code-vb[VbRaddataSaving#1](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_1.vb)]
     [!code-cs[VbRaddataSaving#1](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_1.cs)]  
  
#### Hinzufügen von Code für die Aktualisierung von Datensätzen in der Datenbank  
  
1.  Doppelklicken Sie **UpdateButton**, sodass ein Ereignishandler für Click\-Ereignis erstellt wird und öffnen Sie das Formular im Code\-Editor.  
  
2.  Ersetzen Sie den Ereignishandler `UpdateButton_Click`durch den folgenden Code:  
  
     [!code-vb[VbRaddataSaving#2](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_2.vb)]
     [!code-cs[VbRaddataSaving#2](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_2.cs)]  
  
#### Hinzufügen von Code für das Löschen von Datensätzen in der Datenbank  
  
1.  Doppelklicken Sie **DeleteButton**, sodass ein Ereignishandler für Click\-Ereignis erstellt wird und öffnen Sie das Formular im Code\-Editor.  
  
2.  Ersetzen Sie den Ereignishandler `DeleteButton_Click`durch den folgenden Code:  
  
     [!code-vb[VbRaddataSaving#3](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_3.vb)]
     [!code-cs[VbRaddataSaving#3](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_3.cs)]  
  
## Ausführen der Anwendung  
  
#### So führen Sie die Anwendung aus  
  
-   Drücken Sie F5, um die Anwendung auszuführen.  
  
-   Klicken Sie die Schaltfläche **Einfügen** und stellen Sie sicher, dass der neue Datensatz im Raster angezeigt wird.  
  
-   Klicken Sie die Schaltfläche **Aktualisieren** und stellen Sie sicher, dass der Datensatz im Raster aktualisiert wurde.  
  
-   Klicken Sie die Schaltfläche **Löschen** und stellen Sie sicher, dass der Datensatz aus dem Raster entfernt wurde.  
  
## Nächste Schritte  
 Entsprechend den Anforderungen an Ihre Anwendung können Sie nach der Erstellung eines datengebundenen Formulars noch weitere Schritte ausführen.  Sie können an dieser exemplarischen Vorgehensweise beispielsweise folgende Verbesserungen vornehmen:  
  
-   Fügen Sie dem Formular Suchfunktionalität hinzu.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen einer parametrisierten Abfrage zu einem Formular in einer Windows Forms\-Anwendung](../Topic/How%20to:%20Add%20a%20Parameterized%20Query%20to%20a%20Windows%20Forms%20Application.md).  
  
-   Hinzufügen weiterer Tabellen zum Dataset durch Auswählen von **DataSet mit Assistent konfigurieren** aus dem **Datenquellenfenster**.  Sie können Steuerelemente hinzufügen, die zugehörige Daten anzeigen, indem Sie die entsprechenden Knoten auf das Formular ziehen.  Weitere Informationen finden Sie unter [Gewusst wie: Anzeigen von verknüpften Daten in einer Windows Forms\-Anwendung](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md).  
  
## Siehe auch  
 [Übersicht über TableAdapters](../data-tools/tableadapter-overview.md)   
 [Gewusst wie: Direktes Zugreifen auf die Datenbank mit einem TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)   
 [Gewusst wie: Erstellen von TableAdapter\-Abfragen](../data-tools/how-to-create-tableadapter-queries.md)   
 [Gewusst wie: Speichern von Daten aus einem Objekt in einer Datenbank](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Binden von Windows Forms\-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Herstellen von Datenverbindungen in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung auf den Empfang von Daten](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Abrufen von Daten für die Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in der Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](../Topic/Validating%20Data.md)   
 [Speichern von Daten](../data-tools/saving-data.md)