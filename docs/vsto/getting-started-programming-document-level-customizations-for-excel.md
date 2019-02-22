---
title: Erste Schritte zum Programmieren von Anpassungen auf Dokumentebene für Excel
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel solutions in Visual Studio
- Excel projects [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a336463a3a7d8003c949242ad2f295a76633c894
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56603793"
---
# <a name="get-started-programming-document-level-customizations-for-excel"></a>Erste Schritte zum Programmieren von Anpassungen auf Dokumentebene für Excel
  Wenn Sie gerade die mit Visual Studio erstellen von Anpassungen auf Dokumentebene für Microsoft Office Excel Schritte ersten, ist hier was Sie wissen müssen.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="understand-how-document-level-customizations-for-excel-work"></a>Verstehen Sie, wie Anpassungen auf Dokumentebene für Excel-Aufgaben
 Eine Anpassung auf Dokumentebene für Excel basiert auf eine einzelne Arbeitsmappe. Nutzen Sie die Anpassung, der Endbenutzer öffnet die Arbeitsmappe oder die Arbeitsmappe aus einer Excel-Vorlage erstellt. Ereignisse in der Arbeitsmappe, z. B. Zellen eingeben, oder klicken auf Schaltflächen und Menüelemente, können zur Verarbeitung von Ereignissen-Methoden in der Assembly aufrufen. Wenn die Arbeitsmappe geschlossen wird, stehen die Funktionen von der Anpassung nicht mehr in Excel nur in das Dokument, das sie enthalten sind.

 Weitere Informationen finden Sie unter [Architektur von Anpassungen auf Dokumentebene](../vsto/architecture-of-document-level-customizations.md).

## <a name="create-document-level-projects-for-excel"></a>Erstellen von Projekten auf Dokumentebene für Excel
 Um eine Anpassung auf Dokumentebene für Excel zu erstellen, verwenden Sie die Projektvorlage für Excel-Arbeitsmappen oder Excel-Vorlage in der **neues Projekt** Dialogfeld. Diese Vorlagen enthalten erforderliche Assemblyverweise und Projektdateien.

 Weitere Informationen dazu, wie Sie ein Projekt auf Dokumentebene für Excel erstellen, finden Sie unter [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Weitere Informationen zu den Projektvorlagen finden Sie unter [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md).

## <a name="program-excel-workbooks-by-using-host-items-and-host-controls"></a>Programmieren von Excel-Arbeitsmappen mithilfe von Hostelementen und Hoststeuerelementen
 *Hostelemente* und *Hoststeuerelemente* sind Klassen, die für Anpassungen auf Dokumentebene, die mithilfe von Visual Studio erstellt das Programmiermodell bereitstellen.

 Hostelemente bieten einen Einstiegspunkt für Ihren Code, und sie können auch dienen als Container für Hoststeuerelemente und Windows Forms-Steuerelemente. In Projekten auf Dokumentebene für Excel, werden diese Hostelemente dargestellt, durch die `ThisWorkbook`, `Sheet1`, `Sheet2`, und `Sheet3` Klassen.

 Hosten von Steuerelementen basieren auf systemeigene Excel-Objekte, z. B. Objekte in der Liste und Bereiche. Hoststeuerelemente stellen ähnliche Funktionen wie die systemeigene Excel-Objekte, sie haben jedoch auch neue Ereignisse, Designer-Unterstützung und Datenbindungsfunktion. Sie sind als Objekte erster Klasse in Ihrem Projektcode und IntelliSense, dadurch wird es einfacher, die auf bestimmte Objekte direkt in Ihrem Code zu verweisen, ohne Excel-Objektmodell Navigieren zu müssen.

 Weitere Informationen finden Sie unter den folgenden Themen:

-   [Programmieren von Anpassungen auf Dokumentebene](../vsto/programming-document-level-customizations.md)

-   [Automatisieren von Excel mithilfe von erweiterten Objekten](../vsto/automating-excel-by-using-extended-objects.md)

-   [Hostelemente und Host-Steuerelementen (Übersicht)](../vsto/host-items-and-host-controls-overview.md)

## <a name="customize-the-user-interface-of-excel"></a>Anpassen der Benutzeroberfläche von Excel
 Die meisten Microsoft Office-Projektmappen ändern der Benutzeroberfläche (UI) der Office-Anwendung eine Möglichkeit für Benutzer, für die Interaktion mit der Lösung bereitstellen. Es gibt viele Möglichkeiten, die in denen Sie der Benutzeroberfläche von Excel mit einer Anpassung auf Dokumentebene ändern können. Beispielsweise können Sie Steuerelemente hinzufügen, auf dem Menüband, oder Sie können einen Aktionsbereich anzeigen. Weitere Informationen finden Sie unter [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).

 Sie können auch die Arbeitsmappe öffnen, die dem Projekt direkt in Visual Studio zugeordnet ist. Wenn die Arbeitsmappe in Visual Studio geöffnet ist, können Sie die Arbeitsmappe mithilfe der Excel-Benutzeroberfläche ändern. Sie können auch die Arbeitsmappe als Entwurfsoberfläche, die Sie Steuerelemente auf Arbeitsblättern ziehen können. Weitere Informationen finden Sie unter [Office-Projekten in Visual Studio-Umgebung](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="use-data-binding"></a>Mithilfe der Datenbindung
 Die Hoststeuerelemente sind auch in der Liste der Steuerelemente, die Sie ziehen können, aus der **Datenquellen** Fenster. Hinzufügen von Hoststeuerelementen in dieser Weise automatisch, bindet diese an die Datenquelle, die Sie mithilfe des Fensters eingerichtet. Ohne Code schreiben zu müssen, können Sie Daten aus Datenbanken, Webdienste und Geschäftsobjekte anzeigen. Weitere Informationen finden Sie unter [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md).

## <a name="next-steps"></a>Nächste Schritte
 Vorgehensweise: erstellen eine Anpassung auf Dokumentebene für Excel finden Sie unter [Exemplarische Vorgehensweise: Erstellen Ihrer ersten Anpassung auf Dokumentebene, für Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md). Diese exemplarische Vorgehensweise führt Sie in Office-Entwicklungstools in Visual Studio und das Programmiermodell für Anpassungen auf Anwendungsebene Excel.

 Eine Liste der Themen, die Sie durch einige der allgemeinen Aufgaben in Excel-Projekten zu führen, finden Sie unter [häufig anfallenden Aufgaben in Office-Programmierung](../vsto/common-tasks-in-office-programming.md).

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Programmieren von Anpassungen auf Dokumentebene](../vsto/programming-document-level-customizations.md)
- [Excel-Projektmappen](../vsto/excel-solutions.md)
- [Exemplarische Vorgehensweise: Erstellen Sie Ihrer ersten Anpassung auf Dokumentebene, für Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)
- [Exemplarische Vorgehensweisen in Excel](../vsto/walkthroughs-using-excel.md)
- [Übersicht über Excel-Objektmodell](../vsto/excel-object-model-overview.md)
- [Schreiben Sie Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md)
