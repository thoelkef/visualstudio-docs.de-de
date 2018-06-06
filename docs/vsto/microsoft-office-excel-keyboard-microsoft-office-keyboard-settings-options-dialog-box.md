---
title: Microsoft Office Excel-Tastatur, Microsoft Office-Tastatureinstellungen, Optionen (Dialogfeld)
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ExcelOptions.KeyboardMappingScheme
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Excel_Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Excel.Keyboard
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
ms.openlocfilehash: fc71c699dfea11b8654791efdd52e4c0751a9762
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34692446"
---
# <a name="microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Microsoft Office Excel-Tastatur, Microsoft Office-Tastatureinstellungen, Optionen (Dialogfeld)
  Microsoft Office Excel und Visual Studio behandelt sowohl Tastenkombinationen. Die gleichen Tastenkombination kann für unterschiedliche Befehle in Excel und in Visual Studio verwendet. Wenn Excel in einem Projekt auf Dokumentebene in Visual Studio geöffnet ist, empfängt nur eine Anwendung zu einem Zeitpunkt Befehle der Tastenkombination. Standardmäßig wird die Visual Studio alle Befehle für Tastenkombination geschickt, jedoch können Sie Excel, die sie erhalten, wenn das Dokument durch Auswahl den Fokus besitzt vornehmen **dynamische Folgendes zusätzliches Tastaturzuordnungsschema**.  
  
 Wenn Sie eine Tastenkombination, die nicht an einen Befehl in der Anwendung zugewiesen wird, die zurzeit die Tastenkombinationen bearbeitet verwenden, wird die Tastenkombination auf auf die andere Anwendung übergeben.  
  
 Die Option, die Sie auswählen, bleiben für Excel-Projekte wirksam, bis Sie ihn ändern. Die Auswahl wirkt sich nicht auf Microsoft Office Word-Projekte aus; Sie müssen alle Änderungen für Word, mithilfe der Optionen für die Microsoft Office Word-Tastatur.  
  
## <a name="uielement-list"></a>UIElement-Liste  
 **Visual Studio Folgendes zusätzliches Tastaturzuordnungsschema**  
 Visual Studio empfängt alle Tastenkombinationsbefehle, auch wenn Excel den Fokus besitzt. Angenommen, Sie mit der Taste drücken **F5** während Excel den Fokus besitzt, Visual Studio startet das Debuggen der Projektmappe.  
  
 **Dynamische Folgendes zusätzliches Tastaturzuordnungsschema**  
 Visual Studio empfängt Tastenkombinationsbefehle nur, wenn es den Fokus hat. Wenn Excel den Fokus hat, empfängt Excel alle Befehle für Tastenkombination. Angenommen, Sie mit der Taste drücken **F5** Excel geöffnet wird, während Excel den Fokus besitzt, die **Gehe zu** (Dialogfeld). Wenn Sie drücken **F5** während Visual Studio den Fokus besitzt, Visual Studio startet das Debuggen der Projektmappe.  
  
## <a name="see-also"></a>Siehe auch  
 [Microsoft Office Word-Tastatur, Microsoft Office-Tastatureinstellungen, Optionen (Dialogfeld)](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  