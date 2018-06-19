---
title: ToString-Methode (Datum) | Microsoft Docs
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
ms.assetid: d3037289-d805-409b-8781-045c59a2c404
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67b6dce74e3796c8b54431b56809473e3c5e59a5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640250"
---
# <a name="tostring-method-date"></a>toString-Methode (Datum)
Gibt eine Zeichenfolgendarstellung eines Datums zurück. Das Format der Zeichenfolge hängt von der Gebietsschema ab. USA Englisch (En-us), lautet wie folgt:  
  
 *Tag der Woche* *Monat* *Tag* *Stunde*: *Minute*:*zweite* *Zeitzone* *Jahr*  
  
## <a name="syntax"></a>Syntax  
  
```  
  
date.toString()  
```  
  
## <a name="parameters"></a>Parameter  
 `date`  
 Erforderlich. Das Datum als Zeichenfolge dargestellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt die Zeichenfolgendarstellung des Datums zurück.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der `toString` Methode mit einem Datum.  
  
```JavaScript  
var myDate = new Date();  
myDate.setFullYear(2100, 5, 5);  
var dateString = myDate.toString();  
document.write(dateString);  
  
// Output: <date>  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]