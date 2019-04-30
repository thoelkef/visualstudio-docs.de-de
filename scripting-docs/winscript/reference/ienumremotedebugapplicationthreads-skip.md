---
title: IEnumRemoteDebugApplicationThreads::Skip | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumRemoteDebugApplicationThreads.Skip
apilocation:
- pdm.dll
helpviewer_keywords:
- IEnumRemoteDebugApplicationThreads::Skip
ms.assetid: bb13a18b-bcf8-4542-8b1a-55a4f2769536
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a8ef51b7e1b5e038534fda6e3585304515c7d165
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62807172"
---
# <a name="ienumremotedebugapplicationthreadsskip"></a>IEnumRemoteDebugApplicationThreads::Skip
Überspringt eine angegebene Anzahl von Segmenten in einer Enumerationsfolge.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Skip(  
   ULONG  celt  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `celt`  
 [in] Anzahl von Segmenten in der Enumerationsfolge übersprungen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode überspringt eine angegebene Anzahl von Segmenten in einer Enumerationsfolge.  
  
## <a name="see-also"></a>Siehe auch  
 [IEnumRemoteDebugApplicationThreads-Schnittstelle](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)