---
title: 'IDiaEnumSourceFiles:: get_Count | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::get_Count method
ms.assetid: 04083b97-e1ac-4baf-bf5a-50a4dc1c6f27
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7abc842a65140d1ee127dba99568ff4a57b16873
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744110"
---
# <a name="idiaenumsourcefilesget_count"></a>IDiaEnumSourceFiles::get_Count
Ruft die Anzahl der Quelldateien ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_Count ( 
   LONG* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 pRetVal

vorgenommen Gibt die Anzahl der Quelldateien zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
- [IDiaEnumSourceFiles::Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md)