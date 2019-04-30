---
title: 'Idebugdocumenthost:: Oncreatedocumentcontext | Microsoft-Dokumentation'
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
ms.openlocfilehash: a3b614cdc6aad17ab3a4f6e83927b59390005ac2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62971094"
---
# <a name="idebugdocumenthostoncreatedocumentcontext"></a>IDebugDocumentHost::OnCreateDocumentContext
Benachrichtigt den Host, ein neuen Dokumentkontext erstellt wird und der Host kann optional einen unbekannten für den neuen Kontext steuernden zurückgeben.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT OnCreateDocumentContext(  
   IUnknown**  ppunkOuter  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppunkOuter`  
 [out] Ein Objekt, das den neuen Kontext steuert.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_NOTIMPL`|Der Host ist ein steuerndes Objekt nicht bereit.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ermöglicht den Host, den bereitgestellten Helper dokumentenkontexte neue Funktionalität hinzufügen. Diese Methode zurückgeben kann **E_NOTIMPL** oder ein null-äußeren Objekt, in dem Fall der Aufrufer dafür verantwortlich ist, den Kontext zu erstellen.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentHost-Schnittstelle](../../winscript/reference/idebugdocumenthost-interface.md)