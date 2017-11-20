---
title: IProcessDebugManager::CreateDebugDocumentHelper | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IProcessDebugManager.CreateDebugDocumentHelper
apilocation: pdm.dll
helpviewer_keywords: IProcessDebugManager::CreateDebugDocumentHelper
ms.assetid: d644e192-1bcc-4768-a91e-239cd920adcd
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0b57f941017a0eef7892d43be9ed0414645e55e0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iprocessdebugmanagercreatedebugdocumenthelper"></a>IProcessDebugManager::CreateDebugDocumentHelper
Erstellt ein neues Debug-Dokument-Hilfsprogramm für diese Anwendung an.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT CreateDebugDocumentHelper(  
   IUnknown*               punkOuter,  
   IDebugDocumentHelper**  pddh  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `punkOuter`  
 [in] Wenn das zurückgegebene Objekt ist zu aggregierenden `punkOuter` ist ein Schnittstellenzeiger für die Steuerung der `IUnknown`. Andernfalls ist er ein null-Zeiger.  
  
 `pddh`  
 [out] Das Debug-Dokument-Hilfsobjekt für diese Anwendung.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode erstellt ein neues Debug-Dokument-Hilfsprogramm für diese Anwendung.  
  
## <a name="see-also"></a>Siehe auch  
 [IProcessDebugManager-Schnittstelle](../../winscript/reference/iprocessdebugmanager-interface.md)