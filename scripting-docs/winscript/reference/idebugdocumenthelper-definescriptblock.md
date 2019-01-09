---
title: Definescriptblock | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.DefineScriptBlock
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::DefineScriptBlock
ms.assetid: e4120377-f04f-44b1-950b-2beba06c9c12
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0037df270bc95faaba4d2f04cce65902d08dc6e9
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087996"
---
# <a name="idebugdocumenthelperdefinescriptblock"></a>IDebugDocumentHelper::DefineScriptBlock
Gibt an, das Hilfsprogramm, ein bestimmter Bereich von Zeichen einen Skriptblock, der von der angegebenen Skript-Engine verarbeitet wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT DefineScriptBlock(  
   ULONG           ulCharOffset,  
   ULONG           cChars,  
   IActiveScript*  pas,  
   BOOL            fScriptlet,  
   DWORD_PTR*      pdwSourceContext  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ulCharOffset`  
 [in] Speicherort der Beginn des Skriptblocks.  
  
 `cChars`  
 [in] Anzahl der Zeichen im Skriptblock.  
  
 `pas`  
 [in] Die Skript-Engine für die dieser Skriptblock.  
  
 `fScriptlet`  
 [in] Flag, die angibt, ob der Skriptblock Scriptlet ist.  
  
 `pdwSourceContext`  
 [out] Der Quellkontext für den Skriptblock.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Ein Smarthost kann diese Methode verwenden, wenn seine Dokumente eingebetteter Skriptblöcke enthalten. Eine Sprach-Engine kann diese Methode verwenden, wenn der Code eingebettete Skripts für andere Sprachen enthält.  
  
 Die Skript-Engine ist verantwortlich für alle Syntax Syntaxfarben und Kontext Suchvorgänge im Skriptblock.  
  
 Die `DefineScriptBlock` -Methode aufgerufen werden soll, nachdem der Text hinzugefügt wurde (z. B. die `IDebugDocumentHelper::AddDBCSText` Methode), aber bevor Sie das Skript Block analysiert wurde (z. B. die `IActiveScriptParse ::ParseScriptText` Methode).  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentHelper-Schnittstelle](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [Idebugdocumenthelper:: Adddbcstext](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)