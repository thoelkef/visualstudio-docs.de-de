---
title: IDebugDocumentHelper::DefineScriptBlock | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentHelper.DefineScriptBlock
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentHelper::DefineScriptBlock
ms.assetid: e4120377-f04f-44b1-950b-2beba06c9c12
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b6ec86dacc2e3a8f3d9e28a6db744b778ff01eb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelperdefinescriptblock"></a>IDebugDocumentHelper::DefineScriptBlock
Gibt an für die Hilfe, ein bestimmter Bereich von Zeichen ein Skriptblock, der vom angegebenen Skript-Modul übernommen wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
 [in] Das Skriptmodul für dieses Skriptblocks.  
  
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
 Ein Smarthost kann diese Methode verwenden, wenn die Dokumente eingebettete Skriptblöcke enthalten. Ein Sprachmodul kann diese Methode verwenden, wenn der Code eingebettete Skripts für andere Sprachen enthält.  
  
 Das Skriptmodul ist verantwortlich für alle Syntax Färbung und Code Kontext Suchvorgänge im Skriptblock.  
  
 Die `DefineScriptBlock` Methode sollte aufgerufen werden, nachdem der Text hinzugefügt wurde (z. B. die `IDebugDocumentHelper::AddDBCSText` Methode), aber bevor Sie das Skript Anweisungsblock analysiert wurde (z. B. die `IActiveScriptParse ::ParseScriptText` Methode).  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentHelper-Schnittstelle](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)