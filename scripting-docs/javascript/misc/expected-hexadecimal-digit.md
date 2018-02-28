---
title: Erwartete Hexadezimalziffer | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 67a86df7-49f9-43cb-99c6-99b1a427827a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9e29131c4ecf4f476a30da94ec67676d6bea347
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="expected-hexadecimal-digit"></a>Hexadezimalzahl erwartet
Sie haben eine falsche Unicode-Escapesequenz erstellt. Unicode-Escapesequenzen beginnen mit \u, gefolgt von genau vier hexadezimale Ziffern (nicht mehr und nicht kleiner). Unicode-Hexadezimalzeichen darf nur die Ziffern 0-9, die Großbuchstaben A-F und die Kleinbuchstaben Buchstaben a bis f. Das folgende Beispiel zeigt eine ordnungsgemäß gebildete Unicode-Escapesequenz.  
  
```JavaScript  
z = "\u1A5F";  
```  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Achten Sie darauf die Unicode-Hexadezimalzeichen mit \u beginnen, enthält nur die Ziffern 0-9, die Großbuchstaben A-F, die Kleinbuchstaben Buchstaben a bis f; die in vier Ziffern gruppiert werden.  
  
    > [!NOTE]
    >  Wenn der Literaltext \u in einer Zeichenfolge, und verwenden Sie dann zwei umgekehrte Schrägstriche - werden sollen (\\\u)-eine für den ersten umgekehrten Schrägstrich mit Escapezeichen versehen.  
  
## <a name="see-also"></a>Siehe auch  
 [Datentypen](../../javascript/data-types-javascript.md)