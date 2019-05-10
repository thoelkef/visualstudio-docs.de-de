---
title: 'Iactivescriptprofilercallback3:: Setwebworkerid-Methode | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 47744746-1276-441e-ab60-2a78f550e8e2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0798a23b4c8ad4e5859bec73ebfed47a56b322d6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993102"
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