---
title: Hexadezimale Ziffer erwartet | Microsoft-Dokumentation
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
ms.openlocfilehash: f6672046e0f7bf5e39c334dc0ba30f22eaff6e9a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573372"
---
# <a name="expected-hexadecimal-digit"></a>Hexadezimalzahl erwartet
Sie haben eine falsche Unicode-Escapesequenz erstellt. Unicode-Escapesequenzen beginnen mit \u, gefolgt von genau vier hexadezimalen Ziffern (nicht mehr und nicht weniger). Hexadezimale Unicode-Ziffern können nur die Zahlen 0-9, die Großbuchstaben a-f und die Kleinbuchstaben a-f enthalten. Das folgende Beispiel veranschaulicht eine ordnungsgemäß formatierte Unicode-Escapesequenz.  
  
```JavaScript  
z = "\u1A5F";  
```  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Stellen Sie sicher, dass die hexadezimalen Unicode-Ziffern mit \u beginnen und nur die Zahlen 0-9, die Großbuchstaben a-f, die Kleinbuchstaben a-f; enthalten. und sind in vier Ziffern gruppiert.  
  
    > [!NOTE]
    > Wenn Sie den Literaltext \u in einer Zeichenfolge verwenden möchten, verwenden Sie zwei umgekehrte Schrägstriche (\\ \u)-eine, um den ersten umgekehrten Schrägstrich zu Escapezeichen zu versehen.  
  
## <a name="see-also"></a>Siehe auch  
 [Datentypen](../../javascript/data-types-javascript.md)