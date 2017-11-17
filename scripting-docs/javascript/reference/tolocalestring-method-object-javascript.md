---
title: ToLocaleString-Methode (Objekt) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toLocaleString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toLocaleString method
ms.assetid: 0901afcb-126b-4ed7-bd6a-2301d50e2326
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f88e1c702cd8a7d702630ae90ef840c4af88f30
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="tolocalestring-method-object-javascript"></a>toLocaleString-Methode (Objekt) (JavaScript)
Gibt ein Datum zurück, die in eine Zeichenfolge, die anhand des aktuellen Gebietsschemas konvertiert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
dateObj.toLocaleString()   
```  
  
## <a name="remarks"></a>Hinweise  
 Die erforderliche `dateObj` ist "any" `Date` Objekt.  
  
 Die `toLocaleString` Methode gibt ein `String` -Objekt, das Datum im langen Standardformat des aktuellen Gebietsschemas enthält.  
  
-   Für Tage zwischen 1601 und 1999 n. Chr. wird das Datum gemäß den regionalen Einstellungen des Benutzers der Systemsteuerung formatiert.  
  
-   Für Datumsangaben außerhalb dieses Bereichs liegen, das Standardformat der **ToString** Methode verwendet wird.  
  
 Beispielsweise ist in den USA `toLocaleString` gibt "01/05/96 00:00:00" für den 5. Januar. In Europa Längenwert "05/01/96 00:00:00" für das gleiche Datum als Europäischen Konvention wird den Tag vor dem Monat.  
  
> [!NOTE]
>  `toLocaleString`sollte nur verwendet werden, um die Ergebnisse für einen Benutzer angezeigt; Er sollte nie als Grundlage für die Berechnung in einem Skript verwendet werden wie das zurückgegebene Ergebnis computerspezifisch ist.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung der `toLocaleString`-Methode veranschaulicht.  
  
```JavaScript  
function toLocaleStrDemo(){     
   var d, s;                      //Declare variables.  
   d = new Date();                //Create Date object.  
   s = "Current setting is ";  
   s += d.toLocaleString();       //Convert to current locale.  
   return(s);                     //Return converted date  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Gilt für**: [Array-Objekt](../../javascript/reference/array-object-javascript.md)&#124; [Datum Objekt](../../javascript/reference/date-object-javascript.md)&#124; [Zahl Objekt](../../javascript/reference/number-object-javascript.md)&#124; [Object-Objekt](../../javascript/reference/object-object-javascript.md)  
  
## <a name="see-also"></a>Siehe auch  
 [toLocaleDateString-Methode (Datum)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)