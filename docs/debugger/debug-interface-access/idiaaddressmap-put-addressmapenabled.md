---
title: 'Idiaaddressmap:: Put_addressmapenabled | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cb640a46825d720c5305a408fa716c6e3bed66c4
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31465836"
---
# <a name="idiaaddressmapputaddressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
Gibt an, ob die-Adresszuordnung zum Übersetzen Symbol Adressen verwendet werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT put_addressMapEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 NewVal  
 [in] Legen Sie auf `TRUE` So aktivieren Sie die Übersetzung von Symbolen oder `FALSE` zu deaktivieren.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Ausführbare Datei nach der Prozessoren aktualisieren manchmal die ausführbare Datei. DIA enthält einen Mechanismus, um die Übersetzung der Symbole, um das neue Layout zu unterstützen.  
  
 Eine PDB-Datei geladen wird, ist der in der Datei gespeicherten-Adresszuordnung aktiviert. Es gibt jedoch Situationen, wenn eine Clientanwendung möglicherweise Geben Sie einen eigenen-Adresszuordnung durch Aufrufen der [idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) Methode. Wenn die `set_addressMap` Methode erfolgreich ist, muss die Clientanwendung Aufrufen der `put_addressMapEnabled` Methode mit einer `NewVal` Parameter `TRUE` So aktivieren Sie die Verwendung der Adresse zugeordnet.  
  
 Der aktuelle Status der Adresse Karte aktiviert abgerufen werden kann, durch einen Aufruf der [idiaaddressmap:: Get_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)