---
title: new-Operator (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: new_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: new operator in JavaScript
ms.assetid: 5ea556ba-7ae6-426c-8430-9032eee5a0a5
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ad004abb534d69bed1a1bd9bbd2ae96755544b9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="new-operator-javascript"></a>new-Operator (JavaScript)
Erstellt ein neues Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
new constructor ([arguments])   
```  
  
## <a name="parameters"></a>Parameter  
 `constructor`  
 Erforderlich. Der Konstruktor des Objekts. Die Klammern können ausgelassen werden, wenn der Konstruktor keine Argumente annimmt.  
  
 `arguments`  
 Dies ist optional. Für das neue Objekt Konstruktor zu übergebenden Argumente.  
  
## <a name="remarks"></a>Hinweise  
 Die `new` Operator führt die folgenden Aufgaben:  
  
-   Er erstellt ein Objekt ohne Member.  
  
-   Ruft den Konstruktor für das Objekt, das die Übergabe eines Zeigers auf das neu erstellte Objekt als die `this` Zeiger.  
  
-   Der Konstruktor initialisiert dann das Objekt gemäß den an den Konstruktor übergebenen Argumente.  
  
 Es folgen Beispiele für gültige Verwendungen von der **neue** Operator.  
  
```JavaScript  
my_object = new Object;  
my_array = new Array();  
my_date = new Date("Jan 5 1996");  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [function-Anweisung](../../javascript/reference/function-statement-javascript.md)