---
title: 'Idiainjectedsource:: Get_source | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_source method
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3b5582990ff3db2e03dce9dc0c198a907de978d9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54971074"
---
# <a name="idiainjectedsourcegetsource"></a>IDiaInjectedSource::get_source
Ruft die Quellbytes-Code ab.  
  
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
 [out] Gibt zurückgegeben, die Anzahl der Bytes, die die Bytes darstellt. Wenn `data` ist `NULL`, klicken Sie dann `pcbData` ist die Gesamtzahl der Bytes der Daten verfügbar.  
  
 `data[]`  
 [out] Ein Puffer, der sich die Quellbytes gefüllt werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)