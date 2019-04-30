---
title: VS Shell-Bereitstellung
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70f39dd23851a2ebc0a48afd05da54b0d8deb24a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62934299"
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