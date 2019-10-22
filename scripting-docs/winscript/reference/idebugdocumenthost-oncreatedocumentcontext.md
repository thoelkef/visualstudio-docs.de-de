---
title: 'Idebugdocumerthost:: onkreatedocumentcontext | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.OnCreateDocumentContext
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::OnCreateDocumentContext
ms.assetid: 080c8604-cfd7-484e-a337-15040870e683
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3fdfa64f66288cba47dec7c498db15238e55f954
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569113"
---
# <a name="idebugdocumenthostoncreatedocumentcontext"></a>IDebugDocumentHost::OnCreateDocumentContext
Benachrichtigt den Host, dass ein neuer Dokument Kontext erstellt wird, und ermöglicht es dem Host, optional ein kontrollierendes unbekanntes für den neuen Kontext zurückzugeben.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT OnCreateDocumentContext(  
   IUnknown**  ppunkOuter  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppunkOuter`  
 vorgenommen Ein-Objekt, das den neuen Kontext steuert.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_NOTIMPL`|Der Host stellt kein steuerndes Objekt bereit.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ermöglicht es dem Host, den von Hilfsprogrammen bereitgestellten Dokument Kontexten neue Funktionen hinzuzufügen. Diese Methode gibt möglicherweise **E_NOTIMPL** oder ein äußeres NULL-Objekt zurück. in diesem Fall ist der Aufrufer für die Erstellung des Kontexts verantwortlich.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentHost-Schnittstelle](../../winscript/reference/idebugdocumenthost-interface.md)