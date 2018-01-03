---
title: "Freigeben des Unity-Protokollrückrufs für VSTU | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
caps.latest.revision: "2"
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload: unity
ms.openlocfilehash: 6c078affefbb24a9fbbb65c854911f4b91f12183
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="share-the-unity-log-callback-with-vstu"></a>Freigeben des Unity-Protokollrückrufs für VSTU
Visual Studio-Tools für Unity registrieren einen Protokollrückruf bei Unity, damit dessen Konsole in Visual Studio gestreamt werden kann. Wenn Ihre Editorskripts auch einen Protokollrückruf bei Unity registrieren, kann der VSTU-Rückruf Ihren Rückruf stören. Um dies zu verhindern, verwenden Sie das Ereignis `VisualStudioIntegration.LogCallback` für die Zusammenarbeit mit VSTU.  

## <a name="demonstrates"></a>Veranschaulicht  
 Das Freigeben des von Visual Studio-Tools für Unity erstellten Unity-Protokollrückrufs.  

## <a name="example"></a>Beispiel  

```csharp  
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

## <a name="see-also"></a>Siehe auch  
 [Beispiel: Erstellung der Projektdatei](../cross-platform/customize-project-files-created-by-vstu.md)
