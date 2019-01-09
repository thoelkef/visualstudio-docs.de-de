---
title: IApplicationDebuggerUI::BringDocumentToTop | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebuggerUI.BringDocumentToTop
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebuggerUI::BringDocumentToTop
ms.assetid: ef5fe1e7-4381-4409-a0d7-58f993abe84e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c77c87011c539e02f92aa2aedfdcd7659466d37
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096251"
---
# <a name="iapplicationdebuggeruibringdocumenttotop"></a>IApplicationDebuggerUI::BringDocumentToTop
Bringt das Fenster mit dem angegebenen Debug-Dokument oben im Debugger-Benutzeroberfläche.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT BringDocumentToTop(  
   IDebugDocumentText*  pddt  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pddt`  
 [in] Debuggen von Dokument, in der Debugger-Benutzeroberfläche in den Vordergrund zu bringen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_INVALIDARG`|Das Dokument ist nicht bekannt.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode bringt das Fenster, die mit dem angegebenen Debug-Dokument oben im Debugger-Benutzeroberfläche.  
  
## <a name="see-also"></a>Siehe auch  
 [IApplicationDebuggerUI-Schnittstelle](../../winscript/reference/iapplicationdebuggerui-interface.md)