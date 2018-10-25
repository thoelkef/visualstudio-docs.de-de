---
title: 'Idiaenumframedata:: Clone | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Clone Method
ms.assetid: 28a17300-1626-422f-a17a-3a4d3872c37c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1516babf3576f16b88265903af945a9251dbcf0e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49861149"
---
# <a name="idiaenumframedataclone"></a>IDiaEnumFrameData::Clone
Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT Clone(   
   IDiaEnumFrameData** ppenum  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 ppenum  
 [out] Gibt eine [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md) Objekt, das ein Duplikat des Enumerators enthält. Der Frame, die keine Daten sind doppelt vorhanden, nur den Enumerator.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)