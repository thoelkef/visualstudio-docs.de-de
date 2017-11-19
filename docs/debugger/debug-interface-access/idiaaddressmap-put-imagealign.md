---
title: 'Idiaaddressmap:: Put_imagealign | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaAddressMap::put_imageAlign method
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38856520641ff2ea191e3f712a1f355e841e1aff
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idiaaddressmapputimagealign"></a>IDiaAddressMap::put_imageAlign
Legt die Ausrichtung des Bilds an.  
  
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
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Bilder (geladenen ausführbare Dateien) werden angegebene Speicher-Grenzen ausgerichtet. Diese Ausrichtung kann durch die aktuelle Systemarchitektur und durch Kompilieren und verknüpfen Zeitoptionen beeinflusst werden. Ausrichtung des Hintergrundbilds ist immer auf Byte-Grenzen. Das folgende Bild Ausrichtungswerte sind gültig: 1, 2, 4, 8, 16, 32 und 64-Byte-Grenzen.  
  
 Die Ausrichtung für das aktuelle abgerufen werden kann, durch einen Aufruf der [idiaaddressmap:: Get_imagealign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) Methode.  
  
> [!NOTE]
>  Das Bild geladen wird bereits von der Zeit, die diese Methode aufgerufen werden kann. Die `put_imageAlign` Methode wird normalerweise verwendet, wenn das Image wurde verschoben oder geändert und eine neue Ausrichtung erforderlich ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)