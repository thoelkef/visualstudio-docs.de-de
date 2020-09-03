---
title: Speichern von Daten in einer Datenbank (mehrere Tabellen) | Microsoft-Dokumentation
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
- updating datasets, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], updating
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c5c4d5fc73660c97bcb69957a93d2ff08f64e31c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655459"
---
# <a name="save-data-to-a-database-multiple-tables"></a>Speichern von Daten in einer Datenbank (mehrere Tabellen)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eines der häufigsten Szenarios in der Anwendungsentwicklung ist das Anzeigen von Daten auf einem Formular in einer Windows-Anwendung, das Bearbeiten der Daten und das Senden der aktualisierten Daten zurück an die Datenbank. In dieser exemplarischen Vorgehensweise wird ein Formular erstellt, in dem Daten aus zwei verknüpften Tabellen angezeigt werden. Darüber hinaus wird gezeigt, wie Datensätze bearbeitet und Änderungen wieder in der Datenbank gespeichert werden. In diesem Beispiel werden die Tabellen `Customers` und `Orders` aus der Beispieldatenbank Northwind verwendet.

 Sie können Daten in der Anwendung wieder in der Datenbank speichern, indem Sie die `Update`-Methode eines TableAdapter aufrufen. Wenn Sie Tabellen aus dem **Datenquellen** Fenster auf ein Formular ziehen, wird der Code, der zum Speichern der Daten erforderlich ist, automatisch hinzugefügt. Alle weiteren Tabellen, die zu einem Formular hinzugefügt werden, müssen manuell hinzugefügt werden. In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Code hinzugefügt wird, um Aktualisierungen aus mehreren Tabellen zu speichern.

> [!NOTE]
> Die angezeigten Dialogfelder und Menübefehle können sich je nach den aktiven Einstellungen oder der von Ihnen verwendeten Edition von den in der Hilfe beschriebenen unterscheiden. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 In dieser exemplarischen Vorgehensweise werden u. a. folgende Aufgaben veranschaulicht:

- Erstellen eines neuen **Windows-Anwendungs** Projekts.

- Erstellen und Konfigurieren einer Datenquelle in der Anwendung mit dem Assistenten zum Konfigurieren von [Datenquellen](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).

- Festlegen der Steuerelemente der Elemente im [Datenquellen Fenster](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992). Weitere Informationen finden Sie unter [Festlegen des Steuer Elements, das beim Ziehen aus dem Datenquellen Fenster erstellt wird](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- Erstellen datengebundener Steuerelemente durch Ziehen von Elementen aus dem Fenster **Datenquellen** auf das Formular.

- Ändern einiger Datensätze in jeder Tabelle im DataSet.

- Ändern von Code zum Zurücksenden der aktualisierten Daten des Datasets an die Datenbank.

## <a name="prerequisites"></a>Voraussetzungen
 Für die Durchführung dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- Zugriff auf die Beispieldatenbank Northwind.

## <a name="create-the-windows-application"></a>Erstellen der Windows-Anwendung
 Der erste Schritt besteht darin, eine **Windows-Anwendung**zu erstellen. Die Zuweisung eines Namens zum Projekt ist während dieses Schritts optional, aber wir nennen ihn einen Namen, da wir ihn später speichern möchten.

#### <a name="to-create-the-new-windows-application-project"></a>So erstellen Sie das neue Windows-Anwendungsprojekt

1. Erstellen Sie im Menü **Datei** ein neues Projekt.

2. Benennen Sie das Projekt mit `UpdateMultipleTablesWalkthrough`.

3. Wählen Sie **Windows-Anwendung**aus, und klicken Sie dann auf **OK**. Weitere Informationen finden Sie unter [Client Anwendungen](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Das Projekt **UpdateMultipleTablesWalkthrough** wird erstellt und dem **Projektmappen-Explorer** hinzugefügt.

## <a name="create-the-data-source"></a>Erstellen der Datenquelle
 In diesem Schritt wird mit dem **Assistenten zum Konfigurieren von Datenquellen** eine Datenquelle aus der Northwind-Datenbank erstellt. Sie benötigen Zugriff auf die Beispieldatenbank Northwind, um die Verbindung herstellen zu können.

#### <a name="to-create-the-data-source"></a>So erstellen Sie die Datenquelle

1. Wählen Sie im Menü **Daten** die Option**Datenquellen anzeigen**aus.

2. Wählen Sie im **Datenquellen** Fenster die Option**neue Datenquelle hinzufügen** aus, um den **Assistenten zum Konfigurieren von Datenquellen**zu starten.

3. Wählen Sie auf dem Bildschirm **Daten Quellentyp auswählen**die Option **Datenbank**aus, und klicken Sie dann auf **weiter**.

4. Führen Sie auf dem Bildschirm **Wählen Sie Ihre Datenverbindung**einen der folgenden Schritte aus:

    - Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.

         Oder

    - Wählen Sie **Neue Verbindung** aus, um das Dialogfeld **Verbindung hinzufügen/ändern** zu öffnen.

5. Wenn für die Datenbank ein Kennwort erforderlich ist, wählen Sie die Option zum einschließen sensibler Daten aus, und klicken Sie dann auf **weiter**.

6. Wählen Sie unter **Verbindungs Zeichenfolge in der Anwendungs Konfigurationsdatei speichern**die Option **weiter**aus.

7. Erweitern Sie auf dem Bildschirm **Wählen Sie Ihre Datenbankobjekte**aus den Knoten **Tabellen** .

8. Wählen Sie die Tabellen **Customers** und **Orders** aus, und klicken Sie dann auf **Fertig**stellen.

     **NorthwindDataSet** wird dem Projekt hinzugefügt. Die Tabellen werden im Fenster **Datenquellen** angezeigt.

## <a name="set-the-controls-to-be-created"></a>Festlegen der zu erstellenden Steuerelemente
 In dieser exemplarischen Vorgehensweise befinden sich die Daten in der `Customers` Tabelle in einem **Detail** Layout, in dem die Daten in einzelnen Steuerelementen angezeigt werden. Die Daten aus der `Orders` Tabelle befinden sich in einem **Raster** Layout, das in einem-Steuerelement angezeigt wird <xref:System.Windows.Forms.DataGridView> .

#### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>So legen Sie den Ablagetyp für die Elemente im Datenquellenfenster fest

1. Erweitern Sie im Fenster **Datenquellen** den Knoten **Customers** .

2. Wählen Sie auf dem Knoten **Customers** in der Liste Steuerelement die Option **Details** aus, um das Steuerelement der Tabelle **Customers** in einzelne Steuerelemente zu ändern. Weitere Informationen finden Sie unter [Festlegen des Steuer Elements, das beim Ziehen aus dem Datenquellen Fenster erstellt wird](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="create-the-data-bound-form"></a>Erstellen des Daten gebundenen Formulars
 Sie können die datengebundenen Steuerelemente erstellen, indem Sie Elemente aus dem Fenster **Datenquellen** auf das Formular ziehen.

#### <a name="to-create-data-bound-controls-on-the-form"></a>So erstellen Sie datengebundene Steuerelemente auf dem Formular

1. Ziehen Sie den Hauptknoten **Customers** aus dem Fenster **Datenquellen** auf **Form1**.

     Auf dem Formular werden datengebundene Steuerelemente mit beschreibenden Bezeichnungen sowie ein Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) für die Navigation in den Datensätzen angezeigt. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> und <xref:System.Windows.Forms.BindingNavigator> werden auf der Komponentenleiste angezeigt.

2. Ziehen Sie den Knoten **Orders** aus dem Fenster **Datenquellen** auf **Form1**.

    > [!NOTE]
    > Der verknüpfte Knoten **Orders** befindet sich unter der Spalte **Fax** und ist ein untergeordneter Knoten des Knotens **Customers**.

     Auf dem Formular wird ein <xref:System.Windows.Forms.DataGridView>-Steuerelement und ein Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) für die Navigation in den Datensätzen angezeigt. Ein OrdersTableAdapter- <xref:System.Windows.Forms.BindingSource> Element, das in der Komponenten Leiste angezeigt wird.

## <a name="addcode-to-update-the-database"></a>Addcode zum Aktualisieren der Datenbank
 Sie können die Datenbank aktualisieren, indem Sie die `Update`-Methoden der TableAdapters **Customers** und **Orders** aufrufen. Standardmäßig wird ein Ereignishandler für die Schaltfläche **Speichern** der dem <xref:System.Windows.Forms.BindingNavigator> Code des Formulars hinzugefügt, um Updates an die Datenbank zu senden. Diese Prozedur ändert den Code, um Updates in der richtigen Reihenfolge zu senden. Dadurch ist es nicht mehr möglich, referenzielle Integritäts Fehler zu erhöhen. Mit dem Code wird außerdem die Fehlerbehandlung implementiert, indem der Aktualisierungsaufruf mit einem Try-Catch-Block umschlossen wird. Sie können den Code entsprechend den Anforderungen der Anwendung anpassen.

> [!NOTE]
> Aus Gründen der Übersichtlichkeit wird in dieser exemplarischen Vorgehensweise keine Transaktion verwendet. Wenn Sie jedoch zwei oder mehr verknüpfte Tabellen aktualisieren, schließen Sie die gesamte Aktualisierungs Logik in eine Transaktion ein. Eine Transaktion ist ein Prozess, mit dem sichergestellt wird, dass alle zugehörigen Änderungen an einer Datenbank erfolgreich sind, bevor für Änderungen ein Commit ausgeführt wird. Weitere Informationen finden Sie unter [Transaktionen und](https://msdn.microsoft.com/library/f46570de-9e50-4fe6-8710-a8c31fa8569b)Parallelität.

#### <a name="to-add-update-logic-to-the-application"></a>So fügen Sie der Anwendung Aktualisierungslogik hinzu

1. Klicken Sie auf die Schaltfläche **Speichern** <xref:System.Windows.Forms.BindingNavigator> . Dadurch wird der Code-Editor für den- `bindingNavigatorSaveItem_Click` Ereignishandler geöffnet.

2. Ändern Sie den Code im Ereignishandler, sodass die `Update`-Methoden der verknüpften TableAdapters aufgerufen werden. Mit folgendem Code werden zunächst drei temporäre Datentabellen zum Speichern der aktualisierten Informationen für jeden <xref:System.Data.DataRowState> (<xref:System.Data.DataRowState>, <xref:System.Data.DataRowState> und <xref:System.Data.DataRowState>) erstellt. Updates werden dann in der richtigen Reihenfolge ausgeführt. Der Code sollte wie folgt aussehen:

     [!code-csharp[VbRaddataSaving#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form4.cs#10)]
     [!code-vb[VbRaddataSaving#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form4.vb#10)]

## <a name="test-the-application"></a>Testen der Anwendung

#### <a name="to-test-the-application"></a>So testen Sie die Anwendung

1. Drücken Sie **F5**.

2. Nehmen Sie in jeder Tabelle einige Änderungen an den Daten eines oder mehrerer Datensätze vor.

3. Klicken Sie auf die Schaltfläche **Speichern**.

4. Überprüfen Sie die Werte in der Datenbank, um sicherzustellen, dass die Änderungen gespeichert wurden.

## <a name="next-steps"></a>Nächste Schritte
 Abhängig von den Anforderungen Ihrer Anwendung können Sie nach dem Erstellen eines Daten gebundenen Formulars in der Windows-Anwendung mehrere Schritte ausführen. Sie können an dieser exemplarischen Vorgehensweise beispielsweise folgende Verbesserungen vornehmen:

- Fügen Sie dem Formular Suchfunktionalität hinzu. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen einer parametrisierten Abfrage zu einer Windows Forms Anwendung](https://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).

- Bearbeiten der Datenquelle zum Hinzufügen oder Entfernen von Datenbankobjekten. Weitere Informationen finden Sie unter Gewusst [wie: Bearbeiten eines Datasets](https://msdn.microsoft.com/library/f2dade5f-9c7a-4ddb-96a8-e0a39e50bfd3).

## <a name="see-also"></a>Weitere Informationen
 [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)
