---
title: IDiaAddressMap::put_relativeVirtualAddressEnabled | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_relativeVirtualAddressEnabled method
ms.assetid: 767c078e-8ad7-4940-9e00-cae7704aadee
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f32b83ce4d44a18b3eb50d246a5d5ff4800316c8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54927632"
---
# <a name="idiaaddressmapputrelativevirtualaddressenabled"></a>IDiaAddressMap::put_relativeVirtualAddressEnabled
Ermöglicht dem Client aktivieren oder deaktivieren die Berechnung und Verwenden der relativen virtuellen Adressen (RVA).  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT put_relativeVirtualAddressEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 NewVal  
 [in] Legen Sie auf `TRUE` aktiviert werden, oder `FALSE` deaktivieren.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Anmerkungen  
 Adressen für Debug-Objekte, die von DIA-Schnittstellen und relativ zu der ausführbaren Datei Anwendungsbasis, beschriebenen können als relativen virtuellen Adressen abgerufen werden.  
  
 Die Verwendung von RVA ist aktiviert, wenn Segmente ursprünglich aus einer PDB-Datei geladen werden. Um den aktuellen Status der Verwendung von RVA zu erhalten, rufen die [idiaaddressmap:: Get_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) Methode.  
  
 Die `put_relativeVirtualAddress` -Methode muss aufgerufen werden, zum Aktivieren der RVA nach einem erfolgreichen Aufruf der [idiaaddressmap:: Set_imageheaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) Methode hat das neue Image-Header eingerichtet.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)