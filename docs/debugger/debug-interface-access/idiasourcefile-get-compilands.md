---
title: 'Idiasourcefile:: Get_compilands | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_compilands method
ms.assetid: 57deb50a-9c22-43ea-a80c-eab205997bc4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e977916f55220ba0dad878e8cbcbdaaea973ea13
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55035730"
---
# <a name="idiasourcefilegetcompilands"></a>IDiaSourceFile::get_compilands
Ruft einen Enumerator der Compilands, die auf diese Datei verweist, Zeilennummern ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_compilands (   
   IDiaEnumSymbols** ppRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppRetVal`  
 [out] Gibt eine [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) Objekt, das eine Liste mit allen Compilands enthält, die Zeilennummern verweisen auf diese Datei haben.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)