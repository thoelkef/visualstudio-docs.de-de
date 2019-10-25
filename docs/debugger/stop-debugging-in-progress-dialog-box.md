---
title: Das Debuggen wird beendet (Dialog Feld) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.stopnow
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Stop Debugging in Progress dialog box
ms.assetid: ed7ef49d-e25f-4a4d-9396-9bc7b4143117
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3beefe16f8883eb64d7d0a2641cabf9eb1f702fa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72729657"
---
# <a name="stop-debugging-in-progress-dialog-box"></a>Debuggen wird beendet (Dialogfeld)
Dieses Dialogfeld wird angezeigt, wenn vom Debugger versucht wird, eine Debugsitzung zu beenden, der Beendigungsvorgang jedoch einige Zeit dauert. Das Beenden einer Debugsitzung erfolgt normalerweise sehr schnell, sodass dieses Dialogfeld nicht angezeigt wird. Manchmal dauert es jedoch eine Weile, bis alle derzeit debuggten Prozesse getrennt sind. Wenn das Beenden der Sitzung mehrere Sekunden dauert (bzw. ein Fehler beim Trennen auftritt), wird dieses Dialogfeld angezeigt. Bei wiederholtem Auftreten kann dies auf ein internes Problem hindeuten. Nehmen Sie ggf. Kontakt zum Produktsupport auf.

 Sie können entweder warten, bis alle Prozesse getrennt sind und dieses Dialogfeld ausgeblendet wird, oder Sie erzwingen über die Schaltfläche **Jetzt beenden** die sofortige Beendigung.

 **Jetzt abbrechen** Klicken Sie auf diese Schaltfläche, um die Debugsitzung sofort zu beenden Die Verwendung von " **jetzt** beenden" wird beendet, anstatt die Prozesse zu trennen, die gedeppt werden. Wenn Sie Systemprozesse debuggen und die Prozesse mit **Jetzt beenden** stoppen, kann es zu unerwarteten und unerwünschten Folgen kommen.

## <a name="see-also"></a>Siehe auch
- [Debuggersicherheit](../debugger/debugger-security.md)
- [Trennen von Programmen](/previous-versions/visualstudio/visual-studio-2010/x1thkxez(v=vs.100))