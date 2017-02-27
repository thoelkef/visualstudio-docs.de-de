---
title: "IDebugProperty2::SetValueAsString | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::SetValueAsString"
helpviewer_keywords: 
  - "IDebugProperty2::SetValueAsString"
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProperty2::SetValueAsString
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Legt den Wert einer Eigenschaft einer angegebenen Zeichenfolge fest.  
  
## Syntax  
  
```cpp#  
HRESULT SetValueAsString (   
   LPCOLESTR pszValue,  
   UINT      nRadix,  
   DWORD     dwTimeout  
);  
```  
  
```c#  
int SetValueAsString (   
   string pszValue,  
   uint   nRadix,  
   uint   dwTimeout  
);  
```  
  
#### Parameter  
 `pszValue`  
 \[in\]  Eine Zeichenfolge, die den festzulegenden Wert enthält.  
  
 `nRadix`  
 \[in\]  Eine Basisklasse verwendet werden soll, wenn alle numerischen Daten interpretiert werden.  Dies kann 0 sein, die Basis automatisch bestimmt werden soll.  
  
 `dwTimeout`  
 \[in\]  Bevor der Rückgabe dieser Methode gibt die maximale Zeit in Millisekunden an, zu warten.  `INFINITE` verwenden, um unbegrenzt zu warten.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. gibt andernfalls Fehlercode zurück.  In der folgenden Tabelle werden weitere mögliche Werte an.  
  
|Wert|Beschreibung|  
|----------|------------------|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Die Zeichenfolge kann nicht in einen Eigenschaftswert konvertiert werden, oder der Eigenschaftswert kann nicht festgelegt werden.|  
|`E_SETVALUE_VALUE_IS_READONLY`|Die Eigenschaft ist schreibgeschützt.|  
  
## Siehe auch  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)