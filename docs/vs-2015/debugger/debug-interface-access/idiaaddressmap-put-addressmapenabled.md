---
title: 'Idiaaddressmap:: Put_addressmapenabled | Microsoft-Dokumentation'
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
- IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a81a08001a83fbf9794a6326f448f967947d15a6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49918518"
---
# <a name="idiaaddressmapputaddressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gibt an, ob die Adresszuordnung verwendet werden soll, um Symbol Adressen zu übersetzen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT put_addressMapEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 NewVal  
 [in] Legen Sie auf `TRUE` die Übersetzung von Symbolen, aktivieren oder `FALSE` deaktivieren.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die ausführbare Datei wird von Prozessoren für ausführbare Datei nach der Zeit zu Zeit aktualisiert. DIA enthält einen Mechanismus, um die Übersetzung von Symbolen, für das neue Layout zu unterstützen.  
  
 Wenn eine PDB-Datei geladen wird, ist die Adresse-Karte, die in der Datei gespeicherten aktiviert. Es gibt jedoch Situationen, wenn eine Clientanwendung möglicherweise Geben Sie eine eigene Adresszuordnung durch Aufrufen der [idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) Methode. Wenn die `set_addressMap` Methode erfolgreich ist, muss die Clientanwendung Aufrufen der `put_addressMapEnabled` -Methode mit einem `NewVal` Parameter der `TRUE` So aktivieren Sie die Verwendung der Adresse zugeordnet.  
  
 Der aktuelle Status der Adresszuordnung aktiviert abgerufen werden kann, durch einen Aufruf der [idiaaddressmap:: Get_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Idiaaddressmap:: Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)



