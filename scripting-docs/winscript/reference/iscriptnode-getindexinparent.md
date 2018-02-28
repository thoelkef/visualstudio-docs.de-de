---
title: IScriptNode::GetIndexInParent | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IScriptNode.GetIndexInParent
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetIndexInParent
ms.assetid: 521c1ca1-2d27-4344-bf3b-d8b53132b648
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3862a48ff4649f018eec79bf0411f23bc9f6d7bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptnodegetindexinparent"></a>IScriptNode::GetIndexInParent
Gibt den Index eines Objekts in die untergeordnete Liste des übergeordneten Elements zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetIndexInParent(  
   ULONG              pisn,  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pisn`  
 [out] Gibt den Index eines Objekts in die untergeordnete Liste des übergeordneten Elements zurück.  
  
 Wenn diese Methode, indem aufgerufen wird ein `IScriptNode` -Objekt, dass eine Webseite darstellt, dieser Parameter "0" zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [IScriptNode-Schnittstelle](../../winscript/reference/iscriptnode-interface.md)