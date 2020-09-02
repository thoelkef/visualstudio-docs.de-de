---
title: 'IDiaSession:: findLinesByRVA | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLinesByRVA method
ms.assetid: 06f53b0b-b5b4-42cf-9252-dcee0dbe2d71
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8c066e183d60a1f7d967cafa1114d6241b28caa4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68165500"
---
# <a name="idiasessionfindlinesbyrva"></a>IDiaSession::findLinesByRVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft die Zeilen in einer angegebenen Kompilierungen ab, die eine angegebene relative virtuelle Adresse (RVA) enthalten.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT findLinesByRVA (   
   DWORD                 rva,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `rva`  
 in Gibt die Adresse als RVA an.  
  
 `length`  
 in Gibt die Anzahl der Bytes für den Adressbereich an, die mit dieser Abfrage abgedeckt werden.  
  
 `ppResult`  
 vorgenommen Gibt ein [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) -Objekt zurück, das eine Liste aller Zeilennummern enthält, die den angegebenen Adressbereich abdecken.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt eine Funktion, die alle in der angegebenen Funktion enthaltenen Zeilennummern mithilfe der relativen virtuellen Adresse und Länge der Funktion abruft.  
  
```cpp#  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
