---
title: Keine "break ist" außerhalb der Schleife | Microsoft-Dokumentation
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
ms.openlocfilehash: a02848230187eb465d56ed73e44380e4b043b117
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946627"
---
# <a name="cant-have-break-outside-of-loop"></a>"break" ist außerhalb der Schleife unzulässig
Sie haben versucht, Sie verwenden die **Break** -Schlüsselwort außerhalb einer Schleife. Die **Break** -Schlüsselwort wird verwendet, um eine Schleife zu beenden oder `switch` Anweisung. Es muss im Text einer Schleife eingebettet werden oder `switch` Anweisung. Allerdings eine **Bezeichnung** können der Schlüsselwort "Break" folgen.  
  
```js
break labelname;  
```  
  
 Benötigen Sie nur das bezeichnete Format der **Break** Schlüsselwort bei Verwendung von geschachtelten Schleifen oder `switch` Anweisungen und muss aus einer Schleife zu unterbrechen, die nicht den innersten ist.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Stellen Sie sicher, dass die **Break** Schlüsselwort wird in einer einschließenden Schleife oder Switch-Anweisung angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [break-Anweisung](../../javascript/reference/break-statement-javascript.md)   
 [Steuern des Programmablaufs](../../javascript/controlling-program-flow-javascript.md)   
 [Problembehandlung bei Skripts](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)