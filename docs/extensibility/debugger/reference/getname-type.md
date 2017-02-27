---
title: "GETNAME_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GETNAME_TYPE"
helpviewer_keywords: 
  - "GETNAME_TYPE-enumeration"
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# GETNAME_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt den Typ der Name der Dateien an, der abgerufen werden soll.  
  
## Syntax  
  
```cpp#  
enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
typedef DWORD GETNAME_TYPE;  
```  
  
```c#  
public enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
```  
  
## Mitglieder  
 GN\_NAME  
 Gibt einen Anzeigenamen des Dokuments oder des Kontexts an.  
  
 GN\_FILENAME  
 Gibt den vollständigen Pfad des Dokuments oder des Kontexts an.  
  
 GN\_BASENAME  
 Gibt einen Basisdateinamen anstelle eines vollständigen Pfad des Dokuments oder des Kontexts an.  
  
 GN\_MONIKERNAME  
 Gibt einen eindeutigen Namen des Dokuments oder des Kontexts in Form eines Monikers an.  
  
 GN\_URL  
 Gibt einen URL\-Namen des Dokuments oder des Kontexts an.  
  
 GN\_TITLE  
 Gibt einen Titel des Dokuments, sofern vorhanden.  
  
 GN\_STARTPAGEURL  
 Ruft die Startseite URL für Prozesse ab.  
  
## Hinweise  
 Diese Werte werden als Parameter an den [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md), [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)und [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)\-Methode übergeben, um anzugeben, welcher Art der Name zurückgegeben werden soll.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)