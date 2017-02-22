---
title: "IntelliSenseHostFlags | Microsoft Docs"
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
  - "IntellisenseHostFlags"
helpviewer_keywords: 
  - "IntelliSense, IntellisenseHostFlags-enumeration"
  - "IntellisenseHostFlags-enumeration"
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IntelliSenseHostFlags
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gibt Flags für IntelliSense\-Host.  
  
## Syntax  
  
```cpp#  
enum IntellisenseHostFlags  
{  
    IHF_READONLYCONTEXT      = 0x00000001  
    IHF_NOSEPARATESUBJECT    = 0x00000002  
    IHF_SINGLELINESUBJECT    = 0x00000004  
    IHF_FORCECOMMITTOCONTEXT = 0x00000008  
    IHF_OVERTYPE             = 0x00000010  
};  
```  
  
#### Parameter  
  
|Mitglieder|Beschreibung|  
|----------------|------------------|  
|`IHF_READONLYCONTEXT`|Kontextpuffer ist schreibgeschützt.|  
|`IHF_NOSEPARATESUBJECT`|Der Text kein Thema. Kontextpuffer enthält die IntelliSense\-Ziel \(impliziert `!IHF_READONLYCONTEXT`\).|  
|`IHF_SINGLELINESUBJECT`|Betreff ist keine multi\-Befehlszeile\-fähig.|  
|`IHF_FORCECOMMITTOCONTEXT`|Wie in `CanCommitIntoReadOnlyBuffer`.|  
|`IHF_OVERTYPE`|Bearbeiten \(im Betreff oder Kontextmenü\) sollte im Überschreibmodus erfolgen.|  
  
## Anforderungen  
 SingleFileeditor.idl  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.TextManager.Interop>