---
title: VS Shell-Bereitstellung
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: e7df1991832e954def71a6cee5bd5516dfd4e961
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31946987"
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