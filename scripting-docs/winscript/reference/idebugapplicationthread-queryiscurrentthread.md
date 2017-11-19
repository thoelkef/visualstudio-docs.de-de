---
title: IDebugApplicationThread::QueryIsCurrentThread | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplicationThread.QueryIsCurrentThread
apilocation: pdm.dll
helpviewer_keywords: IDebugApplicationThread::QueryIsCurrentThread
ms.assetid: 1580d3aa-3be8-4779-ac7b-41ab5c9edede
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a291005a7c5b85230c55c736c68de82c0290d0e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthreadqueryiscurrentthread"></a>IDebugApplicationThread::QueryIsCurrentThread
Bestimmt, ob der Thread den derzeit ausgeführten Thread ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT QueryIsCurrentThread();  
```  
  
#### <a name="parameters"></a>Parameter  
 Diese Methode nimmt keine Parameter.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich, und den derzeit ausgeführten Thread ist.|  
|`S_FALSE`|Dies ist nicht der derzeit ausgeführten Thread.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode bestimmt, ob der Thread den derzeit ausgeführten Thread ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplicationThread-Schnittstelle](../../winscript/reference/idebugapplicationthread-interface.md)