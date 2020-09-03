---
title: 'IDiaEnumSymbols:: Item | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Item method
ms.assetid: 2bd1ec04-e677-4e32-8e32-33334f1eed77
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 42180b8e948b93428dc2db92820be336833dcc56
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189676"
---
# <a name="idiaenumsymbolsitem"></a>IDiaEnumSymbols::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft ein Symbol mithilfe eines Indexes ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Item (   
   DWORD        index,  
   IDiaSymbol** symbol  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 Index  
 in Der Index des [idiasymmetribol](../../debugger/debug-interface-access/idiasymbol.md) -Objekts, das abgerufen werden soll. Der Index liegt zwischen 0 und `count` -1, wobei `count` von der [IDiaEnumSymbols:: get_Count](../../debugger/debug-interface-access/idiaenumsymbols-get-count.md) -Methode zurückgegeben wird.  
  
 Symbol  
 vorgenommen Gibt ein [idiasymmetribol](../../debugger/debug-interface-access/idiasymbol.md) -Objekt zurück, das das gewünschte Symbol darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
