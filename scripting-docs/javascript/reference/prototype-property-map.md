---
title: Prototype-Eigenschaft (Map) | Microsoft Docs
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
ms.assetid: c7b429cb-97b7-400e-a214-1b18bddd6b02
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 45601bdff2dfc8047f2499ab07dcdedd66662fc5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-map"></a>prototype-Eigenschaft (Map)
Gibt einen Verweis auf den Prototyp für eine Zuordnung zurück.  
  
## <a name="syntax"></a>Syntax  
  
```JavaScript  
map.prototype  
```  
  
## <a name="remarks"></a>Hinweise  
 Das `map`-Argument ist der Name einer Zuordnung.  
  
 Mit der `prototype`-Eigenschaft können Sie einer Objektklasse grundlegende Funktionen zur Verfügung stellen. Neue Instanzen eines Objekts "erben" das Verhalten des Prototyps, der diesem Objekt zugewiesen ist.  
  
 Um beispielsweise dem `Map`-Objekt eine Methode hinzuzufügen, die den Wert des größten Elements des Satzes zurückgibt, deklarieren Sie die Funktion, fügen Sie sie `Map.prototype` hinzu, und verwenden Sie sie dann.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]