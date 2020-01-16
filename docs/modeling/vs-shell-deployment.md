---
title: VS Shell-Bereitstellung
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99ef0124c06cd6f1a4d24e29b2c02cd0b50a37b0
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115272"
---
# <a name="vs-shell-deployment"></a>VS Shell-Bereitstellung

Mithilfe einer isolierten Shell können Sie feststellen, welche Visual Studio-Funktionalität Sie benötigen, um mit ihrer domänenspezifischen Sprache zu interagieren und wie diese Lösung angezeigt werden soll. Weitere Informationen zur isolierten Visual Studio-Shell finden Sie unter [Anpassen der isolierten Shell](https://vspartner.com/pages/vsshells).

So legen Sie eine Visual Studio-Shell als Bereitstellungs Ziel fest:

1. Öffnen Sie im **dslpackage** -Projekt **Source.Extension.tt**.

2. Klicken Sie unter `<SupportedProducts>` einfügen:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Ersetzen Sie *myisolatedshell* durch den Namen des isolierten shellpakets.
