---
title: Erstellen von Nachschlagetabellen in WPF-Anwendungen
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: ed448c44b46098a6ccaa7ac1194acd76bd64c089
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54988908"
---
# <a name="create-lookup-tables-in-wpf-applications"></a>Erstellen von Nachschlagetabellen in WPF-Anwendungen

Der Begriff *Nachschlagetabelle* (bezeichnet ein *nachschlagebindung*) beschreibt ein Steuerelement, das Informationen aus einer Datentabelle, die anhand des Werts eines Fremdschlüsselfelds in einer anderen Tabelle anzeigt. Sie können eine Nachschlagetabelle erstellen, indem Sie den Hauptknoten einer übergeordneten Tabelle ziehen oder-Objekts in die **Datenquellen** auf ein Steuerelement, das bereits an eine Spalte oder Eigenschaft in einer verknüpften untergeordneten Tabelle gebunden ist.

Als Beispiel kann eine Tabelle mit dem Namen `Orders` dienen, die Teil einer Verkaufsdatenbank ist und Aufträge enthält. Jeder Datensatz in die `Orders` Tabelle enthält eine `CustomerID` , der angibt, welcher Kunde den Auftrag erteilt hat. Die `CustomerID` ist ein Fremdschlüssel, der auf einen Kundendatensatz in zeigt die `Customers` Tabelle. Wenn Sie eine Liste der Bestellungen Anzeigen der `Orders` Tabelle, Sie können anstelle von den tatsächlichen Kundennamen anzeigen möchten die `CustomerID`. Da der Kundenname wird die `Customers` Tabelle müssen Sie eine Nachschlagetabelle, um die Namen der Kunden zu erstellen. Die Lookup-Tabelle verwendet den `CustomerID` Wert in der `Orders` aufzeichnen, um die Beziehung zu navigieren, und geben Sie den Namen des Kunden zurück.

## <a name="to-create-a-lookup-table"></a>So erstellen Sie eine Suchtabelle

1.  Fügen Sie eine der folgenden Typen von Datenquellen mit zugehörigen Daten zu Ihrem Projekt hinzu:

    -   DataSet oder ein Entity Data Model.

    -   WCF Data Service, WCF-Dienst oder einen Webdienst. Weitere Informationen finden Sie unter [Vorgehensweise: Herstellen einer Verbindung mit Daten in einem Dienst](../data-tools/how-to-connect-to-data-in-a-service.md).

    -   Objekte. Weitere Informationen finden Sie unter [Binden an Objekte in Visual Studio](bind-objects-in-visual-studio.md).

    > [!NOTE]
    > Bevor Sie eine Nachschlagetabelle erstellen können, müssen zwei zusammengehörige Tabellen oder Objekte als Datenquelle für das Projekt vorhanden.

2.  Öffnen der **WPF-Designer**, und stellen Sie sicher, dass der Designer ein Container enthält, die für Elemente in ein gültiges Ablageziel ist die **Datenquellen** Fenster.

     Weitere Informationen über gültige Ablageziele finden Sie unter [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

3.  Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**, um das Fenster **Datenquellen** zu öffnen.

4.  Erweitern Sie die Knoten in der **Datenquellen** Fenster, bis die übergeordnete Tabelle oder Objekt und die zugehörige untergeordnete Tabelle oder das Objekt angezeigt werden.

    > [!NOTE]
    > Zugehörige untergeordnete Tabelle oder des Objekts ist der Knoten, der als ein erweiterbarer untergeordneter Knoten unter der übergeordneten Tabelle oder ein Objekt angezeigt wird.

5.  Klicken Sie auf das Dropdownmenü für den untergeordneten Knoten, und wählen **Details**.

6.  Erweitern Sie den untergeordneten Knoten.

7.  Klicken Sie unter den untergeordneten Knoten auf das Dropdownmenü für das Element, das die untergeordneten und übergeordneten Daten beziehen. (Im obigen Beispiel ist dies die **"CustomerID"** Knoten.) Wählen Sie eine der folgenden Typen von Steuerelementen, die nachschlagebindung unterstützt:

    -   **ComboBox**

    -   **ListBox**

    -   **ListView**

        > [!NOTE]
        > Wenn die **ListBox** oder **ListView** Steuerelement erscheint nicht in der Liste, Sie können diese Steuerelemente hinzufügen, um die Liste. Weitere Informationen finden Sie unter [legen Sie das Steuerelement erstellt werden, beim Ziehen aus Datenquellenfenster](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

    -   Jedes benutzerdefinierten Steuerelements, die von abgeleitet <xref:System.Windows.Controls.Primitives.Selector>.

        > [!NOTE]
        > Für Informationen zur Vorgehensweise beim Hinzufügen der benutzerdefinierten Steuerelemente auf die Liste der Steuerelemente Sie, für Elemente in auswählen kann der **Datenquellen** Fenster finden Sie unter [Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellenfenster](../data-tools/add-custom-controls-to-the-data-sources-window.md).

8.  Ziehen Sie den untergeordneten Knoten aus der **Datenquellen** auf einen Container im WPF-Designer. (Im vorherigen Beispiel ist der untergeordnete Knoten ist der **Bestellungen** Knoten.)

     Visual Studio generiert XAML, das neue datengebundene Steuerelemente für jedes der Elemente erstellt, die Sie ziehen. Das XAML fügt auch ein neues <xref:System.Windows.Data.CollectionViewSource> für die untergeordnete Tabelle oder ein Objekt, das die Ressourcen des Ablageziels. Für einige Datenquellen generiert Visual Studio auch Code zum Laden von Daten in der Tabelle oder ein Objekt. Weitere Informationen finden Sie unter [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

9. Ziehen Sie den übergeordneten Knoten aus der **Datenquellen** Fenster auf das Nachschlagesteuerelement für die Bindung, die Sie zuvor erstellt haben. (Im vorherigen Beispiel ist der übergeordnete Knoten ist der **Kunden** Knoten).

     Visual Studio legt einige Eigenschaften des Steuerelements zum Konfigurieren der Bindung für die Suche an. Die folgende Tabelle enthält die Eigenschaften, die Visual Studio ändert. Wenn erforderlich, Sie diese Eigenschaften in der XAML oder in ändern, können die **Eigenschaften** Fenster.

    |Eigenschaft|Erklärung der Einstellung|
    |--------------| - |
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|Diese Eigenschaft gibt die Auflistung oder die Bindung, die verwendet wird, um die Daten abzurufen, die im Steuerelement angezeigt wird. Visual Studio legt diese Eigenschaft auf die <xref:System.Windows.Data.CollectionViewSource> für die übergeordneten Daten, die Sie auf das Steuerelement gezogen haben.|
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|Diese Eigenschaft gibt den Pfad des Datenelements, das im Steuerelement angezeigt wird. Visual Studio legt diese Eigenschaft auf die erste Spalte oder Eigenschaft in der übergeordneten Daten, nach den primären Schlüssel, der einen String-Datentyp aufweist.<br /><br /> Wenn Sie eine andere Spalte oder Eigenschaft in den übergeordneten Daten anzeigen möchten, können ändern Sie diese Eigenschaft auf den Pfad zu einer anderen Eigenschaft.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Visual Studio wird diese Eigenschaft gebunden, auf die Spalte oder Eigenschaft der untergeordneten Daten, die Sie in den Designer gezogen wird. Dies ist der Fremdschlüssel für die übergeordneten Daten.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Visual Studio legt diese Eigenschaft auf den Pfad der Spalte oder eine Eigenschaft der untergeordneten Daten, die die foreign Key für die übergeordneten Daten ist.|

## <a name="see-also"></a>Siehe auch

- [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Anzeigen zugehöriger Daten in WPF-Anwendungen](../data-tools/display-related-data-in-wpf-applications.md)
- [Exemplarische Vorgehensweise: Anzeigen zugehöriger Daten in WPF-Anwendungen](../data-tools/display-related-data-in-wpf-applications.md)