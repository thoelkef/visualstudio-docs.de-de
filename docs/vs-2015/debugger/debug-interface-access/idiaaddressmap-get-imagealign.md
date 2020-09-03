---
title: 'IDiaAddressMap:: get_imageAlign | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_imageAlign method
ms.assetid: f1ba8071-669c-4cf7-9ac0-02f26d99f366
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3f3e7a326c78207976fb8493905b412df65e0c63
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178238"
---
# <a name="idiaaddressmapget_imagealign"></a>IDiaAddressMap::get_imageAlign
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft die aktuelle Bild Ausrichtung ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_imageAlign (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 vorgenommen Gibt den Bild Ausrichtungs Wert aus der ausführbaren Datei zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Abhängig von der Art und Weise, wie das Image geladen und erstellt wurde, werden Bilder an bestimmten Speichergrenzen ausgerichtet. Die Ausrichtung erfolgt in der Regel auf 1, 2, 4, 8, 16, 32 oder 64 Byte-Begrenzungen. Die Bild Ausrichtung kann mit einem Aufruf der [IDiaAddressMap::p ut_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md) -Methode festgelegt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)
