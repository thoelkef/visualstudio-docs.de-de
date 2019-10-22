---
title: Erstellen von Nachschlage Tabellen in WPF-Anwendungen | Microsoft-Dokumentation
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
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6816b7465b8a3271ec6ebc0db5046d76e60ec5b3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657426"
---
# <a name="create-lookup-tables-in-wpf-applications"></a>Erstellen von Nachschlagetabellen in WPF-Anwendungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Begriff Nachschlage *Tabelle* (manchmal als *Such Bindung*bezeichnet) beschreibt ein Steuerelement, das Informationen aus einer Datentabelle basierend auf dem Wert eines Fremdschlüssel Felds in einer anderen Tabelle anzeigt. Sie können eine Nachschlage Tabelle erstellen, indem Sie den Haupt Knoten einer übergeordneten Tabelle oder eines Objekts im **Datenquellen** Fenster auf ein Steuerelement ziehen, das bereits an eine Spalte oder Eigenschaft in einer verknüpften untergeordneten Tabelle gebunden ist.

 Als Beispiel kann eine Tabelle mit dem Namen `Orders` dienen, die Teil einer Verkaufsdatenbank ist und Aufträge enthält. Jeder Datensatz in der `Orders` Tabelle enthält eine `CustomerID`, die angibt, welcher Kunde den Auftrag aufgegeben hat. Der `CustomerID` ist ein Fremdschlüssel, der auf einen Kundendaten Satz in der `Customers` Tabelle zeigt. Wenn Sie eine Liste der Bestellungen aus der `Orders` Tabelle anzeigen, möchten Sie möglicherweise den tatsächlichen Kundennamen anstelle des `CustomerID` anzeigen. Da der Kunden Name in der `Customers` Tabelle enthalten ist, müssen Sie eine Nachschlage Tabelle erstellen, um den Kundennamen anzuzeigen. In der Nachschlage Tabelle wird der `CustomerID` Wert im `Orders` Datensatz verwendet, um in der Beziehung zu navigieren und den Kundennamen zurückzugeben.

## <a name="to-create-a-lookup-table"></a>So erstellen Sie eine Suchtabelle

1. Fügen Sie einem Projekt einen der folgenden Typen von Datenquellen mit verknüpften Daten hinzu:

    - DataSet oder Entity Data Model.

    - WCF-Datendienst, WCF-Dienst oder Webdienst. Weitere Informationen finden Sie unter Gewusst [wie: Herstellen einer Verbindung mit Daten in einem Dienst](../data-tools/how-to-connect-to-data-in-a-service.md).

    - Objekte. Weitere Informationen finden Sie unter Gewusst [wie: Herstellen einer Verbindung mit Daten in Objekten](https://msdn.microsoft.com/library/862fd351-0f4d-4220-9743-6103b87dc24b).

    > [!NOTE]
    > Bevor Sie eine Nachschlage Tabelle erstellen können, müssen zwei verknüpfte Tabellen oder Objekte als Datenquelle für das Projekt vorhanden sein.

2. Öffnen Sie den**WPF-Designer**, und stellen Sie sicher, dass der Designer einen Container enthält, bei dem es sich um ein gültiges Ablage Ziel für Elemente im **Datenquellen** Fenster handelt.

     Weitere Informationen zu gültigen Drop-Zielen finden [Sie unterbinden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

3. Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**, um das Fenster **Datenquellen** zu öffnen.

4. Erweitern Sie die Knoten im **Datenquellen** Fenster, bis die übergeordnete Tabelle oder das übergeordnete Objekt und die zugehörige untergeordnete Tabelle oder das zugehörige Objekt angezeigt werden.

    > [!NOTE]
    > Die zugehörige untergeordnete Tabelle oder das verbundene Objekt ist der Knoten, der als erweiterbarer untergeordneter Knoten unter der übergeordneten Tabelle oder dem übergeordneten Objekt angezeigt wird

5. Klicken Sie auf das Dropdown Menü für den untergeordneten Knoten, und wählen Sie **Details**aus.

6. Erweitern Sie den untergeordneten Knoten.

7. Klicken Sie unter dem untergeordneten Knoten auf das Dropdown Menü für das Element, das die untergeordneten und übergeordneten Daten verknüpft. (Im vorherigen Beispiel ist dies der **CustomerID-** Knoten.) Wählen Sie einen der folgenden Typen von Steuerelementen aus, die die Such Bindung unterstützen:

    - **ComboBox**

    - **ListBox**

    - **ListView**

        > [!NOTE]
        > Wenn das **ListBox** -Steuerelement oder das **ListView** -Steuerelement nicht in der Liste angezeigt wird, können Sie diese Steuerelemente der Liste hinzufügen. Weitere Informationen finden [Sie unter Festlegen des Steuer Elements, das beim Ziehen aus dem Datenquellen Fenster erstellt wird](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

    - Alle benutzerdefinierten Steuerelemente, die von <xref:System.Windows.Controls.Primitives.Selector> abgeleitet werden.

        > [!NOTE]
        > Weitere Informationen zum Hinzufügen von benutzerdefinierten Steuerelementen zur Liste der Steuerelemente, die Sie für Elemente im **Datenquellen** Fenster auswählen können, finden Sie unter [Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellen Fenster](../data-tools/add-custom-controls-to-the-data-sources-window.md).

8. Ziehen Sie den untergeordneten Knoten aus dem **Datenquellen** Fenster auf einen Container im WPF-Designer. (Im vorherigen Beispiel ist der untergeordnete Knoten der Knoten **Orders** .)

     Visual Studio generiert XAML, das neue Daten gebundene Steuerelemente für jedes der Elemente erstellt, die Sie ziehen. Die XAML fügt den Ressourcen des Ablage Ziels außerdem eine neue <xref:System.Windows.Data.CollectionViewSource> für die untergeordnete Tabelle oder das untergeordnete Objekt hinzu. Für einige Datenquellen generiert Visual Studio auch Code zum Laden von Daten in die Tabelle oder das Objekt. Weitere Informationen finden Sie unter [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

9. Ziehen Sie den übergeordneten Knoten aus dem **Datenquellen** Fenster auf das Nachschlage Steuerelement für die Suche, das Sie zuvor erstellt haben. (Im vorherigen Beispiel ist der übergeordnete Knoten der Knoten **Customers** ).

     Visual Studio legt einige Eigenschaften für das Steuerelement fest, um die Such Bindung zu konfigurieren. In der folgenden Tabelle werden die Eigenschaften aufgelistet, die von Visual Studio geändert werden. Bei Bedarf können Sie diese Eigenschaften im XAML-oder im **Eigenschaften** Fenster ändern.

    |property|Erklärung der Einstellung|
    |--------------|----------------------------|
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|Diese Eigenschaft gibt die Auflistung oder Bindung an, die verwendet wird, um die im Steuerelement angezeigten Daten zu erhalten. Visual Studio legt diese Eigenschaft auf die <xref:System.Windows.Data.CollectionViewSource> für die übergeordneten Daten fest, die Sie in das Steuerelement gezogen haben.|
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|Diese Eigenschaft gibt den Pfad des Datenelements an, das im-Steuerelement angezeigt wird. Visual Studio legt diese Eigenschaft auf die erste Spalte oder Eigenschaft in den übergeordneten Daten fest, und zwar nach dem Primärschlüssel, der einen Zeichen folgen-Datentyp aufweist.<br /><br /> Wenn Sie eine andere Spalte oder Eigenschaft in den übergeordneten Daten anzeigen möchten, ändern Sie diese Eigenschaft in den Pfad einer anderen Eigenschaft.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Visual Studio bindet diese Eigenschaft an die Spalte oder Eigenschaft der untergeordneten Daten, die Sie in den Designer gezogen haben. Dies ist der Fremdschlüssel für die übergeordneten Daten.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Diese Eigenschaft wird von Visual Studio auf den Pfad der Spalte oder Eigenschaft der untergeordneten Daten festgelegt, die den Fremdschlüssel zu den übergeordneten Daten ist.|

## <a name="see-also"></a>Siehe auch
 [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md) [Anzeigen verwandter Daten in WPF-Anwendungen](../data-tools/display-related-data-in-wpf-applications.md) Exemplarische Vorgehensweise: Anzeigen verknüpfter [Daten in einer WPF-Anwendung](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)
