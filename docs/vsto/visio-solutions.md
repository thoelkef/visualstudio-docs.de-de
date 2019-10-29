---
title: Visio-Lösungen
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], Visio
- solutions [Office development in Visual Studio], Visio
- Visio [Office development in Visual Studio]
- templates [Office development in Visual Studio], Visio
- projects [Office development in Visual Studio], Visio
- Office solutions [Office development in Visual Studio], Visio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a79b3c9964a24daf0a12ab90f47fb5903d89cdd0
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985509"
---
# <a name="visio-solutions"></a>Visio-Lösungen
  Visual Studio stellt Projektvorlagen bereit, die Sie zum Erstellen von VSTO-Add-Ins für Microsoft Office Visio verwenden können. Mit VSTO-Add-Ins können Sie Visio automatisieren, Visio -Features erweitern oder die Benutzeroberfläche (User Interface, UI) von Visio anpassen.

 Weitere Informationen zu VSTO-Add-Ins finden Sie unter "Einstieg in die [Programmierung von VSTO-Add-ins](../vsto/getting-started-programming-vsto-add-ins.md) und [Architektur von VSTO](../vsto/architecture-of-vsto-add-ins.md)-Add-Ins". Wenn Sie noch nicht mit der Programmierung mit Microsoft Office vertraut sind, finden Sie weitere Informationen unter [ &#40;Office-Entwicklung in Visual&#41;Studio](../vsto/getting-started-office-development-in-visual-studio.md).

 **Betrifft:** Die Informationen in diesem Thema betreffen VSTO-Add-In-Projekte für Visio 2010. Weitere Informationen finden Sie unter [Verfügbare Funktionen nach Office-Anwendung und Projekttyp](../vsto/features-available-by-office-application-and-project-type.md).

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-visio-by-using-the-visio-object-model"></a>Automatisieren von Visio mithilfe des Visio-Objektmodells
 Das Visio-Objektmodell stellt zahlreiche Klassen bereit, die Sie verwenden können, um Visio zum Erstellen von Diagrammen für Organigramme, Flussdiagramme, Projektzeitachsen, Netzwerkdiagramme, Büroräume und mehr automatisieren können. Die API ermöglicht Ihnen das Schreiben von Code zum Ausführen häufige anfallender Aufgaben:

- Erstellen und Positionieren von Shapes und Text in Diagrammen.

- Verwalten des Shape-Verhaltens basierend auf Geschäftslogik und Benutzereingaben.

- Steuern der Darstellung von Diagrammen (z. B. Schwenken und Zoomen).

- Anpassen der Benutzeroberfläche der Anwendung.

- Importieren externer Daten in Visio, Verknüpfen dieser Daten mit Shapes und grafische Darstellung auf einer Seite.

  Sie können schrittweise Anleitungen und Codebeispiele für die Verwendung des Visio-Objektmodells zum Arbeiten mit Dokumenten und Formen in [Arbeiten mit Visio-Dokumenten](../vsto/working-with-visio-documents.md) und zum [Arbeiten mit Visio-Formen](../vsto/working-with-visio-shapes.md)anzeigen.

  Für den Zugriff auf das Visio-Objektmodell aus einem VSTO-Add-In verwenden Sie das Feld `Application` der Klasse `ThisAddIn` in Ihrem Projekt. Das Feld `Application` gibt ein `Microsoft.Office.Interop.Visio.Application`-Objekt zurück, das die aktuelle Instanz von Visio darstellt. Weitere Informationen finden Sie unter [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

  Bei einem Aufruf des Visio-Objektmodells verwenden Sie Typen, die in der primären Interopassembly (PIA) für Visio bereitgestellt werden. Die primäre Interopassembly (PIA) dient als Brücke zwischen verwaltetem Code im VSTO-Add-In und dem COM-Objektmodell in Visio. Alle Typen in der Visio-PIA werden im Namespace `Microsoft.Office.Interop.Visio` definiert. Weitere Informationen zu primären Interopassemblys finden Sie unter [Übersicht &#40;über die Entwicklung&#41; von Office](../vsto/office-solutions-development-overview-vsto.md) -Projektmappen VSTO und [Office Primary Interopassemblys](../vsto/office-primary-interop-assemblies.md)

## <a name="visio-object-model-overview"></a>Übersicht über das Visio-Objektmodell
 Eine Übersicht über das Visio-Objektmodell finden Sie unter [Übersicht über](../vsto/visio-object-model-overview.md)das Visio-Objektmodell, das Links zur Visio-Objektmodell Referenz und den SDOs enthält.

## <a name="customize-the-user-interface-of-visio"></a>Anpassen der Benutzeroberfläche von Visio
 Die Benutzeroberfläche von Visio weist die folgenden Anpassungsoptionen auf.

|Aufgabe|Weitere Informationen|
|----------|--------------------------|
|Anpassen des Menübands.|[Übersicht über das Menüband](../vsto/ribbon-overview.md)|

 Informationen zum Anpassen der Benutzeroberfläche von Visio finden Sie in der VBA-Referenzdokumentation für die Klasse [Visio.UIObject](/office/vba/api/Visio.UIObject) .

## <a name="see-also"></a>Siehe auch
- [Einstieg in das Programmieren von VSTO-Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)
- [Übersicht über &#40;die Entwicklung von Office-Lösungen VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Architektur von VSTO-Add-Ins](../vsto/architecture-of-vsto-add-ins.md)
- [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Program mieren von VSTO-Add-ins](../vsto/programming-vsto-add-ins.md)
- [Schreiben von Code in Office-Lösungen](../vsto/writing-code-in-office-solutions.md)
- [Primäre Interopassemblys für Office](../vsto/office-primary-interop-assemblies.md)
- [Office-Benutzeroberflächen Anpassung](../vsto/office-ui-customization.md)
- [Übersicht über das Visio-Objektmodell](../vsto/visio-object-model-overview.md)
- [Visio 2010 bei der Office-Entwicklung](/previous-versions/office/developer/office-2010/ff604964(v=office.14))
