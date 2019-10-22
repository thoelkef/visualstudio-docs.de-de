---
title: 'Idebugapplicationthread:: queryiscurrentthread | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationThread.QueryIsCurrentThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationThread::QueryIsCurrentThread
ms.assetid: 1580d3aa-3be8-4779-ac7b-41ab5c9edede
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 189de2448d808b777a21b9353a7adc9f6e3dde24
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574550"
---
# <a name="idebugapplicationthreadqueryiscurrentthread"></a>IDebugApplicationThread::QueryIsCurrentThread
Bestimmt, ob es sich bei diesem Thread um den derzeit laufenden Thread handelt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT QueryIsCurrentThread();  
```  
  
#### <a name="parameters"></a>Parameter  
 Diese Methode nimmt keine Parameter an.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode wurde erfolgreich ausgeführt, und dies ist der derzeit ausgeführten Thread.|  
|`S_FALSE`|Dabei handelt es sich nicht um den derzeit laufenden Thread.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode bestimmt, ob es sich bei diesem Thread um den derzeit laufenden Thread handelt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplicationThread-Schnittstelle](../../winscript/reference/idebugapplicationthread-interface.md)