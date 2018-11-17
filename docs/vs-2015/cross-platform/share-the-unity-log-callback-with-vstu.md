---
title: Freigeben des Unity-Protokollrückrufs für VSTU | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
caps.latest.revision: 5
author: conceptdev
ms.author: crdun
manager: ghogen
ms.openlocfilehash: 278258d50f82fc55e26caf51d5989b2a7c4583fb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51758473"
---
# <a name="share-the-unity-log-callback-with-vstu"></a>Freigeben des Unity-Protokollrückrufs für VSTU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
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

