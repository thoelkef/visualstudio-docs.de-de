---
title: Speichern Sie Daten mit den TableAdapter-DBDirect-Methoden
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
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 51f855cca05d2f9f7e6a86524da6bcf866eb0856
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>Speichern Sie Daten mit den TableAdapter-DBDirect-Methoden
Diese exemplarische Vorgehensweise enthält detaillierte Anweisungen zum Ausführen des SQL-Anweisungen direkt für eine Datenbank mithilfe eines TableAdapter DBDirect-Methoden. DBDirect-Methoden eines TableAdapters bieten ein gut Maß an Kontrolle über Ihre Datenbankupdates. Können Sie Sie verwenden, um bestimmte SQL-Anweisungen und gespeicherte Prozeduren ausführen, durch Aufrufen der einzelnen `Insert`, `Update`, und `Delete` Methoden von Ihrer Anwendung nach Bedarf (im Gegensatz zur überladenen `Update` Methode, die das UPDATE ausführt. INSERT- und DELETE-Anweisungen in einem Aufruf).

 Bei dieser exemplarischen Vorgehensweise lernen Sie Folgendes:

-   Erstellen Sie ein neues **Windows Forms-Anwendung**.

-   Erstellen und konfigurieren Sie ein Dataset mit dem [Datenquellen Konfigurations-Assistenten](../data-tools/media/data-source-configuration-wizard.png).

-   Wählen Sie das Steuerelement im Formular erstellt werden, beim Ziehen von Elementen aus der **Datenquellen** Fenster. Weitere Informationen finden Sie unter [festlegen, welches Steuerelement erstellt werden, beim Ziehen aus Datenquellenfenster](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

-   Erstellen ein datengebundenen Formulars durch Ziehen von Elementen aus der **Datenquellen** auf das Formular.

-   Hinzufügen von Methoden, um direkt auf die Datenbank zugreifen, und führen Sie einfügungen, Updates und löschungen...

## <a name="prerequisites"></a>Erforderliche Komponenten
In dieser exemplarischen Vorgehensweise werden die SQL Server Express LocalDB und der Beispieldatenbank Northwind verwendet.

1.  Wenn Sie nicht über SQL Server Express LocalDB verfügen, installieren Sie es entweder aus der [Downloadseite für SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), oder über die **Installer für Visual Studio**. In der Visual Studio-Installer können SQL Server Express LocalDB installiert werden als Teil der **datenspeicherung und Verarbeitung** arbeitsauslastung oder als eine einzelne Komponente.

2.  Installieren Sie die Beispieldatenbank Northwind, indem folgende Schritte:

    1. Öffnen Sie in Visual Studio die **Objekt-Explorer von SQL Server** Fenster. (Objekt-Explorer von SQL Server installiert ist, als Teil der **datenspeicherung und Verarbeitung** arbeitsauslastung in der Visual Studio-Installer.) Erweitern Sie die **SQL Server** Knoten. Rechtsklicken Sie auf der LocalDB-Instanz, und wählen Sie **neue Abfrage...** .

       Ein Abfrage-Editorfenster wird geöffnet.

    2. Kopieren der [Northwind Transact-SQL-Skript](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) in die Zwischenablage. Dieses T-SQL-Skript die Northwind-Datenbank von Grund auf neu erstellt und mit Daten aufgefüllt.

    3. Fügen Sie das T-SQL-Skript im Abfrage-Editor, und wählen Sie dann die **Execute** Schaltfläche.

       Nach kurzer Zeit die Abfrage die Ausführung abgeschlossen ist, und die Northwind-Datenbank wird erstellt.

## <a name="create-a-windows-forms-application"></a>Erstellen Sie eine Windows Forms-Anwendung
 Der erste Schritt ist die Erstellung einer **Windows Forms-Anwendung**.

#### <a name="to-create-the-new-windows-project"></a>So erstellen Sie ein neues Windows-Projekt

1. In Visual Studio auf die **Datei** klicken Sie im Menü **neu**, **Projekt...** .

2. Erweitern Sie entweder **Visual C#-** oder **Visual Basic** im linken Bereich, und wählen Sie dann **klassische Windows-Desktop**.

3. Wählen Sie im mittleren Bereich die **Windows Forms-App** Projekttyp.

4. Nennen Sie das Projekt **TableAdapterDbDirectMethodsWalkthrough**, und wählen Sie dann **OK**.

     Die **TableAdapterDbDirectMethodsWalkthrough** Projekt wird erstellt und hinzugefügt **Projektmappen-Explorer**.

## <a name="create-a-data-source-from-your-database"></a>Erstellen Sie eine Datenquelle aus der Datenbank
 Dieser Schritt wird mithilfe der **Datenquellen Konfigurations-Assistenten** So erstellen eine Datenquelle basierend auf der `Region` Tabelle in der Northwind-Beispieldatenbank. Sie benötigen Zugriff auf die Beispieldatenbank Northwind, um die Verbindung herstellen zu können. Informationen zum Einrichten der Northwind-Beispieldatenbank, finden Sie unter [Vorgehensweise: Installieren von Beispieldatenbanken](../data-tools/installing-database-systems-tools-and-samples.md).

#### <a name="to-create-the-data-source"></a>So erstellen Sie die Datenquelle

1.  Auf der **Daten** klicken Sie im Menü **Datenquellen anzeigen**.

2.  In der **Datenquellen** wählen **neue Datenquelle hinzufügen** zum Starten der **Datenquellen Konfigurations-Assistenten**.

3.  Auf der **wählen Sie einen Datenquellentyp** wählen **Datenbank**, und wählen Sie dann **Weiter**.

4.  Auf der **wählen Sie Ihre Datenverbindung** Bildschirm, führen Sie eine der folgenden:

    -   Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.

         - oder - 

    -   Wählen Sie **neue Verbindung** zum Starten der **Verbindung hinzufügen/ändern** (Dialogfeld).

5.  Wenn die Datenbank ein Kennwort erfordern sollte, wählen Sie die Option auf Einbeziehung vertraulicher Daten, und wählen Sie dann **Weiter**.

6.  Auf der **Verbindungszeichenfolge in der Programmkonfigurationsdatei speichern** wählen **Weiter**.

7.  Auf der **Datenbankobjekte auswählen** Bildschirm, erweitern Sie die **Tabellen** Knoten.

8.  Wählen Sie die `Region` Tabelle, und wählen Sie dann **Fertig stellen**.

     Die **NorthwindDataSet** wird dem Projekt hinzugefügt und die `Region` Tabelle wird angezeigt, der **Datenquellen** Fenster.

## <a name="add-controls-to-the-form-to-display-the-data"></a>Hinzufügen von Steuerelementen zum Formular zum Anzeigen von Daten
 Erstellen Sie datengebundene Steuerelemente durch Ziehen von Elementen aus der **Datenquellen** auf das Formular.

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>So erstellen Sie datengebundene Steuerelemente auf dem Windows form

-   Ziehen Sie den Hauptknoten **Region** Knoten aus der **Datenquellen** auf das Formular.

     Auf dem Formular wird ein <xref:System.Windows.Forms.DataGridView>-Steuerelement und ein Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) für die Navigation in den Datensätzen angezeigt. Ein [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `RegionTableAdapter`, <xref:System.Windows.Forms.BindingSource>, und <xref:System.Windows.Forms.BindingNavigator> auf der Komponentenleiste angezeigt.

#### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Hinzufügen von Schaltflächen, die die einzelnen TableAdapter DbDirect-Methoden aufruft

1.  Ziehen Sie drei <xref:System.Windows.Forms.Button> -Steuerelemente aus der **Toolbox** auf **Form1** (unterhalb der **RegionDataGridView**).

2.  Legen Sie den folgenden **Namen** und **Text** Eigenschaften auf jeder Schaltfläche.

    |name|Text|
    |----------|----------|
    |`InsertButton`|**Einfügen**|
    |`UpdateButton`|**Update (Aktualisieren)**|
    |`DeleteButton`|**Löschen**|

#### <a name="to-add-code-to-insert-new-records-into-the-database"></a>Hinzufügen von Code für das Einfügen neuer Datensätze in die Datenbank

1.  Wählen Sie **InsertButton** erstellen einen Ereignishandler für Click-Ereignis aus, und öffnen Sie das Formular im Code-Editor.

2.  Ersetzen Sie den Ereignishandler `InsertButton_Click`durch den folgenden Code:

     [!code-vb[VbRaddataSaving#1](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_1.vb)]
     [!code-csharp[VbRaddataSaving#1](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_1.cs)]

#### <a name="to-add-code-to-update-records-in-the-database"></a>Hinzufügen von Code für die Aktualisierung von Datensätzen in der Datenbank

1.  Doppelklicken Sie auf die **UpdateButton** erstellen einen Ereignishandler für Click-Ereignis aus, und öffnen Sie das Formular im Code-Editor.

2.  Ersetzen Sie den Ereignishandler `UpdateButton_Click`durch den folgenden Code:

     [!code-vb[VbRaddataSaving#2](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_2.vb)]
     [!code-csharp[VbRaddataSaving#2](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_2.cs)]

#### <a name="to-add-code-to-delete-records-from-the-database"></a>So fügen Sie Code zum Löschen von Datensätzen aus der Datenbank hinzu

1.  Wählen Sie **DeleteButton** erstellen einen Ereignishandler für Click-Ereignis aus, und öffnen Sie das Formular im Code-Editor.

2.  Ersetzen Sie den Ereignishandler `DeleteButton_Click`durch den folgenden Code:

     [!code-vb[VbRaddataSaving#3](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_3.vb)]
     [!code-csharp[VbRaddataSaving#3](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_3.cs)]

## <a name="run-the-application"></a>Ausführen der Anwendung

#### <a name="to-run-the-application"></a>So führen Sie die Anwendung aus

-   Wählen Sie **F5** um die Anwendung auszuführen.

-   Wählen Sie die **einfügen** aus, und stellen Sie sicher, dass der neue Datensatz im Raster angezeigt wird.

-   Wählen Sie die **Update** aus, und stellen Sie sicher, dass der Datensatz im Raster aktualisiert wurde.

-   Wählen Sie die **löschen** aus, und stellen Sie sicher, dass der Datensatz aus dem Raster entfernt wird.

## <a name="next-steps"></a>Nächste Schritte
 Je nach den Anforderungen Ihrer Anwendung sind mehrere Schritte, die Sie möglicherweise nach der Erstellung eines datengebundenen Formulars ausführen möchten. Sie können an dieser exemplarischen Vorgehensweise beispielsweise folgende Verbesserungen vornehmen:

-   Fügen Sie dem Formular Suchfunktionalität hinzu.

-   Hinzufügen weiterer Tabellen zum Dataset durch Auswahl **DataSet mit Assistent konfigurieren** innerhalb der **Datenquellen** Fenster. Sie können Steuerelemente hinzufügen, die zugehörige Daten anzeigen, indem Sie die entsprechenden Knoten auf das Formular ziehen. Weitere Informationen finden Sie unter [Beziehungen in Datasets](relationships-in-datasets.md).

## <a name="see-also"></a>Siehe auch

- [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)