---
title: Funktion enthält kein gültiges Prototype-Objekt. | Microsoft-Dokumentation
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
- VS.WebClient.Help.SCRIPT5023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b9e34652-190f-4b57-b253-df2e8c4d09c6
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4e2cbf198a452cd61f1355682ea3041436d2a27
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346695"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>Funktion enthält kein gültiges prototype-Objekt.
Sie haben versucht, verwenden Sie **Instanceof** zu bestimmen, ob ein Objekt von einer bestimmten Funktion-Klasse abgeleitet wurde, aber Sie neu des Objekts definiert `prototype` Eigenschaft entweder als `null`, oder ein externes Objekt-Typ (beide ungültig [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Objekte). Ein externes Objekt kann es sich um ein Objekt aus dem Host-Objektmodell (z. B. Internet Explorer Dokument oder Window-Objekt) oder ein externes COM-Objekt sein.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Sicherstellen der Funktion `prototype` Eigenschaft bezieht sich auf einen gültigen [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Objekt.  
  
## <a name="see-also"></a>Siehe auch  
 [Function-Objekt](../../javascript/reference/function-object-javascript.md)   
 [prototype-Eigenschaft (Objekt)](../../javascript/reference/prototype-property-object-javascript.md)