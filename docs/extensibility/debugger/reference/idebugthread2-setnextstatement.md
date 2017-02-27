---
title: "IDebugThread2::SetNextStatement | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugThread2::SetNextStatement"
helpviewer_keywords: 
  - "IDebugThread2::SetNextStatement"
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugThread2::SetNextStatement
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Legt den aktuellen Kontext des Codes Anweisungszeiger auf den angegebenen Wert fest.  
  
## Syntax  
  
```cpp#  
HRESULT SetNextStatement (   
   IDebugStackFrame2*  pStackFrame,  
   IDebugCodeContext2* pCodeContext  
);  
```  
  
```c#  
int SetNextStatement (   
   IDebugStackFrame2  pStackFrame,  
   IDebugCodeContext2 pCodeContext  
);  
```  
  
#### Parameter  
 `pStackFrame`  
 Für zukünftige Verwendung reserviert. Auf einem NULL\-Wert.  
  
 `pCodeContext`  
 \[in\]  Ein [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)\-Objekt, das den auszuführenden Code ungefähr beschreibt Speicherort und der Kontext.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  In der folgenden Tabelle werden weitere mögliche Werte an.  
  
|Wert|Beschreibung|  
|----------|------------------|  
|\_SET\_NEXT\_STATEMENT\_ON\_NONLEAF\_FRAME E\_CAN NOT|Die folgende Anweisung kann nicht in einem Stapelrahmen sein, der auf den Frame stapel tiefer liegt.|  
|\_SETIP\_TO\_DIFFERENT\_FUNCTION E\_CAN NOT|In der folgenden Anweisung wird nicht mit einem Rahmen im Stapel zugeordnet.|  
|\_SET\_NEXT\_STATEMENT\_ON\_EXCEPTION E\_CAN NOT|Einige Module können Debuggen der folgenden Anweisung nicht nach einer Ausnahme fest.|  
  
## Hinweise  
 Der Anweisungszeiger gibt die folgende Anweisung oder die Anweisung auszuführen.  Diese Methode wird verwendet, um eine Zeile des Quellcodes zu wiederholen oder Ausführung zu erzwingen, dass in einer anderen Funktion fortzufahren, z. B.  
  
## Siehe auch  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)