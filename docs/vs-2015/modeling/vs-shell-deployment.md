---
title: VS Shell-Bereitstellung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a42ec6a762655589bfd589ae9dc0354e3a7d1cb5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659301"
---
# <a name="vs-shell-deployment"></a>VS Shell-Bereitstellung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mithilfe einer isolierten Shell können Sie feststellen, welche Visual Studio-Funktionalität Sie benötigen, um mit ihrer domänenspezifischen Sprache zu interagieren und wie diese Lösung angezeigt werden soll. Weitere Informationen zur isolierten Visual Studio-Shell finden Sie unter [Anpassen der isolierten Shell](../extensibility/customizing-the-isolated-shell.md). Weitere Informationen zum Anpassen der isolierten Shell finden Sie unter Anpassen [der isolierten Shell](https://msdn.microsoft.com/d75463cd-1155-42e4-8b7a-046ed6becbbf).

### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>So legen Sie eine Visual Studio-Shell als Bereitstellungs Ziel fest

1. Öffnen Sie im **dslpackage** -Projekt **Source.Extension.tt**.

2. Klicken Sie unter `<SupportedProducts>` einfügen:

    ```
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
    ```

     Ersetzen Sie *myisolatedshell* durch den Namen des isolierten shellpakets.
