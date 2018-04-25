---
title: VS Shell-Bereitstellung
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 816997f971e90ddd27f8e24cdc1857559e04ff70
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/20/2018
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