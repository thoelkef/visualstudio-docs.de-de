---
title: Set-Objekt (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Set
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4a4dd749-2a76-44fb-9cb0-a3ef317f75fb
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5134ec09c9a8642499212af9dd5fd44de0068adc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="set-object-javascript"></a>Set-Objekt (JavaScript)
Eine Auflistung eindeutiger Werte eines beliebigen Typs.  
  
## <a name="syntax"></a>Syntax  
  
```  
setObj = new Set()     
```  
  
## <a name="remarks"></a>Hinweise  
 Wenn Sie versuchen, einen nicht eindeutigen Wert zu `Set` hinzuzufügen, wird der neue Wert der Auflistung nicht hinzugefügt.  
  
## <a name="properties"></a>Eigenschaften  
 In der folgenden Tabelle werden die Eigenschaften des `Set`-Objekts aufgelistet.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|[Konstruktor](../../javascript/reference/constructor-property-set.md)|Gibt die Funktion an, durch die ein Satz erstellt wird.|  
|[Prototyp](../../javascript/reference/prototype-property-set.md)|Gibt einen Verweis auf den Prototyp für einen Satz zurück.|  
|[size](../../javascript/reference/size-property-set-javascript.md)|Gibt die Anzahl der Elemente in einem Satz zurück.|  
  
## <a name="methods"></a>Methoden  
 In der folgenden Tabelle werden die Methoden des `Set`-Objekts aufgelistet.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[add](../../javascript/reference/add-method-set-javascript.md)|Fügt einem Satz ein Element hinzu.|  
|[clear](../../javascript/reference/clear-method-set-javascript.md)|Entfernt alle Elemente aus einem Satz.|  
|[Löschen](../../javascript/reference/delete-method-set-javascript.md)|Entfernt ein angegebenes Element aus einem Satz.|  
|[forEach](../../javascript/reference/foreach-method-set-javascript.md)|Führt die angegebene Aktion für jedes Element in einem Satz aus.|  
|[hat](../../javascript/reference/has-method-set-javascript.md)|Gibt `true` zurück, wenn der Satz ein angegebenes Element enthält.|  
|[toString](../../javascript/reference/tostring-method-set-javascript.md)|Gibt eine Zeichenfolgendarstellung eines Satzes zurück.|  
|[valueOf](../../javascript/reference/valueof-method-set-javascript.md)|Gibt den einfachen Wert des angegebenen Objekts zurück.|  
  
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