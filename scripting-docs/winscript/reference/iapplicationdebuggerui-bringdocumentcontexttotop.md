---
title: IApplicationDebuggerUI::BringDocumentContextToTop | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 890cc1b6c38f44c4140274dcaa19deff1fd276e2
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095510"
---
# <a name="iapplicationdebuggeruibringdocumentcontexttotop"></a>IApplicationDebuggerUI::BringDocumentContextToTop
Bringt das Fenster, die den angegebenen Dokument-Kontext oben in der Debugger-Benutzeroberfläche und führt einen Bildlauf durch das Fenster, um den Kontext.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT BringDocumentContextToTop(  
   IDebugDocumentContext*  pddc  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pddc`  
 [in] Dokumentkontext, der in der Debugger-Benutzeroberfläche in den Vordergrund zu bringen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_INVALIDARG`|Der Kontext anhand des `pddc` ist nicht bekannt.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode bringt das Fenster, die den angegebenen Dokument-Kontext oben in der Debugger-Benutzeroberfläche und führt einen Bildlauf durch das Fenster, um den Kontext.  
  
## <a name="see-also"></a>Siehe auch  
 [IApplicationDebuggerUI-Schnittstelle](../../winscript/reference/iapplicationdebuggerui-interface.md)