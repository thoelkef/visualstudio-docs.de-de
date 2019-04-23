---
title: Erwartete Hexadezimalziffer | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 67a86df7-49f9-43cb-99c6-99b1a427827a
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c2507acd42336511dadc3dedd2eba15fe0d5b76
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60050074"
---
# <a name="expected-hexadecimal-digit"></a>Hexadezimalzahl erwartet
Sie haben eine falsche Unicode-Escapesequenz erstellt. Unicode-Escapesequenzen mit \u, gefolgt von genau vier hexadezimale Ziffern (nicht mehr und nicht weniger) beginnen. Unicode-Hexadezimalzeichen können nur die Zahlen 0-9, der Großbuchstaben A bis F und die Kleinbuchstaben Buchstaben a bis f enthalten. Das folgende Beispiel zeigt eine ordnungsgemäß formatierte Unicode-Escapesequenz.  
  
```JavaScript  
z = "\u1A5F";  
```  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Werden Sie sicher, dass Ihre Unicode-Hexadezimalzeichen beginnen mit der \u enthält nur die Zahlen 0-9, der Großbuchstaben A bis F, die Kleinbuchstaben Buchstaben a bis f; die in vier Ziffern gruppiert werden.  
  
    > [!NOTE]
    >  Sollten Sie die \u Literaltext in einer Zeichenfolge verwenden und dann zwei umgekehrte Schrägstriche - (\\\u) – eine der ersten umgekehrten Schrägstrich als Escapezeichen.  
  
## <a name="see-also"></a>Siehe auch  
 [Datentypen](../../javascript/data-types-javascript.md)