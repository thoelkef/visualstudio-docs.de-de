---
title: "\"Default\" darf in einer Switch-Anweisung nur einmal vorkommen | Microsoft-Dokumentation"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 0fdce6a86665b942098e4542dc237bc1ef22ad8a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85815512"
---
# <a name="default-can-only-appear-once-in-a-switch-statement"></a>"default" darf in einer switch-Anweisung nur einmal angegeben werden
Sie haben versucht, die **default** -Anweisung mehrmals in einer Switch-Anweisung zu verwenden. Der Standardfall ist immer die letzte Case-Anweisung in einer Switch-Anweisung (der FallThrough-Fall).  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Entfernen Sie alle zusätzlichen **default** Case-Anweisungen aus der- `switch` Anweisung (verwenden Sie höchstens eine Standard Case-Anweisung in der Switch-Anweisung).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Switch-Anweisung](../../javascript/reference/switch-statement-javascript.md)   
 [Steuern des Programmablaufs](../../javascript/controlling-program-flow-javascript.md)   
 [Reservierte Wörter in JavaScript](../../javascript/reference/javascript-reserved-words.md)