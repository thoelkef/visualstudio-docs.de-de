---
title: IDiaSession::findInlineFramesByRVA | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: ddb3ff0e-cb3d-4fa0-af56-f064b218b264
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0ebb32b9b22de8d4092c53f56accf1d953bbc94a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49876879"
---
# <a name="idiasessionfindinlineframesbyrva"></a>IDiaSession::findInlineFramesByRVA
Ruft eine Enumeration, die einem Client zum iterieren durch alle Inlineframes auf eine angegebene relative virtuelle Adresse (RVA) ermöglicht.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT findInlineFramesByRVA (   
   IDiaSymbol*       parent,   DWORD             rva,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `parent`  
 [in] Ein `IDiaSymbol` Objekt, das das übergeordnete Element darstellt.  
  
 `rva`  
 [in] Gibt die Adresse als eine RVA an.  
  
 `ppResult`  
 [out] Enthält eine `IDiaEnumSymbols` Objekt, das die Liste der Frames enthält, die abgerufen werden.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)