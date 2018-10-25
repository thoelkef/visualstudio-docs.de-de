---
title: 'Idiasymbol:: Get_types | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_types method
ms.assetid: 5f056e0c-e15b-4e00-8f78-aadc8574f7ea
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c611805e2a077caec0a617deda8ac744e0b4e1a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49817314"
---
# <a name="idiasymbolgettypes"></a>IDiaSymbol::get_types
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft ein Array von Compiler-spezifische Typen für dieses Symbol ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_types (   
   DWORD       cTypes,  
   DWORD*      pcTypes,  
   IDiaSymbol* types[]  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `cTypes`  
 [in] Die Größe des Puffers zum Speichern der Daten.  
  
 `pcTypes`  
 [out] Gibt die Anzahl der Typen, die geschrieben wird, oder, wenn Sie die `types` Parameter `NULL`, klicken Sie dann die Gesamtzahl der verfügbaren Typen.  
  
 `types[]`  
 [out] Ein Array, das mit gefüllt werden soll die [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) Objekte, die alle Typen für dieses Symbol darstellen.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



