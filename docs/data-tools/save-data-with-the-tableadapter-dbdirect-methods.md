---
title: Speichern von Daten mit den TableAdapter-DBDirect-Methoden
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 77e620a5611a912c3abf449241670fdb298036f3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54934308"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>Speichern von Daten mit den TableAdapter-DBDirect-Methoden

Diese exemplarische Vorgehensweise enthält detaillierte Anweisungen zum Ausführen von SQL-Anweisungen direkt in einer Datenbank mithilfe von DBDirect-Methoden eines TableAdapters. Die DBDirect-Methoden eines TableAdapters bieten ein sehr gutes Maß an Kontrolle über Änderungen an der Datenbank. Können sie bestimmte SQL-Anweisungen und gespeicherte Prozeduren ausgeführt, indem die einzelnen `Insert`, `Update`, und `Delete` Methoden, die von Ihrer Anwendung nach Bedarf (im Gegensatz zur überladenen `Update` Methode, die das UPDATE ausführt. INSERT- und DELETE-Anweisungen in einem einzigen Aufruf).

Bei dieser exemplarischen Vorgehensweise lernen Sie Folgendes:

-   Erstellen Sie eine neue **Windows Forms-Anwendung**.

-   Erstellen und konfigurieren Sie ein Dataset mit dem [Assistenten zur Datenquellenkonfiguration](../data-tools/media/data-source-configuration-wizard.png).

-   Wählen Sie das Steuerelement aus, das für das Formular erstellt werden soll, wenn Elemente aus dem **Datenquellenfenster** gezogen werden. Weitere Informationen finden Sie unter [legen Sie das Steuerelement erstellt werden, beim Ziehen aus Datenquellenfenster](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

-   Erstellen eines datengebundenen Formulars durch Ziehen von Elementen aus dem **Datenquellenfenster** auf das Formular.

-   Fügen Sie Methoden, um direkt auf die Datenbank zugreifen, und führen Sie einfügungen, Updates und löschungen.

## <a name="prerequisites"></a>Erforderliche Komponenten

In dieser exemplarischen Vorgehensweise verwendet SQL Server Express LocalDB und der Beispieldatenbank Northwind.

1. Wenn Sie SQL Server Express LocalDB nicht haben, installieren Sie es entweder über die [Downloadseite für SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), oder über die **Visual Studio-Installer**. In der **Visual Studio-Installer**, können Sie SQL Server Express LocalDB installieren, als Teil der **datenspeicherung und-Verarbeitung** Workload oder als eine einzelne Komponente.

2. Installieren der Northwind-Beispieldatenbank mit folgenden Schritten:

    1. Öffnen Sie in Visual Studio die **Objekt-Explorer von SQL Server** Fenster. (Objekt-Explorer von SQL Server installiert ist, als Teil der **datenspeicherung und-Verarbeitung** Workload im Visual Studio-Installer.) Erweitern Sie die **SQL Server** Knoten. Mit der rechten Maustaste auf der LocalDB-Instanz, und wählen Sie **neue Abfrage**.

       Ein Abfrage-Editor-Fenster wird geöffnet.

    2. Kopieren der [Northwind Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Dieses T-SQL-Skript wird die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.

    3. Fügen Sie das T-SQL-Skript im Abfrage-Editor, und wählen Sie dann die **Execute** Schaltfläche.

       Klicken Sie nach kurzer Zeit die Ausführung die Abfrage abgeschlossen ist, und die Northwind-Datenbank wird erstellt.

## <a name="create-a-windows-forms-application"></a>Erstellen einer Windows Forms-Anwendung

Der erste Schritt ist die Erstellung einer **Windows Forms-Anwendung**.

1. In Visual Studio auf die **Datei** , wählen Sie im Menü **neu** > **Projekt**.

2. Erweitern Sie entweder **Visual C#**  oder **Visual Basic** wählen Sie im linken Bereich **Windows Desktop**.

3. Wählen Sie im mittleren Bereich die **Windows Forms-App** Projekttyp.

4. Nennen Sie das Projekt **TableAdapterDbDirectMethodsWalkthrough**, und wählen Sie dann **OK**.

     Das Projekt **TableAdapterDbDirectMethodsWalkthrough** wird erstellt und zum **Projektmappen-Explorer** hinzugefügt.

## <a name="create-a-data-source-from-your-database"></a>Erstellen Sie eine Datenquelle aus der Datenbank

Dieser Schritt verwendet den **Assistenten zum Konfigurieren von Datenquellen** auf Grundlage der `Region`-Tabelle in der Beispieldatenbank Northwind. Sie benötigen Zugriff auf die Beispieldatenbank Northwind, um die Verbindung herstellen zu können. Informationen zum Einrichten der Beispieldatenbank Northwind finden Sie unter [Vorgehensweise: Installieren von Beispieldatenbanken](../data-tools/installing-database-systems-tools-and-samples.md).

### <a name="to-create-the-data-source"></a>So erstellen Sie die Datenquelle

1. Auf der **Daten** , wählen Sie im Menü **Datenquellen anzeigen**.

   Das Fenster **Datenquellen** wird geöffnet.

2. Wählen Sie im **Datenquellenfenster** die Option **Neue Datenquelle hinzufügen** aus, um den **Assistenten zum Konfigurieren von Datenquellen** zu starten.

3. Auf der **wählen Sie einen Datenquellentyp** auf **Datenbank**, und wählen Sie dann **Weiter**.

4. Auf der **wählen Sie Ihre Datenverbindung** Bildschirm, führen Sie eine der folgenden:

    -   Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.

         - oder - 

    -   Klicken Sie auf **Neue Verbindung**, um das Dialogfeld **Add/Modify Connection** (Verbindung hinzufügen/ändern) zu öffnen.

5. Wenn Ihre Datenbank ein Kennwort erfordert, wählen Sie die Option Einbeziehung vertraulicher Daten, und wählen Sie dann **Weiter**.

6. Auf der **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern** auf **Weiter**.

7. Auf der **Datenbankobjekte auswählen** Bildschirm, erweitern Sie die **Tabellen** Knoten.

8. Wählen Sie die `Region` Tabelle, und wählen Sie dann **Fertig stellen**.

     Das **NorthwindDataSet** wird Ihrem Projekt hinzugefügt, und die `Region`-Tabelle wird im **Datenquellenfenster** angezeigt.

## <a name="add-controls-to-the-form-to-display-the-data"></a>Hinzufügen von Steuerelementen zum Formular zum Anzeigen der Daten

Erstellen Sie die datengebundenen Steuerelemente, indem Sie Elemente aus dem **Datenquellenfenster** auf das Formular ziehen.

Ziehen Sie den Hauptknoten, um datengebundene Steuerelemente auf dem Windows-Formular zu erstellen, **Region** Knoten aus der **Datenquellen** auf das Formular.

Auf dem Formular wird ein <xref:System.Windows.Forms.DataGridView>-Steuerelement und ein Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) für die Navigation in den Datensätzen angezeigt. Ein [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `RegionTableAdapter`, <xref:System.Windows.Forms.BindingSource>, und <xref:System.Windows.Forms.BindingNavigator> werden in der Komponentenleiste angezeigt.

### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Hinzufügen von Schaltflächen, die die einzelnen TableAdapter DbDirect-Methoden aufruft

1. Ziehen Sie drei <xref:System.Windows.Forms.Button>-Steuerelemente aus der **Toolbox** auf **Form1** (unter **RegionDataGridView**).

2. Legen Sie die folgenden Eigenschaften für **Name** und **Text** auf jeder Schaltfläche fest.

    |name|Text|
    |----------|----------|
    |`InsertButton`|**Einfügen**|
    |`UpdateButton`|**Update (Aktualisieren)**|
    |`DeleteButton`|**Löschen**|

### <a name="to-add-code-to-insert-new-records-into-the-database"></a>Hinzufügen von Code für das Einfügen neuer Datensätze in die Datenbank

1. Wählen Sie **InsertButton** erstellen einen Ereignishandler für Click-Ereignis aus, und öffnen Sie das Formular im Code-Editor.

2. Ersetzen Sie den Ereignishandler `InsertButton_Click`durch den folgenden Code:

     [!code-vb[VbRaddataSaving#1](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_1.vb)]
     [!code-csharp[VbRaddataSaving#1](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_1.cs)]

### <a name="to-add-code-to-update-records-in-the-database"></a>Hinzufügen von Code für die Aktualisierung von Datensätzen in der Datenbank

1. Doppelklicken Sie **UpdateButton**, sodass ein Ereignishandler für Click-Ereignis erstellt wird, und öffnen Sie das Formular im Code-Editor.

2. Ersetzen Sie den Ereignishandler `UpdateButton_Click`durch den folgenden Code:

     [!code-vb[VbRaddataSaving#2](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_2.vb)]
     [!code-csharp[VbRaddataSaving#2](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_2.cs)]

### <a name="to-add-code-to-delete-records-from-the-database"></a>Hinzufügen von Code, um Datensätze aus der Datenbank zu löschen.

1. Wählen Sie **DeleteButton** erstellen einen Ereignishandler für Click-Ereignis aus, und öffnen Sie das Formular im Code-Editor.

2. Ersetzen Sie den Ereignishandler `DeleteButton_Click`durch den folgenden Code:

     [!code-vb[VbRaddataSaving#3](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_3.vb)]
     [!code-csharp[VbRaddataSaving#3](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_3.cs)]

## <a name="run-the-application"></a>Ausführen der Anwendung

-   Wählen Sie **F5** zum Ausführen der Anwendung.

-   Wählen Sie die **einfügen** Schaltfläche, und stellen Sie sicher, dass der neue Datensatz im Raster angezeigt wird.

-   Wählen Sie die **Update** Schaltfläche, und stellen Sie sicher, dass der Datensatz im Raster aktualisiert wird.

-   Wählen Sie die **löschen** Schaltfläche, und stellen Sie sicher, dass der Eintrag aus dem Raster entfernt wird.

## <a name="next-steps"></a>Nächste Schritte

Je nach den Anforderungen Ihrer Anwendung sind mehrere Schritte, die Sie möglicherweise nach dem Erstellen eines datengebundenen Formulars ausführen möchten. Sie können an dieser exemplarischen Vorgehensweise beispielsweise folgende Verbesserungen vornehmen:

-   Fügen Sie dem Formular Suchfunktionalität hinzu.

-   Hinzufügen weiterer Tabellen zum Dataset durch Auswählen von **DataSet mit Assistent konfigurieren** aus dem **Datenquellenfenster**. Sie können Steuerelemente hinzufügen, die zugehörige Daten anzeigen, indem Sie die entsprechenden Knoten auf das Formular ziehen. Weitere Informationen finden Sie unter [Beziehungen in Datasets](relationships-in-datasets.md).

## <a name="see-also"></a>Siehe auch

- [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)