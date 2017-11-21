---
title: IEnumDebugApplicationNodes::Next | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IEnumDebugApplicationNodes.Next
apilocation: pdm.dll
helpviewer_keywords: IEnumDebugApplicationNodes::Next
ms.assetid: 925511c8-4f11-423d-ba2d-01589457050c
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 61bc2b677f12106c9bd8e6c8bec57ae1f7a09605
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="ienumdebugapplicationnodesnext"></a>IEnumDebugApplicationNodes::Next
Ruft eine angegebene Anzahl von Segmenten in die Enumerationsfolge ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT Next(  
   ULONG                    celt,  
   IDebugApplicationNode**  pprddp,  
   ULONG*                   pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `celt`  
 [in] Die Anzahl der Segmente abgerufen werden soll.  
  
 `pprddp`  
 [out] Gibt ein Array von `IDebugApplicationNode` Schnittstellen, die die abgerufenen Segmente darstellt.  
  
 `pceltFetched`  
 [out] Die tatsächliche Anzahl von Segmenten, die vom Enumerator abgerufen werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ruft eine angegebene Anzahl von Segmenten in die Enumerationsfolge ab.  
  
## <a name="see-also"></a>Siehe auch  
 [IEnumDebugApplicationNodes-Schnittstelle](../../winscript/reference/ienumdebugapplicationnodes-interface.md)