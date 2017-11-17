---
title: Prototype-Eigenschaft (WeakSet) | Microsoft Docs
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
ms.assetid: 950e15a2-2f56-4cb9-8e48-020efd97f938
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c66c7854a83dcf3128025350a7fcdd17f4dfaf5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-weakset"></a>prototype-Eigenschaft (WeakSet)
Gibt einen Verweis auf den Prototyp für `WeakSet` zurück.  
  
## <a name="syntax"></a>Syntax  
  
```JavaScript  
weakset.prototype  
```  
  
## <a name="remarks"></a>Hinweise  
 Das `weakset`-Argument ist der Name eines Satzes.  
  
 Mit der `prototype`-Eigenschaft können Sie einer Objektklasse grundlegende Funktionen zur Verfügung stellen. Neue Instanzen eines Objekts "erben" das Verhalten des Prototyps, der diesem Objekt zugewiesen ist.  
  
 Um beispielsweise dem `WeakSet`-Objekt eine Methode hinzuzufügen, die den Wert des größten Elements des Satzes zurückgibt, deklarieren Sie die Funktion, fügen Sie sie `WeakSet.prototype` hinzu, und verwenden Sie sie dann.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]