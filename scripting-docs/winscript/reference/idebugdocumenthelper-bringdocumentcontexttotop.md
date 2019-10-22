---
title: 'Idebugdocumenthelper:: bringdocumentcontexttoptop | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.BringDocumentContextToTop
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::BringDocumentContextToTop
ms.assetid: cf9751c5-e9b7-45c6-b084-3f3873dbf01d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 63b55844c260f693ab5d89ecd564ed6b6ecd32d6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577022"
---
# <a name="idebugdocumenthelperbringdocumentcontexttotop"></a>IDebugDocumentHelper::BringDocumentContextToTop
Führt einen Kontext dieses Dokuments an der obersten Position der Debugger-Benutzeroberfläche.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT BringDocumentContextToTop(  
   IDebugDocumentContext*  pddc  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pddc`  
 Dokument Kontext, der in der Benutzeroberfläche des Debuggers oben angezeigt werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Mit dieser Methode wird ein Kontext dieses Dokuments in der Benutzeroberfläche des Debuggers am oberen Rand angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentHelper-Schnittstelle](../../winscript/reference/idebugdocumenthelper-interface.md)