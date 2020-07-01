---
title: 'Gewusst wie: Auffüllen von Dokumenten mit Daten aus Objekten'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], populating with data
- data [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 38461fc30f71a811033ea70bfe560a6492f56e12
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547172"
---
# <a name="how-to-populate-documents-with-data-from-objects"></a>Gewusst wie: Auffüllen von Dokumenten mit Daten aus Objekten

Der Zugriff auf Daten in einem Datenobjekt funktioniert in Microsoft Office Word-Projekten auf Dokumentebene auf die gleiche Weise wie in Windows Forms-Projekten. Sie verwenden dieselben Tools und denselben Code, um die Daten aus einem Objekt in die Projektmappe einzufügen, und können Windows Forms-Steuerelemente zum Anzeigen der Daten verwenden. Darüber hinaus können Sie Daten mithilfe von Hoststeuerelementen anzeigen. Hoststeuerelemente sind systemeigene Objekte in Microsoft Office Word, die mit Ereignissen und Datenbindungsfunktion erweitert wurden. Weitere Informationen finden Sie unter [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

Sie müssen drei grundlegende Schritte ausführen, um das Dokument mit Daten aus einem Objekt aufzufüllen:

- Fügen Sie ein Steuerelement zum Dokument hinzu, das an Daten gebunden werden kann.

- Fügen Sie ein Datenobjekt zum Dokument hinzu.

- Verbinden Sie das Datenobjekt mit der BindingSource-Komponente.

## <a name="to-add-a-data-object"></a>So fügen Sie ein Datenobjekt hinzu

Öffnen Sie zum Hinzufügen eines Datenobjekts das Fenster **Datenquellen** , und erstellen Sie eine Datenquelle aus einem-Objekt. Weitere Informationen finden Sie unter [Neue Datenquelle hinzufügen](../data-tools/add-new-data-sources.md).

## <a name="connect-the-data-object-to-the-bindingsource"></a>Verbinden des Datenobjekts mit der BindingSource

In Projekten auf Dokumentebene fügen Sie Ihrem Dokument Steuerelemente hinzu und binden diese zur Entwurfszeit an Daten.

In VSTO-Add-In-Projekten erstellen Sie Steuerelemente und binden diese zur Laufzeit.

### <a name="document-level-projects"></a>Projekte auf Dokument Ebene

So verbinden Sie das Datenobjekt mit der BindingSource:

1. Ziehen Sie das gewünschte Datenfeld vom Fenster **Datenquellen** in Ihr Dokument. Dadurch wird automatisch ein Steuerelement erstellt.

2. Erstellen Sie im Code eine Instanz des Typs des Objekts, das Sie für die Datenquelle ausgewählt haben.

3. Weisen Sie die Instanz der <xref:System.Windows.Forms.BindingSource.DataSource%2A> -Eigenschaft der <xref:System.Windows.Forms.BindingSource>-Komponente zu.

### <a name="application-level-projects"></a>Projekte auf Anwendungsebene

So verbinden Sie das Datenobjekt mit der BindingSource:

1. Erstellen Sie im Code eine Instanz des Typs des Objekts, das der Datenquelle zugewiesen wird.

2. Erstellen Sie eine Instanz einer <xref:System.Windows.Forms.BindingSource>-Komponente:

3. Weisen Sie die Datenquelleninstanz der <xref:System.Windows.Forms.BindingSource.DataSource%2A> -Eigenschaft der <xref:System.Windows.Forms.BindingSource>-Komponente zu.

4. Fügen Sie die Datenquelle als eine Datenbindung zum Steuerelement hinzu.

## <a name="see-also"></a>Weitere Informationen

- [Neue Datenquelle hinzufügen](../data-tools/add-new-data-sources.md)
- [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Gewusst wie: Auffüllen von Dokumenten mit Daten aus einer Datenbank](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Vorgehensweise: Aktualisieren einer Datenquelle mit Daten eines Host Steuer Elements](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Übersicht über die BindingSource-Komponente](/dotnet/framework/winforms/controls/bindingsource-component-overview)