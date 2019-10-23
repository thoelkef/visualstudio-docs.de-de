---
title: 'IDiaSectionContrib:: get_comdat | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_comdat method
ms.assetid: 8bd9be8d-59ee-4698-b055-daba354b8dcc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef38d5c4afcb065f7a095501e2bf5d95ee493789
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742725"
---
# <a name="idiasectioncontribget_comdat"></a>IDiaSectionContrib::get_comdat
Ruft ein Flag ab, das angibt, ob der Abschnitt ein COMDAT-Datensatz ist.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_comdat ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

vorgenommen Gibt `TRUE` zurück, wenn der Abschnitt ein COMDAT-Datensatz ist. Andernfalls wird `FALSE` zurückgegeben.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` zurück, wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Ein COMDAT-Datensatz ist ein COFF-Datensatz (Common Object File Format), mit dem Paketfunktionen für den Linker sichtbar werden.

## <a name="see-also"></a>Siehe auch
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)