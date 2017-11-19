---
title: IDebugDocumentHost::OnCreateDocumentContext | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentHost.OnCreateDocumentContext
apilocation: scrobj.dll
helpviewer_keywords: IDebugDocumentHost::OnCreateDocumentContext
ms.assetid: 080c8604-cfd7-484e-a337-15040870e683
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 55598a4191d421d3aea01d27cc7991b70bd6a019
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthostoncreatedocumentcontext"></a>IDebugDocumentHost::OnCreateDocumentContext
Benachrichtigt den Host, dass ein neuer Dokumentenkontext erstellt wird und der Host kann optional einen unbekannten für den neuen Kontext steuernden zurückgeben.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
|`E_NOTIMPL`|Der Host stellt kein steuerndes Objekt bereit.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode kann der Host die Kontexte Helper bereitgestellte Dokument neue Funktionen hinzu. Diese Methode gelegten **E_NOTIMPL** oder ein null-äußeren Objekt, in dem Fall der Aufrufer für die Erstellung des Kontexts verantwortlich ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentHost-Schnittstelle](../../winscript/reference/idebugdocumenthost-interface.md)