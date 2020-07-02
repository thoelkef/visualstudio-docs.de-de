---
title: Hexadezimale Ziffer erwartet | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: c0797d44115fb5b44cb0c670153e8476356bd533
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85816565"
---
# <a name="expected-hexadecimal-digit"></a>Hexadezimalzahl erwartet
Sie haben eine falsche Unicode-Escapesequenz erstellt. Unicode-Escapesequenzen beginnen mit \u, gefolgt von genau vier hexadezimalen Ziffern (nicht mehr und nicht weniger). Hexadezimale Unicode-Ziffern können nur die Zahlen 0-9, die Großbuchstaben a-f und die Kleinbuchstaben a-f enthalten. Das folgende Beispiel veranschaulicht eine ordnungsgemäß formatierte Unicode-Escapesequenz.  
  
```JavaScript  
z = "\u1A5F";  
```  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Stellen Sie sicher, dass die hexadezimalen Unicode-Ziffern mit \u beginnen und nur die Zahlen 0-9, die Großbuchstaben a-f, die Kleinbuchstaben a-f; enthalten. und sind in vier Ziffern gruppiert.  
  
    > [!NOTE]
    > Wenn Sie den Literaltext \u in einer Zeichenfolge verwenden möchten, verwenden Sie zwei umgekehrte Schrägstriche ( \\ \u)-One, um den ersten umgekehrten Schrägstrich mit Escapezeichen zu versehen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datentypen](../../javascript/data-types-javascript.md)