---
title: Constructor-Eigenschaft (Map) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a90d6a29-bd64-4e01-8d2f-988b7e3e4a24
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7050f4a7eab149862c08ea755361b5bd0d297299
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636030"
---
# <a name="constructor-property-map"></a>constructor-Eigenschaft (Map)
Gibt die Funktion an, durch die eine Zuordnung erstellt wird.  
  
## <a name="syntax"></a>Syntax  
  
```JavaScript  
map.constructor  
```  
  
## <a name="remarks"></a>Hinweise  
 Die erforderliche `map` ist der Name der Zuordnung.  
  
 Die `constructor`-Eigenschaft ist ein Member des Prototyps eines jeden Objekts, das einen Prototyp besitzt. Dies schließt alle systeminternen JavaScript-Objekte mit Ausnahme der Objekte `Global` und `Math` ein. Die `constructor`-Eigenschaft enthält einen Verweis auf die Funktion, mit der die Instanzen des betreffenden Objekts erstellt werden.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]