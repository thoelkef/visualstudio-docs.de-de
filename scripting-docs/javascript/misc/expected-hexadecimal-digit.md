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
ms.openlocfilehash: e5cf7d77853cb200afe568656e1055459acad7d1
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2019
ms.locfileid: "56842285"
---
# <a name="expected-hexadecimal-digit"></a>Hexadezimalzahl erwartet
Sie haben eine falsche Unicode-Escapesequenz erstellt. Unicode-Escapesequenzen mit \u, gefolgt von genau vier hexadezimale Ziffern (nicht mehr und nicht weniger) beginnen. Unicode-Hexadezimalzeichen können nur die Zahlen 0-9, der Großbuchstaben A bis F und die Kleinbuchstaben Buchstaben a bis f enthalten. Das folgende Beispiel zeigt eine ordnungsgemäß formatierte Unicode-Escapesequenz.  
  
```JavaScript  
z = "\u1A5F";  
```  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Werden Sie sicher, dass Ihre Unicode-Hexadezimalzeichen beginnen mit der \u enthält nur die Zahlen 0-9, der Großbuchstaben A bis F, die Kleinbuchstaben Buchstaben a bis f; die in vier Ziffern gruppiert werden.  
  
    > [!NOTE]
    >  Sollten Sie die \u Literaltext in einer Zeichenfolge verwenden und dann zwei umgekehrte Schrägstriche - (\\\u) – eine der ersten umgekehrten Schrägstrich als Escapezeichen.  
  
## <a name="see-also"></a>Siehe auch  
 [Datentypen](../../javascript/data-types-javascript.md)