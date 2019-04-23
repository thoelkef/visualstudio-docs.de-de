---
title: "\"Default\" kann nur einmal in einer Switch-Anweisung | Microsoft-Dokumentation"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1027
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a94100f4-6ee5-4759-b635-9d309e47111e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 24162efcc720d9c0073f8a5799c6278b8d3c8c62
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60107826"
---
# <a name="default-can-only-appear-once-in-a-switch-statement"></a>"default" darf in einer switch-Anweisung nur einmal angegeben werden
Sie haben versucht, Sie verwenden die **Standard** Anweisung mehr als einmal in einer Switch-Anweisung. Der Standardfall ist immer der letzte Case-Anweisung in einer Switch-Anweisung (es ist der Fall-through-Fall).  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Entfernen Sie alle zusätzlichen **Standard** case-Anweisungen aus Ihrem `switch` Anweisung (verwenden Sie bei den meisten Groß-/Kleinschreibung von Default-Anweisung in der Switch-Anweisung).  
  
## <a name="see-also"></a>Siehe auch  
 [Switch-Anweisung](../../javascript/reference/switch-statement-javascript.md)   
 [Steuern des Programmablaufs](../../javascript/controlling-program-flow-javascript.md)   
 [Reservierte Wörter in JavaScript](../../javascript/reference/javascript-reserved-words.md)