---
title: Keine Quelle verfügbar | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.nosource
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- No Source Code Available for the Current Location dialog box
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 85d1d1307a119fa23bf7ba015130ab9c7b6f69d5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62905218"
---
# <a name="no-source-available"></a>Keine Quelle verfügbar
Das Projekt enthält keinen Quellcode für den Code, den Sie anzeigen möchten. Grund hierfür ist meist, dass Sie durch Doppelklicken ein Modul ausgewählt haben, für das im **Aufruflistenfenster** oder im **Threadfenster** kein Quellcode vorhanden ist. Sie können das Debuggen fortsetzen, jedoch das Quellcodefenster nicht zum Festlegen von Haltepunkten und zum Durchführen anderer Aktionen an dieser Position verwenden. Wenn Sie einen Haltepunkt setzen müssen, verwenden Sie stattdessen das **Disassemblierungsfenster**.

 Auf den Eigenschaftenseiten für Projektmappen können Sie die Verzeichnisse ändern, in denen der Debugger nach Quelldateien sucht, und den Debugger anweisen, die ausgewählten Quelldateien zu ignorieren. Finden Sie unter [Debuggen Quelle-Dateien, allgemeine Eigenschaften, Lösung Property Pages Dialog Box](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md).

 **Navigieren Sie zur Quellcode** klicken Sie auf diesen Link, um ein Dialogfeld zu öffnen, in dem Sie finden den Quellcode durchsuchen können.

 **Disassembly anzeigen** startet die **Disassemblyfenster**.

 **Disassembly für fehlende Quelldateien immer anzeigen** wählen Sie diese Option zum Anzeigen der **Disassemblyfenster** automatisch Wenn kein Quellcode verfügbar ist. Diese Einstellung kann auch im Dialogfeld **Optionen** in der Kategorie **Debuggen** auf der Seite **Allgemein** geändert werden, indem das Kontrollkästchen **Disassemblierung anzeigen, wenn die Quelle nicht verfügbar ist** aktiviert oder deaktiviert wird.

## <a name="see-also"></a>Siehe auch
- [Quelldateien debuggen, Allgemeine Eigenschaften, Eigenschaftenseiten (Dialogfeld)](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)
- [Angeben von Symbol(PDB)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [SOS.dll (SOS-Debugerweiterung)](/dotnet/framework/tools/sos-dll-sos-debugging-extension)