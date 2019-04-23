---
title: Erstellen von Nachschlagetabellen in Windows Forms-Anwendungen
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 782f5b422058d1564bde04251a92d95145f6edf3
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60045126"
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Erstellen von Nachschlagetabellen in Windows Forms-Anwendungen

Die Begriff *Nachschlagetabelle* bezeichnet Steuerelemente, die an zwei zusammengehörige Datentabellen gebunden werden. Diese Nachschlagesteuerelemente zeigen Daten aus der ersten Tabelle in Abhängigkeit von den in der zweiten Tabelle ausgewählten Werten an.

Sie können Nachschlagetabellen erstellen, indem Sie den Hauptknoten einer übergeordneten Tabelle ziehen (aus der [Fenster "Datenquellen"](add-new-data-sources.md#data-sources-window)) auf ein Steuerelement auf dem Formular, das bereits in die Spalte in die zugehörige untergeordnete Tabelle gebunden ist.

Als Beispiel kann eine Tabelle mit dem Namen `Orders` dienen, die Teil einer Verkaufsdatenbank ist und Aufträge enthält. Jeder Datensatz in der Tabelle `Orders` enthält eine `CustomerID`, die angibt, welcher Kunde den Auftrag erteilt hat. Die `CustomerID` ist ein Fremdschlüssel, der auf einen Kundendatensatz in der Tabelle `Customers` zeigt. Erweitern Sie in diesem Szenario die `Orders` -Tabelle in der **Datenquellen** Fenster, und legen Sie den Hauptknoten auf **Details**. Legen Sie dann die `CustomerID` zu verwendende Spalte ein <xref:System.Windows.Forms.ComboBox> (oder ein anderes Steuerelement verwenden, die nachschlagebindung unterstützt), und ziehen Sie die `Orders` Knoten auf das Formular. Ziehen Sie abschließend die `Customers` Knoten auf das Steuerelement, das an die zugehörige Spalte gebunden ist – in diesem Fall die <xref:System.Windows.Forms.ComboBox> gebunden werden, um die `CustomerID` Spalte.

## <a name="to-databind-a-lookup-control"></a>So stellen Sie die Datenbindung für ein Nachschlagesteuerelement her

1. Öffnen Sie das Projekt, öffnen die **Datenquellen** durch auswählen **Ansicht** > **Other Windows** > **Datenquellen**.

    > [!NOTE]
    > Für Nachschlagetabellen ist es erforderlich, dass zwei zusammengehörige Tabellen oder Objekte im **Datenquellenfenster** verfügbar sind. Weitere Informationen finden Sie unter [Beziehungen in Datasets](relationships-in-datasets.md).

2. Erweitern Sie im **Datenquellenfenster** die Knoten, bis die übergeordnete Tabelle und die zugehörige untergeordnete Tabelle jeweils mit allen Spalten angezeigt werden.

    > [!NOTE]
    > Der Knoten der untergeordneten Tabelle ist der Knoten, der in der übergeordneten Tabelle als ein erweiterbarer untergeordneter Knoten angezeigt wird.

3. Ändern Sie den Ablagetyp auf **Details**, indem Sie am Knoten der untergeordneten Tabelle in der Steuerelementliste die Option **Details** auswählen. Weitere Informationen finden Sie unter [legen Sie das Steuerelement erstellt werden, beim Ziehen aus Datenquellenfenster](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

4. Suchen Sie den Knoten, die zwei Tabellen verknüpft (die `CustomerID` Knoten im vorherigen Beispiel). Ändern Sie den Ablagetyp in einem <xref:System.Windows.Forms.ComboBox> dazu **"ComboBox"** aus der Steuerungsliste.

5. Ziehen Sie den Hauptknoten der untergeordneten Tabelle aus dem **Datenquellenfenster** auf das Formular.

     Auf dem Formular werden datengebundene Steuerelemente (mit beschreibenden Bezeichnungen) sowie ein Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) angezeigt. Die Komponenten [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource> und <xref:System.Windows.Forms.BindingNavigator> werden in der Komponentenleiste angezeigt.

6. Ziehen Sie den Hauptknoten der übergeordneten Tabelle aus dem **Datenquellenfenster** direkt auf das Nachschlagesteuerelement (<xref:System.Windows.Forms.ComboBox>).

     Die Nachschlagebindungen werden jetzt festgelegt. Verweisen Sie auf die folgende Tabelle enthält die spezifischen Eigenschaften, die für das Steuerelement festgelegt wurden.

    |Eigenschaft|Erklärung der Einstellung|
    |--------------| - |
    |**DataSource**|Visual Studio legt diese Eigenschaft auf die <xref:System.Windows.Forms.BindingSource> fest, die für die auf das Steuerelement gezogene Tabelle erstellt wurde (also nicht auf die <xref:System.Windows.Forms.BindingSource>, die bei der Erstellung des Steuerelements erstellt wurde).<br /><br /> Wenn Sie eine Anpassung vornehmen müssen, legen Sie die <xref:System.Windows.Forms.BindingSource> der Tabelle mit der Spalte, die Sie anzeigen möchten.|
    |**DisplayMember**|Visual Studio legt diese Eigenschaft auf die erste Spalte nach dem Primärschlüssel fest, der einen Zeichenfolgendatentyp für die auf das Steuerelement gezogene Tabelle besitzt.<br /><br /> Wenn Sie eine Anpassung vornehmen müssen, legen Sie diese auf den Namen der Spalte, die, den Sie anzeigen möchten.|
    |**ValueMember**|Visual Studio legt diese Eigenschaft auf die erste Spalte im Primärschlüssel bzw. – wenn kein Schlüssel definiert ist – auf die erste Spalte in der Tabelle fest.<br /><br /> Wenn Sie eine Anpassung vornehmen müssen, legen Sie diese auf den Primärschlüssel in der Tabelle mit der Spalte, die Sie anzeigen möchten.|
    |**SelectedValue**|Visual Studio legt diese Eigenschaft auf die ursprüngliche, aus dem **Datenquellenfenster** gezogene und abgelegte Spalte fest.<br /><br /> Wenn Sie eine Anpassung vornehmen müssen, legen Sie diese auf die Fremdschlüsselspalte in der verknüpften Tabelle.|

## <a name="see-also"></a>Siehe auch

- [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)