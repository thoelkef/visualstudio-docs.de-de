---
title: VS Shell-Bereitstellung
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f3729c09198b331728e2cc67299ffc3ad6c3d26
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809647"
---
# <a name="vs-shell-deployment"></a>VS Shell-Bereitstellung

Mithilfe einer isolierten Shell können Sie feststellen, welche Visual Studio-Funktionalität Sie benötigen, um mit ihrer domänenspezifischen Sprache zu interagieren und wie diese Lösung angezeigt werden soll. Weitere Informationen zur isolierten Visual Studio-Shell finden Sie unter [Anpassen der isolierten Shell](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/).

So legen Sie eine Visual Studio-Shell als Bereitstellungs Ziel fest:

1. Öffnen Sie im **dslpackage** -Projekt **Source.Extension.tt**.

2. Unter `<SupportedProducts>` einfügen:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Ersetzen Sie *myisolatedshell* durch den Namen des isolierten shellpakets.