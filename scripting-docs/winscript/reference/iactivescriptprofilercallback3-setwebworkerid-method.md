---
title: 'Iactivescriptprofilercallback3:: Setwebworkerid-Methode | Microsoft Docs'
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
ms.openlocfilehash: 426767b8d4d23964d6bfaa7102ee53b550e7ab9b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724610"
---
# <a name="iactivescriptprofilercallback3setwebworkerid-method"></a>IActiveScriptProfilerCallback3::SetWebWorkerId-Methode
Benachrichtigt den Profiler über die Worker-ID, die für die remoteprofilerstellungs-Sitzung verwendet. Wenn die Funktion im Kontext der Seite nicht ausgeführt wird, wird diese Methode nicht aufgerufen. Der Wert des `webWorkerId` um 1 für jeden Arbeitsthread, beginnend mit 1 erhöht. Die ID-Werte dürfen nicht stabil außerhalb einer Sitzung, und nur der Reihenfolge entsprechen, in der die Arbeitsthreads erstellt wurden.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT SetWebWorkerId([in] DWORD webWorkerId);  
```  
  
#### <a name="parameters"></a>Parameter  
 `webWorkerId`  
 Die Web-Worker-ID.  
  
## <a name="return-value"></a>Rückgabewert  
 Der Rückgabewert dieser Methode wird vom Skriptmodul ignoriert.