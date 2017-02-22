---
title: "IDebugCoreServer3::CreateInstanceInServer | Microsoft Docs"
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
  - "IDebugCoreServer3::CreateInstanceInServer"
helpviewer_keywords: 
  - "IDebugCoreServer3::CreateInstanceInServer"
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCoreServer3::CreateInstanceInServer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Erstellt eine Instanz eines Debugmoduls auf dem Server.  
  
## Syntax  
  
```cpp#  
HRESULT CreateInstanceInServer(  
   LPCWSTR  szDll,  
   WORD     wLangId,  
   REFCLSID clsidObject,  
   REFIID   riid,  
   void**   ppvObject  
);  
```  
  
```c#  
int CreateInstanceInServer(  
   string     szDll,   
   ushort     wLangID,   
   ref Guid   clsidObject,   
   ref Guid   riid,   
   out IntPtr ppvObject  
);  
```  
  
#### Parameter  
 `szDll`  
 \[in\]  Pfad zur DLL, die die CLSID implementiert `clsidObject` im angegebenen Parameter an.  Wenn dieses `NULL`ist, wird `CoCreateInstance`\-Funktion COM aufgerufen.  
  
 `wLangId`  
 \[in\]  Gebietsschema des Debugmoduls.  Dies kann 0 sein, wenn die [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)\-Methode nicht aufgerufen wird.  
  
 `clsidObject`  
 \[in\]  Debuggen CLSID des Moduls zu erstellen.  
  
 `riid`  
 \[in\]  bestimmte Schnittstellen\-ID Schnittstelle aus dem Klassenobjekt abzurufen.  
  
 `ppvObject`  
 \[out\]  `IUnknown`\-Schnittstelle des instanziierten Objekt.  Wandelt um oder marshallen Sie dieses Objekt auf die gewünschte Schnittstelle.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)