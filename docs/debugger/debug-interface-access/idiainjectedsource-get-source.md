---
title: 'Idiainjetedsource:: get_Source | Microsoft-Dokumentation'
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
ms.openlocfilehash: b389df8220766ffbdbf865a2b8e70877fe91b3f1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743335"
---
# <a name="idiainjectedsourceget_source"></a>IDiaInjectedSource::get_source
Ruft die Quell Code Bytes ab.

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

in Die Anzahl von Bytes, die die Größe des Daten Puffers darstellt.

 `pcbData`

vorgenommen Gibt die Anzahl der Bytes zurück, die die zurückgegebenen Bytes darstellen. Wenn `data` `NULL` ist, entspricht `pcbData` der Gesamtzahl der verfügbaren Daten bytes.

 `data[]`

vorgenommen Ein Puffer, der mit den Quell Bytes aufgefüllt werden soll.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` zurück, wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)