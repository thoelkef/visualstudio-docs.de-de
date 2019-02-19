---
title: 'Idiaaddressmap:: Put_imagealign | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_imageAlign method
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a78b1d03eddfcedb04966276c889219630c45f83
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54950740"
---
# <a name="idiaaddressmapputimagealign"></a>IDiaAddressMap::put_imageAlign
Legt die Ausrichtung fest.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT put_imageAlign (   
   DWORD NewVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 NewVal  
 [in] Das neue Image Ausrichtungswert für die ausführbare Datei.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Anmerkungen  
 Bilder (geladenen ausführbaren Dateien) werden angegebene Speicher-Grenzen ausgerichtet. Diese Ausrichtung kann durch die aktuelle Systemarchitektur und Kompilierung und Verknüpfung Zeitoptionen beeinflusst werden. Die Ausrichtung ist immer auf Byte-Begrenzungen. Die folgende Abbildung Ausrichtung-Werte sind gültig: 1, 2, 4, 8, 16, 32 und 64-Byte-Grenzen.  
  
 Die Ausrichtung für das aktuelle abgerufen werden kann, durch einen Aufruf der [idiaaddressmap:: Get_imagealign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) Methode.  
  
> [!NOTE]
>  Das Bild geladen wird bereits mit der Zeit, die diese Methode aufgerufen werden kann. Die `put_imageAlign` Methode wird normalerweise verwendet, wenn das Bild wurde verschoben oder geändert und eine neue Ausrichtung erforderlich ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)