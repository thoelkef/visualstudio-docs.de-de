---
title: "IDebugDisassemblyStream2::Seek | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDisassemblyStream2::Seek"
helpviewer_keywords: 
  - "IDebugDisassemblyStream2::Seek"
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDisassemblyStream2::Seek
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Verschiebt den Zeiger im Disassemblys lesen datenstrom eine festgelegte Anzahl von Anweisungen im Verhältnis zu einer angegebenen Position.  
  
## Syntax  
  
```cpp#  
HRESULT Seek(   
   SEEK_START          dwSeekStart,  
   IDebugCodeContext2* pCodeContext,  
   UINT64              uCodeLocationId,  
   INT64               iInstructions  
);  
```  
  
```c#  
int Seek(   
   enum_SEEK_START    dwSeekStart,  
   IDebugCodeContext2 pCodeContext,  
   ulong              uCodeLocationId,  
   long               iInstructions  
);  
```  
  
#### Parameter  
 `dwSeekStart`  
 \[in\]  Ein Wert aus der [SEEK\_START](../../../extensibility/debugger/reference/seek-start.md)\-Enumeration, der die relative Position angibt, Suchvorgängen Prozess zu starten.  
  
 `pCodeContext`  
 \[in\]  Das [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)\-Objekt, das den Kontext darstellt, dass der Code auch in Zusammenhang steht.  Dieser Parameter wird nur verwendet, wenn `dwSeekStart` \= `SEEK_START_CODECONTEXT`Andernfalls wird dieser Parameter ignoriert, und es kann ein NULL\-Wert sein.  
  
 `uCodeLocationId`  
 \[in\]  Der Bezeichner der Speicherort des Codes, dass der Suchvorgang in Zusammenhang steht.  Dieser Parameter wird verwendet, wenn `dwSeekStart` \= `SEEK_START_CODELOCID`Andernfalls wird dieser Parameter ignoriert und können auf 0 festgelegt werden.  Weitere Informationen finden Sie im Abschnitt " Hinweise " für die [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)\-Methode zum Speicherort der Code eine Beschreibung eines Bezeichners.  
  
 `iInstructions`  
 \[in\]  Die Anzahl der Anweisungen, die sich relativ zur Position angegeben in `dwSeekStart`verschoben werden soll.  Dieser Wert kann negativ sein, sich zurückzubewegen.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` zurück, wenn die Suche auf einen Zeitpunkt Position oberhalb der Liste verfügbarer Anweisungen hinaus war.  Andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Wenn die Suche zu einer Position vor dem Anfang der Liste, die Leseposition zur ersten Anweisung in der Liste festgelegt ist.  Wenn das Sehung wurde auf eine Position nach dem Ende der Liste, die Leseposition zur letzten Anweisung in der Liste festgelegt ist.  
  
## Siehe auch  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [SEEK\_START](../../../extensibility/debugger/reference/seek-start.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)