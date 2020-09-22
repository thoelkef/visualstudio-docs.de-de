---
title: 'Idiasymmetribol:: get_virtualBaseOffset | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualBaseOffset method
ms.assetid: 103b034f-36c4-42d5-aa34-1449a1e66d03
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c9ff5e8e65e46f9c42c5ea149a5bc5025b83d82b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841295"
---
# <a name="idiasymbolget_virtualbaseoffset"></a>IDiaSymbol::get_virtualBaseOffset
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft den Offset in der virtuellen Funktions Tabelle einer virtuellen Funktion ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_virtualBaseOffset (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 vorgenommen Gibt den Offset in der virtuellen Funktions Tabelle einer virtuellen Funktion zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.  
  
> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
