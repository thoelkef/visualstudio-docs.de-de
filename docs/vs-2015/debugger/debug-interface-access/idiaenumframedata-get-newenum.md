---
title: 'IDiaEnumFrameData:: get__NewEnum | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::get__NewEnum method
ms.assetid: f5fe0279-0549-4af5-8f89-bcb535fc5809
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 16cfaf56da7d4cb5a1a3dff943f44930ac887993
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157949"
---
# <a name="idiaenumframedataget__newenum"></a>IDiaEnumFrameData::get__NewEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft die <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> Version dieses Enumerators ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get__NewEnum (   
   IUnknown** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pRetVal  
 vorgenommen Gibt die- `IUnknown` Schnittstelle zurück, die die <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> Version dieses Enumerators darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
