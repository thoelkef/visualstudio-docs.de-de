---
title: "MESSAGETYPE | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MESSAGETYPE"
helpviewer_keywords: 
  - "MESSAGETYPE-enumeration"
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# MESSAGETYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt den Nachrichtentyp und den Grund dafür an.  
  
## Syntax  
  
```cpp#  
enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
typedef DWORD MESSAGETYPE;  
```  
  
```c#  
public enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
```  
  
## Mitglieder  
 MT\_OUTPUTSTRING  
 Gibt an, dass die Meldung im Ausgabefenster gesendet werden soll.  Dies ist `MT_MESSAGEBOX`aus gegenseitig aus.  
  
 MT\_MESSAGEBOX  
 Gibt an, dass die Meldung in einem Meldungsfeld angezeigt werden soll.  Dies ist `MT_OUTPUTSTRING`aus gegenseitig aus.  
  
 MT\_TYPE\_MASK  
 Ein Masken des Ziels für, um die Meldung zu suchen.  
  
 MT\_REASON\_EXCEPTION  
 Gibt an, dass ein Meldungsfeld aufgrund einer Ausnahme angezeigt wird.  Dies ist `MT_REASON_TRACEPOINT`aus gegenseitig aus.  
  
 MT\_REASON\_TRACEPOINT  
 Gibt an, dass ein Meldungsfeld aufgrund des Schlagens eines Ablaufverfolgungspunkts angezeigt wird.  Hierbei handelt es sich gegenseitig aus `MT_REASON_EXCEPTION`soll.  
  
 MT\_REASON\_MASK  
 Ein Masken, mit dem der Wert des Grunds für die Meldung zu suchen, die angezeigt wird.  
  
## Hinweise  
 Diese Werte werden von den [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) und [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)\-Methode zurückgegeben.  
  
 Einer der Werte von Grund auf der Ausgabe kann mit einem Werte mit dem bitweisen `OR`kombiniert werden.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)   
 [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)