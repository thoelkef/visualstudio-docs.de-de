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
ms.openlocfilehash: 604160cdaf8c1ff28b306106afe34e047768f3c4
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56632094"
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
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)