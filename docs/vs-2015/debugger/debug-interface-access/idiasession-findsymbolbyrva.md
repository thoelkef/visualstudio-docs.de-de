---
title: 'IDiaSession:: findSymbolByRVA | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findSymbolByRVA method
ms.assetid: 14fb2903-b771-44d6-b0a8-44e0097c58ce
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bc77a6f5e8be35b86f94dc676648f563f7978ee9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144785"
---
# <a name="idiasessionfindsymbolbyrva"></a>IDiaSession::findSymbolByRVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft einen angegebenen Symboltyp ab, der eine angegebene relative virtuelle Adresse (RVA) enthält oder der am nächsten liegt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT findSymbolByRVA (   
   DWORD        rva,  
   SymTagEnum   symtag,  
   IDiaSymbol** ppSymbol  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `rva`  
 in Gibt die RVA an.  
  
 `symtag`  
 in Symboltyp, der gefunden werden soll. Werte werden aus der Enumeration der [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md) entnommen.  
  
 `ppSymbol`  
 vorgenommen Gibt ein [idiasymmetribol](../../debugger/debug-interface-access/idiasymbol.md) -Objekt zurück, das das abgerufene Symbol darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="example"></a>Beispiel  
  
```cpp#  
IDiaSymbol* pFunc;  
pSession->findSymbolByRVA( rva, SymTagFunction, &pFunc );  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)
