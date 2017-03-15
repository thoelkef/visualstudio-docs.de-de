---
title: "TEXT_DOC_ATTR_2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TEXT_DOC_ATTR_2"
helpviewer_keywords: 
  - "TEXT_DOC_ATTR_2-enumeration"
ms.assetid: 2333b33b-042b-4ac6-9ebe-e66f95f52f51
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# TEXT_DOC_ATTR_2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Beschreibt die Attribute eines Dokuments.  
  
## Syntax  
  
```cpp#  
typedef DWORD TEXT_DOC_ATTR_2;  
const TEXT_DOC_ATTR_2 TEXT_DOC_ATTR_READONLY_2 = 0x00000001;  
```  
  
```c#  
public const uint TEXT_DOC_ATTR_READONLY_2 = 0x00000001;  
```  
  
## Mitglieder  
 TEXT\_DOC\_ATTR\_READONLY\_2  
 Gibt an, dass das Dokument schreibgeschützt ist.  
  
## Hinweise  
  
> [!NOTE]
>  Dieser Wert wird nicht tatsächlich in der Assembly für C\# definiert.  Stattdessen müssen Sie die Definition der Quelldatei kopieren.  
  
 Übergabe als Argument an die [onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)\-Methode.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)