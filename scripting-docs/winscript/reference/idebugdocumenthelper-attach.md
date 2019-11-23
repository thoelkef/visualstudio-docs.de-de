---
title: 'Idebugdocumenthelper:: Attach | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.Attach
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::Attach
ms.assetid: 834f23a9-716d-44df-b23c-d1bf6da60e79
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3400a5bf6cd3e4a9726fdf4b2f20bbf43b9fc989
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577030"
---
# <a name="idebugdocumenthelperattach"></a>IDebugDocumentHelper::Attach
Fügt der Dokumentstruktur dieses Dokument hinzu.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Attach(  
   IDebugDocumentHelper*  pddhParent  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pddhParent`  
 in Die Dokumentstruktur, in der dieses Dokument hinzugefügt wird. Kann möglicherweise NULL sein.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Mit dieser Methode wird dieses Dokument der Dokumentstruktur hinzugefügt, wobei `pddhParent` als übergeordnetes Element verwendet wird. Wenn die `pddhParent` `NULL`ist, wird dieses Dokument als Dokument der obersten Ebene verwendet.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentHelper::Detach](../../winscript/reference/idebugdocumenthelper-detach.md)   
 [IDebugDocumentHelper-Schnittstelle](../../winscript/reference/idebugdocumenthelper-interface.md)