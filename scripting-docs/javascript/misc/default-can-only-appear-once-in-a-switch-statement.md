---
title: "\"Default\" kann nur einmal in einer Switch-Anweisung | Microsoft-Dokumentation"
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1027
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a94100f4-6ee5-4759-b635-9d309e47111e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4f254825e27793999932b772ac4bc2512908fae
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347306"
---
# <a name="default-can-only-appear-once-in-a-switch-statement"></a>"default" darf in einer switch-Anweisung nur einmal angegeben werden
Sie haben versucht, Sie verwenden die **Standard** Anweisung mehr als einmal in einer Switch-Anweisung. Der Standardfall ist immer der letzte Case-Anweisung in einer Switch-Anweisung (es ist der Fall-through-Fall).  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Entfernen Sie alle zusätzlichen **Standard** case-Anweisungen aus Ihrem `switch` Anweisung (verwenden Sie bei den meisten Groß-/Kleinschreibung von Default-Anweisung in der Switch-Anweisung).  
  
## <a name="see-also"></a>Siehe auch  
 [Switch-Anweisung](../../javascript/reference/switch-statement-javascript.md)   
 [Steuern des Programmablaufs](../../javascript/controlling-program-flow-javascript.md)   
 [Reservierte Wörter in JavaScript](../../javascript/reference/javascript-reserved-words.md)