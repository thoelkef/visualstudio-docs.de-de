---
title: 'Idiasymmetribol:: get_types | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_types method
ms.assetid: 5f056e0c-e15b-4e00-8f78-aadc8574f7ea
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 813dcd692669d823548e52ce6bb7eccc9546de61
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841277"
---
# <a name="idiasymbolget_types"></a>IDiaSymbol::get_types
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft ein Array von compilerspezifischen Typen für dieses Symbol ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_types (   
   DWORD       cTypes,  
   DWORD*      pcTypes,  
   IDiaSymbol* types[]  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `cTypes`  
 in Größe des Puffers, der die Daten enthalten soll.  
  
 `pcTypes`  
 vorgenommen Gibt die Anzahl der geschriebenen Typen zurück, oder, wenn der- `types` Parameter ist `NULL` , und dann die Gesamtzahl der verfügbaren Typen.  
  
 `types[]`  
 vorgenommen Ein Array, das mit den [idiasymmetribol](../../debugger/debug-interface-access/idiasymbol.md) -Objekten ausgefüllt werden soll, die alle Typen für dieses Symbol darstellen.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.  
  
> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
