---
title: 'Idiaaddressmap:: Put_relativevirtualaddressenabled | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_relativeVirtualAddressEnabled method
ms.assetid: 767c078e-8ad7-4940-9e00-cae7704aadee
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dbbe2c2299a26834ac40c787aea5504ae7d0ed8a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="idiaaddressmapputrelativevirtualaddressenabled"></a>IDiaAddressMap::put_relativeVirtualAddressEnabled
Ermöglicht dem Client aktivieren oder deaktivieren die Berechnung und die Verwendung von relativen virtuellen Adresse (RVA).  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT put_relativeVirtualAddressEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 NewVal  
 [in] Legen Sie auf `TRUE` aktiviert werden, oder `FALSE` zu deaktivieren.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Adressen für Debug-Objekte, die von DIA Schnittstellen und relativ zu den ausführbaren Image Basisentität beschriebenen können als relative virtuelle Adressen abgerufen werden.  
  
 Die Verwendung von RVA ist aktiviert, wenn Segmente ursprünglich aus einer PDB-Datei geladen werden. Um den aktuellen Status der Verwendung der RVA zu erhalten, rufen die [idiaaddressmap:: Get_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) Methode.  
  
 Die `put_relativeVirtualAddress` Methode muss aufgerufen werden, um nach einem erfolgreichen Aufruf von RVA aktivieren die [idiaaddressmap:: Set_imageheaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) Methode hergestellt hat, dann neue Image-Header.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Idiaaddressmap:: Get_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)