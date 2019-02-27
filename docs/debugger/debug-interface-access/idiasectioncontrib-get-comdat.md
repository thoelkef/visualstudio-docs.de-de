---
title: 'Idiasectioncontrib:: Get_comdat | Microsoft-Dokumentation'
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
ms.openlocfilehash: 49502c0d693c7a309da9756f73c34df361b7d7bb
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56621746"
---
# <a name="idiasectioncontribgetcomdat"></a>IDiaSectionContrib::get_comdat
Ruft ein Flag, das angibt, ob der Bereich einen COMDAT-Datensatz ist.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_comdat ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

[out] Gibt `TRUE` , wenn der Bereich einer COMDAT-Datensatz; ist andernfalls `FALSE`.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Anmerkungen
 Ein COMDAT-Datensatz ist ein Common Object File Format (COFF)-Datensatz, der Paketfunktionen an den Linker sichtbar macht.

## <a name="see-also"></a>Siehe auch
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)