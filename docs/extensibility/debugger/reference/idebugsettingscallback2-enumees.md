---
title: "IDebugSettingsCallback2::EnumEEs | Microsoft Docs"
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
  - "IDebugSettingsCallback2::EnumEEs"
ms.assetid: 9f884c49-426f-461b-b547-9d909486e73f
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSettingsCallback2::EnumEEs
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Listet die verfügbaren Sprach\- und Anbieter die Ausdrucksauswertung angegebenen Bezeichner.  
  
## Syntax  
  
```cpp#  
HRESULT EnumEEs(  
   DWORD  celtBuffer,  
   GUID*  rgguidLang,  
   GUID*  rgguidVendor,  
   DWORD* pceltEEs  
);  
```  
  
```c#  
public int EnumEEs(  
   uint       celtBuffer,  
   ref Guid   rgguidLang,  
   ref Guid   rgguidVendor,  
   ref uint[] pceltEEs  
);  
```  
  
#### Parameter  
 `celtBuffer`  
 \[in\]  Die Anzahl der Elemente im Puffer `pceltEEs` .  
  
 `rgguidLang`  
 \[in, out\]  Eindeutiger Bezeichner für die Programmiersprache.  
  
 `rgguidVendor`  
 \[in, out\]  Eindeutiger Bezeichner für den Anbieter.  
  
 `pceltEEs`  
 \[in, out\]  Array von der Ausdrucksauswertung.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)