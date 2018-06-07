---
title: Microsoft Office Word-Tastatur, Microsoft Office-Tastatureinstellungen, Dialogfeld "Optionen" | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Word.Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Word_Keyboard
- VST.WordOptions.KeyboardMappingScheme
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- keyboard shortcuts, Office development in Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9edd5cd987eb6a4e93b02c8e774adefbc7f969d2
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572110"
---
# <a name="microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Microsoft Office Word-Tastatur, Microsoft Office-Tastatureinstellungen, Optionen (Dialogfeld)
  Microsoft Office Word und Visual Studio behandelt sowohl Tastenkombinationen. Die gleichen Tastenkombination kann für unterschiedliche Befehle in Word und Visual Studio verwendet. Wenn Sie Word in einem Projekt auf Dokumentebene in Visual Studio geöffnet ist, empfängt nur eine Anwendung zu einem Zeitpunkt Befehle der Tastenkombination. Standardmäßig wird die Visual Studio alle Befehle für Tastenkombination geschickt, jedoch können Sie Word, die sie erhalten, wenn das Dokument durch Auswahl den Fokus besitzt vornehmen **dynamische Folgendes zusätzliches Tastaturzuordnungsschema**.  
  
 Wenn Sie eine Tastenkombination, die nicht an einen Befehl in der Anwendung zugewiesen wird, die zurzeit die Tastenkombinationen bearbeitet verwenden, wird die Tastenkombination auf auf die andere Anwendung übergeben.  
  
 Die Option, die Sie auswählen, bleiben für Word-Projekte wirksam, bis Sie ihn ändern. Die Auswahl wirkt sich nicht auf Microsoft Office Excel-Projekten aus; Sie müssen alle Änderungen für Excel, mit den Optionen für die Microsoft Office Excel-Tastatur.  
  
## <a name="uielement-list"></a>UIElement-Liste  
 **Visual Studio Folgendes zusätzliches Tastaturzuordnungsschema**  
 Visual Studio empfängt alle Tastenkombinationsbefehle, selbst wenn das Word-Dokument den Fokus besitzt. Angenommen, Sie mit der Taste drücken **F5** während das Dokument den Fokus besitzt, Visual Studio startet das Debuggen der Projektmappe.  
  
 **Dynamische Folgendes zusätzliches Tastaturzuordnungsschema**  
 Visual Studio empfängt Tastenkombinationsbefehle nur, wenn es den Fokus hat. Wenn Sie das Word-Dokument den Fokus besitzt, empfängt Word alle Befehle für Tastenkombination. Angenommen, Sie mit der Taste drücken **F5** Word geöffnet wird, während das Word-Dokument den Fokus besitzt, die **suchen und Ersetzen** Dialogfeld mit der **Gehe zu** Registerkarte ausgewählt. Wenn Sie drücken **F5** während Visual Studio den Fokus besitzt, Visual Studio startet das Debuggen der Projektmappe.  
  
## <a name="see-also"></a>Siehe auch  
 [Microsoft Office Excel-Tastatur, Microsoft Office-Tastatureinstellungen, Optionen (Dialogfeld)](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  