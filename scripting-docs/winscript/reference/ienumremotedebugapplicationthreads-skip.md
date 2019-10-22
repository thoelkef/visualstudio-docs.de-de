---
title: 'Ienumremotedebugapplicationthreads:: Skip | Microsoft-Dokumentation'
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
ms.openlocfilehash: c92a92c53b4f7638893a5f5a73810e9b939c725b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577772"
---
# <a name="ienumremotedebugapplicationthreadsskip"></a>IEnumRemoteDebugApplicationThreads::Skip
Überspringt eine angegebene Anzahl von Segmenten in einer enumerationssequenz.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Skip(  
   ULONG  celt  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `celt`  
 in Anzahl der zu über springenden Segmente in der enumerationssequenz.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode überspringt eine angegebene Anzahl von Segmenten in einer enumerationssequenz.  
  
## <a name="see-also"></a>Siehe auch  
 [IEnumRemoteDebugApplicationThreads-Schnittstelle](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)