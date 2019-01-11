---
title: 'Iactivescriptprofilercallback3:: Setwebworkerid-Methode | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 47744746-1276-441e-ab60-2a78f550e8e2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4025dbee7b8b5b246163a1919aec335a8863937
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094432"
---
# <a name="iactivescriptprofilercallback3setwebworkerid-method"></a>IActiveScriptProfilerCallback3::SetWebWorkerId-Methode
Benachrichtigt den Profiler über die Worker-ID für diese Profilerstellungssitzung verwenden. Wenn die Funktion im Kontext der Seite nicht ausgeführt wird, wird diese Methode nicht aufgerufen. Der Wert des `webWorkerId` um 1 für jeden Arbeitsthread, beginnend mit 1 erhöht. Die ID-Werte sind nicht gedacht, stabile über eine Sitzung, und nur der Reihenfolge entsprechen, in der die Worker erstellt wurden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT SetWebWorkerId([in] DWORD webWorkerId);  
```  
  
#### <a name="parameters"></a>Parameter  
 `webWorkerId`  
 Die Web-Worker-ID.  
  
## <a name="return-value"></a>Rückgabewert  
 Der Rückgabewert dieser Methode wird von der Skript-Engine ignoriert.