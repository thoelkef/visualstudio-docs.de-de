---
title: 'Idiasymmetribol:: get_restrictedType | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: c48b00a6-26b0-47b0-b824-fe44dedbc756
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 332ed15c4a6bb9a759e18e1df1e7c456c1303754
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62430769"
---
# <a name="idiasymbolget_restrictedtype"></a>IDiaSymbol::get_restrictedType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gibt an, ob der `this` Zeiger als eingeschränkt gekennzeichnet ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT get_restrictedType(   
   BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 vorgenommen Ein Zeiger auf einen-Wert `BOOL` , der angibt, ob der `this` Zeiger als eingeschränkt gekennzeichnet ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
