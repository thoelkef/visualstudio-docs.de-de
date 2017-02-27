---
title: "IDebugProcessSecurity::GetUserName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProcessSecurity::GetUserName"
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugProcessSecurity::GetUserName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Benutzernamen des Anschlusslieferanten ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetUserName(  
    BSTR *pbstrUserName  
);  
```  
  
```c#  
int GetUserName (  
    string pbstrUserName  
);  
```  
  
#### Parameter  
 `pbstrUserName`  
 \[out\]  Eine Zeichenfolge, die den Benutzernamen enthält.  
  
## Rückgabewert  
 Wenn die Methode erfolgreich ausgeführt, gibt sie `S_OK`zurück.  Andernfalls gibt jedoch einen Fehlercode zurück.  
  
## Hinweise  
 `GetUserName` gibt den Benutzernamen zurück, der in der **BenutzernameAn den Prozess anhängen** Spalte des Dialogfelds angezeigt wird.  Um das Dialogfeld anzuzeigen, klicken Sie auf **An den Prozess anhängenAn den Prozess anhängen** im Menü **Extras**[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] in der integrierten Entwicklungsumgebung \(IDE\).  
  
## Siehe auch  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)