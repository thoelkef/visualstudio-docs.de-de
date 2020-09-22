---
title: 'Idiasymmetribol:: get_dataBytes | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_dataBytes method
ms.assetid: 5eb37179-20d8-44ae-a72a-405c1b0435c4
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bb0946c586c7b9ac3bb8907a9b5eb907d8f3ae70
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841239"
---
# <a name="idiasymbolget_databytes"></a>IDiaSymbol::get_dataBytes
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft die Daten Bytes eines OEM-Symbols ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_dataBytes (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `cbData`  
 in Größe des Puffers, der die Daten enthalten soll.  
  
 `pcbData`  
 vorgenommen Gibt die Anzahl der geschriebenen Bytes zurück. wenn der- `data` Parameter ist `NULL` , wird die Anzahl der verfügbaren Bytes zurückgegeben.  
  
 `data[]`  
 [out,] Ein Puffer, der mit den Daten Bytes gefüllt ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.  
  
> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.  
  
## <a name="requirements"></a>Anforderungen  
  
|Anforderung|BESCHREIBUNG|  
|-----------------|-----------------|  
|Header:|dia2.h|  
|Version:|Dia SDK v 7.0|  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
