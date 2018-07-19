---
title: Erstellen von parametrisierten TableAdapter-Abfragen
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- TableAdapters, parameterized queries
- data [Visual Studio], searching data
- queries [Visual Studio], creating
- TableAdapters, searching data
- queries [Visual Studio], TableAdapters
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: fe77d3622e9c41d98ff89972e522bb25aae58b9d
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756008"
---
# <a name="create-parameterized-tableadapter-queries"></a>Erstellen von parametrisierten TableAdapter-Abfragen
Eine parametrisierte Abfrage gibt Daten zurück, die den Bedingungen einer WHERE-Klausel in der Abfrage entsprechen. Sie können beispielsweise eine Kundenliste parametrisieren, sodass nur Kunden in einem bestimmten Ort angezeigt werden. Fügen Sie dazu `WHERE City = @City` am Ende der SQL-Anweisung hinzu, was eine Liste von Kunden ausgibt.

 Erstellen Sie parametrisierte TableAdapter-Abfragen in der **Dataset-Designer**. Sie können sie auch erstellen, in einer Windows-Anwendung mit der **parametrisierte Datenquelle** Befehl die **Daten** Menü. Die **parametrisierte Datenquelle** Befehl erstellt die Steuerelemente im Formular können Sie die Werte der Eingabeparameter und führen Sie die Abfrage.

> [!NOTE]
> Wenn Sie eine parametrisierte Abfrage zu erstellen, verwenden Sie die Parameter-Notation, die für die Datenbank spezifisch ist, die Sie für codieren. Zum Beispiel verwenden Access- und OleDb-Datenquellen das Fragezeichen "?" zur Angabe von Parametern, sodass die WHERE-Klausel wie folgt aussehen würde: `WHERE City = ?`.

> [!NOTE]
> Die angezeigten Dialogfelder und Befehle im Menü angezeigten unterscheiden sich von den in der Hilfe beschriebenen, je nach Ihren aktiven Einstellungen oder die Edition, die Sie verwenden. Um Ihre Einstellungen zu ändern, wechseln Sie zu der **Tools** Menü **Einstellungen importieren und exportieren**. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).

## <a name="create-a-parameterized-tableadapter-query"></a>Erstellen einer parametrisierten TableAdapter-Abfrage

#### <a name="to-create-a-parameterized-query-in-the-dataset-designer"></a>So erstellen Sie parametrisierte Abfrage im DataSet-Designer

-   Erstellen Sie einen neuen TableAdapter und fügen Sie eine WHERE-Klausel mit den gewünschten Parametern zur SQL-Anweisung hinzu. Weitere Informationen finden Sie unter [erstellen und Konfigurieren eines TableAdapters](../data-tools/create-and-configure-tableadapters.md).

     - oder - 

-   Fügen Sie eine Abfrage zu einem vorhandenen TableAdapter hinzu und dann eine WHERE-Klausel mit den gewünschten Parametern für die SQL-Anweisung.

#### <a name="to-create-a-parameterized-query-while-designing-a-data-bound-form"></a>So erstellen Sie eine parametrisierte Abfrage beim Entwerfen eines datengebundenen Formulars

1.  Wählen Sie ein Steuerelement auf dem Formular, das bereits an ein Dataset gebunden ist. Weitere Informationen finden Sie unter [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

2.  Auf der **Daten** , wählen Sie im Menü **Abfrage hinzufügen**.

3.  Abschließen der **Suchkriterien-Generator** Dialogfeld, eine WHERE-Klausel mit den gewünschten Parametern zur SQL-Anweisung hinzufügen.

### <a name="to-add-a-query-to-an-existing-data-bound-form"></a>So fügen Sie eine Abfrage einem vorhandenen datengebundenen Formular hinzu

1.  Öffnen Sie das Formular im **Windows Forms-Designer**.

2.  Auf der **Daten** , wählen Sie im Menü **Abfrage hinzufügen** oder **Smart Tags für Daten**.

    > [!NOTE]
    >  Wenn **Abfrage hinzufügen** ist nicht verfügbar, auf die **Daten** Menü, wählen Sie ein Steuerelement im Formular, zeigt die Sie auf Datenquelle die Parametrisierung hinzufügen. Wenn das Formular beispielsweise Daten in einem <xref:System.Windows.Forms.DataGridView>-Steuerelement anzeigt, wählen Sie dieses aus. Wenn das Formular Daten in einzelnen Steuerelementen anzeigt, wählen Sie irgendein datengebundenes Steuerelement.

3.  In der **Auswählen einer Quelltabelle** Bereich, wählen Sie die Tabelle, zu dem Sie die Parametrisierung hinzufügen möchten.

4.  Geben Sie einen Namen in der **Neuer Abfragename** Feld, wenn Sie eine neue Abfrage erstellen.

     - oder - 

     Wählen Sie eine Abfrage in der **vorhandener Abfragename** Feld.

5.  In der **Abfragetext** geben eine Abfrage, die Parameter annimmt.

6.  Klicken Sie auf **OK**.

     Ein Steuerelement für die Eingabe des Parameters und einen **Load** Schaltfläche hinzugefügt werden, auf das Formular in einem <xref:System.Windows.Forms.ToolStrip> Steuerelement.

#### <a name="querying-for-null-values"></a>Abfragen von null-Werte
TableAdapter-Parameter können null-Werte zugewiesen werden, wenn Sie Datensätze Abfragen, die keinen aktuellen Wert haben möchten. Betrachten Sie beispielsweise die folgende Abfrage, die eine `ShippedDate` Parameter in der `WHERE` Klausel:

 ```sql
SELECT CustomerID, OrderDate, ShippedDate
FROM Orders
WHERE (ShippedDate = @ShippedDate) OR (ShippedDate IS NULL)
```

 Würde dies eine Abfrage auf einem TableAdapter, können Sie alle Aufträge Abfragen, die nicht mit dem folgenden Code geliefert wurden:

 [!code-csharp[VbRaddataTableAdapters#8](../data-tools/codesnippet/CSharp/create-parameterized-tableadapter-queries_1.cs)]
 [!code-vb[VbRaddataTableAdapters#8](../data-tools/codesnippet/VisualBasic/create-parameterized-tableadapter-queries_1.vb)]

 So aktivieren Sie eine Abfrage, um null-Werte annehmen:

1.  In der **Dataset-Designer**, wählen Sie die TableAdapter-Abfrage, die null-Parameterwerte annehmen muss.

2.  In der **Eigenschaften** wählen Sie im Fenster **Parameter**, klicken Sie dann auf die Auslassungspunkte (**...** ) die Schaltfläche, um die **Parametersammlungs-Editor**.

3.  Wählen Sie den Parameter, die null-Werte zulässt, und legen Sie die **AllowDbNull** Eigenschaft `true`.

## <a name="see-also"></a>Siehe auch

- [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)