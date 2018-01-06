---
title: 'Idialoadcallback:: Notifydebugdir | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: fad37acafae21c6e82839979360f4ed9574aef1a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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