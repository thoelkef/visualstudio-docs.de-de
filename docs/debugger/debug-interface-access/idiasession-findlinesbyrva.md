---
title: 'Idiasession:: Findlinesbyrva | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLinesByRVA method
ms.assetid: 06f53b0b-b5b4-42cf-9252-dcee0dbe2d71
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2e2f3713407ad17f468e125a1592ee8d684d27d3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49869742"
---
# <a name="idiasessionfindlinesbyrva"></a>IDiaSession::findLinesByRVA
Ruft ab, die Zeilen in einer angegebenen Kompiliereinheit, die eine angegebene relative virtuelle Adresse (RVA) enthalten.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT findLinesByRVA (   
   DWORD                 rva,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `rva`  
 [in] Gibt die Adresse als eine RVA an.  
  
 `length`  
 [in] Gibt die Anzahl der Bytes der Adressbereich aus, um mit dieser Abfrage abzudecken.  
  
 `ppResult`  
 [out] Gibt eine [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) -Objekt, das eine Liste mit allen in der Zeile enthält Zahlen, die u. a. der angegebene Adressbereich.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt eine Funktion, die alle Zeilennummern enthalten sind, in der angegebenen Funktion, die mit der Funktion relative virtuelle Adresse und die Länge abgerufen werden.  
  
```C++  
IDiaEnumLineNumbers* GetLineNumbersByRVA(IDiaSymbol *pFunc, IDiaSession *pSession)  
{  
    IDiaEnumLineNumbers* pEnum = NULL;  
    DWORD                rva;  
    ULONGLONG            length;  
  
    if (pFunc->get_relativeVirtualAddress ( &rva ) == S_OK)  
    {  
        pFunc->get_length ( &length );  
        pSession->findLinesByRVA( rva, static_cast<DWORD>( length ), &pEnum );  
    }  
    return(pEnum);  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)