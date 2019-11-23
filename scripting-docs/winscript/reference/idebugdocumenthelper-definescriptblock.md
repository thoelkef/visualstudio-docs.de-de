---
title: Idebugdocumenthelper::D efinescriptblock | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 6a2418b18e80ac86b672b3847f24ef9084ed1252
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576978"
---
# <a name="idebugdocumenthelperdefinescriptblock"></a>IDebugDocumentHelper::DefineScriptBlock
Gibt dem Hilfsprogramm an, dass ein bestimmter Bereich von Zeichen ein Skriptblock ist, der von der angegebenen Skript-Engine verarbeitet wird.  
  
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
 in Der Speicherort des Skript Blocks.  
  
 `cChars`  
 in Anzahl der Zeichen im Skriptblock.  
  
 `pas`  
 in Die Skript-Engine für diesen Skriptblock.  
  
 `fScriptlet`  
 in Flag, das angibt, ob der Skriptblock ein Scriptlet ist.  
  
 `pdwSourceContext`  
 vorgenommen Der Quell Kontext für den Skriptblock.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Ein intelligenter Host kann diese Methode verwenden, wenn seine Dokumente eingebettete Skriptblöcke enthalten. Eine Sprach-Engine kann diese Methode verwenden, wenn Ihr Code eingebettete Skripts für andere Sprachen enthält.  
  
 Das Skript Modul ist für alle Syntax Farben und Code Kontext Suchvorgänge im Skriptblock verantwortlich.  
  
 Die `DefineScriptBlock`-Methode sollte aufgerufen werden, nachdem der Text hinzugefügt wurde (z. b. mit der `IDebugDocumentHelper::AddDBCSText`-Methode), aber bevor der Skriptblock analysiert wurde (z. b. mit der `IActiveScriptParse ::ParseScriptText`-Methode).  
  
## <a name="see-also"></a>Siehe auch  
 [Idebugdocumenthelper-Schnittstelle](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)