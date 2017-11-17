---
title: Add-Methode (WeakSet) (JavaScript) | Microsoft Docs
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
ms.assetid: d35d0287-6b33-4720-b9d7-8954c428ce4e
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3ab486beaba4a26c73930b5ceaee927f73aa077a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="add-method-weakset-javascript"></a>add-Methode (WeakSet) (JavaScript)
Fügt `WeakSet` ein neues Element hinzu.  
  
## <a name="syntax"></a>Syntax  
  
```JavaScript  
weaksetObj.add(obj)  
```  
  
#### <a name="parameters"></a>Parameter  
 `weaksetObj`  
 Erforderlich. Ein `WeakSet`-Objekt.  
  
 `obj`  
 Erforderlich. Neues Element des `WeakSet`-Objekts.  
  
## <a name="remarks"></a>Hinweise  
 Das neue Element muss ein eindeutiges Objekt und darf kein beliebiger Wert sein. Wenn Sie einem `WeakSet` ein nicht eindeutiges Element hinzufügen, wird das neue Element der Auflistung nicht hinzugefügt.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird gezeigt, wie Sie einem Satz Member hinzufügen und anschließend prüfen, ob sie hinzugefügt wurden.  
  
```JavaScript  
var ws = new WeakSet();  
  
var str = new String("Thomas Jefferson");  
var num = new Number(1776);  
  
ws.add(str);  
ws.add(num);  
  
console.log(ws.has(str));  
console.log(ws.has(num));  
  
ws.delete(str);  
console.log(ws.has(str));  
  
// Output:  
// true  
// true  
// false  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]