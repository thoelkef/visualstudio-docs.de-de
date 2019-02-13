---
title: 'Exemplarische Vorgehensweise: Erstellen einer DataTable im Dataset-Designer'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7a01a249df088d2a89e64f1c04c69e80d69b111c
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55926748"
---
# <a name="walkthrough-create-a-datatable-in-the-dataset-designer"></a>Exemplarische Vorgehensweise: Erstellen einer DataTable im Dataset-Designer

In dieser exemplarischen Vorgehensweise wird erläutert, wie zum Erstellen einer <xref:System.Data.DataTable> (ohne einen TableAdapter) mithilfe der **Dataset-Designer**. Informationen zum Erstellen von Datentabellen, die TableAdapters enthalten, finden Sie unter [erstellen und Konfigurieren eines TableAdapters](../data-tools/create-and-configure-tableadapters.md).

## <a name="create-a-new-windows-forms-application"></a>Erstellen einer neuen Windows Forms-Anwendung

1. In Visual Studio auf die **Datei** , wählen Sie im Menü **neu** > **Projekt**.

2. Erweitern Sie entweder **Visual C#**  oder **Visual Basic** wählen Sie im linken Bereich **Windows Desktop**.

3. Wählen Sie im mittleren Bereich die **Windows Forms-App** Projekttyp.

4. Nennen Sie das Projekt **DataTableWalkthrough**, und wählen Sie dann **OK**.

     Die **DataTableWalkthrough** Projekt wird erstellt und hinzugefügt **Projektmappen-Explorer**.

## <a name="add-a-new-dataset-to-the-application"></a>Hinzufügen eines neuen Datasets zur Anwendung

1.  Wählen Sie im Menü **Projekt** die Option **Neues Element hinzufügen** aus.

     Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.

2.  Wählen Sie im linken Bereich **Daten**, und wählen Sie dann **DataSet** im mittleren Bereich.

3.  Wählen Sie **Hinzufügen** aus.

     Visual Studio fügt eine Datei namens **DataSet1.xsd** auf das Projekt und öffnet sie in der **Dataset-Designer**.

## <a name="add-a-new-datatable-to-the-dataset"></a>Dem Dataset eine neue DataTable hinzufügen

1.  Ziehen Sie eine **DataTable** aus der **DataSet** Registerkarte die **Toolbox** auf die **Dataset-Designer**.

     Eine Tabelle namens **DataTable1** zum Dataset hinzugefügt wird.

2.  Klicken Sie auf der Titelleiste des Fensters **DataTable1** und benennen Sie sie `Music`.

## <a name="add-columns-to-the-datatable"></a>Hinzufügen von Spalten zu einer DataTable

1.  Mit der rechten Maustaste die **Musik** Tabelle. Zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Spalte**.

2.  Den Namen der Spalte `SongID`.

3.  Legen Sie im Fenster **Eigenschaften** die Eigenschaft <xref:System.Data.DataColumn.DataType%2A> auf <xref:System.Int16?displayProperty=fullName>fest.

4.  Wiederholen Sie diesen Vorgang aus, und fügen Sie die folgenden Spalten:

     `SongTitle`: <xref:System.String?displayProperty=fullName>

     `Artist`: <xref:System.String?displayProperty=fullName>

     `Genre`: <xref:System.String?displayProperty=fullName>

## <a name="set-the-primary-key-for-the-table"></a>Legen Sie den Primärschlüssel für die Tabelle

Alle Datentabellen sollte es sich um einen Primärschlüssel besitzen können. Ein primärer Schlüssel identifiziert eindeutig einen bestimmten Datensatz in einer Datentabelle.

Um den Primärschlüssel festzulegen, Maustaste den **SongID** Spalte, und klicken Sie dann auf **Primärschlüssel festlegen**. Ein Schlüsselsymbol wird neben der **SongID** Spalte.

## <a name="save-your-project"></a>Speichern Ihres Projekts

Zum Speichern der **DataTableWalkthrough** -Projekt im der **Datei** , wählen Sie im Menü **Alles speichern**.

## <a name="see-also"></a>Siehe auch

- [Erstellen und Konfigurieren von Datasets in Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Überprüfen von Daten](../data-tools/validate-data-in-datasets.md)