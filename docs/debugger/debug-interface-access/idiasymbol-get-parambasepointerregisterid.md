---
title: 'Idiasymbol:: Get_parambasepointerregisterid | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_paramBasePointerRegisterId method
ms.assetid: 9f5caeb4-5c88-4054-bf8b-50d34bbbf8c5
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cb6901210e05ef3eb1f8e63b8e6c508d36b2770b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63399184"
---
# <a name="idiasymbolgetparambasepointerregisterid"></a>IDiaSymbol::get_paramBasePointerRegisterId
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft die ID des Registers, die einen grundlegenden Zeiger auf die Parameter enthält. Verwenden, wenn die [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md) nastaven NA hodnotu `SymTagFunction`.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_paramBasePointerRegisterId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt die ID des Registers, die einen grundlegenden Zeiger auf die Parameter enthält.  
  
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
