---
title: Funktion enthält kein gültiges Prototype-Objekt. | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b9e34652-190f-4b57-b253-df2e8c4d09c6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 31226f972ff4714dd81207cf27d862d3449184a5
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2019
ms.locfileid: "56840762"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>Funktion enthält kein gültiges prototype-Objekt.
Sie haben versucht, verwenden Sie **Instanceof** zu bestimmen, ob ein Objekt von einer bestimmten Funktion-Klasse abgeleitet wurde, aber Sie neu des Objekts definiert `prototype` Eigenschaft entweder als `null`, oder ein externes Objekt-Typ (beide ungültig [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Objekte). Ein externes Objekt kann es sich um ein Objekt aus dem Host-Objektmodell (z. B. Internet Explorer Dokument oder Window-Objekt) oder ein externes COM-Objekt sein.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Sicherstellen der Funktion `prototype` Eigenschaft bezieht sich auf einen gültigen [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Objekt.  
  
## <a name="see-also"></a>Siehe auch  
 [Function-Objekt](../../javascript/reference/function-object-javascript.md)   
 [prototype-Eigenschaft (Objekt)](../../javascript/reference/prototype-property-object-javascript.md)