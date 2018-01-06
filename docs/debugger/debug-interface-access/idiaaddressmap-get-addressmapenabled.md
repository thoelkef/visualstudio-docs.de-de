---
title: 'Idiaaddressmap:: Get_addressmapenabled | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaAddressMap::get_addressMapEnabled method
ms.assetid: 6183dc5e-befa-4e5a-ae5a-f4aa24f3ed9e
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 148444b9c7cb1db6df5cb1ed70412bbd049427d9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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