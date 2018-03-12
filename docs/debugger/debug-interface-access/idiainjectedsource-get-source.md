---
title: 'Idiainjectedsource:: Get_source | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_source method
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c58989c6958aa8a604f5e7c7a9ef5c4d3eb84f1f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idiainjectedsourcegetsource"></a>IDiaInjectedSource::get_source
Ruft die Quelle Codebytes ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_source (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `cbData`  
 [in] Die Anzahl der Bytes, die die Größe des Datenpuffers darstellt.  
  
 `pcbData`  
 [out] Gibt zurückgegeben, die Anzahl der Bytes, die die Bytes darstellt. Wenn `data` ist `NULL`, klicken Sie dann `pcbData` ist die Gesamtanzahl der Bytes der Daten verfügbar.  
  
 `data[]`  
 [out] Ein Puffer, der mit der Quellbytes ausgefüllt werden.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`. Gibt `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)