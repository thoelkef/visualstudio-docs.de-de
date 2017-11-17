---
title: Prototype-Eigenschaft (Intl.DateTimeFormat) | Microsoft Docs
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
ms.assetid: e1e693ff-1775-407e-b655-18a60d238ded
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 64dff17e4aaf62940f4c9c5f8b422fcbceb7212a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-intldatetimeformat"></a>prototype-Eigenschaft (Intl.DateTimeFormat)
Gibt einen Verweis auf den Prototyp für eine Formatierung zurück.  
  
## <a name="syntax"></a>Syntax  
  
```JavaScript  
dateTimeFormat.prototype  
```  
  
## <a name="remarks"></a>Hinweise  
 Das `dateTimeFormat`-Argument ist der Name einer Formatierung.  
  
 Mit der `prototype`-Eigenschaft können Sie einer Objektklasse grundlegende Funktionen zur Verfügung stellen. Neue Instanzen eines Objekts "erben" das Verhalten des Prototyps, der diesem Objekt zugewiesen ist.  
  
 Um beispielsweise dem `Intl.DateTimeFormat`-Objekt eine Methode hinzuzufügen, die den Wert des größten Elements des Satzes zurückgibt, deklarieren Sie die Funktion, fügen Sie sie `Intl.DateTimeFormat.prototype` hinzu, und verwenden Sie sie dann.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]