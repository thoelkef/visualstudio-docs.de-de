---
title: "IDebugDocumentPositionOffset2::GetRange | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugDocumentPositionOffset2::GetRange"
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentPositionOffset2::GetRange
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Bereich für die Position des aktuellen Dokuments ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetRange(  
   DWORD* pdwBegOffset,  
   DWORD* pdwEndOffset  
);  
```  
  
```c#  
public int GetRange(  
   ref uint pdwBegOffset,  
   ref uint pdwEndOffset  
);  
```  
  
#### Parameter  
 `pdwBegOffset`  
 \[in, out\]  Offset für die Anfangsposition des Bereichs.  Legen Sie diesen Parameter auf einen NULL\-Wert festgelegt, wenn diese Informationen nicht benötigt werden.  
  
 `pdwEndOffset`  
 \[in, out\]  Offset für die Endposition des Bereichs.  Legen Sie diesen Parameter auf einen NULL\-Wert festgelegt, wenn diese Informationen nicht benötigt werden.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Der Bereich, der in einer Dokumentsequenz Zeilenposition für einen Positionshaltepunkt angegeben wird, wird durch das Debugmodul \(DE\) voran für eine Anweisung zu suchen, die tatsächlich Code beiträgt.  Beachten Sie z. B. folgenden Code:  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 Zeile 5 enthält keinen Code in das Programm, das gedebuggt wird.  Wenn der Debugger den Haltepunkt auf Zeile 5 festgelegt, DE Vorwärts einen bestimmten für die erste Zeile gezeichnet suchen, die Code beiträgt, wird der Debugger einen Bereich angeben, der mögliche zusätzliche Zeilen enthält, würde sich in denen ein Haltepunkt ordnungsgemäß.  DE vorwärts würde dann über die Zeilen suchen, bis er eine Zeile mit einem Haltepunkt gründet annehmen konnte.  
  
## Siehe auch  
 [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)   
 [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)