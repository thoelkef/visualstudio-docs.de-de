---
title: 'Idiasymbol:: Get_name | Microsoft-Dokumentation'
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
- IDiaSymbol::get_name method
ms.assetid: 050ec02f-b7b3-48fc-8e35-58bdf7d938b0
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c47c4e7b2847e9bb15be0250f14e541312792d00
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49864905"
---
# <a name="idiasymbolgetname"></a>IDiaSymbol::get_name
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft den Namen des Symbols.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_name (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt den Namen des Symbols.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.  
  
## <a name="example"></a>Beispiel  
  
```cpp#  
IDiaSymbol* pType;  
BSTR        name;  
pType->get_name( &name );  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



