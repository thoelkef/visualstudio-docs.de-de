---
title: "CONSTRUCTOR_ENUM | Microsoft Docs"
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
  - "CONSTRUCTOR_ENUM"
helpviewer_keywords: 
  - "CONSTRUCTOR_ENUM-enumeration"
ms.assetid: 6d335b2c-66bc-460c-a4a6-4f3f1b697c2c
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# CONSTRUCTOR_ENUM
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Wählt verschiedene Arten von Konstruktoren aus.  
  
## Syntax  
  
```cpp#  
typedef enum ConstructorMatchOptions {   
   crAll       = 0,  
   crNonStatic = 1,  
   crStatic    = 2  
} CONSTRUCTOR_ENUM;  
```  
  
```c#  
public enum ConstructorMatchOptions {   
   crAll       = 0,  
   crNonStatic = 1,  
   crStatic    = 2  
};  
```  
  
## Mitglieder  
 crAll  
 Wählt alle Konstruktoren aus.  
  
 crNonStatic  
 Wählt einen nicht statischen Konstruktoren aus.  
  
 crStatic  
 Wählt statische Konstruktoren aus.  
  
## Hinweise  
 Übergabe als Argument an die [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)\-Methode.  
  
## Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)