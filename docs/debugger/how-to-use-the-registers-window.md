---
title: Ansicht Registerwerte in Visual Studio-Debugger | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/19/2018
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ab40e0b63b2a679b4c36a4625d517a03b6c123ad
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389324"
---
# <a name="view-register-values-in-the-registers-window-c-c-visual-basic-f"></a>Ansicht Registerwerte in das Fenster "Register" (C#, C++, Visual Basic F#)

Die **registriert** Fenster zeigt Registerinhalt während des Debuggens von Visual Studio. Eine allgemeine Einführung in Konzepte hinter Register und die **registriert** Fenster finden Sie unter [Grundlagen des Debuggens: Fenster "Register"](../debugger/debugging-basics-registers-window.md).

> [!NOTE]
> Registerinformationen ist nicht für Skriptsprachen oder SQL-apps verfügbar.

Registrieren Sie während des Debuggens geändert werden, während Code in Ihrer app ausgeführt wird. Kürzlich geänderte Werte angezeigt, in Rot der **registriert** Fenster.

Aus Gründen der Übersichtlichkeit werden Register im Fenster **Register** nach Gruppen eingeteilt, die sich je nach Plattform und Prozessortyp unterscheiden. Sie können anzeigen oder Ausblenden von Registergruppen. Weitere Informationen finden Sie unter [How to: Display and hide register groups (Vorgehensweise: Anzeigen und Ausblenden von Registergruppen)](../debugger/how-to-display-and-hide-register-groups.md).

Die Registerwerte können bearbeitet werden. Weitere Informationen finden Sie unter [Vorgehensweise: Bearbeiten eines Registerwerts](../debugger/how-to-edit-a-register-value.md).

**Um das Fenster "Register" zu öffnen.**

1. Aktivieren von debugging auf Adressebene dazu **Debuggen auf Adressebene aktivieren** in **Tools** (oder **Debuggen**) > **Optionen**  >  **Debuggen**.

1. Wählen Sie beim Debuggen ausgeführt werden oder sich an einem Haltepunkt ist, **Debuggen** > **Windows** > **registriert**, oder drücken Sie **Alt** + **5**.

>[!NOTE]
>Dialogfelder und Menübefehle unterscheiden sich abhängig von der Visual Studio-Edition oder die Einstellungen. Wählen Sie zum Ändern Ihrer Einstellungen **Einstellungen importieren und exportieren** auf der Visual Studio **Tools** Menü. Weitere Informationen finden Sie unter [Reset settings (Zurücksetzen der Einstellungen)](../ide/environment-settings.md#reset-settings).

### <a name="see-also"></a>Siehe auch

- [Debugging basics: Registers window (Grundlagen des Debuggens: Das Registerfenster)](../debugger/debugging-basics-registers-window.md)
- [Viewing data in the debugger (Anzeigen von Daten im Debugger)](../debugger/viewing-data-in-the-debugger.md)
