---
title: 'Gewusst wie: Auffüllen von Dokumenten mit Daten aus Diensten'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], populating with data
- Web services [Office development in Visual Studio], populating documents
- data [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4f53000f7d6aa8bdd8261bbe5658607918b6b449
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985871"
---
# <a name="how-to-populate-documents-with-data-from-services"></a>Gewusst wie: Auffüllen von Dokumenten mit Daten aus Diensten

Der Datenzugriff funktioniert in Microsoft Office-Projekten auf Dokumentebene auf die gleiche Weise wie in Windows Forms-Projekten. Sie verwenden dieselben Tools und denselben Code, um die Daten in die Projektmappe einzufügen, und können außerdem Windows Forms-Steuerelemente zum Anzeigen der Daten verwenden. Darüber hinaus können Sie von so genannten Hoststeuerelemente profitieren – systemeigene Objekte in Microsoft Office Excel und Microsoft Office Word, die um Ereignisse und Datenbindungsfunktionen erweitert wurden. Weitere Informationen finden Sie unter [Übersicht über Host Elemente und Host Steuerelemente](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

Das folgende Beispiel zeigt, wie Sie Dokumenten zur Entwurfszeit datengebundene Steuerelemente hinzufügen. Ein Beispiel zum Hinzufügen von Daten gebundenen Steuerelementen in VSTO-Add-Ins zur Laufzeit finden Sie unter Exemplarische Vorgehensweise [: Binden an Daten aus einem Dienst in einem VSTO-Add-in-Projekt](../vsto/walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project.md).

## <a name="to-populate-a-document-level-project-with-data-from-a-web-service"></a>So füllen Sie ein Projekt auf Dokument Ebene mit Daten aus einem Webdienst auf

1. Öffnen Sie das Fenster **Datenquellen** , und erstellen Sie für Ihr Projekt eine Dienstdatenquelle. Weitere Informationen finden Sie unter [Neue Datenquelle hinzufügen](../data-tools/add-new-data-sources.md).

2. Ziehen Sie die gewünschte Tabelle oder das gewünschte Feld vom Fenster **Datenquellen** in Ihr Dokument.

     Im Dokument wird ein Steuerelement erstellt. Zudem werden für den Dienst eine an die Objektklassen des Projekts gebundene <xref:System.Windows.Forms.BindingSource> und Klassen generiert.

3. Erstellen Sie in Ihrem Code eine Instanz der Webdienst Klasse, mit der Sie in Schritt 1 eine Verbindung hergestellt haben.

4. Wenn für die Kommunikation mit dem Webdienst Eigenschaften erforderlich sind, erstellen Sie Instanzen dieser Eigenschaften.

5. Erstellen und senden Sie mithilfe der vom Webdienst bereitgestellten Methoden und der in Schritt 4 erstellten Dateninstanzen eine Datenanforderung.

     Welche Methoden Sie verwenden, hängt davon ab, was der Webdienst bietet.

6. Weisen Sie die Daten Antwort des Webdiensts der <xref:System.Windows.Forms.BindingSource.DataSource%2A>-Eigenschaft des <xref:System.Windows.Forms.BindingSource>zu.

Wenn Sie das Projekt ausführen, zeigen die Steuerelemente den ersten Datensatz in der Datenquelle an. Sie können einen Bildlauf durch die Datensätze ermöglichen, indem Sie die „Currency“-Ereignisse mit den Objekten in der <xref:System.Windows.Forms.BindingSource>verarbeiten.

## <a name="see-also"></a>Siehe auch

- [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Neue Datenquelle hinzufügen](../data-tools/add-new-data-sources.md)
- [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Gewusst wie: Auffüllen von Arbeitsblättern mit Daten aus einer Datenbank](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Gewusst wie: Auffüllen von Dokumenten mit Daten aus Objekten](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Gewusst wie: Auffüllen von Dokumenten mit Daten aus einer Datenbank](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Vorgehensweise: Aktualisieren einer Datenquelle mit Daten eines Host Steuer Elements](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)