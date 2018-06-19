---
title: Constructor-Eigenschaft (Set) | Microsoft Docs
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
ms.assetid: f350b7eb-8994-40bf-9011-f8b20fcef34f
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea9af6d60c2ae8bc8a383c4cebbf0955e183895e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636210"
---
# <a name="constructor-property-set"></a>constructor-Eigenschaft (Set)
Gibt die Funktion an, durch die ein Satz erstellt wird.  
  
## <a name="syntax"></a>Syntax  
  
```JavaScript  
set.constructor  
```  
  
## <a name="remarks"></a>Hinweise  
 Der erforderliche `set` ist der Name des Satzes.  
  
 Die `constructor`-Eigenschaft ist ein Member des Prototyps eines jeden Objekts, das einen Prototyp besitzt. Dies schließt alle systeminternen JavaScript-Objekte mit Ausnahme der Objekte `Global` und `Math` ein. Die `constructor`-Eigenschaft enthält einen Verweis auf die Funktion, mit der die Instanzen des betreffenden Objekts erstellt werden.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]