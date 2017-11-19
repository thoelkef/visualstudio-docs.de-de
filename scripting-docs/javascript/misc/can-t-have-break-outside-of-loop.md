---
title: "Kann &#39; haben t &#39; Break &#39; außerhalb der Schleife | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT1019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb23f1bc3de087515cad9ba4910cf2ebaf640353
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="can39t-have-39break39-outside-of-loop"></a>Kann &#39; haben t &#39; Break &#39; außerhalb der Schleife unzulässig
Sie haben versucht, die **Break** -Schlüsselwort außerhalb einer Schleife. Die **Break** Schlüsselwort wird verwendet, um eine Schleife beendet oder `switch` Anweisung. Sie müssen im Text einer Schleife eingebettet werden oder `switch` Anweisung. Allerdings eine **Bezeichnung** können die Break-Schlüsselwort folgen.  
  
```  
break labelname;  
```  
  
 Benötigen Sie nur mit der Bezeichnung Form der **Break** Schlüsselwort bei Verwendung von geschachtelten Schleifen oder `switch` -Anweisungen und die Notwendigkeit, die aus einer Schleife zu unterbrechen, die nicht der innersten ist.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass die **Break** -Schlüsselworts in einer einschließenden Schleife oder Switch-Anweisung.  
  
## <a name="see-also"></a>Siehe auch  
 [break-Anweisung](../../javascript/reference/break-statement-javascript.md)   
 [Steuerung des Programmablaufs](../../javascript/controlling-program-flow-javascript.md)   
 [Problembehandlung bei Skripts](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)