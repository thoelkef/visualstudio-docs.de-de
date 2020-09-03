---
title: 'IDiaAddressMap:: set_imageHeaders | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 18fa69929f78d5ae661169a09db97697d98f4d94
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198638"
---
# <a name="idiaaddressmapset_imageheaders"></a>IDiaAddressMap::set_imageHeaders
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Legt Bild Header fest, um die relative virtuelle Adressübersetzung zu aktivieren.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT set_imageHeaders (   
   DWORD cbData,  
   BYTE  data[],  
   BOOL  originalHeaders  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 cbData  
 in Anzahl von Bytes von Header Daten. Muss sein, `n*sizeof(IMAGE_SECTION_HEADER)` wobei `n` die Anzahl der Abschnitts Header in der ausführbaren Datei ist.  
  
 data[]  
 in Ein Array von-  `IMAGE_SECTION_HEADER` Strukturen, die als Bild Header verwendet werden sollen.  
  
 originalHeaders  
 in Festgelegt auf `FALSE` , wenn die Bild Header aus dem neuen Bild stammen, `TRUE` Wenn Sie das ursprüngliche Bild vor einem Upgrade widerspiegeln. In der Regel wird dies `TRUE` nur in Kombination mit Aufrufen der [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) -Methode festgelegt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Die `IMAGE_SECTION_HEADER` -Struktur wird in "Winnt. h" deklariert und stellt das Bild Abschnitts Header Format der ausführbaren Datei dar.  
  
 Relative virtuelle Adress Berechnungen sind abhängig von den `IMAGE_SECTION_HEADER` Werten. In der Regel ruft der Dia diese aus der Programm Datenbankdatei (. pdb) ab. Wenn diese Werte fehlen, kann die Dia keine relativen virtuellen Adressen berechnen, und die [IDiaAddressMap:: get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) -Methode gibt zurück `FALSE` . Der Client muss dann die [IDiaAddressMap::p ut_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) -Methode aufzurufen, um die relativen virtuellen Adress Berechnungen zu aktivieren, nachdem die fehlenden Bild Header aus dem Image selbst bereitgestellt wurden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap:: get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)
