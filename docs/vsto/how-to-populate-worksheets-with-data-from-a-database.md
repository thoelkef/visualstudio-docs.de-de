---
title: 'Vorgehensweise: Auffüllen von Arbeitsblättern mit Daten aus einer Datenbank'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets [Office development in Visual Studio], populating
- databases [Office development in Visual Studio], populating worksheets
- data [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 53267cdd429b9a4d8848026e460776359b55c023
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/27/2018
ms.locfileid: "53802873"
---
# <a name="how-to-populate-worksheets-with-data-from-a-database"></a>Vorgehensweise: Auffüllen von Arbeitsblättern mit Daten aus einer Datenbank

Sie können Daten in Office-Projekten auf Dokumentebene auf die gleiche Weise zugreifen, dass Sie Daten in Windows Forms-Projekte zugreifen. Sie verwenden dieselben Tools und denselben Code, um die Daten in die Projektmappe einzufügen, und können außerdem Windows Forms-Steuerelemente zum Anzeigen der Daten verwenden. Darüber hinaus können Sie die so genannten Hoststeuerelemente sind systemeigene Objekte in Microsoft Office Excel, die mit Ereignissen und Datenbindung Funktion erweitert wurden nutzen. Weitere Informationen finden Sie unter [hosten Elemente und Übersicht zu Steuerelementen](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

Das folgende Beispiel zeigt, wie Sie datengebundene Steuerelemente in Projekten auf Dokumentebene mithilfe eines Designers hinzufügen. Ein Beispiel für datengebundene Steuerelemente in Projekten auf Anwendungsebene zur Laufzeit hinzufügen, finden Sie unter [Exemplarische Vorgehensweise: Komplexe Datenbindung in VSTO-Add-in-Projekt](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md).

![Link zum Video](../vsto/media/playvideo.gif "Link zum Video") eine entsprechende Videodemo finden Sie unter [Gewusst wie: Übertragen von Daten in ein Excel-Arbeitsblatt? ](http://go.microsoft.com/fwlink/?LinkID=130277), und [Gewusst wie: Verwenden von Datenbankdaten in Excel? ](http://go.microsoft.com/fwlink/?LinkID=130287).

## <a name="add-a-data-bound-control-to-a-worksheet-at-design-time"></a>Hinzufügen eines datengebundenen Steuerelements zu einem Arbeitsblatt zur Entwurfszeit

### <a name="to-populate-a-worksheet-with-data-from-a-database"></a>Um ein Arbeitsblatt mit Daten aus einer Datenbank aufzufüllen.

1.  Öffnen Sie ein Excel-Projekt auf Dokumentebene in Visual Studio, mit dem Arbeitsblatt im Designer geöffnet.

2.  Öffnen Sie das Fenster **Datenquellen** , und erstellen Sie für Ihr Projekt eine Datenquelle. Weitere Informationen finden Sie unter [neue Verbindungen hinzufügen](../data-tools/add-new-connections.md).

3.  Ziehen Sie das Feld oder die Tabelle aus der **Datenquellen** in das Arbeitsblatt.

Eines der folgenden Steuerelemente wird auf dem Arbeitsblatt erstellt:

-   Wenn Sie ein Feld, ziehen Sie eine <xref:Microsoft.Office.Tools.Excel.NamedRange> Steuerelement auf dem Arbeitsblatt erstellt wird. Weitere Informationen finden Sie unter [NamedRange-Steuerelement](../vsto/namedrange-control.md).

-   Wenn Sie eine Tabelle, ziehen Sie eine <xref:Microsoft.Office.Tools.Excel.ListObject> Steuerelement auf dem Arbeitsblatt erstellt wird. Weitere Informationen finden Sie unter [ListObject-Steuerelement](../vsto/listobject-control.md).

Sie können das Feld oder ein anderes Steuerelement hinzufügen, indem Sie die Tabelle auswählen der **Datenquellen** Fenster, und klicken Sie dann ein anderes Steuerelement auswählen, aus der Dropdown-Liste.

## <a name="objects-in-the-project"></a>Objekte im Projekt

Neben dem Steuerelement werden die folgenden datenbezogenen Objekte dem Projekt automatisch hinzugefügt:

-   Ein typisiertes Dataset, das die Datentabellen kapselt, mit denen Sie in der Datenbank eine Verbindung hergestellt haben. Weitere Informationen finden Sie unter [datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

-   Eine <xref:System.Windows.Forms.BindingSource>, durch die das Steuerelement mit dem typisierten Dataset verbunden wird. Weitere Informationen finden Sie unter [Übersicht über die BindingSource-Komponente](/dotnet/framework/winforms/controls/bindingsource-component-overview).

-   Einen TableAdapter, der das typisierte Dataset mit der Datenbank verbunden. Weitere Informationen finden Sie unter [Übersicht über TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

-   Einen TableAdapterManager, dient zum Koordinieren von Tabellenadaptern im Dataset um hierarchische Updates zu aktivieren. Weitere Informationen finden Sie unter [hierarchische Aktualisierung](../data-tools/hierarchical-update.md) und [TableAdapterManager-Verweis](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference).

Beim Ausführen des Projekts zeigt das Steuerelement den ersten Datensatz in der Datenquelle an. Sie können die <xref:System.Windows.Forms.BindingSource> verwenden, um Benutzern einen Bildlauf in den Datensätzen zu ermöglichen.

### <a name="to-scroll-through-the-records"></a>So führen Sie einen Bildlauf durch die Datensätze durch

-   Verwenden Sie <xref:System.Windows.Forms.BindingSource>-Methoden wie <xref:System.Windows.Forms.BindingSource.MoveNext%2A> und <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.

Informationen dazu, wie Sie Updates für das typisierte Dataset und die Datenbank zu senden, finden Sie unter [Vorgehensweise: Aktualisieren einer Datenquelle mit Daten eines Hoststeuerelements](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

## <a name="see-also"></a>Siehe auch

- [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Neue Datenquelle hinzufügen](../data-tools/add-new-data-sources.md)
- [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Vorgehensweise: Auffüllen von Dokumenten mit Daten aus Objekten](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Vorgehensweise: Auffüllen von Dokumenten mit Daten aus einer Datenbank](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Vorgehensweise: Auffüllen von Dokumenten mit Daten aus Diensten](../vsto/how-to-populate-documents-with-data-from-services.md)
- [Vorgehensweise: Aktualisieren einer Datenquelle mit Daten eines Hoststeuerelements](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Gewusst wie: Übertragen von Daten in ein Excel-Arbeitsblatt](http://go.microsoft.com/fwlink/?LinkID=130277)
- [Gewusst wie: Verwenden von Datenbankdaten in Excel?](http://go.microsoft.com/fwlink/?LinkID=130287)