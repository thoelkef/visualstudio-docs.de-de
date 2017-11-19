---
title: has-Methode (Set) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: fb80f2e0-fc5e-4508-af14-1c3b3b833636
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9690e3d091e8ae0f9670fd737a29590524834c9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="has-method-set-javascript"></a>has-Methode (Set) (JavaScript)
Gibt `true` zurück, wenn der Satz das angegebene Element enthält.  
  
## <a name="syntax"></a>Syntax  
  
```JavaScript  
setObj.has(value)  
```  
  
#### <a name="parameters"></a>Parameter  
 `setObj`  
 Erforderlich. Ein `Set`-Objekt.  
  
 `value`  
 Erforderlich. Das zu testende Element.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 `true`, wenn der Satz das angegebene Element enthält.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird gezeigt, wie Sie einem `Set` Member hinzufügen und anschließend überprüfen, ob der Satz einen bestimmten Member enthält.  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
  
document.write(s.has(1776));  
document.write(s.has("1776"));  
  
// Output:  
// true  
// false  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]