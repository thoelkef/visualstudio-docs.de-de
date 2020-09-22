---
title: IDiaAddressMap::p ut_imageAlign | Microsoft-Dokumentation
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
ms.openlocfilehash: 5e0fa57c38c8451bde84d96ab32bc7980c5e2d8b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840994"
---
# <a name="idiaaddressmapput_imagealign"></a>IDiaAddressMap::put_imageAlign
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Legt die Bild Ausrichtung fest.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT put_imageAlign (   
   DWORD NewVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 NewVal  
 in Der neue Bild Ausrichtungs Wert für die ausführbare Datei.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Bilder (geladene ausführbare Dateien) werden an den angegebenen Speichergrenzen ausgerichtet. Diese Ausrichtung kann von der aktuellen Systemarchitektur und den Optionen Kompilierungs-und Linkzeit beeinflusst werden. Die Bild Ausrichtung erfolgt immer über Byte-Begrenzungen. Die folgenden Bild Ausrichtungs Werte sind gültig: 1, 2, 4, 8, 16, 32 und 64 Byte-Begrenzungen.  
  
 Die aktuelle Bild Ausrichtung kann mit einem Aufruf der [IDiaAddressMap:: get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) -Methode abgerufen werden.  
  
> [!NOTE]
> Das Bild wird bereits von dem Zeitpunkt geladen, zu dem diese Methode aufgerufen werden kann. Die `put_imageAlign` -Methode wird normalerweise verwendet, wenn das Bild verschoben oder geändert wurde und eine neue Ausrichtung erforderlich ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)
