---
title: Erstellen von Nachschlagetabellen in WPF-Anwendungen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 78322512fdc59b4ba661bca0d40d1532ac4c98e2
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2017
---
# <a name="create-lookup-tables-in-wpf-applications"></a>Erstellen von Nachschlagetabellen in WPF-Anwendungen
Der Begriff *Nachschlagetabelle* (bezeichnet einen *Suche Bindung*) beschreibt ein Steuerelement, das Informationen aus einer Datentabelle, die anhand des Werts eines Fremdschlüsselfelds in einer anderen Tabelle anzeigt. Sie können eine Nachschlagetabelle erstellen, indem Sie den Hauptknoten der übergeordneten Tabelle ziehen oder Objekt in der **Datenquellen** auf ein Steuerelement, das bereits an eine Spalte oder Eigenschaft in einer verknüpften untergeordneten Tabelle gebunden ist.  
  
Als Beispiel kann eine Tabelle mit dem Namen `Orders` dienen, die Teil einer Verkaufsdatenbank ist und Aufträge enthält. Jeder Datensatz in der `Orders` Tabelle enthält eine `CustomerID` , der angibt, welcher Kunde den Auftrag erteilt. Die `CustomerID` ist ein Fremdschlüssel, der auf einen Kundendatensatz in zeigt den `Customers` Tabelle. Wenn Sie eine Liste der Aufträge anzeigen der `Orders` Tabelle, Sie können den tatsächlichen Kundennamen anstelle von anzeigen möchten die `CustomerID`. Da der Kundenname wird die `Customers` Tabelle, müssen Sie eine Nachschlagetabelle, um die Namen der Kunden zu erstellen. Die Suche wird die `CustomerID` Wert in der `Orders` aufzeichnen, um die Beziehung zu navigieren, und geben Sie den Namen des Kunden zurück.  
  
## <a name="to-create-a-lookup-table"></a>So erstellen Sie eine Suchtabelle  
  
1.  Fügen Sie eine der folgenden Typen von Datenquellen mit verbundenen Daten zu Ihrem Projekt hinzu:  
  
    -   DataSet oder ein Entity Data Model. 
  
    -   WCF-Datendienst, WCF-Dienst oder einen Webdienst. Weitere Informationen finden Sie unter [Vorgehensweise: Herstellen einer Verbindung mit Daten in einem Dienst](../data-tools/how-to-connect-to-data-in-a-service.md).  
  
    -   -Objekte. Weitere Informationen finden Sie unter [Binden an Objekte in Visual Studio](bind-objects-in-visual-studio.md).  
  
    > [!NOTE]
    >  Bevor Sie eine Nachschlagetabelle erstellen können, müssen zwei zusammengehörige Tabellen oder Objekte als Datenquelle für das Projekt vorhanden sein.  
  
2.  Öffnen der **WPF-Designer**, und stellen Sie sicher, dass der Designer einen Container enthält, ein gültiges Ablageziel für die Elemente in der **Datenquellen** Fenster.  
  
     Weitere Informationen zu gültigen Ablagezielen, finden Sie unter [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).  
  
3.  Auf der **Daten** Menü klicken Sie auf **Datenquellen anzeigen** So öffnen die **Datenquellen** Fenster.  
  
4.  Erweitern Sie die Knoten in der **Datenquellen** Fenster, bis Sie der übergeordneten Tabelle oder Objekt und die zugehörige untergeordnete Tabelle oder das Objekt angezeigt werden.  
  
    > [!NOTE]
    >  Die zugehörige untergeordnete Tabelle oder das Objekt ist der Knoten, der als ein erweiterbarer untergeordneter Knoten unter der übergeordneten Tabelle oder ein Objekt angezeigt wird.  
  
5.  Klicken Sie auf das Dropdownmenü für den untergeordneten Knoten, und wählen Sie **Details**.  
  
6.  Erweitern Sie den untergeordneten Knoten.  
  
7.  Klicken Sie unter den untergeordneten Knoten auf das Dropdownmenü für das Element, das die untergeordneten und übergeordneten Daten beziehen. (Im vorherigen Beispiel ist dies die **CustomerID** Knoten.) Wählen Sie eine der folgenden Typen von Steuerelementen, die Bindung der Suche zu unterstützen:  
  
    -   **ComboBox**  
  
    -   **ListBox**  
  
    -   **ListView**  
  
        > [!NOTE]
        >  Wenn die **ListBox** oder **ListView** Steuerelement nicht in der Liste angezeigt, Sie können diese Steuerelemente hinzufügen, um die Liste. Informationen finden Sie unter [festlegen, welches Steuerelement erstellt werden, beim Ziehen aus Datenquellenfenster](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
    -   Jedes benutzerdefinierte Steuerelement, das von abgeleitet ist <xref:System.Windows.Controls.Primitives.Selector>.  
  
        > [!NOTE]
        >  Für Informationen zum Hinzufügen benutzerdefinierter Steuerelemente zur Liste der Steuerelemente, für Elemente in auswählen kann der **Datenquellen** Fenster finden Sie unter [Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellenfenster](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
8.  Ziehen Sie den untergeordneten Knoten aus der **Datenquellen** auf einen Container im WPF-Designer. (Im vorherigen Beispiel ist der untergeordnete Knoten der **Aufträge** Knoten.)  
  
     Visual Studio generiert XAML, das neue datengebundene Steuerelemente für jedes der Elemente erstellt, die Sie ziehen. Der XAML-Code wird auch ein neues <xref:System.Windows.Data.CollectionViewSource> für die untergeordnete Tabelle oder das Objekt, das die Ressourcen des Ablageziels. Für einige Datenquellen generiert Visual Studio auch Code zum Laden von Daten in der Tabelle oder das Objekt. Weitere Informationen finden Sie unter [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).  
  
9. Ziehen Sie den übergeordneten Knoten aus der **Datenquellen** Fenster auf das Nachschlagesteuerelement für die Bindung, die Sie zuvor erstellt haben. (Im vorherigen Beispiel ist der übergeordnete Knoten der **Kunden** Knoten).  
  
     Visual Studio legt das Steuerelement so konfigurieren Sie die Bindung für die Suche einige Eigenschaften fest. Die folgende Tabelle enthält die Eigenschaften, die Visual Studio ändert. Wenn erforderlich, Sie diese Eigenschaften in XAML oder in ändern, können die **Eigenschaften** Fenster.  
  
    |Eigenschaft|Erklärung der Einstellung|  
    |--------------|----------------------------|  
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|Diese Eigenschaft gibt die Auflistung oder die Bindung, die verwendet wird, um die Daten abzurufen, die im Steuerelement angezeigt wird. Visual Studio legt diese Eigenschaft auf die <xref:System.Windows.Data.CollectionViewSource> für die übergeordneten Daten, die Sie an das Steuerelement gezogen haben.|  
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|Diese Eigenschaft gibt den Pfad des Datenelements, das im Steuerelement angezeigt wird. Visual Studio legt diese Eigenschaft auf die erste Spalte oder Eigenschaft in den übergeordneten Daten nach dem Primärschlüssel, der einen String-Datentyp aufweist.<br /><br /> Wenn Sie eine andere Spalte oder Eigenschaft in den übergeordneten Daten anzeigen möchten, ändern Sie diese Eigenschaft auf den Pfad einer anderen Eigenschaft.|  
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Visual Studio bindet diese Eigenschaft an die Spalte oder Eigenschaft der untergeordneten Daten, die Sie in den Designer gezogen haben. Dies ist der Fremdschlüssel für die übergeordneten Daten.|  
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Visual Studio legt diese Eigenschaft den Pfad der Spalte oder Eigenschaft der untergeordneten Daten, die der Fremdschlüssel für die übergeordneten Daten ist.|  
  
## <a name="see-also"></a>Siehe auch
[Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)   
[Zeigen Sie verknüpfter Daten in WPF-Anwendungen an](../data-tools/display-related-data-in-wpf-applications.md)   
[Exemplarische Vorgehensweise: Anzeigen verknüpfter Daten in einer WPF-Anwendung](../data-tools/display-related-data-in-wpf-applications.md)