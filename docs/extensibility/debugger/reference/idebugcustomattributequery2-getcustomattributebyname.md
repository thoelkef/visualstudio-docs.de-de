---
title: "IDebugCustomAttributeQuery2::GetCustomAttributeByName | Microsoft Docs"
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
  - "IDebugCustomAttributeQuery2::GetCustomAttributeByName"
helpviewer_keywords: 
  - "IDebugCustomAttributeQuery2::GetCustomAttributeByName"
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCustomAttributeQuery2::GetCustomAttributeByName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft die Bytes angegebene benutzerdefinierte Attribut für den Namen des benutzerdefinierten Attributs.  
  
## Syntax  
  
```cpp#  
HRESULT GetCustomAttributeByName(   
   LPCOLESTR pszCustomAttributeName,  
   BYTE*     ppBlob,  
   DWORD*    pdwLen  
);  
```  
  
```c#  
int GetCustomAttributeByName(  
   [In] string        pszCustomAttributeName,   
   [In, Out] byte[]   ppBlob,   
   [In, Out] ref uint pdwLen  
);  
```  
  
#### Parameter  
 `pszCustomAttributeName`  
 \[in\]  Eine Zeichenfolge, die den Namen des benutzerdefinierten Attributs, das gesucht werden soll.  
  
 `ppBlob`  
 \[in, out\]  Ein Array, das die benutzerdefinierte Attributdaten gefüllt wird.  
  
 `pdwLen`  
 \[in, out\]  Gibt die maximale Anzahl von Bytes an, die im `ppBlob` Array zurückzukehren und gibt die Anzahl von Bytes zurück, die sich tatsächlich in das Array geschrieben werden.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück oder gibt S\_FALSE zurück, wenn das benutzerdefinierte Attribut nicht vorhanden ist.  Andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Legen Sie den `ppBlob`\-Parameter zu einem NULL\-Wert fest, um die Anzahl der Attributdaten verfügbar.  Anschließend ordnen Sie ein Array, und übergeben Sie das Array in `ppBlob` für den Parameter.  
  
 Die Attributdaten stellen die unformatierten Daten des benutzerdefinierten Attributs dar.  
  
 Wenn die `ppBlob` und `pdwLen`\-Parameter zu einem NULL\-Wert festgelegt sind, kann diese Methode verwendet werden, um zu bestimmen, ob das benutzerdefinierte Attribut lediglich vorhanden ist.  Eine einfachere Möglichkeit besteht darin, die jedoch [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)\-Methode aufzurufen.  
  
## Siehe auch  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)