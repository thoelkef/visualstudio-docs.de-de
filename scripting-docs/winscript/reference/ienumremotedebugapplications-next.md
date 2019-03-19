---
title: IEnumRemoteDebugApplications::Next | Microsoft-Dokumentation
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
ms.openlocfilehash: 9b14874891e739fc95b877e41e76559a1ab0060a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58156332"
---
# <a name="ienumremotedebugapplicationsnext"></a>IEnumRemoteDebugApplications::Next
Die `Next` Methode ruft eine angegebene Anzahl von Segmenten in der Enumerationsfolge ab.  
  
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
 [in] Die Anzahl von Segmenten abgerufen werden soll.  
  
 `ppda`  
 [out] Gibt ein Array von `IRemoteDebugApplication` Schnittstellen, die die Segmente, die abgerufen werden darstellt.  
  
 `pceltFetched`  
 [out] Die tatsächliche Anzahl von Segmenten, die vom Enumerator abgerufen werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ruft eine angegebene Anzahl von Segmenten in der Enumerationsfolge ab.  
  
## <a name="see-also"></a>Siehe auch  
 [IEnumRemoteDebugApplications-Schnittstelle](../../winscript/reference/ienumremotedebugapplications-interface.md)