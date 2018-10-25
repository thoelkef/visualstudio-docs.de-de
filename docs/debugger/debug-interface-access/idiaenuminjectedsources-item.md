---
title: 'Idiaenuminjectedsources:: Item | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::Item method
ms.assetid: 14846955-7270-451d-91d2-9cb34bb65187
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e8299bce906c5f3e7a38296a9c19e9c85d03501b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49917445"
---
# <a name="idiaenuminjectedsourcesitem"></a>IDiaEnumInjectedSources::Item
Ruft eine eingefügte Quelle über einen Index ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT Item (   
   DWORD                index,  
   IDiaInjectedSource** injectedSource  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 Index  
 [in] Der Index der [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) Objekt abgerufen werden sollen. Der Index ist der Bereich von 0 bis `count`-1 und, in dem `count` wird zurückgegeben, durch die [idiaenuminjectedsources:: Get_count](../../debugger/debug-interface-access/idiaenuminjectedsources-get-count.md) Methode.  
  
 injectedSource  
 [out] Gibt eine [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) Objekt, das die eingefügte Quelle darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)