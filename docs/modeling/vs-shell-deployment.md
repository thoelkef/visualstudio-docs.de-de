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
ms.openlocfilehash: 663e706dba9ec7b6479e3e9360ef8aa2d12b1400
ms.sourcegitcommit: 159ed9d4f56cdc1dff2fd19d9dffafe77e46cd4e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/21/2018
ms.locfileid: "53739496"
---
# <a name="vs-shell-deployment"></a>VS Shell-Bereitstellung

Eine isolierte Shell können Sie bestimmen, welche Visual Studio Funktionalität müssen Sie interagieren mit Ihrem Domain-Specific Languge und wie diese Lösung angezeigt werden soll. Weitere Informationen zu Visual Studio isolierte Shell, finden Sie unter [Anpassen der Isolated Shell](https://vspartner.com/pages/vsshells).

So legen Sie eine Visual Studio-Shell als Bereitstellungsziel fest:

1. In der **DslPackage** geöffneten Projekt **source.extension.tt**.

2. Klicken Sie unter `<SupportedProducts>` einfügen:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Ersetzen Sie dies *MyIsolatedShell* mit dem Namen Ihres isolierten Shell-Pakets.