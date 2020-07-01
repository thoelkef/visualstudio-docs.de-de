---
title: Anzeigen von Registerwerten im Debugger | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 11/19/2018
ms.topic: how-to
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
ms.openlocfilehash: ed60b21d7c8e90e18b389a29c3343713ac8ece3d
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2020
ms.locfileid: "85348573"
---
# <a name="view-register-values-in-the-registers-window-c-c-visual-basic-f"></a>Anzeigen von Registerwerten im Fenster „Register“ (C#, C++, Visual Basic, F#)

Der Registerinhalt wird während des Debuggens in Visual Studio im Fenster **Register** angezeigt. Eine allgemeine Einführung in Konzepte hinter Register und die **registriert** Fenster finden Sie unter [Grundlagen des Debuggens:  Fenster „Register“](../debugger/debugging-basics-registers-window.md).

> [!NOTE]
> Registerinformationen sind für Skript- und SQL-Apps nicht verfügbar.

Während des Debuggens ändern sich die Registerwerte, wenn Code in ihrer App ausgeführt wird. Kürzlich geänderte Werte werden im Fenster **Register** rot angezeigt.

Aus Gründen der Übersichtlichkeit werden Register im Fenster **Register** nach Gruppen eingeteilt, die sich je nach Plattform und Prozessortyp unterscheiden. Sie können Registergruppen ein- oder ausblenden. Weitere Informationen finden Sie unter [Vorgehensweise: Display and hide register groups (Anzeigen und Ausblenden von Registergruppen)](../debugger/how-to-display-and-hide-register-groups.md)

Informationen zu den Flags, die im Fenster **Register** angezeigt werden, finden Sie unter [Informationen zum Fenster „Register“](../debugger/debugging-basics-registers-window.md).

Die Registerwerte können bearbeitet werden. Weitere Informationen finden Sie unter [Vorgehensweise: Edit a register value (Bearbeiten eines Registerwerts)](../debugger/how-to-edit-a-register-value.md).

**So öffnen Sie das Fenster „Register“**

1. Aktivieren Sie das Debuggen auf Adressebene, indem Sie **Debuggen auf Adressebene aktivieren** in **Tools** (oder **Debuggen**) > **Optionen** > **Debuggen** auswählen.

1. Wählen Sie während des Debugvorgangs oder bei einem Haltepunkt **Debuggen** > **Fenster** > **Register** aus, oder drücken Sie **ALT**+**5**.

>[!NOTE]
>Die Dialogfelder und Menübefehle können abweichen, je nach Ihrer Visual Studio-Edition bzw. deren Einstellungen. Wählen Sie im Visual Studio-Menü **Tools** die Option **Einstellungen importieren und exportieren** aus, um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Reset settings (Zurücksetzen der Einstellungen)](../ide/environment-settings.md#reset-settings).

### <a name="see-also"></a>Siehe auch

- [Debuggrundlagen: Registerfenster](../debugger/debugging-basics-registers-window.md)
- [Viewing data in the debugger (Anzeigen von Daten im Debugger)](../debugger/viewing-data-in-the-debugger.md)
