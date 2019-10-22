---
title: 'Idebugapplication:: kreateasyncdebugoperation | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.CreateAsyncDebugOperation
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::CreateAsyncDebugOperation
ms.assetid: bc32b101-6364-4498-8458-bd5f3ab5ad94
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1feb8207fb7e7a7faf4427be189c4952139ef32c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575558"
---
# <a name="idebugapplicationcreateasyncdebugoperation"></a>IDebugApplication::CreateAsyncDebugOperation
Bietet asynchronen Zugriff auf einen angegebenen synchronen Debugvorgang.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT CreateAsyncDebugOperation(  
   IDebugSyncOperation*    psdo,  
   IDebugAsyncOperation**  ppado  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `psdo`  
 in Das synchrone Debug-Vorgangs Objekt.  
  
 `ppado`  
 vorgenommen Das asynchrone Debug Operation-Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ermöglicht Sprachmodulen das asynchrone Auswerten von Ausdrücken ohne explizite Synchronisierung mit dem Debuggerthread. Weitere Informationen finden Sie unter [idebugsyncoperation-Schnittstelle](../../winscript/reference/idebugsyncoperation-interface.md) und [idebugasyncoperation-Schnittstelle](../../winscript/reference/idebugasyncoperation-interface.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Idebugapplication-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)    
 [Idebugsyncoperation-Schnittstelle](../../winscript/reference/idebugsyncoperation-interface.md)    
 [IDebugAsyncOperation-Schnittstelle](../../winscript/reference/idebugasyncoperation-interface.md)