---
title: 'IActiveScriptSiteDebug32:: getdocumentcontextfromposition | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53348dff-35a6-4303-b263-90c10af06bf3
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 7acbe2a5741fa94ac42470a85803d1720e0a8fa1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574846"
---
# <a name="iactivescriptsitedebug32getdocumentcontextfromposition"></a>IActiveScriptSiteDebug32:: getdocumentcontextfromposition
Wird von der Sprach-Engine verwendet, um `IDebugCodeContext::GetSourceContext` zu delegieren.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetDocumentContextFromPosition(  
   DWORD_PTR                dwSourceContext,  
   ULONG                    uCharacterOffset,  
   ULONG                    uNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwSourceContext`  
 in Der Quell Inhalt, der für `ParseScriptText` oder `AddScriptlet` bereitgestellt wird.  
  
 `uCharacterOffset`  
 in Zeichen Offset relativ zum Anfang des Skript Blocks oder Scriptlet.  
  
 `uNumChars`  
 in Anzahl der Zeichen in diesem Kontext.  
  
 `ppsc`  
 vorgenommen Der Dokument Kontext, der diesem Zeichen Positions Bereich entspricht.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Sprachmodule verwenden diese Methode, um `IDebugCodeContext::GetSourceContext` zu delegieren.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptSiteDebug32-Schnittstelle](../../winscript/reference/iactivescriptsitedebug32-interface.md)