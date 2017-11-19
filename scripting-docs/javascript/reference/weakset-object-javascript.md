---
title: WeakSet-Objekt (JavaScript) | Microsoft Docs
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
ms.assetid: f97e6e7c-d678-4e32-978e-d949a7cafa3a
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e42849c03f698d6ed5f8b0e28725c85555a74d2b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="weakset-object-javascript"></a>WeakSet-Objekt (JavaScript)
Eine Auflistung eindeutiger Objekte eines beliebigen Typs.  
  
## <a name="syntax"></a>Syntax  
  
```  
setObj = new WeakSet()  
```  
  
## <a name="remarks"></a>Hinweise  
 Wenn Sie versuchen, ein nicht eindeutiges Objekt zu `WeakSet` hinzuzufügen, wird das neue Objekt nicht der Auflistung hinzugefügt.  
  
 Im Gegensatz zu einem `Set` dürfen der Auflistung nur Objekte hinzugefügt werden. Willkürliche Werte können nicht der Auflistung hinzugefügt werden.  
  
 In einem `WeakSet` Objekt Verweise auf Objekte in der Gruppe "schwach" gehalten werden. Dies bedeutet, dass `WeakSet` die Ausführung einer Garbage Collection für die Objekte nicht verhindert. Wenn (außer `WeakSet`) keine Verweise auf die Objekte vorhanden sind, kann der Garbage Collector die Objekte erfassen.  
  
 `WeakSet` (oder `WeakMap`) kann in einigen Szenarien im Zusammenhang mit dem Zwischenspeichern von Objekten oder Objektmetadaten im Cache hilfreich sein. Beispielsweise können Metadaten für nicht erweiterbare Objekte in einem `WeakSet` gespeichert werden. Sie können auch mit `WeakSet` einen Cache von Benutzerimages erstellen.  
  
## <a name="properties"></a>Eigenschaften  
 In der folgenden Tabelle werden die Eigenschaften des `WeakSet`-Objekts aufgelistet.  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|Konstruktor|Gibt die Funktion an, durch die ein Satz erstellt wird.|  
|Prototyp|Gibt einen Verweis auf den Prototyp für einen Satz zurück.|  
  
## <a name="methods"></a>Methoden  
 In der folgenden Tabelle werden die Methoden des `WeakSet`-Objekts aufgelistet.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|Hinzufügen|Fügt einem Satz ein Element hinzu.|  
|Löschen|Entfernt ein angegebenes Element aus einem Satz.|  
|has|Gibt `true` zurück, wenn der Satz ein angegebenes Element enthält.|  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird gezeigt, wie Sie einem Satz Member hinzufügen und dann prüfen, ob sie hinzugefügt wurden.  
  
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