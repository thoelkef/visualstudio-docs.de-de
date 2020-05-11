---
title: VS Shell-Bereitstellung
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ca497244a806324d9d2315fa1b1b89404838ff3
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444998"
---
# <a name="vs-shell-deployment"></a>VS Shell-Bereitstellung

Mit einer isolierten Shell können Sie bestimmen, welche Visual Studio-Funktionalität Sie für die Interaktion mit Ihrer domänenspezifischen Sprache benötigen und wie diese Lösung angezeigt werden soll. Weitere Informationen zur isolierten Visual Studio-Shell finden Sie unter [Anpassen der isolierten Shell](https://docs.microsoft.com/visualstudio/extensibility/customizing-the-isolated-shell).

So legen Sie eine Visual Studio-Shell als Bereitstellungsziel fest:

1. Öffnen Sie im **DslPackage-Projekt** **source.extension.tt**.

2. Unter `<SupportedProducts>` Einfügen:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Ersetzen Sie *MyIsolatedShell* durch den Namen Ihres isolierten Shellpakets.
