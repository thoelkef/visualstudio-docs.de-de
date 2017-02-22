---
title: "IDebugProviderProgramNode2::UnmarshalDebuggeeInterface | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProviderProgramNode2::UnmarshalDebuggeeInterface"
helpviewer_keywords: 
  - "IDebugProviderProgramNode2::UnmarshalDebuggeeInterface"
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft eine angegebene Schnittstelle über Prozessgrenzen hinweg.  
  
## Syntax  
  
```cpp  
HRESULT UnmarshalDebuggeeInterface(  
   REFIID riid,  
   void** ppvObject  
);  
```  
  
```c#  
int UnmarshalDebuggeeInterface(  
   ref Guid   riid,  
   out IntPtr ppvObject  
);  
```  
  
#### Parameter  
 `riid`  
 \[in\]  GUID der Schnittstelle abzurufen.  
  
 `ppvObject`  
 \[out\]  Gibt das Objekt zurück, das die gewünschte Schnittstelle implementiert.  \[C\+\+\] kann es sich direkt auf die gewünschte Schnittstellentyp umgewandelt werden.  \[C\#\] Verwenden Sie die <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A>\-Methode, um die gewünschte Schnittstelle abzurufen.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode wird verwendet, wenn das Debugmodul in den [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Prozessbereich ausgeführt wird und das Programm, das gedebuggt wird, in seinen eigenen Prozessbereich ausgeführt wird.  
  
## Siehe auch  
 [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)