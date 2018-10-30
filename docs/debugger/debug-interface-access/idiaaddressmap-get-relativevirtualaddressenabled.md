---
title: 'Idiaaddressmap:: Get_relativevirtualaddressenabled | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_relativeVirtualAddressEnabled method
ms.assetid: 4c48af81-7148-4d9a-818e-dbe62cbfc638
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aa61da69f30b759ade63798d681ae8036bcd8ece
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49849085"
---
# <a name="idiaaddressmapgetrelativevirtualaddressenabled"></a>IDiaAddressMap::get_relativeVirtualAddressEnabled
Gibt an, ob die Berechnung und Verwenden der relativen virtuellen Adressen (RVA) aktiviert ist.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_relativeVirtualAddressEnabled (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pRetVal  
 [out] Gibt `TRUE` , wenn die Berechnung der RVA aktiviert ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 RVA sind aktiviert, wenn die Segmente ursprünglich aus einer PDB-Datei geladen wurden. Die Verwendung von RVA kann vorübergehend deaktiviert werden, durch den Aufruf der [idiaaddressmap:: Put_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) Methode.  
  
 Darüber hinaus für die neue Image-Header hergestellt werden können, durch den Aufruf der [idiaaddressmap:: Set_imageheaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) Methode, gefolgt von einem Aufruf der `put_relativeVirtualAddressEnabled` Methode, um die Verwendung der RVA verwenden der neuen Image-Header zu ermöglichen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Idiaaddressmap:: Set_imageheaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)   
 [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)