---
title: 'Idiasymmetribol:: get_virtualTableShape | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualTableShape method
ms.assetid: 92360cbd-0761-446e-93f9-04dc8f4b66c6
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8dfc91a63634f47cc2a8bc16d0dfbede1e14abf4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841148"
---
# <a name="idiasymbolget_virtualtableshape"></a>IDiaSymbol::get_virtualTableShape
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft die Symbol Schnittstelle des Typs der virtuellen Tabelle für einen benutzerdefinierten Typ ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_virtualTableShape (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 vorgenommen Gibt ein [idiasymmetribol](../../debugger/debug-interface-access/idiasymbol.md) -Objekt zurück, das die virtuelle Tabelle für einen benutzerdefinierten Typ darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird der- `S_FALSE` oder-Fehlercode zurückgegeben.  
  
> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
