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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b30f51da001c62166a97c954b1416e35fd8b540f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671091"
---
# <a name="save-data-in-a-transaction"></a>Speichern von Daten in einer Transaktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Daten mithilfe des <xref:System.Transactions>-Namespace in einer Transaktion gespeichert werden. In diesem Beispiel werden die Tabellen `Customers` und `Orders` aus der Beispieldatenbank Northwind verwendet.

## <a name="prerequisites"></a>Erforderliche Voraussetzungen
 Für diese exemplarische Vorgehensweise wird die Beispieldatenbank Northwind benötigt.

## <a name="create-a-windows-application"></a>Erstellen einer Windows-Anwendung
 Der erste Schritt besteht darin, eine **Windows-Anwendung**zu erstellen.

#### <a name="to-create-the-new-windows-project"></a>So erstellen Sie ein neues Windows-Projekt

1. Erstellen Sie in Visual Studio im Menü **Datei** ein neues **Projekt**.

2. Nennen Sie das Projekt **SavingDataInATransactionWalkthrough**.

3. Wählen Sie **Windows-Anwendung**aus, und klicken Sie dann auf **OK**. Weitere Informationen finden Sie unter [Client Anwendungen](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Das Projekt **SavingDataInATransactionWalkthrough** wird erstellt und zum **Projektmappen-Explorer** hinzugefügt.

## <a name="create-a-database-data-source"></a>Erstellen einer Datenbank-Datenquelle
 In diesem Schritt wird mithilfe des [Assistenten zum Konfigurieren von Datenquellen](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) eine Datenquelle erstellt, die auf den `Customers`-und `Orders` Tabellen in der Beispieldatenbank Northwind basiert.

#### <a name="to-create-the-data-source"></a>So erstellen Sie die Datenquelle

1. Wählen Sie im Menü **Daten** die Option**Datenquellen anzeigen**aus.

2. Wählen Sie im Fenster **Datenquellen** die Option **Neue Datenquelle hinzufügen** aus, um den **Assistenten zum Konfigurieren von Datenquellen** zu starten.

3. Wählen Sie auf dem Bildschirm **Daten Quellentyp auswählen**die Option **Datenbank**aus, und klicken Sie dann auf **weiter**.

4. Führen Sie auf dem Bildschirm **Wählen Sie Ihre Datenverbindung**einen der folgenden Schritte aus:

    - Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.

         - oder -

    - Klicken Sie auf **neue Verbindung**, um das Dialogfeld **Add/Modify Connection** (Verbindung hinzufügen/ändern) zu starten und eine Verbindung mit der Datenbank Northwind herzustellen.

5. Wenn für die Datenbank ein Kennwort erforderlich ist, wählen Sie die Option zum einschließen sensibler Daten aus, und klicken Sie dann auf **weiter**.

6. Wählen Sie auf der Seite **Verbindungs Zeichenfolge in der Anwendungs Konfigurationsdatei speichern** die Option **weiter**aus.

7. Erweitern Sie auf dem Bildschirm **Wählen Sie Ihre Datenbankobjekte** aus den Knoten **Tabellen** .

8. Wählen Sie die Tabellen `Customers` und `Orders` aus, und klicken Sie dann auf **Fertig**stellen.

     Das **NorthwindDataSet** wird Ihrem Projekt hinzugefügt, und die Tabellen `Customers` und `Orders` werden im Fenster **Datenquellen** angezeigt.

## <a name="addcontrols-to-the-form"></a>Addcontrols zum Formular
 Sie können die datengebundenen Steuerelemente erstellen, indem Sie Elemente aus dem Fenster **Datenquellen** auf das Formular ziehen.

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>So erstellen Sie Daten gebundene Steuerelemente auf dem Windows Form

- Erweitern Sie im Fenster **Datenquellen** den Knoten **Customers** .

- Ziehen Sie den Hauptknoten **Customers** aus dem Fenster **Datenquellen** auf **Form1**.

     Auf dem Formular wird ein <xref:System.Windows.Forms.DataGridView>-Steuerelement und ein Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) für die Navigation in den Datensätzen angezeigt. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> und <xref:System.Windows.Forms.BindingNavigator> werden auf der Komponentenleiste angezeigt.

- Ziehen Sie den zugehörigen Knoten **Orders** (nicht den Haupt Knoten **Orders** , sondern den zugehörigen untergeordneten Tabellen Knoten unterhalb der Spalte **Fax** ) auf das Formular unterhalb von **CustomersDataGridView**.

     Ein <xref:System.Windows.Forms.DataGridView> wird auf dem Formular angezeigt. Ein OrdersTableAdapter und <xref:System.Windows.Forms.BindingSource> werden in der Komponenten Leiste angezeigt.

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>Fügen Sie einen Verweis auf die System. Transactions-Assembly hinzu.
 Transaktionen verwenden den Namespace <xref:System.Transactions>. Ein Projekt Verweis auf die System. Transactions-Assembly wird standardmäßig nicht hinzugefügt, daher müssen Sie Sie manuell hinzufügen.

#### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>So fügen Sie einen Verweis zur DLL-Datei System.Transactions hinzu

1. Wählen Sie im Menü **Projekt** die Option**Verweis hinzufügen**aus.

2. Wählen Sie auf der Registerkarte **.net** die Option **System. Transactions**aus, und klicken Sie dann auf **OK**.

     Dem Projekt wird ein Verweis auf **System.Transactions** hinzugefügt.

## <a name="modifythe-code-in-the-bindingnavigators-saveitem-button"></a>Ändern Sie den Code in der Schaltfläche "SaveItem" von BindingNavigator.
 Für die erste Tabelle, die auf dem Formular abgelegt wird, wird standardmäßig Code dem `click`-Ereignis der Schaltfläche Speichern auf der <xref:System.Windows.Forms.BindingNavigator> hinzugefügt. Sie müssen für das Ändern weiterer Tabellen den Code manuell hinzufügen. In dieser exemplarischen Vorgehensweise wird der vorhandene Save-Code aus dem Click-Ereignishandler der Schaltfläche "Save" umgestalten. Wir erstellen außerdem einige weitere Methoden, um bestimmte Aktualisierungs Funktionen bereitzustellen, je nachdem, ob die Zeile hinzugefügt oder gelöscht werden muss.

#### <a name="to-modify-the-auto-generated-save-code"></a>So ändern Sie automatisch generierten Speichern-Code

1. Wählen Sie im **CustomersBindingNavigator** die Schaltfläche **Speichern** aus (die Schaltfläche mit dem Diskettensymbol).

2. Ersetzen Sie die `CustomersBindingNavigatorSaveItem_Click`-Methode durch folgenden Code:

    [!code-csharp[VbRaddataSaving#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#4)]
    [!code-vb[VbRaddataSaving#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#4)]

   Der Befehl für das Abgleichen zugehöriger Daten lautet wie folgt:

- Löschen Sie untergeordnete Datensätze. (Löschen Sie in diesem Fall Datensätze aus der `Orders` Tabelle.)

- Löschen Sie übergeordnete Datensätze. (Löschen Sie in diesem Fall Datensätze aus der `Customers` Tabelle.)

- Übergeordnete Datensätze einfügen. (Fügen Sie in diesem Fall Datensätze in die `Customers` Tabelle ein.)

- Untergeordnete Datensätze einfügen. (Fügen Sie in diesem Fall Datensätze in die `Orders` Tabelle ein.)

#### <a name="to-delete-existing-orders"></a>So löschen Sie eine vorhandene Bestellungen

- Fügen Sie die folgende Methode `DeleteOrders` zu **Form1** hinzu:

     [!code-csharp[VbRaddataSaving#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#5)]
     [!code-vb[VbRaddataSaving#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#5)]

#### <a name="to-delete-existing-customers"></a>So löschen Sie eine vorhandene Kunden

- Fügen Sie die folgende Methode `DeleteCustomers` zu **Form1** hinzu:

     [!code-csharp[VbRaddataSaving#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#6)]
     [!code-vb[VbRaddataSaving#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#6)]

#### <a name="to-add-new-customers"></a>Neue Kunden hinzufügen

- Fügen Sie die folgende Methode `AddNewCustomers` zu **Form1** hinzu:

     [!code-csharp[VbRaddataSaving#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#7)]
     [!code-vb[VbRaddataSaving#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#7)]

#### <a name="to-add-new-orders"></a>Neue Bestellungen hinzufügen

- Fügen Sie die folgende Methode `AddNewOrders` zu **Form1** hinzu:

     [!code-csharp[VbRaddataSaving#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#8)]
     [!code-vb[VbRaddataSaving#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#8)]

## <a name="run-the-application"></a>Ausführen der Anwendung

#### <a name="to-run-the-application"></a>So führen Sie die Anwendung aus

- Drücken Sie **F5** , um die Anwendung auszuführen.

## <a name="see-also"></a>Siehe auch
 [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)
