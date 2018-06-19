---
title: Add-Methode (Set) (JavaScript) | Microsoft Docs
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
ms.assetid: b4eea447-fd5b-4380-978e-1b95f6dbc438
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 287dbfb6480289ed57edc26d41e9900e4a76c27b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633170"
---
# <a name="add-method-set-javascript"></a>add-Methode (Set) (JavaScript)
Fügt einem Satz ein neues Element hinzu.  
  
## <a name="syntax"></a>Syntax  
  
```JavaScript  
setObj.add(value)  
```  
  
#### <a name="parameters"></a>Parameter  
 `setObj`  
 Erforderlich. Ein `Set`-Objekt.  
  
 `value`  
 Erforderlich. Neues Element des `Set`-Objekts.  
  
## <a name="remarks"></a>Hinweise  
 Das neue Element kann einem beliebigen Typ angehören und muss eindeutig sein. Wenn Sie einem `Set` ein nicht eindeutiges Element hinzufügen, wird das neue Element der Auflistung nicht hinzugefügt.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird gezeigt, wie Sie einem Satz Member hinzufügen und sie dann abrufen.  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]