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
ms.openlocfilehash: 9f08ed499e61e54ffbc6508bc8353ea955d9a20c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72730870"
---
# <a name="no-source-available"></a>Keine Quelle verfügbar
Das Projekt enthält keinen Quellcode für den Code, den Sie anzeigen möchten. Grund hierfür ist meist, dass Sie durch Doppelklicken ein Modul ausgewählt haben, für das im **Aufruflistenfenster** oder im **Threadfenster** kein Quellcode vorhanden ist. Sie können das Debuggen fortsetzen, jedoch das Quellcodefenster nicht zum Festlegen von Haltepunkten und zum Durchführen anderer Aktionen an dieser Position verwenden. Wenn Sie einen Haltepunkt setzen müssen, verwenden Sie stattdessen das **Disassemblierungsfenster**.

 Auf den Eigenschaftenseiten für Projektmappen können Sie die Verzeichnisse ändern, in denen der Debugger nach Quelldateien sucht, und den Debugger anweisen, die ausgewählten Quelldateien zu ignorieren. Weitere Informationen finden Sie [unter Debugquelldateien, allgemeine Eigenschaften, Eigenschaften Seiten](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)für Projektmappen.

 **Suchen nach Quellcode** Klicken Sie auf diesen Link, um ein Dialogfeld zu öffnen, in dem Sie nach dem Quellcode suchen können.

 **Disassembly anzeigen** Öffnet das **Disassemblyfenster**.

 **Disassembly für fehlende Quelldateien immer anzeigen** Wählen Sie diese Option aus, um das **Fenster Disassembly** automatisch anzuzeigen, wenn keine Quelle verfügbar ist. Diese Einstellung kann auch im Dialogfeld **Optionen** in der Kategorie **Debuggen** auf der Seite **Allgemein** geändert werden, indem das Kontrollkästchen **Disassemblierung anzeigen, wenn die Quelle nicht verfügbar ist** aktiviert oder deaktiviert wird.

## <a name="see-also"></a>Siehe auch
- [Quelldateien debuggen, Allgemeine Eigenschaften, Eigenschaftenseiten (Dialogfeld)](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)
- [Angeben von Symbol(PDB)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [SOS.dll (SOS-Debugerweiterung)](/dotnet/framework/tools/sos-dll-sos-debugging-extension)