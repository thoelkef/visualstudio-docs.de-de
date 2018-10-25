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
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f68cb2178242e5589f312f6ddc2c555da3f47a0e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49872823"
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Erstellen von Nachschlagetabellen in Windows Forms-Anwendungen
Der Begriff *Nachschlagetabelle* bezeichnet Steuerelemente, die an zwei zusammengehörige Datentabellen gebunden sind. Diese Nachschlagesteuerelemente zeigen Daten aus der ersten Tabelle in Abhängigkeit von den in der zweiten Tabelle ausgewählten Werten an.

 Sie können Nachschlagetabellen erstellen, indem Sie den Hauptknoten einer übergeordneten Tabelle ziehen (aus der [Fensters "Datenquellen"](add-new-data-sources.md)) auf ein Steuerelement auf dem Formular, das bereits in die Spalte in die zugehörige untergeordnete Tabelle gebunden ist.

 Als Beispiel kann eine Tabelle mit dem Namen `Orders` dienen, die Teil einer Verkaufsdatenbank ist und Aufträge enthält. Jeder Datensatz in die `Orders` Tabelle enthält eine `CustomerID`, der angibt, welcher Kunde den Auftrag erteilt hat. Die `CustomerID` ist ein Fremdschlüssel, der auf einen Kundendatensatz in der Tabelle `Customers` zeigt. Erweitern Sie in diesem Szenario die `Orders` -Tabelle in der **Datenquellen** Fenster, und legen Sie den Hauptknoten auf **Details**. Legen Sie dann die `CustomerID` zu verwendende Spalte ein <xref:System.Windows.Forms.ComboBox> (oder ein anderes Steuerelement verwenden, die nachschlagebindung unterstützt), und ziehen Sie die `Orders` Knoten auf das Formular. Ziehen Sie abschließend die `Customers` Knoten auf das Steuerelement, das an die zugehörige Spalte gebunden ist – in diesem Fall die <xref:System.Windows.Forms.ComboBox> gebunden werden, um die `CustomerID` Spalte.

## <a name="to-databind-a-lookup-control"></a>So stellen Sie die Datenbindung für ein Nachschlagesteuerelement her

1.  Öffnen der **Datenquellen** Fenster.

    > [!NOTE]
    >  Nachschlagetabellen ist es erforderlich, dass zwei zusammengehörige Tabellen oder Objekte in verfügbar sind die **Datenquellen** Fenster. Weitere Informationen finden Sie unter [Beziehungen in Datasets](relationships-in-datasets.md).

2.  Erweitern Sie die Knoten in der **Datenquellen** Fenster, bis der übergeordneten Tabelle und alle enthaltenen Spalten und die zugehörige untergeordnete Tabelle und alle darin enthaltenen Spalten angezeigt werden.

    > [!NOTE]
    >  Der Knoten der untergeordneten Tabelle ist der Knoten, der in der übergeordneten Tabelle als ein erweiterbarer untergeordneter Knoten angezeigt wird.

3.  Ändern Sie den Ablagetyp für die untergeordnete Tabelle von **Details** dazu **Details** aus der Steuerungsliste auf dem Knoten. Weitere Informationen finden Sie unter [legen Sie das Steuerelement erstellt werden, beim Ziehen aus Datenquellenfenster](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

4.  Suchen Sie den Knoten, die zwei Tabellen verknüpft (die `CustomerID` Knoten im vorherigen Beispiel). Ändern Sie den Ablagetyp in einem <xref:System.Windows.Forms.ComboBox> dazu **"ComboBox"** aus der Steuerungsliste.

5.  Ziehen Sie den Hauptknoten der untergeordneten Tabelle aus der **Datenquellen** auf das Formular.

     Auf dem Formular werden datengebundene Steuerelemente (mit beschreibenden Bezeichnungen) sowie ein Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) angezeigt. Ein [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource>, und <xref:System.Windows.Forms.BindingNavigator> werden in der Komponentenleiste angezeigt.

6.  Nun, ziehen Sie den Hauptknoten der übergeordneten Tabelle aus der **Datenquellen** direkt auf das Nachschlagesteuerelement (die <xref:System.Windows.Forms.ComboBox>).

     Die Nachschlagebindungen werden jetzt festgelegt. Verweisen Sie auf die folgende Tabelle enthält die spezifischen Eigenschaften, die für das Steuerelement festgelegt wurden.

    |Eigenschaft|Erklärung der Einstellung|
    |--------------| - |
    |**DataSource**|Visual Studio legt diese Eigenschaft auf die <xref:System.Windows.Forms.BindingSource>, der für die Tabelle, die Sie in das Steuerelement ziehen (im Gegensatz zu den <xref:System.Windows.Forms.BindingSource>, erstellt, wenn das Steuerelement erstellt wurde).<br /><br /> Wenn Sie eine Anpassung vornehmen müssen, legen Sie die <xref:System.Windows.Forms.BindingSource> der Tabelle mit der Spalte, die Sie anzeigen möchten.|
    |**DisplayMember**|Visual Studio legt diese Eigenschaft auf die erste Spalte nach dem Primärschlüssel fest, der einen Zeichenfolgendatentyp für die auf das Steuerelement gezogene Tabelle besitzt.<br /><br /> Wenn Sie eine Anpassung vornehmen müssen, legen Sie diese auf den Namen der Spalte, die, den Sie anzeigen möchten.|
    |**ValueMember**|Visual Studio legt diese Eigenschaft auf die erste Spalte im Primärschlüssel bzw. – wenn kein Schlüssel definiert ist – auf die erste Spalte in der Tabelle fest.<br /><br /> Wenn Sie eine Anpassung vornehmen müssen, legen Sie diese auf den Primärschlüssel in der Tabelle mit der Spalte, die Sie anzeigen möchten.|
    |**SelectedValue**|Visual Studio legt diese Eigenschaft auf die ursprüngliche Spalte gelöscht wird, aus der **Datenquellen** Fenster.<br /><br /> Wenn Sie eine Anpassung vornehmen müssen, legen Sie diese auf die Fremdschlüsselspalte in der verknüpften Tabelle.|

## <a name="see-also"></a>Siehe auch

- [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)