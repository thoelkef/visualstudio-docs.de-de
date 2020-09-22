---
title: 'Idiasymmetribol:: get_packed | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_packed method
ms.assetid: e42ff368-56c4-49a2-8676-f80e349efa21
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 90351c3319f8354685ae0d907379b8446f76cb7f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841211"
---
# <a name="idiasymbolget_packed"></a>IDiaSymbol::get_packed
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft ein Flag ab, das angibt, ob der benutzerdefinierte Datentyp (User-Defined Data Type, UDT) verpackt ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_packed (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 vorgenommen Gibt zurück, `TRUE` Wenn der UDT gepackt ist; andernfalls wird zurückgegeben `FALSE` .  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.  
  
> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.  
  
## <a name="remarks"></a>Bemerkungen  
 "Gepackt" bedeutet, dass alle Member des UDT so nah wie möglich nebeneinander positioniert sind, ohne dass dazwischen liegende Auffüll Zeichen an den Speichergrenzen ausgerichtet sind.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
