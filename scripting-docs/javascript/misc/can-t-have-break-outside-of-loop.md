---
title: "\"Break\" ist außerhalb der Schleife unzulässig | Microsoft-Dokumentation"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 356e7022f940e696030b0cda4f71a599c147dd5a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576019"
---
# <a name="cant-have-break-outside-of-loop"></a>"break" ist außerhalb der Schleife unzulässig
Sie haben versucht, das **break** -Schlüsselwort außerhalb einer-Schleife zu verwenden. Das **break** -Schlüsselwort wird verwendet, um eine Schleife oder eine `switch` Anweisung zu beenden. Er muss in den Text einer-Schleife oder einer `switch`-Anweisung eingebettet werden. Allerdings kann eine **Bezeichnung** dem break-Schlüsselwort folgen.  
  
```js
break labelname;  
```  
  
 Sie benötigen nur die Bezeichnung mit dem Schlüsselwort " **break** ", wenn Sie mit der Verwendung von "schsted Loops" oder `switch`-Anweisungen eine Schleife verlassen müssen, die nicht die innerste Schleife ist.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Stellen Sie sicher, dass das **break** -Schlüsselwort in einer einschließenden Schleife oder Switch-Anweisung erscheint.  
  
## <a name="see-also"></a>Siehe auch  
 [break-Anweisung](../../javascript/reference/break-statement-javascript.md)   
 [Steuern des Programmablaufs](../../javascript/controlling-program-flow-javascript.md)   
 [Problembehandlung bei Skripts](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)