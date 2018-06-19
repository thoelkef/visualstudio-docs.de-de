---
title: ToString-Methode (Zahl) | Microsoft Docs
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
ms.assetid: 07c3484b-d9d8-4451-a2be-88a19a081966
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6be170061faf4c2782c7247c80c55065c3a6742
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640390"
---
# <a name="tostring-method-number"></a>toString-Methode (Zahl)
Gibt eine Zeichenfolgendarstellung einer Zahl zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
number.toString()  
```  
  
## <a name="parameters"></a>Parameter  
 `number`  
 Erforderlich. Die Zahl, die als Zeichenfolge darzustellen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Zeichenfolgendarstellung der Zahl.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der **ToString** Methode mit einer Zahl.  
  
```JavaScript  
var number = 234.567;  
var s = number.toString();  
document.write(s.length);  
  
// Output: 7  
  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]