---
title: 'Idiaenumsourcefiles:: Item | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Item method
ms.assetid: 3c19d7ed-0232-4b0e-9b10-f33ed9e0c93b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aafa4143551afdc6fc057d6c83cf1b08303ac9a2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55029530"
---
# <a name="idiaenumsourcefilesitem"></a>IDiaEnumSourceFiles::Item
Ruft eine Quelldatei mithilfe eines Indexes ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT Item (   
   DWORD            index,  
   IDiaSourceFile** sourceFile  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 Index  
 [in] Der Index der [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) Objekt abgerufen werden sollen. Der Index befindet sich im Bereich von 0 bis `count`-1 und, in dem `count` wird zurückgegeben, durch die [idiaenumsourcefiles:: Get_count](../../debugger/debug-interface-access/idiaenumsourcefiles-get-count.md) Methode.  
  
 sourceFile  
 [out] Gibt eine [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) Objekt, das die gewünschte Quelldatei darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)