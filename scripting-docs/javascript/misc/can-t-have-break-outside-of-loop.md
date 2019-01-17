---
title: Keine "break ist" außerhalb der Schleife | Microsoft-Dokumentation
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
- VS.WebClient.Help.SCRIPT1019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 53f32da997b775e01959df5abc7e72fb55c1b194
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345044"
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