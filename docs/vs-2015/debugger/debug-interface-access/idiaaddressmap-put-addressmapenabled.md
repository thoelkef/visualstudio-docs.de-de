---
title: IDiaAddressMap::p ut_addressMapEnabled | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4f2f7fc6fd512fa121cf96cb64f4ce4b961772e1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198681"
---
# <a name="idiaaddressmapput_addressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gibt an, ob die Adress Zuordnung zum Übersetzen von Symbol Adressen verwendet werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT put_addressMapEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 NewVal  
 in Legen Sie auf fest, `TRUE` um die Übersetzung von Symbolen zu aktivieren oder `FALSE` zu deaktivieren.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Ausführbare Postprozessoren aktualisieren manchmal die ausführbare Datei. Dia enthält einen Mechanismus, mit dem die Übersetzung von Symbolen in das neue Layout unterstützt wird.  
  
 Beim Laden einer PDB-Datei wird die in der Datei gespeicherte Adress Zuordnung aktiviert. Es gibt jedoch Zeiten, in denen eine Client Anwendung möglicherweise eine eigene Adress Zuordnung bereitstellen muss, indem Sie die [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) -Methode aufrufen. Wenn die `set_addressMap` Methode erfolgreich ist, muss die Client Anwendung die- `put_addressMapEnabled` Methode mit dem-Parameter aufrufen, `NewVal` `TRUE` um die Verwendung dieser Adress Zuordnung zu aktivieren.  
  
 Der aktuelle Zustand der aktivierten Adress Zuordnung kann mit einem Aufruf der [IDiaAddressMap:: get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) -Methode abgerufen werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)
