---
title: 'Gewusst wie: Auffüllen von Dokumenten mit Daten aus einer Datenbank'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents, populating with data
- data, adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: af068fc9cdacc0f681232ee4c7424d67d77f3a11
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756800"
---
# <a name="how-to-populate-documents-with-data-from-a-database"></a>Gewusst wie: Auffüllen von Dokumenten mit Daten aus einer Datenbank

Sie können in Microsoft Office-Projekten auf Dokumentebene auf die gleiche Weise auf Daten zugreifen wie in Windows Forms-Projekten. Sie verwenden dieselben Tools und denselben Code, um die Daten aus einer Datenbank in die Projektmappe einzufügen, und können Windows Forms-Steuerelemente zum Anzeigen der Daten verwenden.

Darüber hinaus können Sie Daten mithilfe von Hoststeuerelementen anzeigen. Hoststeuerelemente sind systemeigene Objekte in Microsoft Office Word, die mit Ereignissen und Datenbindungsfunktion erweitert wurden. Weitere Informationen finden Sie unter [hosten Elemente und Übersicht zu Steuerelementen](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

Das folgende Beispiel zeigt, wie Sie datengebundene Steuerelemente in Projekten auf Dokumentebene mithilfe eines Designers hinzufügen. Ein Beispiel, das von datengebundenen Steuerelementen zur Laufzeit in VSTO-Add-in-Projekten hinzufügen, finden Sie unter [Exemplarische Vorgehensweise: einfache Datenbindung in VSTO-Add-in-Projekt](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).

![Link zum Video](../vsto/media/playvideo.gif "Link zum Video") eine entsprechende Videodemo finden Sie unter [Binden von Daten an Word 2007-Inhalte steuert mithilfe von Visual Studio-Tools für Office System (3.0)](http://go.microsoft.com/fwlink/?LinkId=136785).

## <a name="add-a-control-to-a-document-at-design-time"></a>Hinzufügen eines Steuerelements zu einem Dokument zur Entwurfszeit

### <a name="to-populate-a-document-with-data-from-a-database"></a>So füllen Sie ein Dokument mit Daten aus einer Datenbank auf

1.  Öffnen Sie in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ein Word-Projekt auf Dokumentebene, während das Dokument im Designer geöffnet ist.

2.  Öffnen der **Datenquellen** Fenster, und erstellen Sie eine Datenquelle aus einer Datenbank. Weitere Informationen finden Sie unter [neue Verbindungen hinzufügen](../data-tools/add-new-connections.md).

3.  Ziehen Sie das Feld aus der **Datenquellen** Fenster in Ihr Dokument.

Ein Inhaltssteuerelement wird dem Dokument hinzugefügt. Der Typ des Inhaltssteuerelements hängt vom Datentyp des ausgewählten Felds ab. Weitere Informationen finden Sie unter [Inhaltssteuerelemente](../vsto/content-controls.md).

Sie können ein anderes Steuerelement hinzufügen, indem Sie das Datenfeld im Auswählen der **Datenquellen** Fenster, und klicken Sie dann ein anderes Steuerelement auswählen, aus der Dropdown-Liste.

## <a name="objects-in-the-project"></a>Objekte im Projekt

Neben dem Steuerelement werden die folgenden datenbezogenen Objekte dem Projekt automatisch hinzugefügt:

-   Ein typisiertes Dataset, das die Datentabellen kapselt, mit denen Sie in der Datenbank eine Verbindung hergestellt haben. Weitere Informationen finden Sie unter [datasettools in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

-   Eine <xref:System.Windows.Forms.BindingSource>, durch die das Steuerelement mit dem typisierten Dataset verbunden wird. Weitere Informationen finden Sie unter [Übersicht über die BindingSource-Komponente](/dotnet/framework/winforms/controls/bindingsource-component-overview).

-   Einen TableAdapter, der das typisierte Dataset mit der Datenbank verbunden. Weitere Informationen finden Sie unter [erstellen und Konfigurieren eines TableAdapters](../data-tools/create-and-configure-tableadapters.md).

-   Einen TableAdapterManager, dient zum Koordinieren von Tabellenadaptern im Dataset um hierarchische Updates zu aktivieren. Weitere Informationen finden Sie unter [hierarchische Aktualisierung](../data-tools/hierarchical-update.md) und [TableAdapterManager-Verweis](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference).

Beim Ausführen des Projekts zeigt das Steuerelement den ersten Datensatz in der Datenquelle an. Sie können die <xref:System.Windows.Forms.BindingSource> verwenden, um Benutzern einen Bildlauf in den Datensätzen zu ermöglichen.

### <a name="to-scroll-through-the-records"></a>So führen Sie einen Bildlauf durch die Datensätze durch

-   Verwenden Sie <xref:System.Windows.Forms.BindingSource>-Methoden wie <xref:System.Windows.Forms.BindingSource.MoveNext%2A> und <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.

Informationen dazu, wie Sie Updates für das typisierte Dataset und die Datenbank zu senden, finden Sie unter [Vorgehensweise: Aktualisieren einer Datenquelle mit Daten eines Hoststeuerelements](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

## <a name="see-also"></a>Siehe auch

- [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Neue Datenquelle hinzufügen](../data-tools/add-new-data-sources.md)
- [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Gewusst wie: Auffüllen von Dokumenten mit Daten aus Objekten](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Gewusst wie: Aktualisieren einer Datenquelle mit Daten eines Hoststeuerelements](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Verwenden Sie lokaler Datenbankdateien in Office Solutions (Übersicht)](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Übersicht über die BindingSource-Komponente](/dotnet/framework/winforms/controls/bindingsource-component-overview)