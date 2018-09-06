---
title: Im Dialogfeld "Optionen" Microsoft Office Word-Tastatur, Microsoft Office-Tastatureinstellungen,
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
ms.openlocfilehash: 2f0785ec339da51f4f6b52e2093c1bb2ba273285
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "35671841"
---
# <a name="microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Im Dialogfeld "Optionen" Microsoft Office Word-Tastatur, Microsoft Office-Tastatureinstellungen,
  Microsoft Office Word und Visual Studio behandelt sowohl Tastenkombinationen. Die gleichen Tastenkombination kann für verschiedene Befehle, die in Word und Visual Studio verwendet. Wenn Sie Word in einem Projekt auf Dokumentebene in Visual Studio geöffnet ist, empfängt jeweils nur eine Anwendung Befehle der Tastenkombination. Standardmäßig Visual Studio alle Befehle für Tastenkombination erhält, aber Sie können Word diese empfangen werden, wenn das Dokument den Fokus durch Auswahl besitzt **Dynamisches Tastaturschema**.  
  
 Wenn Sie eine Tastenkombination, die nicht an einen Befehl in der Anwendung zugewiesen ist, die gerade die Tastenkombination gedrückt wird verwenden, wird die Tastenkombination für an eine andere Anwendung übergeben.  
  
 Die von Ihnen auszuwählende Option bleibt für Word-Projekte wirksam, bis Sie ihn ändern. Die Auswahl wirkt sich nicht auf Microsoft Office Excel-Projekte aus; Sie müssen alle Änderungen für Excel, mit den Optionen für die Microsoft Office Excel-Tastatur.  
  
## <a name="uielement-list"></a>UIElement-Liste  
 **Visual Studio-Tastaturschema**  
 Visual Studio empfängt alle Tastenkombinationsbefehle, selbst wenn das Word-Dokument den Fokus besitzt. Wenn Sie die Taste z. B. **F5** während das Dokument den Fokus besitzt, Visual Studio startet das Debuggen der Projektmappe.  
  
 **Dynamisches Tastaturschema**  
 Visual Studio erhält Tastenkombinationsbefehle nur, wenn es den Fokus besitzt. Wenn Sie das Word-Dokument den Fokus besitzt, empfängt Word alle Kontextmenübefehle. Angenommen, Sie die Taste **F5** Word wird geöffnet, während das Word-Dokument den Fokus besitzt, die **suchen und Ersetzen** Dialogfeld mit der **Gehe zu** Registerkarte ausgewählt. Wenn Sie drücken **F5** während Visual Studio den Fokus besitzt, Visual Studio startet das Debuggen der Projektmappe.  
  
## <a name="see-also"></a>Siehe auch  
 [Im Dialogfeld "Optionen" Microsoft Office Excel-Tastatur, Microsoft Office-Tastatureinstellungen,](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  