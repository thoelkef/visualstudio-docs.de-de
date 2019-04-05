---
title: Speichern von Daten in einer Transaktion | Microsoft-Dokumentation
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
- System.Transactions namespace
- data [Visual Studio], saving in a transaction
- transactions, saving data
- Transactions namespace
- saving data
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 48c8732f75f23a0d0b0929eeef8865044f19d27b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58946288"
---
# <a name="save-data-in-a-transaction"></a>Speichern von Daten in einer Transaktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie zum Speichern von Daten in einer Transaktion mithilfe der <xref:System.Transactions> Namespace. In diesem Beispiel werden die Tabellen `Customers` und `Orders` aus der Beispieldatenbank Northwind verwendet.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Für diese exemplarische Vorgehensweise wird die Beispieldatenbank Northwind benötigt.
  
## <a name="create-a-windows-application"></a>Erstellen Sie eine Windows-Anwendung  
 Der erste Schritt ist die Erstellung einer **Windows-Anwendung**.  
  
#### <a name="to-create-the-new-windows-project"></a>So erstellen Sie ein neues Windows-Projekt  
  
1.  In Visual Studio auf die **Datei** im Menü Erstellen Sie ein neues **Projekt**.  
  
2.  Nennen Sie das Projekt **SavingDataInATransactionWalkthrough**.  
  
3.  Wählen Sie **Windows-Anwendung**, und wählen Sie dann **OK**. Weitere Informationen finden Sie unter [Clientanwendungen](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     Das Projekt **SavingDataInATransactionWalkthrough** wird erstellt und zum **Projektmappen-Explorer** hinzugefügt.  
  
## <a name="create-a-database-data-source"></a>Erstellen einer Datenbank-Datenquelle  
 Dieser Schritt verwendet den [Assistenten zur Datenquellenkonfiguration](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) zum Erstellen einer Datenquelle basierend auf den `Customers` und `Orders` Tabellen in der Beispieldatenbank Northwind.  
  
#### <a name="to-create-the-data-source"></a>So erstellen Sie die Datenquelle  
  
1.  Auf der **Daten** , wählen Sie im Menü**Datenquellen anzeigen**.  
  
2.  Wählen Sie im **Datenquellenfenster** die Option **Neue Datenquelle hinzufügen** aus, um den **Assistenten zum Konfigurieren von Datenquellen** zu starten.  
  
3.  Auf der **wählen Sie einen Datenquellentyp**auf **Datenbank**, und wählen Sie dann **Weiter**.  
  
4.  Auf der **wählen Sie Ihre Datenverbindung**Bildschirm führen Sie einen der folgenden:  
  
    -   Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.  
  
         - oder -   
  
    -   Klicken Sie auf **neue Verbindung**, um das Dialogfeld **Add/Modify Connection** (Verbindung hinzufügen/ändern) zu starten und eine Verbindung mit der Datenbank Northwind herzustellen.  
  
5.  Wenn Ihre Datenbank ein Kennwort erfordert, wählen Sie die Option Einbeziehung vertraulicher Daten, und wählen Sie dann **Weiter**.  
  
6.  Auf der **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern** auf **Weiter**.  
  
7.  Auf der **Datenbankobjekte auswählen** Bildschirm, erweitern Sie die **Tabellen** Knoten.  
  
8.  Wählen Sie die `Customers` und `Orders` Tabellen, und wählen Sie dann **Fertig stellen**.  
  
     Das **NorthwindDataSet** wird Ihrem Projekt hinzugefügt, und die Tabellen `Customers` und `Orders` werden im Fenster **Datenquellen** angezeigt.  
  
## <a name="addcontrols-to-the-form"></a>Addcontrols zum Formular  
 Sie können die datengebundenen Steuerelemente erstellen, indem Sie Elemente aus dem Fenster **Datenquellen** auf das Formular ziehen.  
  
#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>So erstellen Sie datengebundene Steuerelemente auf dem Windows-Formular  
  
-   In der **Datenquellen** Fenster, erweitern Sie die **Kunden** Knoten.  
  
-   Ziehen Sie den Hauptknoten **Customers** aus dem Fenster **Datenquellen** auf **Form1**.  
  
     Auf dem Formular wird ein <xref:System.Windows.Forms.DataGridView>-Steuerelement und ein Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) für die Navigation in den Datensätzen angezeigt. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> und <xref:System.Windows.Forms.BindingNavigator> werden auf der Komponentenleiste angezeigt.  
  
-   Ziehen Sie den zugehörigen **Bestellungen** Knoten (nicht der Hauptknoten **Bestellungen** Knoten, aber die verknüpfte untergeordnete Tabellenknoten unter der **Fax** Spalte) auf das Formular unten die  **CustomersDataGridView**.  
  
     Ein <xref:System.Windows.Forms.DataGridView> wird auf dem Formular angezeigt. OrdersTableAdapter und <xref:System.Windows.Forms.BindingSource> werden in der Komponentenleiste angezeigt.  
  
## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>Fügen Sie einen Verweis zur Assembly System.Transactions  
 Transaktionen verwenden den Namespace <xref:System.Transactions>. Ein Projektverweis zur Assembly System.Transactions wird standardmäßig nicht hinzugefügt werden, sodass Sie sie manuell hinzufügen müssen.  
  
#### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>So fügen Sie einen Verweis zur DLL-Datei System.Transactions hinzu  
  
1.  Auf der **Projekt** , wählen Sie im Menü**Verweis hinzufügen**.  
  
2.  Wählen Sie **System.Transactions**(auf der **.NET** Registerkarte), und wählen Sie dann **OK**.  
  
     Dem Projekt wird ein Verweis auf **System.Transactions** hinzugefügt.  
  
## <a name="modifythe-code-in-the-bindingnavigators-saveitem-button"></a>Modifythe-Code in die SaveItem-Schaltfläche  
 Für die erste auf dem Formular abgelegte Tabelle Code hinzugefügt, werden standardmäßig die `click` Ereignis speichern-Schaltfläche auf der <xref:System.Windows.Forms.BindingNavigator>. Sie müssen für das Ändern weiterer Tabellen den Code manuell hinzufügen. In dieser exemplarischen Vorgehensweise gestalten wir den vorhandenen speichern-Code aus der Save-click-Ereignishandler der Schaltfläche. Außerdem erstellen wir ein paar weitere Methoden zum Bereitstellen von spezifische änderungsfunktionalität basierend auf, ob die Zeile hinzugefügt oder gelöscht werden muss.  
  
#### <a name="to-modify-the-auto-generated-save-code"></a>So ändern Sie automatisch generierten Speichern-Code  
  
1. Wählen Sie die **speichern** Schaltfläche der **CustomersBindingNavigator** (die Schaltfläche mit dem Diskettensymbol).  
  
2. Ersetzen Sie die `CustomersBindingNavigatorSaveItem_Click`-Methode durch folgenden Code:  
  
    [!code-csharp[VbRaddataSaving#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#4)]
    [!code-vb[VbRaddataSaving#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#4)]  
  
   Der Befehl für das Abgleichen zugehöriger Daten lautet wie folgt:  
  
-   Löschen Sie untergeordnete Datensätze. (In diesem Fall Löschen von Datensätzen aus der `Orders` Tabelle.)  
  
-   Löschen Sie übergeordnete Datensätze. (In diesem Fall Löschen von Datensätzen aus der `Customers` Tabelle.)  
  
-   Übergeordnete Datensätze einfügen. (In diesem Fall Einfügen von Datensätzen in der `Customers` Tabelle.)  
  
-   Untergeordnete Datensätze einfügen. (In diesem Fall Einfügen von Datensätzen in der `Orders` Tabelle.)  
  
#### <a name="to-delete-existing-orders"></a>So löschen Sie eine vorhandene Bestellungen  
  
-   Fügen Sie die folgende Methode `DeleteOrders` zu **Form1** hinzu:  
  
     [!code-csharp[VbRaddataSaving#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#5)]
     [!code-vb[VbRaddataSaving#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#5)]  
  
#### <a name="to-delete-existing-customers"></a>So löschen Sie eine vorhandene Kunden  
  
-   Fügen Sie die folgende Methode `DeleteCustomers` zu **Form1** hinzu:  
  
     [!code-csharp[VbRaddataSaving#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#6)]
     [!code-vb[VbRaddataSaving#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#6)]  
  
#### <a name="to-add-new-customers"></a>Neue Kunden hinzufügen  
  
-   Fügen Sie die folgende Methode `AddNewCustomers` zu **Form1** hinzu:  
  
     [!code-csharp[VbRaddataSaving#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#7)]
     [!code-vb[VbRaddataSaving#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#7)]  
  
#### <a name="to-add-new-orders"></a>Neue Bestellungen hinzufügen  
  
-   Fügen Sie die folgende Methode `AddNewOrders` zu **Form1** hinzu:  
  
     [!code-csharp[VbRaddataSaving#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#8)]
     [!code-vb[VbRaddataSaving#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#8)]  
  
## <a name="run-the-application"></a>Ausführen der Anwendung  
  
#### <a name="to-run-the-application"></a>So führen Sie die Anwendung aus  
  
-   Wählen Sie **F5** zum Ausführen der Anwendung.  
  
## <a name="see-also"></a>Siehe auch  
 [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)
