---
title: "IDebugObject2::IsUserData | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject2::IsUserData"
helpviewer_keywords: 
  - "IDebugObject2::IsUserData-Methode"
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugObject2::IsUserData
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Bestimmt, ob das Objekt Benutzerdaten darstellt.  
  
## Syntax  
  
```cpp  
HRESULT IsUserData(  
   BOOL* pfUser  
);  
```  
  
```c#  
int IsUserData(  
   out int pfUser  
);  
```  
  
#### Parameter  
 `pfUser`  
 \[out\]  Gibt Wert ungleich 0 \(null\) zurück \(`TRUE`\), wenn das Objekt Benutzerdaten darstellt. \(null\)`FALSE`.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Benutzerdaten ist jedes Objekt, das Teil eines Moduls befindet, das als JustMyCode festgelegt ist \(eine vom Benutzer konfiguriert werden, die ein Modul sichtbar und daher als Benutzercode markiert\) in einer Stapelüberwachung.  
  
## Siehe auch  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)