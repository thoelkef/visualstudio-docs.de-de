---
title: 'Idiaaddressmap:: Put_addressmapenabled | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a53d66879155ae1ce2cd831c029bc5776a7dd863
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54999209"
---
# <a name="idiaaddressmapputaddressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
Gibt an, ob die Adresszuordnung verwendet werden soll, um Symbol Adressen zu übersetzen.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT put_addressMapEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 NewVal  
 [in] Legen Sie auf `TRUE` die Übersetzung von Symbolen, aktivieren oder `FALSE` deaktivieren.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Anmerkungen  
 Die ausführbare Datei wird von Prozessoren für ausführbare Datei nach der Zeit zu Zeit aktualisiert. DIA enthält einen Mechanismus, um die Übersetzung von Symbolen, für das neue Layout zu unterstützen.  
  
 Wenn eine PDB-Datei geladen wird, ist die Adresse-Karte, die in der Datei gespeicherten aktiviert. Es gibt jedoch Situationen, wenn eine Clientanwendung möglicherweise Geben Sie eine eigene Adresszuordnung durch Aufrufen der [idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) Methode. Wenn die `set_addressMap` Methode erfolgreich ist, muss die Clientanwendung Aufrufen der `put_addressMapEnabled` -Methode mit einem `NewVal` Parameter der `TRUE` So aktivieren Sie die Verwendung der Adresse zugeordnet.  
  
 Der aktuelle Status der Adresszuordnung aktiviert abgerufen werden kann, durch einen Aufruf der [idiaaddressmap:: Get_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)