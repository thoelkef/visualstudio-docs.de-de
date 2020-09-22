---
title: 'Idiasymmetribol:: get_libraryName | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_libraryName method
ms.assetid: d04ddd9a-812d-46e4-bd39-28bdf3edfb70
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cdab8fdff421da751f3813789a6dee8b5b640771
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841098"
---
# <a name="idiasymbolget_libraryname"></a>IDiaSymbol::get_libraryName
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft den Dateinamen der Bibliothek oder der Objektdatei ab, aus der das Objekt geladen wurde.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_libraryName (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 vorgenommen Gibt den Dateinamen der Bibliothek oder der Objektdatei zurück, aus der das Objekt geladen wurde.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.  
  
> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
