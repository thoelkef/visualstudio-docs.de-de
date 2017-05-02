---
title: "IDebugDocumentHelper::DefineScriptBlock | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.DefineScriptBlock
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::DefineScriptBlock"
ms.assetid: e4120377-f04f-44b1-950b-2beba06c9c12
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::DefineScriptBlock
Gibt die Hilfe an, dass ein bestimmter Bereich von Zeichen ein Skriptblock ist, der durch das angegebene Skriptmodul behandelt wird.  
  
## Syntax  
  
```  
HRESULT DefineScriptBlock(  
   ULONG           ulCharOffset,  
   ULONG           cChars,  
   IActiveScript*  pas,  
   BOOL            fScriptlet,  
   DWORD_PTR*      pdwSourceContext  
);  
```  
  
#### Parameter  
 `ulCharOffset`  
 \[in\] Speicherort Start des Skriptblocks.  
  
 `cChars`  
 \[in\] Anzahl von Zeichen im Skriptblock.  
  
 `pas`  
 \[in\] Das Skriptmodul für diesen Skriptblock.  
  
 `fScriptlet`  
 \[in\] Der Funktion, das angibt, ob der Skriptblock ein Skriptlet ist.  
  
 `pdwSourceContext`  
 \[out\] Der Quellkontext für den Skriptblock.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Ein Smarthost kann diese Methode verwenden, wenn die Dokumente eingebettete Skriptblöcke enthalten.  Ein Sprachmodul kann diese Methode verwenden, wenn der Code eingebettete Skripts für andere Sprachen enthält.  
  
 Das Skriptmodul ist für alle Syntaxfarben\- und Codekontextsuchen im Skriptblock zuständig.  
  
 Die `DefineScriptBlock`\-Methode sollte aufgerufen werden, nachdem der Text hinzugefügt wurde, \(beispielsweise mithilfe der `IDebugDocumentHelper::AddDBCSText`\-Methode\) jedoch vor dem Skriptblock analysiert wurde \(beispielsweise, mit der `IActiveScriptParse ::ParseScriptText`\-Methode\).  
  
## Siehe auch  
 [IDebugDocumentHelper\-Schnittstelle](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)