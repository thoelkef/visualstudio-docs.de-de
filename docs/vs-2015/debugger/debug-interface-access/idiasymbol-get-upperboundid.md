---
title: 'Idiasymmetribol:: get_upperBoundId | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_upperBoundId method
ms.assetid: ddfa1617-bd0f-4187-ba77-a225bab93a95
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2cca35fb1369214672b8740d41f65a2a725517e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841250"
---
# <a name="idiasymbolget_upperboundid"></a>IDiaSymbol::get_upperBoundId
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft den Symbol Bezeichner der oberen Grenze einer Fortran-Array Dimension ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_upperBoundId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out,] Gibt die ID des Symbols zurück, das die obere Grenze einer Fortran-Array Dimension darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.  
  
> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Der Bezeichner ist ein eindeutiger Wert, der vom Dia SDK erstellt wird, um alle Symbole als eindeutig zu markieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
