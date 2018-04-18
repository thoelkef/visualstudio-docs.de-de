---
title: 'Idiaaddressmap:: Get_addressmapenabled | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_addressMapEnabled method
ms.assetid: 6183dc5e-befa-4e5a-ae5a-f4aa24f3ed9e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 225cac39cb56bbf5b03478c6009162c711baad87
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idiaaddressmapgetaddressmapenabled"></a>IDiaAddressMap::get_addressMapEnabled
Gibt an, ob eine Adresszuordnung für eine bestimmte Sitzung eingerichtet wurde.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_addressMapEnabled (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pRetVal  
 [out] Gibt `TRUE` , wenn die Adresszuordnung aktiviert ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Ausführbare Datei nach der Prozessoren aktualisieren manchmal die ausführbare Datei. DIA enthält einen Mechanismus, um die Übersetzung der Symbole, um das neue Layout zu unterstützen.  
  
 Clientanwendungen können die Adresszuordnung für eine bestimmte Sitzung festlegen, durch Abrufen der [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md) -Schnittstelle aus der [IDiaSession](../../debugger/debug-interface-access/idiasession.md) Schnittstelle und der Aufruf der [IDiaAddressMap::set_ AddressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) Methode gefolgt von einem Aufruf der [idiaaddressmap:: Put_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) Methode. Die `get_addressMapEnabled` Methode gibt die Ergebnisse eines Aufrufs der `put_addressMapEnabled` Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)