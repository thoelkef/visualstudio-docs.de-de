---
title: Deaktivieren Sie den Just-in-Time-Debugger | Microsoft-Dokumentation
ms.date: 05/23/2018
ms.topic: troubleshooting
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0024716875dce7e81567d60a6e61069be64ec185
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911459"
---
# <a name="disable-the-just-in-time-debugger"></a>Deaktivieren des Just-In-Time-Debuggers

Das Dialogfeld Just-in-Time-Debugger kann geöffnet werden, wenn ein Fehler in einer laufenden app auftritt, und verhindert, dass die APP fortgesetzt wird.

Der Just-in-Time-Debugger bietet Ihnen die Möglichkeit, Visual Studio zu starten, um den Fehler zu debuggen. Sie müssen [Visual Studio](https://visualstudio.microsoft.com/) oder einen anderen ausgewählten Debugger installiert haben, um ausführliche Informationen zum Fehler anzuzeigen oder zu debuggen.

Wenn Sie ein Visual Studio-Benutzer sind und versuchen möchten, den Fehler zu debuggen, lesen Sie [Debuggen mithilfe des Just-in-Time-Debuggers](../debugger/debug-using-the-just-in-time-debugger.md). Wenn Sie den Fehler nicht beheben können oder den Just-in-Time-Debugger nicht öffnen möchten, können Sie [Just-in-Time-Debuggen in Visual Studio deaktivieren](debug-using-the-just-in-time-debugger.md#BKMK_Enabling).

Wenn Sie Visual Studio installiert haben, aber nicht mehr tun, müssen Sie möglicherweise [das Just-in-Time-Debuggen aus der Windows-Registrierung deaktivieren](debug-using-the-just-in-time-debugger.md#disable-just-in-time-debugging-from-the-windows-registry).

Wenn Sie Visual Studio nicht installiert haben, können Sie das Just-in-Time-Debuggen verhindern, indem Sie das Skript Debugging oder das serverseitige Debuggen deaktivieren.

- Wenn Sie versuchen, eine Web-App auszuführen, deaktivieren Sie das Skript Debugging:

  Wählen Sie in der Windows- **Systemsteuerung** > **Netzwerk-und Internet** > **Internetoptionen** **Skript Debugging deaktivieren (Internet Explorer)** aus, und deaktivieren Sie das **Skript Debuggen (Sonstiges)** . Die genauen Schritte und Einstellungen hängen von Ihrer Windows-Version und dem Browser ab.

  ![JIT-Internet Optionen](../debugger/media/jitinternetoptions.png "JIT-Internetoptionen")

- Wenn Sie eine ASP.net-Web-App in IIS gehostet haben, deaktivieren Sie das serverseitige Debuggen:

  1. Doppelklicken Sie in der **Ansicht**IIS-Manager-Features im Abschnitt **ASP.net** auf **.NET-Kompilierung**, oder wählen Sie Sie aus, und wählen Sie dann im Bereich **Aktionen** die Option **Funktion öffnen** aus.
  1. Wählen Sie unter **Verhalten** > **Debuggen**die Option **false**. Die Schritte unterscheiden sich in älteren Versionen von IIS.

Nachdem Sie das Just-in-Time-Debuggen deaktiviert haben, kann die APP den Fehler möglicherweise verarbeiten und ordnungsgemäß ausführen.

Wenn für die APP weiterhin ein nicht behandelter Fehler vorliegt, wird möglicherweise eine Fehlermeldung angezeigt, oder die APP stürzt ab oder stürzt ab. Die APP wird normalerweise erst ausgeführt, wenn der Fehler korrigiert wurde. Sie können versuchen, den Besitzer der APP zu kontaktieren und ihn zu korrigieren.
