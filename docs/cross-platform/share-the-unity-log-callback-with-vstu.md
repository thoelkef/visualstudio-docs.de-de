---
title: "Freigeben des Unity-Protokollr&#252;ckrufs f&#252;r VSTU | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "tgt-pltfrm-cross-plat"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
caps.latest.revision: 2
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 2
---
# Freigeben des Unity-Protokollr&#252;ckrufs f&#252;r VSTU
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio\-Tools für Unity registrieren einen Protokollrückruf bei Unity, damit dessen Konsole in Visual Studio gestreamt werden kann.  Wenn Ihre Editorskripts auch einen Protokollrückruf bei Unity registrieren, kann der VSTU\-Rückruf Ihren Rückruf stören.  Um dies zu verhindern, verwenden Sie das Ereignis `VisualStudioIntegration.LogCallback` für die Zusammenarbeit mit VSTU.  
  
## Veranschaulicht  
 Das Freigeben des von Visual Studio\-Tools für Unity erstellten Unity\-Protokollrückrufs.  
  
## Beispiel  
  
```c#  
using System;  
  
using UnityEngine;  
using UnityEditor;  
  
using SyntaxTree.VisualStudio.Unity.Bridge;  
  
[InitializeOnLoad]  
public class LogCallbackHook  
{  
    static LogCallbackHook()  
    {  
        VisualStudioIntegration.LogCallback += (string condition, string trace, LogType type) =>  
        {  
            // place code that implements your log callback here  
        };  
    }  
}  
```  
  
## Siehe auch  
 [Beispiel: Erstellung der Projektdatei](../cross-platform/customize-project-files-created-by-vstu.md)