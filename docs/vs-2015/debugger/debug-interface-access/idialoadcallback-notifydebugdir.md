---
title: 'IDiaLoadCallback:: notifydebug-Verzeichnis | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2e8fe8ffe9d7d495e40c8c84b08aeaefb03e8d17
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151999"
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wird aufgerufen, wenn ein Debugverzeichnis in der exe-Datei gefunden wurde.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT NotifyDebugDir (   
   BOOL  fExecutable,  
   DWORD cbData,  
   BYTE  data[]  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `fExecutable`  
 [in] `TRUE` , wenn das Debugverzeichnis aus einer ausführbaren Datei gelesen wird (anstatt einer dbg-Datei).  
  
 `cbData`  
 in Anzahl der Daten Bytes im Debugverzeichnis.  
  
 `data[]`  
 in Ein Array, das mit dem Debugverzeichnis ausgefüllt ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. Der Rückgabecode wird in der Regel ignoriert.  
  
## <a name="remarks"></a>Bemerkungen  
 Die [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) -Methode ruft diesen Rückruf auf, wenn beim Verarbeiten der ausführbaren Datei ein Debugverzeichnis gefunden wird.  
  
 Durch diese Methode entfällt die Notwendigkeit, dass der Client die ausführbare Datei und/oder Debugdatei rückgängig machen muss, um andere Debuginformationen als in der PDB-Datei zu unterstützen. Mit diesen Daten kann der Client den Typ der verfügbaren Debuginformationen erkennen und davon, ob er sich in der ausführbaren Datei oder der dbg-Datei befindet.  
  
 Die meisten Clients benötigen diesen Rückruf nicht, da die `IDiaDataSource::loadDataForExe` -Methode bei Bedarf transparent sowohl PDB-als auch dbg-Dateien öffnet, um Symbole zu verarbeiten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
