---
title: 'IDiaFrameData:: Execute | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4042cf58ee34b5f49df601b94e1110f03e0b6f5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197553"
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Führt die Stapel Auflösung aus und gibt die Ergebnisse in einer Stapel Durchlauf-Frame Schnittstelle zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT execute (   
   IDiaStackWalkFrame* frame  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `frame`  
 in Ein [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) -Objekt, das den Zustand von Frame Registern enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. In der folgenden Tabelle sind die möglichen Rückgabewerte für diese Methode aufgeführt.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|E_DIA_INPROLOG|Ein Stapel Rahmen kann im Prologcode nicht ausgeführt werden.|  
|E_DIA_SYNTAX|Analysefehler im Rahmenprogramm.|  
|E_DIA_FRAME_ACCESS|Auf die Register oder den Arbeitsspeicher kann nicht zugegriffen werden.|  
|E_DIA_VALUE|Fehler bei der Berechnung eines Werts (z. b. Division durch null).|  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode wird während des Debuggens aufgerufen, um den Stapel zu entladen. Das [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) -Objekt wird von der Client Anwendung implementiert, um Aktualisierungen der Register zu empfangen und von der-Methode verwendete Methoden bereitzustellen `execute` .  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
