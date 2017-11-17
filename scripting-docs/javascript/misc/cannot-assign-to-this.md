---
title: Kann nicht zuweisen &#39; dies &#39; | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5000
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c164b9b7d2989076a9dc0ef0bafba6159bc08885
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="cannot-assign-to-39this39"></a>Kann nicht zuweisen &#39; dies &#39;
Sie haben versucht, einen Wert zuzuweisen **dies**. **Dies** ist eine [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Schlüsselwort, das entweder verweist:  
  
-   das Objekt derzeit Ausführen einer Methode  
  
-   das globale Objekt, wenn keine aktuelle Methode vorhanden ist (oder die Methode nicht zu jedem anderen Objekt gehört).  
  
 Eine Methode ist eine [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] -Funktion, die über ein Objekt aufgerufen wird. Innerhalb einer Methode der **dies** Schlüsselwort ist ein Verweis auf das Objekt über die Methode aufgerufen wurde (die geschieht, um das Objekt durch Aufrufen des Klassenkonstruktors mit erstellt werden die **neue** Operator).  
  
 Sie können innerhalb einer Methode verwenden **dies** zum Verweisen auf das aktuelle Objekt, aber Sie können nicht auf einen neuen Wert zuweisen **dies**.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Versuchen Sie nicht zuzuweisende **dies**. Um eine Eigenschaft oder Methode eines instanziierten Objekts zuzugreifen, verwenden Sie den Punktoperator (z. B. circle**.** RADIUS).  
  
    > [!NOTE]
    >  Sie können nicht den Namen einer benutzerdefinierten Variablen **dies**; es ist ein [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] reservierten Wort.  
  
## <a name="see-also"></a>Siehe auch  
 [Diese Anweisung](../../javascript/reference/this-statement-javascript.md)   
 [Problembehandlung bei Skripts](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)