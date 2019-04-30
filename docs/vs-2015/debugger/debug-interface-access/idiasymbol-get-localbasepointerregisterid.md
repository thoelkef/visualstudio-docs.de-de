---
title: 'Idiasymbol:: Get_localbasepointerregisterid | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_localBasePointerRegisterId method
ms.assetid: 9cbcaf00-9ace-45e1-b164-7a9439e08083
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9692e9de7a3551b437691c5ca089756d1e2d50a5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430286"
---
# <a name="idiasymbolgetlocalbasepointerregisterid"></a>IDiaSymbol::get_localBasePointerRegisterId
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft die ID des Registers, das ein basiszeiger auf lokale Variablen im Stapel enthält ab. Verwenden, wenn die [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md) nastaven NA hodnotu `SymTagFunction`.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_localBasePointerRegisterId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt die ID des Registers, das ein basiszeiger auf lokale Variablen im Stapel enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="requirements"></a>Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
