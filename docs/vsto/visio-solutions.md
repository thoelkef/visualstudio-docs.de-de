---
title: Visio-Projektmappen
ms.date: 02/02/2017
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
ms.openlocfilehash: beb51866fdce18c640e41cb90a5f357fda6e5190
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56628896"
---
# <a name="visio-solutions"></a>Visio-Projektmappen
  Visual Studio stellt Projektvorlagen bereit, die Sie zum Erstellen von VSTO-Add-Ins für Microsoft Office Visio verwenden können. Mit VSTO-Add-Ins können Sie Visio automatisieren, Visio -Features erweitern oder die Benutzeroberfläche (User Interface, UI) von Visio anpassen.

 Weitere Informationen zu VSTO-Add-ins finden Sie unter [erste Schritte zum Programmieren von VSTO-Add-ins](../vsto/getting-started-programming-vsto-add-ins.md) und [Architecture of VSTO-Add-ins](../vsto/architecture-of-vsto-add-ins.md). Wenn Sie die mit Microsoft Office-Programmierung vertraut sind, finden Sie unter [Einstieg &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).

 **Gilt für:** Die Informationen in diesem Thema betreffen VSTO-Add-in-Projekte für Visio 2010. Weitere Informationen finden Sie unter [Verfügbare Funktionen nach Office-Anwendung und Projekttyp](../vsto/features-available-by-office-application-and-project-type.md).

> [!NOTE]
>  Möchten Sie bei der Entwicklung von Lösungen, die über die Office-Erfahrungen erweitern [mehrere Plattformen](https://dev.office.com/add-in-availability)? Sehen Sie sich die neue [Office-Add-ins Modell](https://dev.office.com/docs/add-ins/overview/office-add-ins). Office-Add-ins verfügen, einen geringen Ressourcenbedarf im Vergleich zu VSTO-add-ins und Lösungen, und Sie können sie mithilfe von fast allen Web-Technologien, wie HTML5, JavaScript, CSS3 und XML-Programmierung erstellen.

## <a name="automate-visio-by-using-the-visio-object-model"></a>Automatisieren von PowerPoint mithilfe von Visio-Objektmodell
 Das Visio-Objektmodell stellt zahlreiche Klassen bereit, die Sie verwenden können, um Visio zum Erstellen von Diagrammen für Organigramme, Flussdiagramme, Projektzeitachsen, Netzwerkdiagramme, Büroräume und mehr automatisieren können. Die API ermöglicht Ihnen das Schreiben von Code zum Ausführen häufige anfallender Aufgaben:

- Erstellen und Positionieren von Shapes und Text in Diagrammen.

- Verwalten des Shape-Verhaltens basierend auf Geschäftslogik und Benutzereingaben.

- Steuern der Darstellung von Diagrammen (z. B. Schwenken und Zoomen).

- Anpassen der Benutzeroberfläche der Anwendung.

- Importieren externer Daten in Visio, Verknüpfen dieser Daten mit Shapes und grafische Darstellung auf einer Seite.

  Sie können anzeigen schrittweise Anleitungen und Codebeispiele für die Verwendung von des Visio-Objektmodells zum Arbeiten mit Dokumenten und Shapes in [arbeiten mit Visio-Dokumenten](../vsto/working-with-visio-documents.md) und [arbeiten mit Visio-Shapes](../vsto/working-with-visio-shapes.md).

  Für den Zugriff auf das Visio-Objektmodell aus einem VSTO-Add-In verwenden Sie das Feld `Application` der Klasse `ThisAddIn` in Ihrem Projekt. Das Feld `Application` gibt ein `Microsoft.Office.Interop.Visio.Application`-Objekt zurück, das die aktuelle Instanz von Visio darstellt. Weitere Informationen finden Sie unter [Programm VSTO-Add-ins](../vsto/programming-vsto-add-ins.md).

  Bei einem Aufruf des Visio-Objektmodells verwenden Sie Typen, die in der primären Interopassembly (PIA) für Visio bereitgestellt werden. Die primäre Interopassembly (PIA) dient als Brücke zwischen verwaltetem Code im VSTO-Add-In und dem COM-Objektmodell in Visio. Alle Typen in der Visio-PIA werden im Namespace `Microsoft.Office.Interop.Visio` definiert. Weitere Informationen zu primären Interopassemblys finden Sie unter [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) und [primären Interopassemblys für Office](../vsto/office-primary-interop-assemblies.md).

## <a name="visio-object-model-overview"></a>Übersicht über das Visio-Objektmodell
 Finden Sie eine Übersicht über das Visio-Objektmodell auf [Visio-Objektmodell-Übersicht](../vsto/visio-object-model-overview.md), einschließlich Links zur Visio-Objektmodellreferenz und der SDKs.

## <a name="customize-the-user-interface-of-visio"></a>Anpassen der Benutzeroberfläche von Visio
 Die Benutzeroberfläche von Visio weist die folgenden Anpassungsoptionen auf.

|Aufgabe|Weitere Informationen|
|----------|--------------------------|
|Anpassen des Menübands.|[Übersicht über das Menüband](../vsto/ribbon-overview.md)|

 Informationen zum Anpassen der Benutzeroberfläche von Visio finden Sie in der VBA-Referenzdokumentation für die Klasse [Visio.UIObject](/office/vba/api/Visio.UIObject) .

## <a name="see-also"></a>Siehe auch
- [Erste Schritte zum Programmieren von VSTO-Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)
- [Übersicht über die Entwicklung von Office-Projektmappen &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Architektur von VSTO-Add-Ins](../vsto/architecture-of-vsto-add-ins.md)
- [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Programmieren von VSTO-Add-ins](../vsto/programming-vsto-add-ins.md)
- [Schreiben Sie Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md)
- [Primäre Interopassemblys für Office](../vsto/office-primary-interop-assemblies.md)
- [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md)
- [Übersicht über das Visio-Objektmodell](../vsto/visio-object-model-overview.md)
- [Visio 2010 unter Office-Entwicklung](http://go.microsoft.com/fwlink/?LinkId=199017)
