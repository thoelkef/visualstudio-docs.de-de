---
title: "IDebugProcessQueryProperties::QueryProperty | Microsoft Docs"
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
  - "IDebugProcessQueryProperties::QueryProperty"
ms.assetid: 9a91707d-a590-44ef-b122-69d9816a7a79
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcessQueryProperties::QueryProperty
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Abfragen dieser Methode für einen angegebenen Eigenschaftswert des Debuggens Prozesses.  
  
## Syntax  
  
```cpp#  
HRESULT QueryProperty(  
   PROCESS_PROPERTY_TYPE  dwPropType,  
   VARIANT               *pvarPropValue);  
```  
  
```c#  
int QueryProperty(  
   enum_PROCESS_PROPERTY_TYPE dwPropType,  
   out object                 pvarPropValue);  
```  
  
#### Parameter  
 `dwPropType`  
 \[in\]  Die Definition der Eigenschaft abgefragt.  Folgende Werte sind möglich:  
  
-   PROCESS\_PROPERTY\_COMMAND\_LINE \= 1  
  
-   PROCESS\_PROPERTY\_CURRENT\_DIRECTORY \= 2  
  
-   PROCESS\_PROPERTY\_ENVIRONMENT\_VARIABLES \= 3  
  
 `pvarPropValue`  
 \[out\]  Der Wert der Eigenschaft.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode wird selten verwendet.  
  
## Siehe auch  
 [IDebugProcessQueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties.md)