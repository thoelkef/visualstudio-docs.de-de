---
title: Erste Schritte zum Programmieren von Anpassungen auf Dokumentebene für Word
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word solutions in Visual Studio
- Word projects [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2b2872ca6496444cbb3878dc39800a8661400a76
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60056327"
---
# <a name="get-started-programming-document-level-customizations-for-word"></a>Erste Schritte zum Programmieren von Anpassungen auf Dokumentebene für Word
  Wenn Sie gerade die Erstellen von Anpassungen auf Dokumentebene für Microsoft Office Word mit Visual Studio Schritte ersten, ist hier was Sie wissen müssen.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

## <a name="understand-how-document-level-customizations-for-word-work"></a>Verstehen Sie, wie Anpassungen auf Dokumentebene für Word Arbeit
 Jede Anpassung von Word, die Sie erstellen, basiert auf einem einzelnen Dokument. Nutzen Sie die Anpassung, der Endbenutzer Öffnet das Dokument oder das Dokument aus einer Word-Vorlage erstellt. Ereignisse in das Dokument, z. B. das Verschieben des Cursors in bestimmte Bereiche oder durch Klicken auf Schaltflächen und Menüelemente, können zur Verarbeitung von Ereignissen-Methoden in der Assembly aufrufen. Wenn das Dokument geschlossen wird, sind die von der Anpassung bereitgestellten Funktionen nicht mehr verfügbar in Word.

 Weitere Informationen finden Sie unter [Architektur von Anpassungen auf Dokumentebene](../vsto/architecture-of-document-level-customizations.md).

## <a name="create-document-level-projects-for-word"></a>Erstellen von Projekten auf Dokumentebene für Word
 Um eine Anpassung auf Dokumentebene für Word zu erstellen, verwenden Sie die Projektvorlage für Word-Dokument oder Word-Vorlage in der **neues Projekt** Dialogfeld. Diese Vorlagen enthalten erforderliche Assemblyverweise und Projektdateien.

 Weitere Informationen dazu, wie Sie ein Projekt auf Dokumentebene für Word erstellen, finden Sie unter [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Weitere Informationen zu den Projektvorlagen finden Sie unter [Übersicht über Office-Projektvorlagen](../vsto/office-project-templates-overview.md).

## <a name="program-word-documents-by-using-host-items-host-controls"></a>Programm-Word-Dokumenten mithilfe von Hostelementen und Hoststeuerelementen
 *Hostelemente* und *Hoststeuerelemente* sind Klassen, die das Programmiermodell für Anpassungen auf Dokumentebene bereitstellen.

 Hostelemente bieten einen Einstiegspunkt für Ihren Code, und sie können auch dienen als Container für Hoststeuerelemente und Windows Forms-Steuerelemente. In Projekten auf Dokumentebene für Word, wird durch das Hostelement dargestellt die `ThisDocument` Klasse.

 Hosten von Steuerelementen basieren auf systemeigene Word-Objekte, z. B. ContentControl-Elemente, Lesezeichen und XML-Knoten. Hoststeuerelemente stellen ähnliche Funktionen wie die systemeigene Word-Objekte, sie haben jedoch auch neue Ereignisse, Designer-Unterstützung und Funktion der Datenbindung. Sie sind als Objekte erster Klasse in Ihrem Projektcode und IntelliSense, dadurch wird es einfacher, die für bestimmte Objekte direkt in Ihrem Code verweisen, ohne die Word-Objektmodell Navigieren zu müssen.

 Weitere Informationen finden Sie unter den folgenden Themen:

- [Programmieren von Anpassungen auf Dokumentebene](../vsto/programming-document-level-customizations.md)

- [Automatisieren von Word mithilfe von erweiterten Objekten](../vsto/automating-word-by-using-extended-objects.md)

- [Hostelemente und Host-Steuerelementen (Übersicht)](../vsto/host-items-and-host-controls-overview.md)

## <a name="customize-the-user-interface-of-word"></a>Anpassen der Benutzeroberfläche von Word
 Die meisten Microsoft Office-Projektmappen ändern der Benutzeroberfläche (UI) der Office-Anwendung eine Möglichkeit für Benutzer, für die Interaktion mit der Lösung bereitstellen. Es gibt viele Möglichkeiten, die in denen Sie die Benutzeroberfläche von Word mithilfe einer Anpassung auf Dokumentebene ändern können. Beispielsweise können Sie Steuerelemente hinzufügen, auf dem Menüband, und Sie können einen Aktionsbereich anzeigen. Weitere Informationen finden Sie unter [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md).

 Sie können auch das Dokument öffnen, das dem Projekt direkt in Visual Studio zugeordnet ist. Wenn das Dokument in Visual Studio geöffnet ist, können Sie das Dokument mithilfe der Word-Benutzeroberfläche ändern. Sie können auch das Dokument als Entwurfsoberfläche, die Sie Steuerelemente ziehen können. Weitere Informationen finden Sie unter [Office-Projekten in Visual Studio-Umgebung](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="bind-controls-to-data"></a>Binden von Steuerelementen an Daten
 Die Inhaltssteuerelemente und <xref:Microsoft.Office.Tools.Word.Bookmark> sind in der Liste der Steuerelemente, die Sie ziehen können, aus der **Datenquellen** Fenster. Hinzufügen Inhaltssteuerelemente und Lesezeichen in dieser Weise automatisch, bindet sie an die Datenquelle, die Sie eingerichtet haben, mithilfe des Fensters. Ohne Code schreiben zu müssen, können Sie Daten aus Datenbanken, Diensten und Geschäftsobjekten anzeigen. Weitere Informationen finden Sie unter [Binden von Daten an Steuerelemente in Office-Projektmappen](../vsto/binding-data-to-controls-in-office-solutions.md).

## <a name="next-steps"></a>Nächste Schritte
 Um zu erfahren, wie Sie eine Anpassung auf Dokumentebene für Word zu erstellen, finden Sie unter [Exemplarische Vorgehensweise: Erstellen der ersten Anpassung der auf Dokumentebene für Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md). Diese exemplarische Vorgehensweise führt Sie in Office-Entwicklungstools in Visual Studio und das Programmiermodell für Anpassungen auf Anwendungsebene Word.

 Eine Liste der Themen, die Sie durch einige der allgemeinen Aufgaben in Word-Projekten zu führen, finden Sie unter [häufig anfallenden Aufgaben in Office-Programmierung](../vsto/common-tasks-in-office-programming.md).

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Programmieren von Anpassungen auf Dokumentebene](../vsto/programming-document-level-customizations.md)
- [Word-Projektmappen](../vsto/word-solutions.md)
- [Exemplarische Vorgehensweise: Erstellen der ersten Anpassung der auf Dokumentebene für Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)
- [Exemplarische Vorgehensweisen mit Word](../vsto/walkthroughs-using-word.md)
- [Übersicht über das Word-Objektmodell](../vsto/word-object-model-overview.md)
- [Schreiben Sie Code in Office-Projektmappen](../vsto/writing-code-in-office-solutions.md)
