---
title: 'IDiaAddressMap:: get_addressMapEnabled | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_addressMapEnabled method
ms.assetid: 6183dc5e-befa-4e5a-ae5a-f4aa24f3ed9e
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0cf874590d6bcf7f259d7a59eee1b81b79ffe1a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178243"
---
# <a name="idiaaddressmapget_addressmapenabled"></a>IDiaAddressMap::get_addressMapEnabled
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gibt an, ob eine Adress Zuordnung für eine bestimmte Sitzung eingerichtet wurde.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_addressMapEnabled (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pRetVal  
 vorgenommen Gibt zurück, `TRUE` Wenn die Adress Zuordnung aktiviert ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Ausführbare Postprozessoren aktualisieren manchmal die ausführbare Datei. Dia enthält einen Mechanismus, mit dem die Übersetzung von Symbolen in das neue Layout unterstützt wird.  
  
 Client Anwendungen können die Adress Zuordnung für eine bestimmte Sitzung festlegen, indem Sie die [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md) -Schnittstelle von der [IDiaSession](../../debugger/debug-interface-access/idiasession.md) -Schnittstelle abrufen und die [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) -Methode gefolgt von einem Aufruf der [IDiaAddressMap::p ut_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) -Methode aufrufen. Die- `get_addressMapEnabled` Methode gibt die Ergebnisse des Aufruf der- `put_addressMapEnabled` Methode zurück.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)
