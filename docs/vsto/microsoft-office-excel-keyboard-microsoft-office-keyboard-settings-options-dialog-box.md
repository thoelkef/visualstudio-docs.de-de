---
title: Office Excel-Tastatur, Tastatur Einstellungen, Dialogfeld "Optionen"
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 090e943df2b61352c2342218c3c71c8f0e60eaad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "66836038"
---
# <a name="microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Microsoft Office Excel-Tastatur, Microsoft Office Tastatur Einstellungen, Dialogfeld "Optionen"
  Microsoft Office in Excel und Visual Studio werden Tastenkombinationen behandelt. Die gleiche Tastenkombination kann für verschiedene Befehle in Excel und in Visual Studio stehen. Wenn Excel in einem Projekt auf Dokument Ebene in Visual Studio geöffnet ist, empfängt jeweils nur eine Anwendung die Tastenkombinationen. Standardmäßig empfängt Visual Studio alle Tastenkombinationen, aber Sie können Excel-Befehle empfangen, wenn das Dokument den Fokus besitzt, indem Sie **dynamisches Tastatur Schema**auswählen.

 Wenn Sie eine Tastenkombination verwenden, die keinem Befehl in der Anwendung zugewiesen ist, die gerade die Tastenkombinationen verarbeitet, wird die Tastenkombination an die andere Anwendung weitergegeben.

 Die Option, die Sie auswählen, bleibt für Excel-Projekte wirksam, bis Sie Sie ändern. Die Auswahl wirkt sich nicht auf Microsoft Office Word-Projekte aus. Sie müssen eine beliebige Änderung für Word mithilfe der Microsoft Office Word-Tastatur Optionen vornehmen.

## <a name="uielement-list"></a>UIElement-Liste
 **Visual Studio-Tastatur Schema** Visual Studio empfängt alle Tastenkombinationen, auch wenn Excel den Fokus besitzt. Wenn Sie z. b. die Funktionstaste **F5** drücken, während Excel den Fokus besitzt, beginnt Visual Studio mit dem Debuggen der Projekt Mappe.

 **Dynamisches Tastatur Schema** Visual Studio empfängt Tastenkombinationen nur dann, wenn es den Fokus besitzt. Wenn Excel den Fokus besitzt, empfängt Excel alle Tastenkombinationen. Wenn Sie z. b. die Funktionstaste **F5** drücken, während Excel den Fokus besitzt, öffnet Excel das Dialogfeld **Gehe zu** . Wenn Sie **F5** drücken, während Visual Studio den Fokus besitzt, beginnt Visual Studio mit dem Debuggen der Projekt Mappe.

## <a name="see-also"></a>Weitere Informationen
- [Microsoft Office Word-Tastatur, Microsoft Office Tastatur Einstellungen, Dialogfeld "Optionen"](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)
