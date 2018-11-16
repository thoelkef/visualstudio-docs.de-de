---
title: 'Idiaaddressmap:: Get_addressmapenabled | Microsoft-Dokumentation'
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
- IDiaAddressMap::get_addressMapEnabled method
ms.assetid: 6183dc5e-befa-4e5a-ae5a-f4aa24f3ed9e
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 59a3ded58dcec258acdc9620f92ae6a9c653bff7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51754109"
---
# <a name="idiaaddressmapgetaddressmapenabled"></a>IDiaAddressMap::get_addressMapEnabled
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gibt an, ob eine Adresszuordnung für eine bestimmte Sitzung eingerichtet wurde.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_addressMapEnabled (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pRetVal  
 [out] Gibt `TRUE` , wenn die Adresszuordnung aktiviert ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die ausführbare Datei wird von Prozessoren für ausführbare Datei nach der Zeit zu Zeit aktualisiert. DIA enthält einen Mechanismus, um die Übersetzung von Symbolen, für das neue Layout zu unterstützen.  
  
 Clientanwendungen können die Adresszuordnung für eine bestimmte Sitzung festlegen, durch Abrufen der [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md) -Schnittstelle aus der [IDiaSession](../../debugger/debug-interface-access/idiasession.md) -Schnittstelle ab, und rufen die [IDiaAddressMap::set_ AddressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) Methode, gefolgt von einem Aufruf der [idiaaddressmap:: Put_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) Methode. Die `get_addressMapEnabled` Methode gibt die Ergebnisse des Aufrufs der `put_addressMapEnabled` Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)



