---
title: Deaktivieren Sie den Just-In-Time-Debugger | Microsoft-Dokumentation
ms.date: 05/23/18
ms.topic: troubleshooting
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f946c44039407ac413fb0b49234a8590025e12d3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53959786"
---
# <a name="disable-the-just-in-time-debugger"></a>Deaktivieren des Just-In-Time-Debuggers 

Das Dialogfeld "Just-in-Time-Debugger" möglicherweise tritt ein Fehler in einer ausgeführten app zu öffnen und zu verhindern, dass die app nicht fortgesetzt werden kann. 

Der Just-in-Time-Debugger bietet Ihnen die Option zum Starten von Visual Studio, um den Fehler zu debuggen. Sie benötigen [Visual Studio](http://visualstudio.microsoft.com) oder einem anderen ausgewählten Debugger installiert, um detaillierte Informationen zu diesem Fehler anzuzeigen, oder versuchen Sie es zum Debuggen. 

Wenn Sie ein Visual Studio-Benutzer und möchten, versuchen Sie es zum Debuggen des Fehlers finden Sie unter [Debuggen mithilfe des Just-in-Time-Debuggers](../debugger/debug-using-the-just-in-time-debugger.md). Wenn Sie können nicht den Fehler beheben, oder der Just-in-Time-Debugger nicht geöffnet bleiben soll, können Sie [deaktivieren Sie Just-in-Time-Debuggen in Visual Studio](debug-using-the-just-in-time-debugger.md#BKMK_Enabling). 

Wenn Sie Visual Studio installiert, aber nicht mehr ausführen mussten, müssen Sie möglicherweise auf [deaktivieren Sie Just-in-Time-Debuggen aus der Windows-Registrierung](debug-using-the-just-in-time-debugger.md#disable-just-in-time-debugging-from-the-windows-registry). 

Wenn Sie Visual Studio installiert haben, können Sie die Just-In-Time-Debuggen deaktivieren, Debuggen von Skripts oder das serverseitige debugging verhindern. 

- Wenn Sie eine Web-app ausführen möchten, deaktivieren Sie das Skriptdebugging:
  
  In Windows **Systemsteuerung** > **Netzwerk und Internet** > **Internetoptionen**Option **deaktivieren Skript debuggen () InternetExplorer)** und **Skriptdebugging deaktivieren (andere)**. Die genauen Schritte und die Einstellungen abhängig von Ihrer Version von Windows und Ihren Browser.
  
  ![JIT-Internetoptionen](../debugger/media/jitinternetoptions.png "JIT Internetoptionen")
  
- Wenn Sie eine ASP.NET Web-app in IIS hosten, deaktivieren Sie die serverseitige debugging:

  1. Im IIS-Manager **Ansicht "Features"** unter der **ASP.NET** Abschnitt, doppelklicken Sie auf **.NET Kompilierung**, oder wählen Sie ihn, und wählen Sie dann **Funktion öffnen**in die **Aktionen** Bereich. 
  1. Klicken Sie unter **Verhalten** > **Debuggen**Option **"false"**. Die Schritte unterscheiden sich in älteren Versionen von IIS.

Nachdem Sie die Just-In-Time-Debuggen deaktivieren, die app möglicherweise der Fehler behandelt, und führen Sie wie gewohnt. 

Wenn die app immer noch einen nicht behandelten Fehler hat, möglicherweise eine Fehlermeldung angezeigt oder die app Absturz oder aufhängen führt, kann. Die app nicht normal ausgeführt, bis der Fehler behoben wurde. Sie können versuchen, wenden Sie sich an den Besitzer der app, und bitten Sie diesen Fehler beheben.
