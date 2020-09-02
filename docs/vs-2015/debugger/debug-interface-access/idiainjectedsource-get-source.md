---
title: 'Idiainjetedsource:: get_Source | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_source method
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 856d0111e65b51b798dfe44a324c58c4db5457fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192425"
---
# <a name="idiainjectedsourceget_source"></a>IDiaInjectedSource::get_source
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft die Quell Code Bytes ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_source (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `cbData`  
 in Die Anzahl von Bytes, die die Größe des Daten Puffers darstellt.  
  
 `pcbData`  
 vorgenommen Gibt die Anzahl der Bytes zurück, die die zurückgegebenen Bytes darstellen. Wenn `data` ist `NULL` , dann `pcbData` ist die Gesamtzahl der verfügbaren Daten bytes.  
  
 `data[]`  
 vorgenommen Ein Puffer, der mit den Quell Bytes aufgefüllt werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt bei Erfolg `S_OK` zurück. Gibt zurück, `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
