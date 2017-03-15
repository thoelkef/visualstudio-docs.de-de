---
title: "IDebugDocumentPosition2::GetRange | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentPosition2::GetRange"
helpviewer_keywords: 
  - "IDebugDocumentPosition2::GetRange"
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentPosition2::GetRange
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Bereich für diese Position des Dokuments ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```c#  
int GetRange(   
   TEXT_POSITION[] pBegPosition,  
   TEXT_POSITION[] pEndPosition  
);  
```  
  
#### Parameter  
 `pBegPosition`  
 \[in, out\]  Eine [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) Struktur, die mit der Anfangsposition gefüllt wird.  Legen Sie dieses Argument mit einem NULL\-Wert fest, wenn diese Informationen nicht benötigt werden.  
  
 `pEndPosition`  
 \[in, out\]  Eine [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) Struktur, die mit der Endposition gefüllt wird.  Legen Sie dieses Argument mit einem NULL\-Wert fest, wenn diese Informationen nicht benötigt werden.  
  
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
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)