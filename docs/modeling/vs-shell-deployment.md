---
title: VS Shell-Bereitstellung
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e010d2efd8174f2c61d7c97eb63d585f47812ff
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663661"
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