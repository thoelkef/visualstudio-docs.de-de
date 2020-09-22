---
title: 'Idiasymmetribol:: get_hfaDouble | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hfaDouble method
ms.assetid: efc247b9-c16e-4fa3-89b0-901caf7b74c3
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: db12f9dfb0a5a5594c08ab0cd58446cac100f7ae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841095"
---
# <a name="idiasymbolget_hfadouble"></a>IDiaSymbol::get_hfaDouble
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft ein Flag ab, das angibt, ob ein benutzerdefinierter Typ (User-Defined Type, UDT) homogene Gleit Komma Aggregatdaten (HFA) vom Typ Double enthält.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_hfaDouble(   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 vorgenommen Gibt zurück, `TRUE` Wenn der UDT HFA-Daten vom Typ Double enthält; andernfalls wird zurückgegeben `FALSE` .  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.  
  
> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 Header: Dia2.h  
  
 Bibliothek: diaguids. lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)
