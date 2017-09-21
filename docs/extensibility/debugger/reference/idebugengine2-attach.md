---
title: "IDebugEngine2::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::Attach"
helpviewer_keywords: 
  - "IDebugEngine2::Attach"
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugEngine2::Attach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Fügt eine Debug\- Modul \(DE\) in ein Programm oder Programme an.  Wird vom Debugbuild Manager der Sitzung \(SDM\), wenn die Ausführung DE prozessintern zum SDM ist.  
  
## Syntax  
  
```cpp#  
HRESULT Attach(   
   IDebugProgram2**      pProgram,  
   IDebugProgramNode2**  rgpProgramNodes,  
   DWORD                 celtPrograms,  
   IDebugEventCallback2* pCallback,  
   ATTACH_REASON         dwReason  
);  
```  
  
```c#  
int Attach(   
   IDebugProgram2[]     pProgram,  
   IDebugProgramNode2[] rgpProgramNodes,  
   uint                 celtPrograms,  
   IDebugEventCallback2 pCallback,  
   Enum_ATTACH_REASON   dwReason  
);  
```  
  
#### Parameter  
 `pProgram`  
 \[in\]  Ein Array [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)\-Objekte, die die Software darstellen, die angefügt werden soll.  Hierbei handelt es programme Port.  
  
 `rgpProgramNodes`  
 \[in\]  Ein Array von Objekten, die [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) Knoten Programmierung darstellen, eines für jedes Programm.  Die Programmierung der Knoten in diesem Array stellen die gleichen wie in Programme `pProgram`dar.  Die Knoten Programm angegeben sind, damit DE Programme identifizieren kann, um angefügt werden soll.  
  
 `celtPrograms`  
 \[in\]  Anzahl von Programmen und\/oder Programm in den Knoten `pProgram` und `rgpProgramNodes` Arrays.  
  
 `pCallback`  
 \[in\]  Das Debuggen von Ereignissen verwendet werden soll [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)\-Objekt in den SDM zu senden.  
  
 `dwReason`  
 \[in\]  Ein Wert aus der [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md)\-Enumeration, der den Grund für das Anfügen dieser Programme angibt.  Weitere Informationen finden Sie im Abschnitt "Hinweise".  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Drei Gründe sprechen für das Anfügen an ein Programm wie folgt:  
  
-   DE`ATTACH_REASON_LAUNCH` gibt an, dass dem Programm angefügt werden, weil der Benutzer den Vorgang ausgelöst hat, der sie enthält.  
  
-   `ATTACH_REASON_USER` gibt an, dass der Benutzer explizit angefordert hat, DE zu einem Programm \(oder den Prozess anzufügen, der ein Programm enthält\).  
  
-   DE gibt`ATTACH_REASON_AUTO` Anfügen an ein bestimmtes Programm, da es bereits andere Programme in einem bestimmten Prozess gedebuggt wird.  Dies wird auch selbstklebend aufgerufen.  
  
 Wenn diese Methode aufgerufen wird, muss diese Ereignisse DE nacheinander senden:  
  
1.  [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) \(sofern es noch nicht für eine bestimmte Instanz des Debugmoduls gesendet wurden\)  
  
2.  [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
3.  [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)  
  
 Wenn der Grund für das Anfügen `ATTACH_REASON_LAUNCH`ist, muss das DE [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)\-Ereignis senden.  
  
 Sobald das DE [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) entsprechend dem Objekt abrufen, das Programm gedebuggt wird, kann es für jede private Schnittstelle abgefragt werden.  
  
 Bevor Sie die Methoden eines Programms `pProgram` Knotens im angegebenen Array oder `rgpProgramNodes`aufruft, sollte der Identitätswechsel auf der `IDebugProgram2`\-Schnittstelle nach Bedarf aktiviert sind, die den Knoten Programm darstellt.  Normalerweise diesem Schritt ist jedoch nicht erforderlich.  Weitere Informationen finden Sie unter [Sicherheitsprobleme](../../../extensibility/debugger/security-issues.md).  
  
## Siehe auch  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)