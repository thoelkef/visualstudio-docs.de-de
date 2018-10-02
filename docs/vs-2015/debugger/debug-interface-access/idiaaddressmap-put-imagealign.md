---
title: 'Idiaaddressmap:: Put_imagealign | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_imageAlign method
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6743d2a39f2326b167da746fbb2da928c0b75aaf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512223"
---
# <a name="idiaaddressmapputimagealign"></a>IDiaAddressMap::put_imageAlign
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [idiaaddressmap:: Put_imagealign](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaaddressmap-put-imagealign).  
  
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
 Bilder (geladenen ausführbaren Dateien) werden angegebene Speicher-Grenzen ausgerichtet. Diese Ausrichtung kann durch die aktuelle Systemarchitektur und Kompilierung und Verknüpfung Zeitoptionen beeinflusst werden. Die Ausrichtung ist immer auf Byte-Begrenzungen. Die folgende Abbildung Ausrichtungswerte sind gültig: 1, 2, 4, 8, 16, 32 und 64-Byte-Grenzen.  
  
 Die Ausrichtung für das aktuelle abgerufen werden kann, durch einen Aufruf der [idiaaddressmap:: Get_imagealign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) Methode.  
  
> [!NOTE]
>  Das Bild geladen wird bereits mit der Zeit, die diese Methode aufgerufen werden kann. Die `put_imageAlign` Methode wird normalerweise verwendet, wenn das Bild wurde verschoben oder geändert und eine neue Ausrichtung erforderlich ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)



