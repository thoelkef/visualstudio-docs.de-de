---
title: Microsoft Office Word-Tastatur, Microsoft Office-Tastatureinstellungen, Dialogfeld "Optionen" | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
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
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 7fc2f6ea9f9f404efae6ca85c8e6a4b0f70be129
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Microsoft Office Word-Tastatur, Microsoft Office-Tastatureinstellungen, Dialogfeld "Optionen"
  Microsoft Office Word und Visual Studio behandelt sowohl Tastenkombinationen. Die gleichen Tastenkombination kann für unterschiedliche Befehle in Word und Visual Studio verwendet. Wenn Sie Word in einem Projekt auf Dokumentebene in Visual Studio geöffnet ist, empfängt nur eine Anwendung zu einem Zeitpunkt Befehle der Tastenkombination. Standardmäßig wird die Visual Studio alle Befehle für Tastenkombination geschickt, jedoch können Sie Word, die sie erhalten, wenn das Dokument durch Auswahl den Fokus besitzt vornehmen **dynamische Folgendes zusätzliches Tastaturzuordnungsschema**.  
  
 Wenn Sie eine Tastenkombination, die nicht an einen Befehl in der Anwendung zugewiesen wird, die zurzeit die Tastenkombinationen bearbeitet verwenden, wird die Tastenkombination auf auf die andere Anwendung übergeben.  
  
 Die Option, die Sie auswählen, bleiben für Word-Projekte wirksam, bis Sie ihn ändern. Die Auswahl wirkt sich nicht auf Microsoft Office Excel-Projekten aus; Sie müssen alle Änderungen für Excel, mit den Optionen für die Microsoft Office Excel-Tastatur.  
  
## <a name="uielement-list"></a>UIElement-Liste  
 **Visual Studio Folgendes zusätzliches Tastaturzuordnungsschema**  
 Visual Studio empfängt alle Tastenkombinationsbefehle, selbst wenn das Word-Dokument den Fokus besitzt. Beispielsweise, wenn Sie mit der Taste F5 drücken, während das Dokument den Fokus hat, startet Visual Studio Debuggen der Projektmappe.  
  
 **Dynamische Folgendes zusätzliches Tastaturzuordnungsschema**  
 Visual Studio empfängt Tastenkombinationsbefehle nur, wenn es den Fokus hat. Wenn Sie das Word-Dokument den Fokus besitzt, empfängt Word alle Befehle für Tastenkombination. Beispielsweise, wenn Sie mit der Taste F5 drücken, während das Word-Dokument den Fokus besitzt, Word öffnet die **suchen und Ersetzen** Dialogfeld mit den **Gehe zu** Registerkarte ausgewählt. Wenn Sie F5 drücken, während Visual Studio den Fokus hat, startet Visual Studio mit dem Debuggen der Projektmappe.  
  
## <a name="see-also"></a>Siehe auch  
 [Microsoft Office Excel-Tastatur, Microsoft Office-Tastatureinstellungen, Dialogfeld „Optionen“](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  