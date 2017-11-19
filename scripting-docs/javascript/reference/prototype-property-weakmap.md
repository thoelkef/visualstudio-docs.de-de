---
title: Prototype-Eigenschaft (WeakMap) | Microsoft Docs
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
ms.assetid: d28b8a9b-38c9-443d-9586-7cc74784bd99
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5cc1bff0d62f2aeb8d6fb78a0857f287fb34078c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-weakmap"></a>prototype-Eigenschaft (WeakMap)
Gibt einen Verweis auf den Prototyp für ein `WeakMap`-Objekt zurück.  
  
## <a name="syntax"></a>Syntax  
  
```JavaScript  
weakmap.prototype  
```  
  
## <a name="remarks"></a>Hinweise  
 Das `weakmap`-Argument ist der Name eines `WeakMap`-Objekts.  
  
 Mit der `prototype`-Eigenschaft können Sie einer Objektklasse grundlegende Funktionen zur Verfügung stellen. Neue Instanzen eines Objekts "erben" das Verhalten des Prototyps, der diesem Objekt zugewiesen ist.  
  
 Um beispielsweise dem `WeakMap`-Objekt eine Methode hinzuzufügen, die den Wert des größten Elements der `WeakMap` zurückgibt, deklarieren Sie die Funktion, fügen Sie sie `WeakMap.prototype` hinzu, und verwenden Sie sie dann.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]