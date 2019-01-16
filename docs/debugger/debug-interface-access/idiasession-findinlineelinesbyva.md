---
title: IDiaSession::findInlineeLinesByVA | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: dffe6594-e0d1-4ed5-aeea-8773f88d82a6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 637161fc197a34ceb1b8e2704bbc0e695aaa2ff1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53893444"
---
# <a name="idiasessionfindinlineelinesbyva"></a>IDiaSession::findInlineeLinesByVA
Ruft eine Enumeration, die ermöglicht es einem Client zu durchlaufen und die Zeilennummerninformationen aller Funktionen, die inline erweitert wird, direkt oder indirekt durch das angegebene übergeordnete-Symbol und befinden sich innerhalb der angegebenen virtuellen Adresse (VA) ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT findInlineeLinesByVA (   
   IDiaSymbol*           parent,   ULONGLONG             va,   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `parent`  
 [in] Ein `IDiaSymbol` Objekt, das das übergeordnete Element darstellt.  
  
 `va`  
 [in] Gibt die Adresse an, wie eine VA.  
  
 `length`  
 [in] Gibt den Adressbereich in Anzahl von Bytes, die mit dieser Abfrage abzudecken.  
  
 `ppResult`  
 [out] Enthält eine `IDiaEnumLineNumbers` Objekt, das die Liste der Zeilennummern enthält, die abgerufen werden.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)