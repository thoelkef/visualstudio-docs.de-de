---
title: IDiaSymbol::findInlineeLinesByAddr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f1ab47ca-c851-48ea-9c12-47fb80b31102
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b4b0470bc77be8089b9b66949bdb9a0161317d3d
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbolfindinlineelinesbyaddr"></a>IDiaSymbol::findInlineeLinesByAddr
Ruft eine Enumeration, die ermöglicht einem Client zum iterieren durch die Zeilennummerninformationen aller Funktionen, die inline erweitert wird, direkt oder indirekt in dieses Symbol in der angegebenen Adressbereich ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT findInlineeLinesByAddr (   
   DWORD                 isect,  
   DWORD                 offset,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `isect`  
 [in] Gibt die Komponente im Abschnitt der Adresse.  
  
 `offset`  
 [in] Gibt den Offset-Komponente der Adresse an.  
  
 `length`  
 [in] Gibt an, der Adressbereich in Anzahl von Bytes, die mit dieser Abfrage abzudecken.  
  
 `ppResult`  
 [out] Enthält eine `IDiaEnumLineNumbers` -Objekt, das die Liste der Zeilennummern enthält, die abgerufen werden.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)