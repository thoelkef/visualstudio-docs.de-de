---
title: Anzeigen zugehöriger Daten in WPF-Anwendungen
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
ms.assetid: 3aa80194-0191-474d-9d28-5ec05654b426
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: da6f276e714c816ea9b3c1b735ad50f31ffdc3c0
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55931506"
---
# <a name="display-related-data-in-wpf-applications"></a>Anzeigen zugehöriger Daten in WPF-Anwendungen

In einigen Anwendungen empfiehlt es sich zum Arbeiten mit Daten, die stammen aus mehreren Tabellen oder Entitäten, die in einer über-/ unterordnungsbeziehung miteinander verknüpft sind. Beispielsweise möchten Sie ein Raster anzuzeigen, die Kunden aus einem `Customers` Tabelle. Wenn der Benutzer einen bestimmten Kunden auswählt, handelt es sich bei einem anderen Raster zeigt die Aufträge dieses Kunden aus einem verbundenen `Orders` Tabelle.

Sie können angeben, Erstellen von datengebundenen Steuerelementen, die zugehörigen Daten anzeigen, indem das Ziehen von Elementen aus der **Datenquellen** in den WPF-Designer.

## <a name="to-create-controls-that-display-related-records"></a>So erstellen Sie Steuerelemente, die verknüpfte Datensätze anzeigen

1. Klicken Sie im Menü **Daten** auf **Datenquellen anzeigen**, um das Fenster **Datenquellen** zu öffnen.

2. Klicken Sie auf **Neue Datenquelle hinzufügen**, und führen Sie den **Assistenten zum Konfigurieren von Datenquellen** aus.

3. Öffnen Sie den WPF-Designer, und stellen Sie sicher, dass der Designer ein Container enthält, die ein gültiges Ablageziel für die Elemente in der **Datenquellen** Fenster.

     Weitere Informationen über gültige Ablageziele finden Sie unter [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

4. In der **Datenquellen** Fenster, erweitern Sie den Knoten, die die übergeordnete Tabelle darstellt oder ein Objekt in der Beziehung. Die übergeordnete Tabelle oder das Objekt ist auf der Seite "1" einer 1: n Beziehung.

5. Ziehen Sie den übergeordneten Knoten (oder einzelne Elemente im übergeordneten Knoten) aus der **Datenquellen** auf ein gültiges Ablageziel im Designer.

     Visual Studio generiert XAML, das neue datengebundene Steuerelemente für jedes Element erstellt, die Sie ziehen. Das XAML fügt auch ein neues <xref:System.Windows.Data.CollectionViewSource> für die übergeordnete Tabelle oder ein Objekt, das die Ressourcen des Ablageziels. Für einige Datenquellen generiert Visual Studio auch Code aus, um die Daten in die übergeordnete Tabelle oder das Objekt laden. Weitere Informationen finden Sie unter [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

6. In der **Datenquellen** Fenster Suchen Sie die zugehörige untergeordnete Tabelle oder das Objekt. Verknüpfte untergeordnete Tabellen und Objekte werden als erweiterbare Knoten am unteren Rand des übergeordneten Knotens der Liste der Daten.

7. Ziehen Sie den untergeordneten Knoten (oder einzelne Elemente in der untergeordnete Knoten) aus der **Datenquellen** auf ein gültiges Ablageziel im Designer.

     Visual Studio generiert XAML, das neue datengebundene Steuerelemente für jedes der Elemente erstellt, die Sie ziehen. Das XAML fügt auch ein neues <xref:System.Windows.Data.CollectionViewSource> für die untergeordnete Tabelle oder ein Objekt, das die Ressourcen des Ablageziels. Diese neue <xref:System.Windows.Data.CollectionViewSource> an die übergeordnete Tabelle oder ein Objekt, das Sie gerade in den Designer gezogen haben die Eigenschaft gebunden ist. Für einige Datenquellen generiert Visual Studio auch Code aus, um die Daten in die untergeordnete Tabelle oder ein Objekt zu laden.

     Die folgende Abbildung veranschaulicht den dazugehörigen **Bestellungen** Tabelle mit den **Kunden** Tabelle in einem Dataset in der **Datenquellen** Fenster.

     ![Relation im Datenquellenfenster](../data-tools/media/datasources2.gif)

## <a name="see-also"></a>Siehe auch

- [Binden von WPF-Steuerelementen an Daten in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Erstellen von Nachschlagetabellen in WPF-Anwendungen](../data-tools/create-lookup-tables-in-wpf-applications.md)