---
title: 'Idiaaddressmap:: Set_imageheaders | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
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
- IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f8ef978dfe6da37c06574fd2ec72e87ba21b214b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49294943"
---
# <a name="idiaaddressmapsetimageheaders"></a>IDiaAddressMap::set_imageHeaders
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Legt image-Header, um die relative virtuelle adressenübersetzung aktivieren.  
  
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
 [in] Anzahl der Bytes der Daten im Anforderungsheader. Muss `n*sizeof(IMAGE_SECTION_HEADER)` , in denen `n` ist die Anzahl der im Abschnittsheader in der ausführbaren Datei.  
  
 Daten]  
 [in] Ein Array von `IMAGE_SECTION_HEADER` Strukturen als die Image-Header verwendet werden soll.  
  
 originalHeaders  
 [in] Legen Sie auf `FALSE` Wenn die Image-Header aus dem neuen Abbild, sind `TRUE` , wenn sie das ursprüngliche Bild vor einem Upgrade widerspiegeln. Dies würde in der Regel festgelegt werden, um `TRUE` nur in Kombination mit Aufrufe an die [idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) Methode.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die `IMAGE_SECTION_HEADER` Struktur wird in "Winnt.h" deklariert, und das Bildformat für die Header von Abschnitt der ausführbaren Datei darstellt.  
  
 Relative virtuelle Adresse Berechnungen hängen von der `IMAGE_SECTION_HEADER` Werte. In der Regel ruft der DIA diese über die Programmdatenbankdatei (.pdb). Wenn diese Werte fehlen, kann die DIA nicht relative virtuelle Adressen zu berechnen und die [idiaaddressmap:: Get_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) Methodenrückgabe `FALSE`. Der Client muss dann Aufrufen der [idiaaddressmap:: Put_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) Methode, um die relative virtuelle Adresse Berechnungen zu ermöglichen, nach dem fehlenden Header von Images aus dem Image selbst bereitstellen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [Idiaaddressmap:: Get_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)



