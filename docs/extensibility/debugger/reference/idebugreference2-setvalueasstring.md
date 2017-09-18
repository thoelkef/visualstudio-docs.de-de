---
title: "IDebugReference2::SetValueAsString | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugReference2::SetValueAsString"
helpviewer_keywords: 
  - "IDebugReference2::SetValueAsString"
ms.assetid: 9a508ced-fd54-44f5-bb42-ec15c80384d7
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugReference2::SetValueAsString
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Legt den Wert eines Verweises aus einer Zeichenfolge fest.  Für zukünftige Verwendung reserviert.  
  
## Syntax  
  
```cpp#  
HRESULT SetValueAsString (   
   LPCOLESTR pszValue,  
   DWORD     dwRadix,  
   DWORD     dwTimeout  
);  
```  
  
```c#  
int SetValueAsString (   
   string pszValue,  
   uint   dwRadix,  
   uint   dwTimeout  
);  
```  
  
#### Parameter  
 `pszValue`  
 \[in\]  Der Wert wird als Zeichenfolge.  
  
 `dwRadix`  
 \[in\]  Die Basis verwendet werden soll, wenn alle numerischen Daten formatiert werden.  
  
 `dwTimeout`  
 \[in\]  Maximale Zeit in Millisekunden, bevor der Rückgabe dieser Methode zu warten.  `INFINITE` verwenden, um unbegrenzt zu warten.  
  
## Rückgabewert  
 Gibt immer `E_NOTIMPL` zurück.  
  
## Siehe auch  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)