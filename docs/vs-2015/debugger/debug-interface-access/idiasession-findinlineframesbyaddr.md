---
title: IDiaSession::findInlineFramesByAddr | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: e7dc1ac7-bb09-45be-96d2-365a9b7336e4
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 418968eabaa2af77b2c67eed6589d9ac437fd76e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68165526"
---
# <a name="idiasessionfindinlineframesbyaddr"></a>IDiaSession::findInlineFramesByAddr
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft eine Enumeration, die einem Client zum iterieren durch alle Inlineframes auf einer bestimmten Adresse ermöglicht.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT findInlineFramesByAddr (   
   IDiaSymbol*       parent,   DWORD             isect,  
   DWORD             offset,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `parent`  
 [in] Ein `IDiaSymbol` Objekt, das das übergeordnete Element darstellt.  
  
 `isect`  
 [in] Gibt die Komponente im Abschnitt der Adresse.  
  
 `offset`  
 [in] Gibt die Offset-Komponente der Adresse.  
  
 `ppResult`  
 [out] Enthält eine `IDiaEnumSymbols` Objekt, das die Liste der Frames enthält, die abgerufen werden.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
