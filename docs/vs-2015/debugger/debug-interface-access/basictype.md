---
title: BasicType | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 633fb76a8177f239b988554a5d15bee09e00c2d9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745025"
---
# <a name="basictype"></a>BasicType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gibt an, die grundlegende Symboltyp.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum BasicType {   
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
 Basistyp ist ein Breitzeichen (Unicode) ist (`WCHAR`).  
  
 btInt  
 Ist der Basistyp `signed int` (C/C++-Typ).  
  
 btUInt  
 Ist der Basistyp `unsigned int` (C/C++-Typ).  
  
 btFloat  
 Basistyp ist eine Gleitkommazahl (`FLOAT`).  
  
 btBCD  
 Basistyp ist eine Dezimalzahl Binär codierte (`BCD`).  
  
 btBool  
 Basistyp ist ein boolescher Wert (`BOOL`).  
  
 btLong  
 Ist der Basistyp ein `long int` (C/C++-Typ).  
  
 btULong  
 Ist der Basistyp ein `unsigned long int` (C/C++-Typ).  
  
 btCurrency  
 Basistyp ist die Währung.  
  
 btDate  
 Basistyp ist die Datum/Uhrzeit (`DATE`).  
  
 btVariant  
 Basistyp ist eine Variable vom Typ-Struktur (`VARIANT`).  
  
 btComplex  
 Basistyp ist die komplexe Zahl.  
  
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



