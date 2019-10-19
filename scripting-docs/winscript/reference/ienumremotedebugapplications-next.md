---
title: 'Ienumremotedebuapplications:: Next | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumRemoteDebugApplications.Next
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumRemoteDebugApplications::Next
ms.assetid: 33f6c620-6dd3-4057-b982-b88a7a1f02b4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9a9ebcbbd786ba8545e19b9833d26e5e385738c4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575213"
---
# <a name="ienumremotedebugapplicationsnext"></a>IEnumRemoteDebugApplications::Next
Die `Next`-Methode ruft eine angegebene Anzahl von Segmenten in der enumerationssequenz ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Next(  
   ULONG                      celt,  
   IRemoteDebugApplication**  ppda,  
   ULONG*                     pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `celt`  
 in Die Anzahl der abzurufenden Segmente.  
  
 `ppda`  
 vorgenommen Gibt ein Array von `IRemoteDebugApplication`-Schnittstellen zurück, die die abgerufenen Segmente darstellen.  
  
 `pceltFetched`  
 vorgenommen Die tatsächliche Anzahl der Segmente, die vom Enumerator abgerufen wurden.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ruft eine angegebene Anzahl von Segmenten in der enumerationssequenz ab.  
  
## <a name="see-also"></a>Siehe auch  
 [IEnumRemoteDebugApplications-Schnittstelle](../../winscript/reference/ienumremotedebugapplications-interface.md)