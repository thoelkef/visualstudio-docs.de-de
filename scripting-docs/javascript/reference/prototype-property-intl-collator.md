---
title: Prototype-Eigenschaft (Intl.Collator) | Microsoft Docs
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
ms.assetid: c1bbb523-fb55-4395-b357-34d91cf5bba0
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 696535afde8c497bc98fc2c81a03854d66add6f4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639120"
---
# <a name="prototype-property-intlcollator"></a>prototype-Eigenschaft (Intl.Collator)
Gibt einen Verweis auf den Prototyp für einen Sortierer zurück.  
  
## <a name="syntax"></a>Syntax  
  
```JavaScript  
collator.prototype  
```  
  
## <a name="remarks"></a>Hinweise  
 Das `collator`-Argument ist der Name eines Sortierers.  
  
 Mit der `prototype`-Eigenschaft können Sie einer Objektklasse grundlegende Funktionen zur Verfügung stellen. Neue Instanzen eines Objekts "erben" das Verhalten des Prototyps, der diesem Objekt zugewiesen ist.  
  
 Um beispielsweise dem `Intl.Collator`-Objekt eine Methode hinzuzufügen, die den Wert des größten Elements des Satzes zurückgibt, deklarieren Sie die Funktion, fügen Sie sie `Intl.Collator.prototype` hinzu, und verwenden Sie sie dann.  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]