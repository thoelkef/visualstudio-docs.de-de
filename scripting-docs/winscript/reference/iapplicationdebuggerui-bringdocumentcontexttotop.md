---
title: 'Iapplicationdebuggerui:: bringdocumentcontextretop | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebuggerUI.BringDocumentContextToTop
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebuggerUI::BringDocumentContextToTop
ms.assetid: 7844217d-658b-42af-8d10-2714f4eded20
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8648a4377e901908df20cdb5f413ee73ede5c1a6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577808"
---
# <a name="iapplicationdebuggeruibringdocumentcontexttotop"></a>IApplicationDebuggerUI::BringDocumentContextToTop
Ruft das Fenster mit dem angegebenen Dokument Kontext am oberen Rand der Debugger-Benutzeroberfläche ab und führt einen Bildlauf zum Kontext durch.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT BringDocumentContextToTop(  
   IDebugDocumentContext*  pddc  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pddc`  
 in Dokument Kontext, der in der Benutzeroberfläche des Debuggers oben angezeigt werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_INVALIDARG`|Der durch `pddc` angegebene Kontext ist nicht bekannt.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ruft das Fenster mit dem angegebenen Dokument Kontext am oberen Rand der Debugger-Benutzeroberfläche auf und führt einen Bildlauf zum Kontext durch.  
  
## <a name="see-also"></a>Siehe auch  
 [IApplicationDebuggerUI-Schnittstelle](../../winscript/reference/iapplicationdebuggerui-interface.md)