---
title: Dokumenthostelement
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio]
- documents [Office development in Visual Studio], document host items
- document host items
- Word [Office development in Visual Studio], Word documents
- Word [Office development in Visual Studio]
- Word documents
- host items [Office development in Visual Studio], Document
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8710fb703b353b267e7057973865cf845ebf79a9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62976489"
---
# <a name="document-host-item"></a>Dokumenthostelement
  Das <xref:Microsoft.Office.Tools.Word.Document> Hostelement ist ein Typ, der den <xref:Microsoft.Office.Interop.Word.Document> -Typ aus der primären Interopassembly für Word erweitert. Das <xref:Microsoft.Office.Tools.Word.Document> -Hostelement stellt die gleichen Eigenschaften, Methoden und Ereignisse wie ein <xref:Microsoft.Office.Interop.Word.Document> -Objekt bereit, es macht jedoch auch zusätzliche Ereignisse verfügbar und fungiert als Container für Hoststeuerelemente und Windows Forms-Steuerelemente.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 In Projekten auf Dokumentebene gibt es ein <xref:Microsoft.Office.Tools.Word.Document> -Standardhostelement, das das Dokument im Projekt darstellt. In VSTO-Add-In-Projekten können Sie <xref:Microsoft.Office.Tools.Word.Document> -Hostelemente zur Laufzeit generieren.

## <a name="understand-the-document-host-item-in-document-level-projects"></a>Verstehen des dokumenthostelements in Projekten auf Dokumentebene
 Verwenden Sie die `ThisDocument` -Klasse, um auf das Dokument im Projekt zuzugreifen. Wenn Sie ein Projekt auf Dokumentebene erstellen, generiert Visual Studio die `ThisDocument` -Klasse, die als Kommunikationsverbindung zwischen Word und dem Anpassungscode dient. Über die `ThisDocument` -Klasse erhalten Sie Zugriff auf Member des <xref:Microsoft.Office.Tools.Word.Document> -Hostelements, um grundlegende Aufgaben in der Anpassung auszuführen, z. B. das Ausführen von Code, wenn das Dokument geöffnet bzw. geschlossen wird. Sie können die Klasse auch verwenden, um dem Dokument Steuerelemente hinzuzufügen. Sie können Steuerelemente an Daten binden, Benutzerinformationen abfragen und auf Benutzeraktionen reagieren, indem Sie verschiedene Gruppen von Steuerelementen kombinieren und Code schreiben. Weitere Informationen finden Sie unter [Programmieren von Anpassungen auf Dokumentebene](../vsto/programming-document-level-customizations.md).

 Die `ThisDocument` -Klasse stellt einen Ausgangspunkt bereit, an dem Sie mit dem Schreiben von Code im Projekt beginnen können. Da die Klasse die gleichen Eigenschaften, Methoden und Ereignisse wie das <xref:Microsoft.Office.Interop.Word.Document> -Objekt in der primären Interop_Assembly für Word bereitstellt, können Sie auch mit `ThisDocument` auf das Word-Objektmodell zugreifen. Weitere Informationen finden Sie unter [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md).

### <a name="limitations-of-the-document-host-item-in-document-level-projects"></a>Einschränkungen des dokumenthostelements in Projekten auf Dokumentebene
 Ein Projekt auf Dokumentebene kann nur ein <xref:Microsoft.Office.Tools.Word.Document> -Hostelement (die `ThisDocument` -Klasse) enthalten. Sie können keine neuen hinzufügen <xref:Microsoft.Office.Tools.Word.Document> -Hostelemente zur Entwurfszeit zu Ihrem Projekt, und Sie können nicht neu erstellen <xref:Microsoft.Office.Tools.Word.Document> Hostelemente zur Laufzeit von einer Anpassung auf Dokumentebene.

 Wenn Sie ein neues Worddokument zur Laufzeit erstellen, werden sie vom Typ <xref:Microsoft.Office.Interop.Word.Document>. Da das Arbeitsblatt kein Hostelement ist, kann es keine Hoststeuerelemente bzw. Windows Forms-Steuerelemente enthalten. Weitere Informationen zum Erstellen von Dokumenten zur Laufzeit finden Sie unter [Vorgehensweise: Programmgesteuertes Erstellen neuer Dokumente](../vsto/how-to-programmatically-create-new-documents.md).

## <a name="understand-document-host-items-in-application-level-projects"></a>Verstehen der Dokument-Hostelemente in Projekten auf Anwendungsebene
 In VSTO-Add-In-Projekten können Sie für jedes Dokument, das in Word geöffnet ist, zur Laufzeit ein <xref:Microsoft.Office.Tools.Word.Document> -Hostelement erstellen. Sie können das <xref:Microsoft.Office.Tools.Word.Document> -Hostelement verwenden, um dem zugeordneten Dokument Steuerelemente hinzuzufügen, oder um Ereignisse zu behandeln, die für <xref:Microsoft.Office.Interop.Word.Document> -Objekte nicht verfügbar sind.

 Verwenden Sie zum Generieren eines <xref:Microsoft.Office.Tools.Word.Document>-Hostelements die `GetVstoObject`-Methode. Weitere Informationen finden Sie unter [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="see-also"></a>Siehe auch
- [Hostelemente und Host-Steuerelementen (Übersicht)](../vsto/host-items-and-host-controls-overview.md)
- [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)
- [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md)
- [Einschränkungen für programmgesteuerte Aufgaben von Hostelementen und Hoststeuerelementen](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Erweitern von Word-Dokumenten und Excel-Arbeitsmappen in VSTO-Add-ins zur Laufzeit](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
