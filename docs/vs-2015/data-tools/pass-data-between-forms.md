---
title: Übergeben von Daten zwischen Formularen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- walkthroughs [Windows Forms], data
- walkthroughs [Visual Studio], data
- data [Visual Studio], passing between forms
- forms, passing data between
- Windows Forms, walkthroughs
ms.assetid: 78bf038b-9296-4fbf-b0e8-d881d1aff0df
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 27d4b1ec935444009be1f85f4c1ad95f9da91f68
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63425499"
---
# <a name="pass-data-between-forms"></a>Übergeben von Daten zwischen Formularen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese exemplarische Vorgehensweise enthält eine Schritt-für-Schritt-Anleitung für die Datenübergabe von einem Formular zum anderen. Verwenden die Tabellen Customers und Orders von Northwind, ein Formular ermöglicht Benutzern, um einen Kunden auszuwählen, und eine zweite Form zeigt die ausgewählte Bestellungen des Kunden. In dieser exemplarischen Vorgehensweise zeigt, wie Sie eine Methode auf das zweite Formular erstellen, die Daten aus dem ersten Formular empfängt.  
  
> [!NOTE]
> Diese exemplarische Vorgehensweise zeigt nur eine Möglichkeit der Datenübergabe zwischen Formularen. Es gibt andere Optionen zum Übergeben von Daten zu einem Formular, einschließlich der Erstellung eines zweiten Konstruktors, um Daten zu erhalten, oder erstellen eine öffentliche Eigenschaft, die mit Daten aus dem ersten Formular festgelegt werden.  
  
 In dieser exemplarischen Vorgehensweise werden u. a. folgende Aufgaben veranschaulicht:  
  
- Erstellen eines neuen **Windows-Anwendung** Projekt.  
  
- Erstellen und Konfigurieren eines Datasets mithilfe der [Assistenten zur Datenquellenkonfiguration](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
- Auswählen des Steuerelements, das für das Formular erstellt werden soll, wenn Elemente aus dem **Datenquellenfenster** gezogen werden. Weitere Informationen finden Sie unter [legen Sie das Steuerelement erstellt werden, beim Ziehen aus Datenquellenfenster](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
- Erstellen eines datengebundenen Steuerelements durch Ziehen von Elementen aus dem **Datenquellenfenster** auf das Formular.  
  
- Erstellen eines zweiten Formulars mit einem Raster für die Datenanzeige.  
  
- Erstellen einer TableAdapter-Abfrage für das Abrufen der Bestellungen eines bestimmten Kunden.  
  
- Übergeben von Daten zwischen Formularen.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Für die Durchführung dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:  
  
- Zugriff auf die Beispieldatenbank Northwind.
  
## <a name="create-the-windows-application"></a>Erstellen Sie die Windows-Anwendung  
  
#### <a name="to-create-the-new-windows-project"></a>So erstellen Sie ein neues Windows-Projekt  
  
1. Von der **Datei** Menü ein neues Projekt erstellen.  
  
2. Benennen Sie das Projekt mit `PassingDataBetweenForms`.  
  
3. Wählen Sie **Windows Forms-Anwendung**, und klicken Sie auf **OK**. Weitere Informationen finden Sie unter [Clientanwendungen](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     Das Projekt **PassingDataBetweenForms** wird erstellt und zum **Projektmappen-Explorer** hinzugefügt.  
  
## <a name="create-the-data-source"></a>Erstellen der Datenquelle  
  
#### <a name="to-create-the-data-source"></a>So erstellen Sie die Datenquelle  
  
1. Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**.  
  
2. Klicken Sie im **Datenquellenfenster** auf **Neue Datenquelle hinzufügen**, um den **Assistenten zum Konfigurieren von Datenquellen** zu starten.  
  
3. Wählen Sie auf der Seite **Datenquellentyp auswählen** die Option **Datenbank** aus, und klicken Sie auf **Weiter**.  
  
4. Stellen Sie sicher, dass **Dataset** auf der Seite **Datenbankmodell auswählen** festgelegt ist, und klicken Sie dann auf **Weiter**.  
  
5. Führen Sie auf der Seite **Wählen Sie Ihre Datenverbindung aus** einen der folgenden Schritte aus:  
  
    - Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.  
  
    - Klicken Sie auf **Neue Verbindung**, um das Dialogfeld **Add/Modify Connection** (Verbindung hinzufügen/ändern) zu öffnen.  
  
6. Falls die Datenbank ein Kennwort erfordern sollte und die Option für die Einbeziehung vertraulicher Daten aktiviert ist, wählen Sie die Option aus, und klicken Sie dann auf **Weiter**.  
  
7. Klicken Sie auf der Seite **Save connection string to the Application Configuration file** (Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern) auf **Weiter**.  
  
8. Erweitern Sie auf der Seite **Datenbankobjekte auswählen** den Knoten **Tabellen**.  
  
9. Wählen Sie die Tabellen **Customers** und **Orders** aus, und klicken Sie dann auf **Fertig stellen**.  
  
     Das **NorthwindDataSet** wird dem Projekt hinzugefügt, und die Tabellen **Customers** und **Orders** werden im **Datenquellenfenster** angezeigt.  
  
## <a name="create-the-first-form-form1"></a>Erstellen Sie das erste Formular (Form1)  
 Sie können ein datengebundenes Raster erstellen (ein <xref:System.Windows.Forms.DataGridView>-Steuerelement), indem Sie den Knoten **Customers** aus dem **Datenquellenfenster** auf das Formular ziehen.  
  
#### <a name="to-create-a-data-bound-grid-on-the-form"></a>So erstellen Sie ein datengebundenes Raster auf dem Formular  
  
- Ziehen Sie den Hauptknoten **Customers** aus dem Fenster **Datenquellen** auf **Form1**.  
  
     Eine <xref:System.Windows.Forms.DataGridView> und eine Toolleiste (<xref:System.Windows.Forms.BindingNavigator>) zum Navigieren durch Datensätze wird auf **Form1** angezeigt. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> und <xref:System.Windows.Forms.BindingNavigator> werden auf der Komponentenleiste angezeigt.  
  
## <a name="create-the-second-form-form2"></a>Erstellen Sie das zweite Formular (Form2)  
  
#### <a name="to-create-a-second-form-to-pass-the-data-to"></a>Erstellen eines zweiten Formulars, an das die Daten übergeben werden  
  
1. Wählen Sie aus dem Menü **Projekt** die Option **Windows Form hinzufügen** aus.  
  
2. Übernehmen Sie den Standardnamen **Form2**, und klicken Sie auf **Hinzufügen**.  
  
3. Ziehen Sie den Hauptknoten **Orders** aus dem **Datenquellenfenster** auf **Form2**.  
  
     Eine <xref:System.Windows.Forms.DataGridView> und eine Toolleiste (<xref:System.Windows.Forms.BindingNavigator>) zum Navigieren durch Datensätze wird auf **Form2** angezeigt. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> und <xref:System.Windows.Forms.BindingNavigator> werden auf der Komponentenleiste angezeigt.  
  
4. Löschen Sie **OrdersBindingNavigator** aus der Komponentenleiste.  
  
     **OrdersBindingNavigator** wird von **Form2** entfernt.  
  
## <a name="add-a-tableadapter-query-to-form2-to-load-orders-for-the-selected-customer-on-form1"></a>Hinzufügen einer TableAdapter-Abfrage zu Form2 für das Laden der Bestellungen für den ausgewählten Kunden auf Form1  
  
#### <a name="to-create-a-tableadapter-query"></a>Zum Erstellen einer TableAdapter-Abfrage  
  
1. Doppelklicken Sie im **Projektmappen-Explorer** auf die Datei **NorthwindDataSet.xsd**.  
  
2. Klicken Sie mit der rechten Maustaste auf **OrdersTableAdapter**, und wählen Sie **Abfrage hinzufügen** aus.  
  
3. Übernehmen Sie die Standardeinstellung für **SQL-Anweisung verwenden**, und klicken Sie anschließend auf **Weiter**.  
  
4. Übernehmen Sie die Standardeinstellung für **SELECT-Anweisung, die Zeilen zurückgibt**, und klicken Sie anschließend auf **Weiter**.  
  
5. Fügen Sie eine WHERE-Klausel zur Abfrage hinzu, sodass `Orders` auf Grundlage der `CustomerID` zurückgeben wird. Die Abfrage müsste ungefähr wie folgt aussehen:  
  
    ```  
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry  
    FROM Orders   
    WHERE CustomerID = @CustomerID  
    ```  
  
    > [!NOTE]
    > Überprüfen Sie die korrekte Parametersyntax für Ihre Datenbank. In Microsoft Access würde die WHERE-Klausel wie folgt aussehen: `WHERE CustomerID = ?`.  
  
6. Klicken Sie auf **Weiter**.  
  
7. Für die **Geben Sie einen Namen für die DataTableMethod**, Typ `FillByCustomerID`.  
  
8. Löschen Sie die Option **DataTable zurückgeben**, und klicken Sie anschließend **Weiter**.  
  
9. Klicken Sie auf **Fertig stellen**.  
  
## <a name="create-a-method-on-form2-to-pass-data-to"></a>Erstellen Sie eine Methode auf Form2 für das Übergeben von Daten an  
  
#### <a name="to-create-a-method-to-pass-data-to"></a>Erstellen einer Methode für das Übergeben von Daten an  
  
1. Klicken Sie mit der rechten Maustaste auf **Form2**, und klicken Sie auf **Code anzeigen**, um **Form2** im **Code-Editor** zu öffnen.  
  
2. Fügen Sie den folgenden Code zu **Form2** nach der `Form2_Load`-Methode hinzu:  
  
     [!code-csharp[VbRaddataDisplaying#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form2.cs#1)]
     [!code-vb[VbRaddataDisplaying#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form2.vb#1)]  
  
## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>Erstellen Sie eine Methode auf Form1 für das Übergeben von Daten und Anzeigen von Form2  
  
#### <a name="to-create-a-method-to-pass-data-to-form2"></a>Erstellen einer Methode für das Übergeben von Daten an Form2  
  
1. Klicken Sie in **Form1** mit der rechten Maustaste auf das Customer-Datenraster, und klicken Sie dann auf **Eigenschaften**.  
  
2. Klicken Sie im Fenster **Eigenschaften** auf **Ereignisse**.  
  
3. Doppelklicken Sie das Ereignis **CellDoubleClick**.  
  
     Der Code-Editor wird angezeigt.  
  
4. Aktualisieren Sie die Methodendefinition, sodass sie dem folgenden Beispiel entspricht:  
  
     [!code-csharp[VbRaddataDisplaying#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#2)]
     [!code-vb[VbRaddataDisplaying#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#2)]  
  
## <a name="run-the-application"></a>Ausführen der Anwendung  
  
#### <a name="to-run-the-application"></a>So führen Sie die Anwendung aus  
  
- Drücken Sie F5, um die Anwendung auszuführen.  
  
- Doppelklicken Sie einen Kundendatensatz in **Form1**, sodass dieser in **Form2** mit den Bestellungen dieses Kunden geöffnet wird.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Entsprechend den Anforderungen an Ihre Anwendung können Sie nach dem Übergeben der Daten zwischen den Formularen noch weitere Schritte ausführen. Sie können an dieser exemplarischen Vorgehensweise beispielsweise folgende Verbesserungen vornehmen:  
  
- Hinzufügen oder Entfernen von Datenbankobjekten aus dem Dataset durch Bearbeiten. Weitere Informationen finden Sie unter [Erstellen und Konfigurieren von Datasets in Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
- Hinzufügen einer Funktion für das Zurückspeichern von Daten in der Datenbank. Weitere Informationen finden Sie unter [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
