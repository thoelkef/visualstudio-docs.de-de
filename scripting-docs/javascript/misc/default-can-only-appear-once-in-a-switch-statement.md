---
title: "\"Default\" darf in einer Switch-Anweisung nur einmal vorkommen | Microsoft-Dokumentation"
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
ms.openlocfilehash: 90652e44a4bd0362f679be71d0d6401165487aec
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572883"
---
# <a name="default-can-only-appear-once-in-a-switch-statement"></a>"default" darf in einer switch-Anweisung nur einmal angegeben werden
Sie haben versucht, die **default** -Anweisung mehrmals in einer Switch-Anweisung zu verwenden. Der Standardfall ist immer die letzte Case-Anweisung in einer Switch-Anweisung (der FallThrough-Fall).  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Entfernen Sie alle zusätzlichen **default** Case-Anweisungen aus der `switch`-Anweisung (verwenden Sie höchstens eine Standard Case-Anweisung in der Switch-Anweisung).  
  
## <a name="see-also"></a>Siehe auch  
 [Switch-Anweisung](../../javascript/reference/switch-statement-javascript.md)    
 [Steuern des Programmablaufs](../../javascript/controlling-program-flow-javascript.md)    
 [Reservierte Wörter in JavaScript](../../javascript/reference/javascript-reserved-words.md)