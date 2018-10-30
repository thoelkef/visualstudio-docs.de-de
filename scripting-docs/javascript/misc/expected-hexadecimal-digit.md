---
title: Erwartete Hexadezimalziffer | Microsoft-Dokumentation
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
- VS.WebClient.Help.SCRIPT1023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 67a86df7-49f9-43cb-99c6-99b1a427827a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9e29131c4ecf4f476a30da94ec67676d6bea347
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836176"
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