---
title: 'Gewusst wie: Auffüllen von Dokumenten mit Daten aus Diensten'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], populating with data
- Web services [Office development in Visual Studio], populating documents
- data [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4ac901b524818086d6dbf23b7b55487054170b3e
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758541"
---
# <a name="how-to-populate-documents-with-data-from-services"></a>Gewusst wie: Auffüllen von Dokumenten mit Daten aus Diensten

Der Datenzugriff funktioniert in Microsoft Office-Projekten auf Dokumentebene auf die gleiche Weise wie in Windows Forms-Projekten. Sie verwenden dieselben Tools und denselben Code, um die Daten in die Projektmappe einzufügen, und können außerdem Windows Forms-Steuerelemente zum Anzeigen der Daten verwenden. Darüber hinaus können Sie von so genannten Hoststeuerelemente profitieren – systemeigene Objekte in Microsoft Office Excel und Microsoft Office Word, die um Ereignisse und Datenbindungsfunktionen erweitert wurden. Weitere Informationen finden Sie unter [hosten Elemente und Übersicht zu Steuerelementen](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

Das folgende Beispiel zeigt, wie Sie Dokumenten zur Entwurfszeit datengebundene Steuerelemente hinzufügen. Ein Beispiel für datengebundene Steuerelemente in VSTO-Add-ins zur Laufzeit hinzufügen, finden Sie unter [Exemplarische Vorgehensweise: Binden an Daten von einem Dienst in einem VSTO-Add-in-Projekt](../vsto/walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project.md).

![Link zum Video](../vsto/media/playvideo.gif "Link zum Video") eine entsprechende Videodemo finden Sie unter [: interagieren mit Webdiensten aus Microsoft Excel Gewusst?](http://go.microsoft.com/fwlink/?LinkID=130284).

## <a name="to-populate-a-document-level-project-with-data-from-a-web-service"></a>Zum Auffüllen von einem Projekt auf Dokumentebene mit Daten von einem Webdienst

1.  Öffnen Sie das Fenster **Datenquellen** , und erstellen Sie für Ihr Projekt eine Dienstdatenquelle. Weitere Informationen finden Sie unter [Neue Datenquelle hinzufügen](../data-tools/add-new-data-sources.md).

2.  Ziehen Sie die gewünschte Tabelle oder das gewünschte Feld vom Fenster **Datenquellen** in Ihr Dokument.

     Im Dokument wird ein Steuerelement erstellt. Zudem werden für den Dienst eine an die Objektklassen des Projekts gebundene <xref:System.Windows.Forms.BindingSource> und Klassen generiert.

3.  Erstellen Sie in Ihrem Code eine Instanz der Webdienstklasse, die Sie in Schritt 1 eine Verbindung hergestellt.

4.  Wenn Eigenschaften, die für die Kommunikation mit dem Webdienst erforderlich sind, erstellen Sie Instanzen dieser Eigenschaften.

5.  Erstellen und senden Sie mithilfe der vom Webdienst bereitgestellten Methoden und der in Schritt 4 erstellten Dateninstanzen eine Datenanforderung.

     Die Methoden, die Sie verwenden, hängt davon ab, die vom Webdienst bietet.

6.  Weisen Sie die vom Webdienst, der <xref:System.Windows.Forms.BindingSource.DataSource%2A> Eigenschaft der <xref:System.Windows.Forms.BindingSource>.

Wenn Sie das Projekt ausführen, zeigen die Steuerelemente den ersten Datensatz in der Datenquelle an. Sie können einen Bildlauf durch die Datensätze ermöglichen, indem Sie die „Currency“-Ereignisse mit den Objekten in der <xref:System.Windows.Forms.BindingSource>verarbeiten.

## <a name="see-also"></a>Siehe auch

- [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Neue Datenquelle hinzufügen](../data-tools/add-new-data-sources.md)
- [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Gewusst wie: Auffüllen von Arbeitsblättern mit Daten aus einer Datenbank](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Gewusst wie: Auffüllen von Dokumenten mit Daten aus Objekten](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Gewusst wie: Auffüllen von Dokumenten mit Daten aus einer Datenbank](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Gewusst wie: Aktualisieren einer Datenquelle mit Daten eines Hoststeuerelements](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)