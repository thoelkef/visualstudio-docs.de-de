---
title: Speichern von Daten mit den TableAdapter-DBDirect-Methoden | Microsoft-Dokumentation
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
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ce987f5ef90448c41da45a39c62710b968e11199
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655420"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>Speichern von Daten mit den TableAdapter-DBDirect-Methoden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese exemplarische Vorgehensweise enthält ausführliche Anweisungen zum Ausführen von SQL-Anweisungen direkt für eine-Datenbank mithilfe der DBDirect-Methoden eines TableAdapter. Die DBDirect-Methoden eines TableAdapters bieten ein sehr gutes Maß an Kontrolle über Änderungen an der Datenbank. Sie können Sie verwenden, um bestimmte SQL-Anweisungen und gespeicherte Prozeduren auszuführen, indem Sie die einzelnen `Insert`-, `Update`-und `Delete`-Methoden aufrufen, die von der Anwendung benötigt werden (im Gegensatz zur überladenen `Update` Methode, die das Update ausführt, einfügen und DELETE-Anweisungen in einem einzigen-Befehl.

 Bei dieser exemplarischen Vorgehensweise lernen Sie Folgendes:

- Erstellen Sie eine neue **Windows-Anwendung**.

- Erstellen und konfigurieren Sie mit dem Assistenten zum Konfigurieren von [Datenquellen](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)ein DataSet.

- Wählen Sie das Steuerelement aus, das für das Formular erstellt werden soll, wenn Elemente aus dem **Datenquellenfenster** gezogen werden. Weitere Informationen finden Sie unter [Festlegen des Steuer Elements, das beim Ziehen aus dem Datenquellen Fenster erstellt wird](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- Erstellen eines datengebundenen Formulars durch Ziehen von Elementen aus dem **Datenquellenfenster** auf das Formular.

- Fügen Sie Methoden hinzu, um direkt auf die Datenbank zuzugreifen und Einfügungen, Updates und Löschungen auszuführen.

## <a name="prerequisites"></a>Erforderliche Voraussetzungen
 Für die Durchführung dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- Zugriff auf die Beispieldatenbank Northwind.

## <a name="create-a-windows-application"></a>Erstellen einer Windows-Anwendung
 Der erste Schritt besteht darin, eine **Windows-Anwendung**zu erstellen.

#### <a name="to-create-the-new-windows-project"></a>So erstellen Sie ein neues Windows-Projekt

1. Erstellen Sie in Visual Studio im Menü **Datei** ein neues **Projekt**.

2. Nennen Sie das Projekt **TableAdapterDbDirectMethodsWalkthrough**.

3. Wählen Sie **Windows-Anwendung**aus, und klicken Sie dann auf **OK**. Weitere Informationen finden Sie unter [Client Anwendungen](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Das Projekt **TableAdapterDbDirectMethodsWalkthrough** wird erstellt und zum **Projektmappen-Explorer** hinzugefügt.

## <a name="create-a-data-source-from-your-database"></a>Erstellen einer Datenquelle aus der Datenbank
 Dieser Schritt verwendet den **Assistenten zum Konfigurieren von Datenquellen** auf Grundlage der `Region`-Tabelle in der Beispieldatenbank Northwind. Sie benötigen Zugriff auf die Beispieldatenbank Northwind, um die Verbindung herstellen zu können.

#### <a name="to-create-the-data-source"></a>So erstellen Sie die Datenquelle

1. Wählen Sie im Menü **Daten** die Option **Datenquellen anzeigen**aus.

2. Wählen Sie im Fenster **Datenquellen** die Option **Neue Datenquelle hinzufügen** aus, um den **Assistenten zum Konfigurieren von Datenquellen** zu starten.

3. Wählen Sie auf dem Bildschirm **Daten Quellentyp auswählen** die Option **Datenbank**aus, und klicken Sie dann auf **weiter**.

4. Führen Sie auf dem Bildschirm **Wählen Sie Ihre Datenverbindung** aus einen der folgenden Schritte aus:

    - Wenn in der Dropdownliste eine Datenverbindung zur Beispieldatenbank „Northwind“ verfügbar ist, wählen Sie diese aus.

         - oder -

    - Klicken Sie auf **Neue Verbindung**, um das Dialogfeld **Add/Modify Connection** (Verbindung hinzufügen/ändern) zu öffnen.

5. Wenn für die Datenbank ein Kennwort erforderlich ist, wählen Sie die Option zum einschließen sensibler Daten aus, und klicken Sie dann auf **weiter**.

6. Wählen Sie auf der Seite **Verbindungs Zeichenfolge in der Anwendungs Konfigurationsdatei speichern** die Option **weiter**aus.

7. Erweitern Sie auf dem Bildschirm **Wählen Sie Ihre Datenbankobjekte** aus den Knoten **Tabellen** .

8. Wählen Sie die `Region` Tabelle aus, und klicken Sie dann auf **Fertig**stellen.

     Das **NorthwindDataSet** wird Ihrem Projekt hinzugefügt, und die `Region`-Tabelle wird im **Datenquellenfenster** angezeigt.

## <a name="addcontrols-to-the-form-to-display-the-data"></a>Addcontrols zum Formular zum Anzeigen der Daten
 Erstellen Sie die datengebundenen Steuerelemente, indem Sie Elemente aus dem **Datenquellenfenster** auf das Formular ziehen.

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>So erstellen Sie Daten gebundene Steuerelemente auf dem Windows Form

- Ziehen Sie den Haupt **Regions** Knoten aus dem **Datenquellen** Fenster auf das Formular.

     Auf dem Formular wird ein <xref:System.Windows.Forms.DataGridView>-Steuerelement und ein Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) für die Navigation in den Datensätzen angezeigt. Ein [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), RegionTableAdapter, <xref:System.Windows.Forms.BindingSource> und <xref:System.Windows.Forms.BindingNavigator> werden in der Komponenten Leiste angezeigt.

#### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Hinzufügen von Schaltflächen, die die einzelnen TableAdapter DbDirect-Methoden aufruft

1. Ziehen Sie drei <xref:System.Windows.Forms.Button>-Steuerelemente aus der **Toolbox** auf **Form1** (unter **RegionDataGridView**).

2. Legen Sie die folgenden Eigenschaften für **Name** und **Text** auf jeder Schaltfläche fest.

    |-Name|Text|
    |----------|----------|
    |`InsertButton`|**Einfügen**|
    |`UpdateButton`|**Update (Aktualisieren)**|
    |`DeleteButton`|**Löschen**|

#### <a name="to-add-code-to-insert-new-records-into-the-database"></a>Hinzufügen von Code für das Einfügen neuer Datensätze in die Datenbank

1. Wählen Sie **InsertButton** aus, um einen Ereignishandler für das Click-Ereignis zu erstellen und das Formular im Code-Editor zu öffnen.

2. Ersetzen Sie den Ereignishandler `InsertButton_Click`durch den folgenden Code:

     [!code-csharp[VbRaddataSaving#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#1)]
     [!code-vb[VbRaddataSaving#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#1)]

#### <a name="to-add-code-to-update-records-in-the-database"></a>Hinzufügen von Code für die Aktualisierung von Datensätzen in der Datenbank

1. Doppelklicken Sie **UpdateButton**, sodass ein Ereignishandler für Click-Ereignis erstellt wird, und öffnen Sie das Formular im Code-Editor.

2. Ersetzen Sie den Ereignishandler `UpdateButton_Click`durch den folgenden Code:

     [!code-csharp[VbRaddataSaving#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#2)]
     [!code-vb[VbRaddataSaving#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#2)]

#### <a name="to-add-code-to-delete-records-from-the-database"></a>So fügen Sie Code hinzu, um Datensätze aus der Datenbank zu löschen

1. Wählen Sie **DeleteButton** aus, um einen Ereignishandler für das Click-Ereignis zu erstellen und das Formular im Code-Editor zu öffnen.

2. Ersetzen Sie den Ereignishandler `DeleteButton_Click`durch den folgenden Code:

     [!code-csharp[VbRaddataSaving#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#3)]
     [!code-vb[VbRaddataSaving#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#3)]

## <a name="run-the-application"></a>Ausführen der Anwendung

#### <a name="to-run-the-application"></a>So führen Sie die Anwendung aus

- Drücken Sie **F5** , um die Anwendung auszuführen.

- Wählen Sie die Schaltfläche **Einfügen** aus, und überprüfen Sie, ob der neue Datensatz im Raster angezeigt wird.

- Wählen Sie die Schaltfläche **Aktualisieren** aus, und überprüfen Sie, ob der Datensatz im Raster aktualisiert wurde.

- Wählen Sie die Schaltfläche **Löschen** aus, und überprüfen Sie, ob der Datensatz aus dem Raster entfernt wurde.

## <a name="next-steps"></a>Nächste Schritte
 Abhängig von den Anforderungen Ihrer Anwendung können Sie nach dem Erstellen eines Daten gebundenen Formulars einige Schritte ausführen. Sie können an dieser exemplarischen Vorgehensweise beispielsweise folgende Verbesserungen vornehmen:

- Fügen Sie dem Formular Suchfunktionalität hinzu. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen einer parametrisierten Abfrage zu einer Windows Forms Anwendung](https://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).

- Hinzufügen weiterer Tabellen zum Dataset durch Auswählen von **DataSet mit Assistent konfigurieren** aus dem **Datenquellenfenster**. Sie können Steuerelemente hinzufügen, die zugehörige Daten anzeigen, indem Sie die entsprechenden Knoten auf das Formular ziehen.

## <a name="see-also"></a>Siehe auch
 [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)
