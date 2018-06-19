---
title: 'Idiasymbol:: Get_age | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_age method
ms.assetid: 60d05654-e832-4a2e-a4a7-fe9922c459fe
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9a81c41902b5e6a8421f15b69ebc77fe5ae6eebf
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31464780"
---
# <a name="idiasymbolgetage"></a>IDiaSymbol::get_age
Ruft den Wert "Age" einer PDB-Datei.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_age (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt die ALTER-Wert, der eine PDB-Datei.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls gibt `S_FALSE` oder Fehlercode.  
  
> [!NOTE]
>  Ein Rückgabewert von `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.  
  
## <a name="remarks"></a>Hinweise  
 Das Alter entspricht nicht unbedingt alle bekannten Time-Werten; Es wird normalerweise verwendet, um festzustellen, ob eine PDB-Datei mit einer entsprechenden .exe-Datei synchron ist.  
  
## <a name="requirements"></a>Anforderungen  
  
|Anforderung|Beschreibung|  
|-----------------|-----------------|  
|Header:|dia2.h|  
|Version:|DIA-SDK Version 7.0|  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)