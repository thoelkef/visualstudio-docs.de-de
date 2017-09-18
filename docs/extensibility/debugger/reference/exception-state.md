---
title: "EXCEPTION_STATE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EXCEPTION_STATE"
helpviewer_keywords: 
  - "EXCEPTION_STATE-enumeration"
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# EXCEPTION_STATE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt den Ausnahmezustand an.  
  
## Syntax  
  
```cpp#  
enum enum_EXCEPTION_STATE {   
   EXCEPTION_NONE                          = 0x0000,  
   EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,  
   EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,  
   EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,  
   EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,  
   EXCEPTION_STOP_ALL                      = 0x00FF,  
   EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,  
  
   // These are for exception types only  
   EXCEPTION_CODE_SUPPORTED                = 0x1000,  
   EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,  
   EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,  
   EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,  
  
   // These are no longer used  
   EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,  
   EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,  
   EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,  
   EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,  
};  
typedef DWORD EXCEPTION_STATE;  
```  
  
```c#  
public enum enum_EXCEPTION_STATE {   
   EXCEPTION_NONE                          = 0x0000,  
   EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,  
   EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,  
   EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,  
   EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,  
   EXCEPTION_STOP_ALL                      = 0x00FF,  
   EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,  
  
   // These are for exception types only  
   EXCEPTION_CODE_SUPPORTED                = 0x1000,  
   EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,  
   EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,  
   EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,  
  
   // These are no longer used  
   EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,  
   EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,  
   EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,  
   EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,  
};  
```  
  
## Mitglieder  
 EXCEPTION\_NONE  
 Beenden Sie keine Verbindung mit der Ausnahme ausgelöst.  
  
 EXCEPTION\_STOP\_FIRST\_CHANCE  
 Anhalten an den ersten Auslösen der Ausnahme.  Wenn ein Ausnahmeereignis wird, gibt dieses Flag an, dass das Ausnahmeereignis der ersten Chance ein Ausnahmeereignis ist.  
  
 EXCEPTION\_STOP\_SECOND\_CHANCE  
 Beenden Sie am Schwarzbrennen der Ausnahme ausgelöst.  Wenn ein Ausnahmeereignis beschreibend, gibt an, dass das Ausnahmeereignis ein Ausnahmeereignis der zweiten Chance ist.  
  
 EXCEPTION\_STOP\_USER\_FIRST\_CHANCE  
 Lauschen an den ersten Auslösen einer Benutzermodus ausnahme auf.  Wenn ein Ausnahmeereignis beschreibend, gibt an, dass das Ausnahmeereignis der ersten Chance ein Ereignis Benutzer\-Ausnahme ist.  
  
 EXCEPTION\_STOP\_USER\_UNCAUGHT  
 Lauschen auf, wenn eine Benutzermodus ausnahme nicht abgefangen wird.  Wenn ein Ausnahmeereignis beschreibend, gibt an, dass das Ausnahmeereignis ein Ereignis ausnahme Benutzermodus nicht abgefangen wird.  
  
 EXCEPTION\_STOP\_ALL  
 Beenden einer Ausnahme.  Nicht verwendet, wenn ein Ausnahmeereignis beschrieben wird.  
  
 \_BE\_CONTINUED EXCEPTION\_CAN NOT  
 Wenn ein Ausnahmeereignis beschreibend, gibt an, dass die Ausnahme nicht fortgesetzt werden kann.  
  
 EXCEPTION\_CODE\_SUPPORTED  
 Gibt an, dass die Ausnahme den Code verfügt, der dies unterstützt.  Wird beim Auftreten einer Ausnahme angezeigt wird  
  
 EXCEPTION\_CODE\_DISPLAY\_IN\_HEX  
 Gibt an, dass der angegebenen Ausnahmecode in hexadezimalen Zahlen angezeigt werden soll.  Wird beim Auftreten einer Ausnahme angezeigt wird.  
  
 EXCEPTION\_JUST\_MY\_CODE\_SUPPORTED  
 Gibt an, dass der angegebenen Ausnahmecode JustMyCode unterstützt.  Wird beim Auftreten einer Ausnahme angezeigt wird.  
  
 EXCEPTION\_MANAGED\_DEBUG\_ASSISTANT  
 Gibt an, dass der Debugger Code verwaltete Ausnahmen behandeln soll.  Wenn nicht festgelegt, werden die standardmäßigen Debugger die Ausnahmen.  Dies wird an die Methode übergeben [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) verwendet und nicht in der [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md) Struktur.  
  
 EXCEPTION\_STOP\_FIRST\_CHANCE\_USE\_PARENT  
 VERALTET. USE, TUN NOT  
  
 EXCEPTION\_STOP\_SECOND\_CHANCE\_USE\_PARENT  
 VERALTET. USE, TUN NOT  
  
 EXCEPTION\_STOP\_USER\_FIRST\_CHANCE\_USE\_PARENT  
 VERALTET. USE, TUN NOT  
  
 EXCEPTION\_STOP\_USER\_SECOND\_CHANCE\_USE\_PARENT  
 VERALTET. USE, TUN NOT  
  
## Hinweise  
 Wird als `dwState`\-Member der [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md) Struktur, um den Zustand der Ausnahme und was über die sie ausgeführt werden können.  
  
 Diese Werte werden auch zur [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)\-Methode übergeben, um den Zustand aller Ausnahmen festzulegen.  
  
 Diese Flags werden mit einem bitweisen OR\-Operation kombiniert werden.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)