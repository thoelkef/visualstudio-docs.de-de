---
title: 'Iapplicationdebuggerui:: bringdocumenttoptop | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: b51e7b588750fc72e61840c4748c006eea732c22
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577792"
---
# <a name="iapplicationdebuggeruibringdocumenttotop"></a>IApplicationDebuggerUI::BringDocumentToTop
Führt das Fenster, das das angegebene debugdokument enthält, am oberen Rand der Debugger-Benutzeroberfläche.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT BringDocumentToTop(  
   IDebugDocumentText*  pddt  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pddt`  
 in Debuggen Sie das Dokument, um es in die Benutzeroberfläche des Debuggers zu verschieben.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_INVALIDARG`|Das Dokument ist nicht bekannt.|  
  
## <a name="remarks"></a>Hinweise  
 Mit dieser Methode wird das Fenster, das das angegebene debugdokument enthält, am oberen Rand der Debugger-Benutzeroberfläche angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [IApplicationDebuggerUI-Schnittstelle](../../winscript/reference/iapplicationdebuggerui-interface.md)