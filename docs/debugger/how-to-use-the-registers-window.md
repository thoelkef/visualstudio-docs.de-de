---
title: Ansicht im Debugger Registerwerte | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 11/19/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.registers
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- registers, debugging
- register contents
- flags, Registers window
- register groups
- debugging [Visual Studio], Registers window
- Registers window
ms.assetid: 2918ffa2-562f-40d6-9053-ef321bbeb767
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: afcada407060af2072e3cf1c30e86153762890b5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62906000"
---
# <a name="view-register-values-in-the-registers-window-c-c-visual-basic-f"></a>Ansicht Registerwerte in das Fenster "Register" (C#, C++, Visual Basic F#)

Die **registriert** Fenster zeigt Registerinhalt während des Debuggens von Visual Studio. Eine allgemeine Einführung in Konzepte hinter Register und die **registriert** Fenster finden Sie unter [Grundlagen des Debuggens: Registerfenster](../debugger/debugging-basics-registers-window.md).

> [!NOTE]
> Registerinformationen ist nicht für Skriptsprachen oder SQL-apps verfügbar.

Registrieren Sie während des Debuggens geändert werden, während Code in Ihrer app ausgeführt wird. Kürzlich geänderte Werte angezeigt, in Rot der **registriert** Fenster.

Aus Gründen der Übersichtlichkeit werden Register im Fenster **Register** nach Gruppen eingeteilt, die sich je nach Plattform und Prozessortyp unterscheiden. Sie können anzeigen oder Ausblenden von Registergruppen. Weitere Informationen finden Sie unter [Vorgehensweise: Display and hide register groups (Anzeigen und Ausblenden von Registergruppen)](../debugger/how-to-display-and-hide-register-groups.md)

Informationen zu den Flags finden Sie der **registriert** Fenster finden Sie unter [Fensters "über das Register"](../debugger/debugging-basics-registers-window.md)

Die Registerwerte können bearbeitet werden. Weitere Informationen finden Sie unter [Vorgehensweise: Edit a register value (Bearbeiten eines Registerwerts)](../debugger/how-to-edit-a-register-value.md).

**Um das Fenster "Register" zu öffnen.**

1. Aktivieren von debugging auf Adressebene dazu **Debuggen auf Adressebene aktivieren** in **Tools** (oder **Debuggen**) > **Optionen**  >  **Debuggen**.

1. Wählen Sie beim Debuggen ausgeführt werden oder sich an einem Haltepunkt ist, **Debuggen** > **Windows** > **registriert**, oder drücken Sie **Alt** + **5**.

>[!NOTE]
>Dialogfelder und Menübefehle unterscheiden sich abhängig von der Visual Studio-Edition oder die Einstellungen. Wählen Sie zum Ändern Ihrer Einstellungen **Einstellungen importieren und exportieren** auf der Visual Studio **Tools** Menü. Weitere Informationen finden Sie unter [Reset settings (Zurücksetzen der Einstellungen)](../ide/environment-settings.md#reset-settings).

### <a name="see-also"></a>Siehe auch

- [Debuggrundlagen: Registerfenster](../debugger/debugging-basics-registers-window.md)
- [Viewing data in the debugger (Anzeigen von Daten im Debugger)](../debugger/viewing-data-in-the-debugger.md)
