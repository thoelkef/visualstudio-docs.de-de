---
title: 'Idialoadcallback:: Notifyopenpdb | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyOpenPDB method
ms.assetid: c0547f99-8468-4e57-82ca-9ef7d6707c8a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1367d444a498c1c066cbdfb38ee4f2cec12c9a2b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915320"
---
# <a name="idialoadcallbacknotifyopenpdb"></a>IDiaLoadCallback::NotifyOpenPDB
Aufgerufen, wenn eine Kandidat PDB-Datei geöffnet wird.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT NotifyOpenPDB (   
   LPCOLESTR pdbPath,  
   HRESULT   resultCode  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pdbPath`  
 [in] Der vollständige Pfad der PDB-Datei.  
  
 `resultCode`  
 [in] Code, der den Erfolg angibt (`S_OK`) oder das Fehlschlagen der Last auf diese Datei angewendet.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben. Der Rückgabecode wird in der Regel ignoriert.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)