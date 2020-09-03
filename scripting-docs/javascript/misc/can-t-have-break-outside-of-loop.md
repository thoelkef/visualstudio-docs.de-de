---
title: "\"Break\" ist außerhalb der Schleife unzulässig | Microsoft-Dokumentation"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0959bad452d3b24ca1475b66e37fbdab1e9c3e7f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817657"
---
# <a name="cant-have-break-outside-of-loop"></a>"break" ist außerhalb der Schleife unzulässig
Sie haben versucht, das **break** -Schlüsselwort außerhalb einer-Schleife zu verwenden. Das **break** -Schlüsselwort wird zum Beenden einer-Schleife oder- `switch` Anweisung verwendet. Er muss in den Text einer-Schleife oder-Anweisung eingebettet werden `switch` . Allerdings kann eine **Bezeichnung** dem break-Schlüsselwort folgen.  
  
```js
break labelname;  
```  
  
 Sie benötigen nur die Bezeichnung mit dem Schlüsselwort " **break** ", wenn Sie die Verwendung von "schsted Loops" oder "-Anweisungen" durchlaufen `switch` und aus einer Schleife Herausbrechen müssen, die nicht die innerste ist.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Stellen Sie sicher, dass das **break** -Schlüsselwort in einer einschließenden Schleife oder Switch-Anweisung erscheint.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Break-Anweisung](../../javascript/reference/break-statement-javascript.md)   
 [Steuern des Programmablaufs](../../javascript/controlling-program-flow-javascript.md)   
 [Problembehandlung bei Skripts](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)