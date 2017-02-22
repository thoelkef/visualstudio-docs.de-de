---
title: "IDebugProgramPublisher2::PublishProgram | Microsoft Docs"
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
  - "IDebugProgramPublisher2::PublishProgram"
helpviewer_keywords: 
  - "IDebugProgramPublisher2::PublishProgram"
ms.assetid: 92ff63f0-e869-4040-b3ae-b2c899e708ff
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramPublisher2::PublishProgram
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode stellt ein Programm für Module Debuggen DES \(Debuggen\) und den Manager der Sitzung bereit.  
  
## Syntax  
  
```cpp  
HRESULT PublishProgram(  
   CONST_GUID_ARRAY Engines,  
   LPCOLESTR        szFriendlyName,  
   IUnknown*        pDebuggeeInterface  
);  
```  
  
```c#  
int PublishProgram(  
   CONST_GUID_ARRAY Engines,  
   string           szFriendlyName,  
   object           pDebuggeeInterface  
);  
```  
  
#### Parameter  
 `Engines`  
 \[in\]  Ein Array von GUIDs für DES, die diesem Programm starten oder angefügt werden kann.  
  
 `szFriendlyName`  
 \[in\]  Anzeigename für das Programm \(dies wird in den Menüs oder Dialogfeldern, die dem Benutzer angezeigt werden\).  
  
 `pDebuggeeInterface`  
 \[in\]  `IUnknown`\-Schnittstelle für das Programm \(z. B. ein Cookie wird dieser Wert verwendet, um das Programm eindeutig identifiziert. „wird der gleiche Wert“ Aufheben der Veröffentlichung des Programms verwendet\)  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 So erstellen Sie ein Programm nicht mehr bereitstellen, müssen Sie zum Debuggen [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md).  
  
## Siehe auch  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)