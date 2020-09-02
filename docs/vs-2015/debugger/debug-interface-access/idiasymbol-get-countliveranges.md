---
title: 'Idiasymmetribol:: get_countLiveRanges | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_countLiveRanges
ms.assetid: 55f79e1a-d4c2-42cd-ab37-d8253b20e34c
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 066e8d9e6f64984f861a5e14335020c625e96bb6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149779"
---
# <a name="idiasymbolget_countliveranges"></a>IDiaSymbol::get_countLiveRanges
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft die Anzahl der gültigen Adressbereiche ab, die dem lokalen Symbol zugeordnet sind.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_countLiveRanges (   
   DWORD* count  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `count`  
 vorgenommen Gibt die Anzahl der Adressbereiche zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids. lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
