---
title: Im Dialogfeld "Optionen" Microsoft Office Excel-Tastatur, Microsoft Office-Tastatureinstellungen,
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
ms.openlocfilehash: 63f3bfc9295501d5f9b8f0267037302cdbb04a76
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970214"
---
# <a name="microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Im Dialogfeld "Optionen" Microsoft Office Excel-Tastatur, Microsoft Office-Tastatureinstellungen,
  Microsoft Office Excel und Visual Studio behandelt sowohl Tastenkombinationen. Die gleichen Tastenkombination kann für verschiedene Befehle, die in Excel und in Visual Studio verwendet. Wenn Excel in einem Projekt auf Dokumentebene in Visual Studio geöffnet ist, empfängt nur eine Anwendung zu einem Zeitpunkt Befehle der Tastenkombination. Standardmäßig Visual Studio alle Befehle für Tastenkombination erhält, werden Sie jedoch Excel, die sie empfangen werden, wenn das Dokument den Fokus durch Auswahl besitzt **Dynamisches Tastaturschema**.

 Wenn Sie eine Tastenkombination, die nicht an einen Befehl in der Anwendung zugewiesen ist, die gerade die Tastenkombination gedrückt wird verwenden, wird die Tastenkombination für an eine andere Anwendung übergeben.

 Der, die von Ihnen auszuwählende Option bleibt für Excel-Projekte wirksam, bis Sie ihn ändern. Die Auswahl wirkt sich nicht auf Microsoft Office Word-Projekten aus; Sie müssen alle Änderungen für Word, mit den Optionen für die Microsoft Office Word-Tastatur.

## <a name="uielement-list"></a>UIElement-Liste
 **Visual Studio-Tastaturschema** Visual Studio erhält alle Tastenkombinationsbefehle, auch wenn Excel den Fokus hat. Wenn Sie die Taste z. B. **F5** während Excel den Fokus besitzt, Visual Studio startet das Debuggen der Projektmappe.

 **Dynamisches Tastaturschema** Visual Studio erhält die Tastenkombinationsbefehle nur, wenn es den Fokus besitzt. Wenn Excel den Fokus hat, erhält die Excel Verknüpfung alle Befehle. Angenommen, Sie die Taste **F5** Excel geöffnet wird, während Excel den Fokus besitzt, die **Gehe zu** im Dialogfeld. Wenn Sie drücken **F5** während Visual Studio den Fokus besitzt, Visual Studio startet das Debuggen der Projektmappe.

## <a name="see-also"></a>Siehe auch
- [Im Dialogfeld "Optionen" Microsoft Office Word-Tastatur, Microsoft Office-Tastatureinstellungen,](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)
