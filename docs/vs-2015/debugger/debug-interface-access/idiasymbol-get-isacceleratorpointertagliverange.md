---
title: 'Idiasymmetribol:: get_isAcceleratorPointerTagLiveRange | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: d195aec4-6d3c-42e0-88a5-3d463539f0b8
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5a53faf8c9395867b570909ac4d34cf329da12c6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149446"
---
# <a name="idiasymbolget_isacceleratorpointertagliverange"></a>IDiaSymbol::get_isAcceleratorPointerTagLiveRange
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft ein Flag ab, das angibt, ob das Symbol dem *Definitions Bereichs Symbol* für die Tagkomponente einer Zeiger Variablen in Code entspricht, der für eine C++ amp Accelerator kompiliert wurde. Das Symbol für den Definitionsbereich ist der Speicherort einer Variablen für eine Adress Spanne.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT get_isAcceleratorPointerTagLiveRange(   
   BOOL* pFlag);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pFlag`  
 vorgenommen Ein Zeiger auf einen-Wert `BOOL` , der angibt, ob das Symbol dem Definitions Bereichs Symbol entspricht.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
