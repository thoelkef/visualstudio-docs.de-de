---
title: IDiaAddressMap::put_relativeVirtualAddressEnabled | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_relativeVirtualAddressEnabled method
ms.assetid: 767c078e-8ad7-4940-9e00-cae7704aadee
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 14c9924346471e098d9ba9f1abb52fda0d3c9969
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68198670"
---
# <a name="idiaaddressmapputrelativevirtualaddressenabled"></a>IDiaAddressMap::put_relativeVirtualAddressEnabled
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ermöglicht dem Client aktivieren oder deaktivieren die Berechnung und Verwenden der relativen virtuellen Adressen (RVA).  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT put_relativeVirtualAddressEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 NewVal  
 [in] Legen Sie auf `TRUE` aktiviert werden, oder `FALSE` deaktivieren.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Adressen für Debug-Objekte, die von DIA-Schnittstellen und relativ zu der ausführbaren Datei Anwendungsbasis, beschriebenen können als relativen virtuellen Adressen abgerufen werden.  
  
 Die Verwendung von RVA ist aktiviert, wenn Segmente ursprünglich aus einer PDB-Datei geladen werden. Um den aktuellen Status der Verwendung von RVA zu erhalten, rufen die [idiaaddressmap:: Get_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) Methode.  
  
 Die `put_relativeVirtualAddress` -Methode muss aufgerufen werden, zum Aktivieren der RVA nach einem erfolgreichen Aufruf der [idiaaddressmap:: Set_imageheaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) Methode hat das neue Image-Header eingerichtet.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)
