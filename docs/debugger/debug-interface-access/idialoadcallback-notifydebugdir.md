---
title: 'Idialoadcallback:: Notifydebugdir | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 006d507a2c77cf2cf3191ce639404ef84b7a7a46
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
Wird aufgerufen, wenn ein Debugverzeichnis im .exe-Datei gefunden wurde.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT NotifyDebugDir (   
   BOOL  fExecutable,  
   DWORD cbData,  
   BYTE  data[]  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `fExecutable`  
 [in] `TRUE` Wenn das Debugverzeichnis aus einer ausführbaren Datei (statt einer .dbg-Datei) gelesen wird.  
  
 `cbData`  
 [in] Die Anzahl der Bytes der Daten in der Debugverzeichnis.  
  
 `data[]`  
 [in] Ein Array, das mit dem Debugverzeichnis ausgefüllt ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben. Der Rückgabecode wird in der Regel ignoriert.  
  
## <a name="remarks"></a>Hinweise  
 Die [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) Methode wird dieser Rückruf aufgerufen, wenn beim Verarbeiten der ausführbaren Datei ein Debugverzeichnis gefunden wird.  
  
 Diese Methode beseitigt die Notwendigkeit für den Client zurückentwickeln, die ausführbare Datei und/oder Debug-Datei unterstützen Debuginformationen anderen als den in der PDB-Datei gefunden. Mithilfe dieser Daten kann der Client erkennen, den Typ der Debuginformationen verfügbar und gibt an, ob es in die ausführbare Datei oder die .dbg-Datei befindet.  
  
 Die meisten Clients werden diesem Rückruf nicht benötigt, weil die `IDiaDataSource::loadDataForExe` Methode öffnet transparent PDB und .dbg-Dateien bei Bedarf, um Symbole zu fungieren.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)