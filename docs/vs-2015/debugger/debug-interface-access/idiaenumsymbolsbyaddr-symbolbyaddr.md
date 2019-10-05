---
title: IDiaEnumSymbolsByAddr::symbolByAddr | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::symbolByAddr method
ms.assetid: 0b6f5a68-8402-4f29-8219-20576fda8166
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6561c3afd273a2a559138ed2363b4ffa4fdd0fd8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68189605"
---
# <a name="idiaenumsymbolsbyaddrsymbolbyaddr"></a>IDiaEnumSymbolsByAddr::symbolByAddr
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Positioniert den Enumerator durch eine Suche nach Anzahl der Bild-im Abschnitt "und" Offset an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT symbolByAddr (   
   DWORD**      isect,  
   DWORD**      offsect,  
   IDiaSymbol** ppsymbol  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 isect  
 [in] Anzahl der Image-Abschnitt.  
  
 offsect  
 [in] Der Offset in Abschnitt.  
  
 ppsymbol  
 [out] Gibt eine [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) Objekt, das das Symbol gefunden darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` , wenn das Symbol nicht gefunden werden konnte. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
