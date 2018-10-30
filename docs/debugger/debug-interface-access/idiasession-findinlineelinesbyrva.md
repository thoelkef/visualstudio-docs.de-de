---
title: IDiaSession::findInlineeLinesByRVA | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 7a74d5ee-0dbf-47c0-92b4-47ec03b13ce9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bf5b7ee1359ac4a7943187f9170df08eb9c7858c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49875657"
---
# <a name="idiasessionfindinlineelinesbyrva"></a>IDiaSession::findInlineeLinesByRVA
Ruft eine Enumeration, die ermöglicht es einem Client zu durchlaufen und die Zeilennummerninformationen aller Funktionen, die inline erweitert wird, direkt oder indirekt durch das angegebene übergeordnete-Symbol und befinden sich in die angegebene relative virtuelle Adresse (RVA) ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT findInlineeLinesByRVA (   
   IDiaSymbol*           parent,  
   DWORD                 rva,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `parent`  
 [in] Ein `IDiaSymbol` Objekt, das das übergeordnete Element darstellt.  
  
 `rva`  
 [in] Gibt die Adresse als eine RVA an.  
  
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