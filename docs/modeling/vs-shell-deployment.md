---
title: VS Shell-Bereitstellung | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 4964ce162efac640ea7581b4d3f26f3d50087319
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="vs-shell-deployment"></a>VS Shell-Bereitstellung

Eine isolierte Shell können Sie bestimmen, welche Visual Studio Funktionalität müssen Sie für die Interaktion mit einer domänenspezifischen Sprache und wie diese Lösung angezeigt werden soll. Weitere Informationen zu den Visual Studio isolated Shell, finden Sie unter [anpassen Isolated Shell](../extensibility/customizing-the-isolated-shell.md).

## <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Eine Visual Studio-Shell als das Bereitstellungsziel entweder festlegen
  
1.  In der **DslPackage** geöffneten Projekts **source.extension.tt**.  
  
2.  Unter `<SupportedProducts>` einfügen:  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     Ersetzen Sie *MyIsolatedShell* mit dem Namen des Pakets isolierte Shell.