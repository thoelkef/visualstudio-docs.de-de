---
title: 'Idiaframedata:: Execute | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
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
- IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1f76bf5e5ef30c748f310e6a8a610035b7c08bb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511840"
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [idiaframedata:: Execute](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaframedata-execute).  
  
Führt die stapelentladung und gibt Ergebnisse in eine Stackwalk-Frame-Schnittstelle zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT execute (   
   IDiaStackWalkFrame* frame  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `frame`  
 [in] Ein [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) -Objekt, das den Zustand der Frame-Register enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben. Die folgende Tabelle zeigt die möglichen Rückgabewerte für diese Methode.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|E_DIA_INPROLOG|Einen Stapelrahmen im Prolog Code kann nicht ausgeführt werden.|  
|E_DIA_SYNTAX|Analysieren Sie Fehler im Frame-Programm.|  
|E_DIA_FRAME_ACCESS|Kann nicht den Zugriff registriert oder Arbeitsspeicher.|  
|E_DIA_VALUE|Fehler bei der Berechnung eines Werts (z. B. Division durch 0 (null)).|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird aufgerufen, während des Debuggens, um den Stapel zu entladen. Die [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) Objekt wird von der Clientanwendung zum Empfangen von Updates für die Register und Bereitstellen von verwendete Methoden implementiert die `execute` Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)



