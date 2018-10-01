---
title: IDiaSession::findSymbolsForAcceleratorPointerTag | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: 95fd5e7a-c637-437e-b369-c864eef733c2
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a97f24807bd069f9d0c352838ac1d098be7f0e2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522306"
---
# <a name="idiasessionfindsymbolsforacceleratorpointertag"></a>IDiaSession::findSymbolsForAcceleratorPointerTag
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDiaSession::findSymbolsForAcceleratorPointerTag](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag).  
  
Gibt eine Enumeration von Symbolen für die Variable, die der angegebenen Tagwert entspricht, in der übergeordneten Accelerator-Stub-Funktion zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT findSymbolsForAcceleratorPointerTag (   
   IDiaSymbol*           parent,  
   DWORD                 tagValue,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `parent`  
 [in] Ein IDiaSymbol, die die Zugriffstaste-Stub-Funktion, die durchsucht werden entspricht.  
  
 `tagValue`  
 [in] Der Tag-Zeigerwert.  
  
 `ppResult`  
 [out] Ein Zeiger auf ein `IDiaEnumSymbols` Schnittstellenzeiger, der mit dem Ergebnis initialisiert wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)



