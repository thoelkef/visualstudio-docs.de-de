---
title: Unvollständig Kommentar | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT1016
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d4286315-814b-4966-b4c4-1ee19d796eff
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9fde5d5edd7e81060b088e4940d752aa05e65ded
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/10/2018
---
# <a name="unterminated-comment"></a>Nicht abgeschlossener Kommentar
Sie begonnen hat einen mehrzeiligen Kommentar-Block, jedoch nicht ordnungsgemäß beendet. Mehrzeilige Kommentare beginnen mit einem "/ *" Kombination und mit der umgekehrten "\*/" Kombination. Im Folgenden finden Sie ein Beispiel dazu:  
  
```JavaScript  
/* This is a comment  
This is another part of the same comment.*/  
```  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Achten Sie darauf, dass Sie zum Beenden der mehrzeilige Kommentare mit "* /".  
  
## <a name="see-also"></a>Siehe auch  
 [Comment-Anweisungen](../../javascript/reference/comment-statements-javascript.md)