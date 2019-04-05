---
title: 'Idiaaddressmap:: Put_imagealign | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_imageAlign method
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 833fed131ea99817b78c3834833021a50e3e6d80
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58947478"
---
# <a name="idiaaddressmapputimagealign"></a>IDiaAddressMap::put_imageAlign
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Legt die Ausrichtung fest.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT put_imageAlign (   
   DWORD NewVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 NewVal  
 [in] Das neue Image Ausrichtungswert für die ausführbare Datei.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Bilder (geladenen ausführbaren Dateien) werden angegebene Speicher-Grenzen ausgerichtet. Diese Ausrichtung kann durch die aktuelle Systemarchitektur und Kompilierung und Verknüpfung Zeitoptionen beeinflusst werden. Die Ausrichtung ist immer auf Byte-Begrenzungen. Die folgende Abbildung Ausrichtung-Werte sind gültig: 1, 2, 4, 8, 16, 32 und 64-Byte-Grenzen.  
  
 Die Ausrichtung für das aktuelle abgerufen werden kann, durch einen Aufruf der [idiaaddressmap:: Get_imagealign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) Methode.  
  
> [!NOTE]
>  Das Bild geladen wird bereits mit der Zeit, die diese Methode aufgerufen werden kann. Die `put_imageAlign` Methode wird normalerweise verwendet, wenn das Bild wurde verschoben oder geändert und eine neue Ausrichtung erforderlich ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)
