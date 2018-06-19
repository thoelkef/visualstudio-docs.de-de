---
title: 'Idialinenumber:: Get_relativevirtualaddress | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_relativeVirtualAddress method
ms.assetid: ba8142e3-5c77-43cc-bd33-c077dcc18cab
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 32d31b404079760f29828fdd777117244a429338
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31468683"
---
# <a name="idialinenumbergetrelativevirtualaddress"></a>IDiaLineNumber::get_relativeVirtualAddress
Ruft die relative virtuelle Adresse (RVA) des Blocks ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_relativeVirtualAddress (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt die Bild-Relative virtuelle Adresse des Blocks zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`. Gibt `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)