---
title: BasicType | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 38de89b9774ac20f67b91e4ba864534122f4cdb0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62580836"
---
# <a name="basictype"></a>BasicType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gibt den Basistyp des Symbols an.  
  
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
  
## <a name="elements"></a>Elemente  
 btNoType  
 Es ist kein Basistyp angegeben.  
  
 btVoid  
 Der Basistyp ist ein `void` .  
  
 btChar  
 Der Basistyp ist ein `char` (C/C++-Typ).  
  
 btWChar  
 Der Basistyp ist ein breit Zeichen (Unicode) `WCHAR` .  
  
 btInt  
 Der Basistyp ist `signed int` (C/C++-Typ).  
  
 btUInt  
 Der Basistyp ist `unsigned int` (C/C++-Typ).  
  
 btFloat  
 Der Basistyp ist eine Gleit Komma Zahl ( `FLOAT` ).  
  
 btBCD  
 Der Basistyp ist ein Binär codiertes Dezimaltrennzeichen ( `BCD` ).  
  
 btBool  
 Der Basistyp ist ein boolescher Wert ( `BOOL` ).  
  
 btLong  
 Der Basistyp ist ein `long int` (C/C++-Typ).  
  
 btULong  
 Der Basistyp ist ein `unsigned long int` (C/C++-Typ).  
  
 btCurrency  
 Der Basistyp ist "Currency".  
  
 btdate  
 Der Basistyp ist "Date/Time ( `DATE` )".  
  
 btVariant  
 Der Basistyp ist eine Variablentyp Struktur ( `VARIANT` ).  
  
 btComplex  
 Der Basistyp ist eine komplexe Zahl.  
  
 btBit  
 Der Basistyp ist ein Bit.  
  
 btBSTR  
 Der Basistyp ist eine einfache oder binäre Zeichenfolge ( `BSTR` ).  
  
 btHresult  
 Der Basistyp ist ein `HRESULT` .  
  
## <a name="remarks"></a>Bemerkungen  
 Die Werte in dieser Enumeration werden von der [idiasymmetribol:: get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) -Methode zurückgegeben.  
  
## <a name="requirements"></a>Anforderungen  
 Header: cvconst.h  
  
## <a name="see-also"></a>Weitere Informationen  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Idiasymmetribol:: get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
