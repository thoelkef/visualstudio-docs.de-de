---
title: Freigeben des Unity-Protokollrückrufs für VSTU | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/26/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: aa8a4a229102a6a9439ffb36582cd03e322a086b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "62815664"
---
# <a name="share-the-unity-log-callback-with-vstu"></a>Freigeben des Unity-Protokollrückrufs für VSTU
Visual Studio-Tools für Unity registrieren einen Protokollrückruf bei Unity, damit dessen Konsole in Visual Studio gestreamt werden kann. Wenn Ihre Editorskripts auch einen Protokollrückruf bei Unity registrieren, kann der VSTU-Rückruf Ihren Rückruf stören. Um dies zu verhindern, verwenden Sie das Ereignis `VisualStudioIntegration.LogCallback` für die Zusammenarbeit mit VSTU.

## <a name="demonstrates"></a>Veranschaulicht
 Das Freigeben des von Visual Studio-Tools für Unity erstellten Unity-Protokollrückrufs.

## <a name="example"></a>Beispiel

```csharp
#if ENABLE_VSTU
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
#endif
```

## <a name="see-also"></a>Weitere Informationen
 [Beispiel: Erstellen der Projektdatei](../cross-platform/customize-project-files-created-by-vstu.md)
