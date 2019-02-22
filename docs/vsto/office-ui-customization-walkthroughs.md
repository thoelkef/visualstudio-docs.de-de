---
title: Exemplarische Vorgehensweisen für die Anpassung von Office-Benutzeroberfläche
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes, walkthroughs
- smart documents, walkthroughs
- walkthroughs [Office development in Visual Studio], smart tags
- walkthroughs [Office development in Visual Studio], action panes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 95561f1404da1efd71ff3418f9154392f393795c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596593"
---
# <a name="office-ui-customization-walkthroughs"></a>Exemplarische Vorgehensweisen für die Anpassung von Office-Benutzeroberfläche
  Die folgenden exemplarischen Vorgehensweisen veranschaulichen, wie Sie Anpassungen auf Dokumentebene und VSTO-Add-Ins zum Anpassen der Benutzeroberfläche von Microsoft Office-Anwendungen verwenden können.

## <a name="actions-pane-walkthroughs"></a>Aktionsbereiche
- [Exemplarische Vorgehensweise: Einfügen von Text in ein Dokument aus einem Aktionsbereich](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md) wird veranschaulicht, wie ein Bereich "Aktionen" in einem Word-Dokument zu erstellen. Der Aktionsbereich enthält zwei Steuerelemente, die Benutzereingaben an das Dokument senden.

- [Exemplarische Vorgehensweise: Binden von Daten an Steuerelemente in einem Word-Aktionsbereich](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md) wird veranschaulicht, wie Sie Steuerelemente in einem Aktionsbereich in Word an Daten binden. Die Steuerelemente zeigen eine Master/Detail-Beziehung zwischen Tabellen in einer SQL Server-Datenbank.

- [Exemplarische Vorgehensweise: Binden von Daten an Steuerelemente in einem Excel-Aktionsbereich](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md) beschreibt, wie Sie Steuerelemente hinzufügen, die an einem Aktionsbereich in Excel eine Datenquelle gebunden sind.

## <a name="custom-task-pane-walkthroughs"></a>Exemplarische Vorgehensweisen für benutzerdefinierte Tasks
- [Exemplarische Vorgehensweise: Automatisieren einer Anwendung über einen benutzerdefinierten Aufgabenbereich](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md) wird veranschaulicht, wie Sie einen benutzerdefinierten Aufgabenbereich zu erstellen, die ein Steuerelement, die die hostanwendung automatisiert enthält, wenn der Benutzer das Steuerelement klickt.

- [Exemplarische Vorgehensweise: Synchronisieren ein benutzerdefinierten Aufgabenbereichs mit einer Menübandschaltfläche](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md) wird veranschaulicht, wie Sie einen benutzerdefinierten Aufgabenbereich zu erstellen, die Benutzer durch Klicken auf eine Umschaltfläche auf dem Menüband anzeigen oder ausblenden können.

- [Exemplarische Vorgehensweise: Anzeigen von benutzerdefinierten Aufgabenbereichen mit e-Mails in Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md) wird veranschaulicht, wie Sie eine eindeutige Instanz eines benutzerdefinierten Aufgabenbereichs mit einer einzelnen e-Mail-Nachrichten anzeigen, die erstellt oder in Outlook geöffnet ist.

## <a name="ribbon-walkthroughs"></a>Exemplarische Vorgehensweisen für Menübänder
- [Exemplarische Vorgehensweise: Erstellen eine benutzerdefinierte Registerkarte mit Menüband-Designer](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md) veranschaulicht, wie eine benutzerdefinierte Registerkarte des Menübands mithilfe des Menüband-Designers. Die Registerkarte enthält eine Schaltfläche, mit der ein Aktionsbereich ausgeblendet oder angezeigt werden kann.

- [Exemplarische Vorgehensweise: Aktualisieren der Steuerelemente auf einem Menüband zur Laufzeit](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md) veranschaulicht, wie die Menüband-Objektmodells zum Aktualisieren der Steuerelemente auf einem Menüband, nachdem das Menüband in der Office-Anwendung geladen wird.

- [Exemplarische Vorgehensweise: Erstellen eine benutzerdefinierte Registerkarte mit Menüband-XML-](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md) veranschaulicht, wie eine benutzerdefinierte Menüband-Registerkarte mit Menüband-XML anstelle des Menüband-Designers.

## <a name="controls-on-word-documents"></a>Steuerelemente in Word-Dokumenten
- [Exemplarische Vorgehensweise: Hinzufügen von Steuerelementen zu einem Dokument zur Laufzeit in einem VSTO-Add-In](../vsto/walkthrough-adding-controls-to-a-document-at-run-time-in-a-vsto-add-in.md) veranschaulicht das Hinzufügen von Steuerelementen zu einem Dokument mithilfe eines VSTO-Add-Ins.

- [Exemplarische Vorgehensweise: Ändern der dokumentformatierung mit CheckBox-Steuerelementen](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md) veranschaulicht das Ändern der Formatierung in einem Word-Dokument mithilfe der Kontrollkästchen in einer Anpassung auf Dokumentebene.

- [Exemplarische Vorgehensweise: Anzeigen von Text in einem Textfeld in einem Dokument mithilfe einer Schaltfläche](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md) veranschaulicht, wie Schaltflächen und Textfeldern in Word-Dokumenten.

- [Exemplarische Vorgehensweise: Aktualisieren eines Diagramms in einem Dokument mithilfe von Optionsfeldern](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md) wird veranschaulicht, wie Diagrammformatvorlagen in einem Word-Dokument zu ändern, indem Sie mithilfe von Optionsfeldern in einer Anpassung auf Dokumentebene.

## <a name="controls-on-excel-worksheets"></a>Steuerelemente in Excel-Arbeitsblättern
- [Exemplarische Vorgehensweise: Hinzufügen von Steuerelementen zu einem Arbeitsblatt zur Laufzeit in VSTO-add-in-Projekt](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md) veranschaulicht das Hinzufügen von Steuerelementen zu einem Arbeitsblatt mithilfe eines VSTO-Add-Ins.

- [Exemplarische Vorgehensweise: Ändern der arbeitsblattformatierung mithilfe von CheckBox-Steuerelementen](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md) veranschaulicht die Grundlagen der Verwendung von Kontrollkästchen zum Ändern der Formatierung in einem Excel-Arbeitsblatt.

- [Exemplarische Vorgehensweise: Anzeigen von Text in einem Textfeld eines Arbeitsblatts mithilfe einer Schaltfläche](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md) veranschaulicht die Grundlagen der Verwendung von Schaltflächen und Textfeldern in Excel-Arbeitsblättern.

- [Exemplarische Vorgehensweise: Aktualisieren eines Diagramms in einem Arbeitsblatt mithilfe von Optionsfeldern](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md) veranschaulicht die Grundlagen zum Ändern von Diagrammformaten mithilfe von Optionsfeldern in einem Excel-Arbeitsblatt.

## <a name="see-also"></a>Siehe auch
- [Exemplarische Vorgehensweisen mit Word](../vsto/walkthroughs-using-word.md)
- [Exemplarische Vorgehensweisen in Excel](../vsto/walkthroughs-using-excel.md)
- [Daten in Exemplarische Vorgehensweisen für Office-Lösungen](../vsto/data-in-office-solutions-walkthroughs.md)
- [Vorgehensweisen für Sicherheit und Bereitstellung](../vsto/security-and-deployment-walkthroughs.md)
- [Erste Schritte &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Allgemeine Aufgaben in Office-Programmierung](../vsto/common-tasks-in-office-programming.md)
- [Entwerfen und Erstellen von Office-Projektmappen](../vsto/designing-and-creating-office-solutions.md)
