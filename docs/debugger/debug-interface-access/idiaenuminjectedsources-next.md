---
title: 'Idiaenuminjectedsources:: Next | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumInjectedSources::Next method
ms.assetid: 38af80fc-748f-4b15-bff1-823db21dd4d0
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aadfe4a6d4e66cca92f6e84cef23ebeace77afa1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenuminjectedsourcesnext"></a>IDiaEnumInjectedSources::Next
Ruft eine angegebene Anzahl von eingefügtem Quellen in die Enumerationsfolge ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT Next (   
   ULONG                celt,   
   IDiaInjectedSource** rgelt,  
   ULONG*               pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 celt  
 [in] Die Anzahl der eingefügten Quellen im Enumerator abgerufen werden sollen.  
  
 rgelt  
 [out] Gibt ein Array von [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) Objekte, die die gewünschten eingefügten Quellen darstellt.  
  
 pceltFetched  
 [out] Gibt die Anzahl der eingefügten Quellen in der abgerufenen Enumerator zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`. Gibt `S_FALSE` Wenn keine weiteren eingefügte Quellen vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)