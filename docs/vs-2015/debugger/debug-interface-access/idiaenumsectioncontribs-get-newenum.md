---
title: 'Idiaenumsectioncontribs:: Get__newenum | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::get__NewEnum method
ms.assetid: a16ee92f-3081-416a-98f6-ce6bc8288a8b
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 728f214460bbbe3e6334d7692c8842be5c10631f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68189983"
---
# <a name="idiaenumsectioncontribsgetnewenum"></a>IDiaEnumSectionContribs::get__NewEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft die <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> Version von diesem Enumerator.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get__NewEnum (   
   IUnknown** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pRetVal  
 [out] Gibt die `IUnknown` Schnittstelle, die darstellt der <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> Version von diesem Enumerator.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)
