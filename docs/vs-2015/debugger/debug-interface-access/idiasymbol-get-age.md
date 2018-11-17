---
title: 'Idiasymbol:: Get_age | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_age method
ms.assetid: 60d05654-e832-4a2e-a4a7-fe9922c459fe
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 740b3903977642d129907df9c75a643d091b0206
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724992"
---
# <a name="idiasymbolgetage"></a>IDiaSymbol::get_age
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft den Age-Wert, der eine PDB-Datei ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_age (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt die Age-Wert, der eine PDB-Datei.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder den Fehlercode.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.  
  
## <a name="remarks"></a>Hinweise  
 Das Alter entspricht nicht unbedingt alle bekannten Zeitwert; Es wird normalerweise verwendet, um festzustellen, ob eine PDB-Datei mit einer entsprechenden .exe-Datei synchron sind.  
  
## <a name="requirements"></a>Anforderungen  
  
|Anforderung|Beschreibung|  
|-----------------|-----------------|  
|Header:|dia2.h|  
|Version:|DIA-SDK V7. 0|  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



