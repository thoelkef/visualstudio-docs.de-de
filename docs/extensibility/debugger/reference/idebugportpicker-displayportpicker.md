---
title: "IDebugPortPicker::DisplayPortPicker | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DisplayPortPicker"
  - "IDebugPortPicker::DisplayPortPicker"
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortPicker::DisplayPortPicker
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Zeigt das angegebene Dialogfeld an, das es dem Benutzer ermöglicht, einen Port auszuwählen.  
  
## Syntax  
  
```cpp#  
HRESULT DisplayPortPicker(  
   HWND hwndParentDialog,  
   BSTR* pbstrPortId  
);  
```  
  
```c#  
public int DisplayPortPicker(  
   int hwndParentDialog,  
   out string pbstrPortId  
);  
```  
  
#### Parameter  
 `hwndParentDialog`  
 \[in\]  Handle für das übergeordnete Dialogfeld.  
  
 `pbstrPortId`  
 \[out\]  Bezeichner des Anschlusses.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  Der Rückgabewert `S_FALSE` \(oder ein Rückgabewert von `S_OK` mit `BSTR` festgelegt `NULL`\) gibt an, dass der Benutzer auf **Abbrechen**geklickt hat.  
  
## Siehe auch  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)