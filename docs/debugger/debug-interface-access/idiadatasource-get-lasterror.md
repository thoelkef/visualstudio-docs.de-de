---
title: 'Idiadatasource:: Get_lasterror | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34954cd32b350a7c5f9c176deffd9943f8e05100
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62554195"
---
# <a name="idiadatasourcegetlasterror"></a>IDiaDataSource::get_lastError
Ruft den Dateinamen für die letzten Ladefehler ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_lastError (
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 pRetVal

[out] Gibt eine Zeichenfolge, die den letzten zugeordneten PDB-Dateinamen enthält.

## <a name="return-value"></a>Rückgabewert
 Gibt den letzten Fehlercode, der einen Ladevorgang zurückzuführen. Gibt `E_INVALIDARG` Wenn die `pRetVal` Parameter `NULL`.

## <a name="example"></a>Beispiel

```C++
BSTR    fileName;
HRESULT errorCode = pSource->get_lastError( &fileName );
```

## <a name="see-also"></a>Siehe auch
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)