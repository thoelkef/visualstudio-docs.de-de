---
title: Binden von Windows Forms-Steuerelementen an Daten
ms.date: 11/03/2017
ms.topic: conceptual
helpviewer_keywords:
- data [Windows Forms], data sources
- Windows Forms, data binding
- Windows Forms, displaying data
- displaying data on forms
- forms, displaying data
- data sources, displaying data
- displaying data, Windows Forms
- data [Windows Forms], displaying
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6b961af0bf35bb4476f9f336fcf5298bb0bd3651
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55951669"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Binden von Windows Forms-Steuerelementen an Daten in Visual Studio

Sie können Daten für Benutzer der Anwendung anzeigen, indem Sie Daten an Windows Forms binden. Ziehen Sie Elemente aus, um diese datengebundene Steuerelemente zu erstellen, die **Datenquellen** auf Windows Forms-Designer in Visual Studio.

![Ziehen Sie von Datenquellenvorgang](../data-tools/media/raddata-data-source-drag-operation.png)

> [!TIP]
> Wenn die **Datenquellen** nicht sichtbar ist, können Sie Sie öffnen, indem Sie die Auswahl **Ansicht** > **Other Windows** > **Datenquellen** , oder durch Drücken der **UMSCHALT**+**Alt**+**D**. Benötigen Sie ein Projekt, öffnen Sie in Visual Studio finden Sie unter den **Datenquellen** Fenster.

Bevor Sie Elemente ziehen, können Sie den Typ des Steuerelements festlegen, die, denen Sie binden möchten. Je nachdem, ob Sie in der Tabelle selbst oder eine einzelne Spalte auswählen, werden unterschiedliche Werte angezeigt.  Sie können auch benutzerdefinierte Werte festlegen. Für eine Tabelle **Details** bedeutet, dass jede Spalte an einem separaten Steuerelement gebunden ist.

![Binden Sie die Datenquelle an DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png)

## <a name="bindingsource-and-bindingnavigator-controls"></a>BindingSource und BindingNavigator-Steuerelement

Die <xref:System.Windows.Forms.BindingSource>-Komponente dient zwei Zwecken. Erstens stellt es eine Abstraktionsebene bereit, wenn die Steuerelemente an Daten gebunden. Steuerelemente im Formular gebunden sind, um die <xref:System.Windows.Forms.BindingSource> Komponente statt direkt an eine Datenquelle. Zweitens kann so eine Auflistung von Objekten verwaltet werden. Wenn Sie zur <xref:System.Windows.Forms.BindingSource>-Komponente einen Typ hinzuzufügen, wird eine Liste dieses Typs erstellt.

Weitere Informationen über die <xref:System.Windows.Forms.BindingSource>-Komponente finden Sie unter:

- [BindingSource component (BindingSource-Komponente)](/dotnet/framework/winforms/controls/bindingsource-component)

- [BindingSource component overview (Übersicht über die BindingSource-Komponente)](/dotnet/framework/winforms/controls/bindingsource-component-overview)

- [BindingSource component architecture (Architektur der BindingSource-Komponente)](/dotnet/framework/winforms/controls/bindingsource-component-architecture)

Die [BindingNavigator-Steuerelement](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms) bietet eine Benutzeroberfläche zum Navigieren durch Daten, die von einer Windows-Anwendung angezeigt.

## <a name="bind-to-data-in-a-datagridview-control"></a>Binden Sie an Daten in einem DataGridView-Steuerelement

Für eine [DataGridView-Steuerelement](/dotnet/framework/winforms/controls/datagridview-control-overview-windows-forms), die gesamte Tabelle auf dieses einzelne Steuerelement gebunden ist. Beim Ziehen einer **DataGridView** auf das Formular, ein Tool zu entfernen, für die Navigation in Datensätzen (<xref:System.Windows.Forms.BindingNavigator>) wird auch angezeigt. Die Komponenten [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource> und <xref:System.Windows.Forms.BindingNavigator> werden in der Komponentenleiste angezeigt. In der folgenden Abbildung wird eine [TableAdapterManager](https://msdn.microsoft.com/library/bb384426.aspx) wird ebenfalls hinzugefügt werden, da die Customers-Tabelle eine Beziehung zu der Orders-Tabelle hat. Diese Variablen werden in den automatisch generierten Code als Private Member in der Form-Klasse deklariert. Die automatisch generierten Code für das Ausfüllen der **DataGridView** befindet sich in der `Form_Load` -Ereignishandler. Der Code zum Speichern der Daten zum Aktualisieren der Datenbank befindet sich der `Save` -Ereignishandler für die **BindingNavigator**. Sie können verschieben oder diesen Code nach Bedarf ändern.

![GridView mit BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png)

Sie können das Verhalten der Anpassen der **DataGridView** und **BindingNavigator** durch Klicken auf das Smarttag, in der oberen rechten Ecke der einzelnen:

![DataGridView-Steuerelement und Bindung Navigator Smarttags](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png)

Wenn die Steuerelemente die Anwendung muss nicht in verfügbar sind die **Datenquellen** Fenster können Sie Steuerelemente hinzufügen. Weitere Informationen finden Sie unter [Hinzufügen benutzerdefinierter Steuerelemente zum Datenquellenfenster](../data-tools/add-custom-controls-to-the-data-sources-window.md).

Sie können Elemente auch ziehen die **Datenquellen** auf Steuerelemente, die bereits in einem Formular das Steuerelement an Daten gebunden. Ein Steuerelement, das bereits an Daten gebunden ist, hat seine Daten, die Bindungen auf das Element zuletzt gezogen zurückgesetzt. Um gültige Ablageziele sein, müssen der Steuerelemente zum Anzeigen von der zugrunde liegenden Datentyp des Element gezogene auf ihn von der Lage sein den **Datenquellen** Fenster. Es ist z. B. nicht zulässig, ein Element zu ziehen, die den Datentyp <xref:System.DateTime> auf eine <xref:System.Windows.Forms.CheckBox>, da die <xref:System.Windows.Forms.CheckBox> kann keine Datum anzeigen.

## <a name="bind-to-data-in-individual-controls"></a>Binden Sie an Daten in einzelnen Steuerelementen

Wenn Sie eine Datenquelle binden **Details**, jede Spalte im Dataset auf einem separaten Steuerelement gebunden ist.

![Binden Sie die Datenquelle zu details](../data-tools/media/raddata-bind-data-source-to-details.png)

> [!IMPORTANT]
> Beachten Sie, dass in der vorherigen Abbildung, die Sie aus der Eigenschaft "Orders" in der Customers-Tabelle, nicht aus der Orders-Tabelle ziehen. Durch Bindung an die `Customer.Orders` Eigenschaft Navigationsbefehle vorgenommen, der **DataGridView** werden sofort in den Details-Steuerelementen. Wenn Sie aus der Tabelle Orders gezogen haben, die Steuerelemente weiterhin auf das Dataset gebunden werden würde, aber nicht würden sie nicht mit synchronisiert die **DataGridView**.

Die folgende Abbildung zeigt die von datengebundenen Steuerelementen, die dem Formular hinzugefügt werden, nachdem die Orders-Eigenschaft in der Tabelle Customers gebunden ist **Details** in die **Datenquellen** Fenster.

![Zu den Details gebunden Orders-Tabelle](../data-tools/media/raddata-orders-table-bound-to-details.png)

Beachten Sie außerdem, dass für jedes Steuerelement ein Smarttag. Dieses Tag ermöglicht Anpassungen, die auf dieses Steuerelement wird nur angewendet werden.

## <a name="see-also"></a>Siehe auch

- [Binding controls to data in Visual Studio (Binden von Steuerelementen an Daten in Visual Studio)](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Die Datenbindung in Windows Forms ((.NET Framework)](/dotnet/framework/winforms/windows-forms-data-binding)