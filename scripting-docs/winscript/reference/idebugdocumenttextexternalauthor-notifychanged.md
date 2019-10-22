---
title: 'Idebugdocumenttextexternalauthor:: notifychanged | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextExternalAuthor.NotifyChanged
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentTextExternalAuthor::NotifyChanged
ms.assetid: f0de7984-3a15-49e2-bd29-f768f34d2a4d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad02db80bd24a8a5ba96abaa61e85be9d69e553e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575955"
---
# <a name="idebugdocumenttextexternalauthornotifychanged"></a>IDebugDocumentTextExternalAuthor::NotifyChanged
Benachrichtigt den Host, dass sich die Dokument Quelle geändert hat.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT NotifyChanged();  
```  
  
#### <a name="parameters"></a>Parameter  
 Diese Methode nimmt keine Parameter an.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird von einem externen Editor aufgerufen, nachdem ein Datei basiertes debuggerdokument geändert und gespeichert wurde, um den Host zu benachrichtigen, dass sich die Dokument Quelle geändert hat. Der Host aktualisiert dann das Dokument aus der Quelldatei.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentTextExternalAuthor-Schnittstelle](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)