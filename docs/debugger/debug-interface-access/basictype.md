---
title: BasicType | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f93fa1380dbb2d7623cddec3780593cd50513f2a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="basictype"></a>BasicType
Gibt die grundlegende Symboltyp.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
enum BasicType {   
   btNoType   = 0,  
   btVoid     = 1,  
   btChar     = 2,  
   btWChar    = 3,  
   btInt      = 6,  
   btUInt     = 7,  
   btFloat    = 8,  
   btBCD      = 9,  
   btBool     = 10,  
   btLong     = 13,  
   btULong    = 14,  
   btCurrency = 25,  
   btDate     = 26,  
   btVariant  = 27,  
   btComplex  = 28,  
   btBit      = 29,  
   btBSTR     = 30,  
   btHresult  = 31  
};  
```  
  
## <a name="elements"></a>Elements  
 btNoType  
 Es ist kein Basistyp angegeben.  
  
 btVoid  
 Ist der Basistyp ein `void`.  
  
 btChar  
 Ist der Basistyp ein `char` (C/C++-Typ).  
  
 btWChar  
 Basistyp ist ein Breitzeichen (Unicode) (`WCHAR`).  
  
 btInt  
 Ist der Basistyp `signed int` (C/C++-Typ).  
  
 btUInt  
 Ist der Basistyp `unsigned int` (C/C++-Typ).  
  
 btFloat  
 Basistyp ist eine Gleitkommazahl (`FLOAT`).  
  
 btBCD  
 Basistyp ist ein Binary coded Decimal (`BCD`).  
  
 btBool  
 Basistyp ist ein boolescher Wert (`BOOL`).  
  
 btLong  
 Ist der Basistyp ein `long int` (C/C++-Typ).  
  
 btULong  
 Ist der Basistyp ein `unsigned long int` (C/C++-Typ).  
  
 btCurrency  
 Basistyp ist die Währung.  
  
 btDate  
 Grundlegende Datentyp Datum/Uhrzeit (`DATE`).  
  
 btVariant  
 Basistyp ist eine Struktur, Variablentyp (`VARIANT`).  
  
 btComplex  
 Basistyp ist eine komplexe Zahl.  
  
 btBit  
 Basistyp ist ein wenig.  
  
 btBSTR  
 Basistyp ist eine grundlegende oder binäre Zeichenfolge (`BSTR`).  
  
 btHresult  
 Ist der Basistyp ein `HRESULT`.  
  
## <a name="remarks"></a>Hinweise  
 Die Werte in dieser Enumeration werden zurückgegeben, durch die [idiasymbol:: Get_basetype](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: cvconst.h  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Idiasymbol:: Get_basetype](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)