---
title: Können&#39;wurden &#39;Break&#39; außerhalb der Schleife | Microsoft-Dokumentation
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
ms.openlocfilehash: bb23f1bc3de087515cad9ba4910cf2ebaf640353
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49928554"
---
# <a name="can39t-have-39break39-outside-of-loop"></a>Können&#39;wurden &#39;Break&#39; außerhalb der Schleife unzulässig
Sie haben versucht, Sie verwenden die **Break** -Schlüsselwort außerhalb einer Schleife. Die **Break** -Schlüsselwort wird verwendet, um eine Schleife zu beenden oder `switch` Anweisung. Es muss im Text einer Schleife eingebettet werden oder `switch` Anweisung. Allerdings eine **Bezeichnung** können der Schlüsselwort "Break" folgen.  
  
```  
break labelname;  
```  
  
 Benötigen Sie nur das bezeichnete Format der **Break** Schlüsselwort bei Verwendung von geschachtelten Schleifen oder `switch` Anweisungen und muss aus einer Schleife zu unterbrechen, die nicht den innersten ist.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass die **Break** Schlüsselwort wird in einer einschließenden Schleife oder Switch-Anweisung angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [break-Anweisung](../../javascript/reference/break-statement-javascript.md)   
 [Steuern des Programmablaufs](../../javascript/controlling-program-flow-javascript.md)   
 [Problembehandlung bei Skripts](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)