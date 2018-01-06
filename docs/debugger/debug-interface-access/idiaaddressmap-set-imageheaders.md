---
title: 'Idiaaddressmap:: Set_imageheaders | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 74556e2e67478cef9b495d3740dc910b62cc8293
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idiaaddressmapsetimageheaders"></a>IDiaAddressMap::set_imageHeaders
Legt image-Header, um die relative virtuelle Adresse-Übersetzung aktivieren.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT set_imageHeaders (   
   DWORD cbData,  
   BYTE  data[],  
   BOOL  originalHeaders  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 cbData  
 [in] Anzahl der Bytes, des Header-Daten. Muss `n*sizeof(IMAGE_SECTION_HEADER)` , in denen `n` ist die Anzahl der Abschnittsheader in der ausführbaren Datei.  
  
 Daten]  
 [in] Ein Array von `IMAGE_SECTION_HEADER` Strukturen als die Image-Header verwendet werden soll.  
  
 originalHeaders  
 [in] Legen Sie auf `FALSE` , wenn die Image-Header aus dem neuen Image sind `TRUE` , wenn sie das ursprüngliche Image vor dem Upgrade wiedergeben. Dies würde i. d. r. festgelegt werden, um `TRUE` nur in Kombination mit Aufrufen an die [idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) Methode.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die `IMAGE_SECTION_HEADER` Struktur ist in "Winnt.h" deklariert und das Abschnitt Header-Bildformat der ausführbaren Datei darstellt.  
  
 Relative virtuelle Adresse Berechnungen hängt von der `IMAGE_SECTION_HEADER` Werte. In der Regel ruft der DIA diese über die Programmdatenbankdatei (.pdb). Wenn diese Werte fehlen, wird die DIA nicht relative virtuelle Adressen berechnet und die [idiaaddressmap:: Get_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) -Methode zurückkehrt `FALSE`. Der Client muss dann Aufrufen der [idiaaddressmap:: Put_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) Methode, um die relative virtuelle Adresse Berechnungen zu ermöglichen, nach der Bereitstellung der fehlenden Image-Header aus das eigentliche Bild.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [Idiaaddressmap:: Get_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)