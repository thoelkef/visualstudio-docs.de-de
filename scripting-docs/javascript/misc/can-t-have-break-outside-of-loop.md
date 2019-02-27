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
ms.openlocfilehash: 36551a1a70973409768b7971545c783b3621ffb6
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2019
ms.locfileid: "56839892"
---
# <a name="cant-have-break-outside-of-loop"></a>"break" ist außerhalb der Schleife unzulässig
Sie haben versucht, Sie verwenden die **Break** -Schlüsselwort außerhalb einer Schleife. Die **Break** -Schlüsselwort wird verwendet, um eine Schleife zu beenden oder `switch` Anweisung. Es muss im Text einer Schleife eingebettet werden oder `switch` Anweisung. Allerdings eine **Bezeichnung** können der Schlüsselwort "Break" folgen.  
  
```js
break labelname;  
```  
  
 Benötigen Sie nur das bezeichnete Format der **Break** Schlüsselwort bei Verwendung von geschachtelten Schleifen oder `switch` Anweisungen und muss aus einer Schleife zu unterbrechen, die nicht den innersten ist.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass die **Break** Schlüsselwort wird in einer einschließenden Schleife oder Switch-Anweisung angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [break-Anweisung](../../javascript/reference/break-statement-javascript.md)   
 [Steuern des Programmablaufs](../../javascript/controlling-program-flow-javascript.md)   
 [Problembehandlung bei Skripts](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)