---
title: Entwickeln von Office-Projektmappen
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, about developing solutions
- solutions [Office development in Visual Studio], developing
- Office solutions [Office development in Visual Studio], developing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6d4ee308c5c689644c9fd9ca6e85493a081e2cdf
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440754"
---
# <a name="develop-office-solutions"></a>Entwickeln von Office-Projektmappen
  Nachdem Sie ein Projekt mit den Office Developer Tools in Visual Studio entworfen und die Projektdateien eingerichtet haben, können Sie damit beginnen, sich auf das Implementieren des Codes und der benutzerdefinierten Benutzeroberfläche (UI) zu konzentrieren.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

> [!NOTE]
> Möchten Sie bei der Entwicklung von Lösungen, die über die Office-Erfahrungen erweitern [mehrere Plattformen](https://dev.office.com/add-in-availability)? Sehen Sie sich die neue [Office-Add-ins Modell](https://dev.office.com/docs/add-ins/overview/office-add-ins). Office-Add-ins verfügen, einen geringen Ressourcenbedarf im Vergleich zu VSTO-Add-ins und Lösungen, und Sie können sie mithilfe von fast allen Web-Technologien, wie HTML5, JavaScript, CSS3 und XML-Programmierung erstellen.

## <a name="office-solutions-programming-model"></a>Programmiermodell von Office-Projektmappen
 Über das Office-Objektmodell werden viele verschiedene Objekte für die Programmierung verfügbar gemacht. Wenn Sie Office-Projektmappen mit verwaltetem Code programmieren, schreiben Sie Code, bei dem Typen in den primären Interopassemblys von Office verwendet werden. In Projektmappen, die Sie mit Office-Projektvorlagen in Visual Studio erstellen, können Sie Code auch direkt für generierte Klassen in Ihrem Projekt schreiben. Weitere Informationen finden Sie unter [schreiben Sie Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md).

## <a name="program-different-types-of-office-solutions"></a>Programmieren von verschiedenen Typen von Office-Projektmappen
 Der Typ der Projektmappe, den Sie erstellen, bestimmt, welche Funktionen Sie in Ihrem Projekt verwenden können. Beispielsweise können Sie Anpassungen auf Dokumentebene Windows Forms-Steuerelemente und erweiterte Office-Steuerelemente (als *Hoststeuerelemente*bezeichnet) hinzufügen, indem Sie die Elemente zur Entwurfszeit aus der **Werkzeugpalette** in Visual Studio ziehen. Wenn Sie aber ein VSTO-Add-In entwickeln, können Sie diese Arten von Steuerelementen Dokumenten zur Laufzeit nur hinzufügen, indem Sie Code schreiben.

 Weitere Informationen zu Funktionen, die speziell für verschiedene Typen von Projektmappen gelten, finden Sie unter den folgenden Themen:

- [Programmieren von VSTO-Add-ins](../vsto/programming-vsto-add-ins.md).

- [Programmieren von Anpassungen auf Dokumentebene](../vsto/programming-document-level-customizations.md).

- [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).

  Hintergrundinformationen zum Planen von Office-Projektmappen und die Verfahren zum Erstellen von Projekten unterstützen, finden Sie unter [entwerfen und Erstellen von Office-Projektmappen](../vsto/designing-and-creating-office-solutions.md).

## <a name="related-topics"></a>Verwandte Themen

|Titel|Beschreibung|
|-----------|-----------------|
|[Schreiben Sie Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md)|Hier werden verschiedene Aspekte des Schreibens von Code in Office-Projektmappen beschrieben.|
|[Programmieren von VSTO-Add-ins](../vsto/programming-vsto-add-ins.md)|Enthält eine Übersicht über das Programmiermodell von VSTO-Add-Ins und die zugehörigen Programmieraufgaben.|
|[Programmieren von Anpassungen auf Dokumentebene](../vsto/programming-document-level-customizations.md)|Enthält eine Übersicht über das Programmiermodell von Anpassungen auf Dokumentebene und die zugehörigen Programmieraufgaben.|
|[Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md)|Hier werden die verschiedenen Wege beschrieben, wie Sie die Benutzeroberfläche von Office-Anwendungen anpassen können, indem Sie VSTO-Add-Ins und Anpassungen auf Dokumentebene verwenden.|
|[Daten in Office-Projektmappen](../vsto/data-in-office-solutions.md)|Hier werden die unterschiedlichen Wege beschrieben, wie Sie in Office-Projektmappen mit Daten arbeiten können, z. B. das Binden von Daten an Steuerelemente und das Zwischenspeichern von Daten in Anpassungen auf Dokumentebene.|
|[Auswirkungen des AutoSave Office-Projektmappen](./how-autosave-impacts-office-solutions.md)|Beschreibt die Korrekturen, die Sie möglicherweise für Office-Projektmappen vornehmen, wenn die automatische Speicherung aktiviert ist.|
|[Problembehandlung bei Office-Projektmappen](../vsto/troubleshooting-office-solutions.md)|Enthält Tipps zur Lösung von allgemeinen Problemen, die beim Erstellen von Office-Projektmappen auftreten können.|
|[Threading-Unterstützung in Office](../vsto/threading-support-in-office.md)|Hier erhalten Sie einen Überblick über die Arbeit mit mehreren Threads in Office-Projektmappen.|
|[Barrierefreiheit in Office-Projekten](../vsto/accessibility-in-office-projects.md)|Beschreibt die Barrierefreiheitsfunktionen, die in Office-Projektmappen verfügbar sind.|

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Erstellen und Ändern von benutzerdefinierten Dokumenteigenschaften](../vsto/how-to-create-and-modify-custom-document-properties.md)
- [Vorgehensweise: Lesen aus und Schreiben in Dokumenteigenschaften](../vsto/how-to-read-from-and-write-to-document-properties.md)
- [Vorgehensweise: Die mehrsprachige Benutzeroberfläche von Office als Ziel](../vsto/how-to-target-the-office-multilingual-user-interface.md)
- [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)
- [Exemplarische Vorgehensweise: Erstellen Sie Ihrer ersten Anpassung auf Dokumentebene, für Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)
- [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)
- [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)
- [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)
- [Exemplarische Vorgehensweise: Erstellen des ersten VSTO-Add-Ins für Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)
- [Exemplarische Vorgehensweise: Erstellen der ersten Anpassung der auf Dokumentebene für Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)
