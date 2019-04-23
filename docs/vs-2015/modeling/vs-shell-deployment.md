---
title: VS Shell-Bereitstellung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6503efd0fa606042089e26b4cac23adcabdcb6e7
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60041015"
---
# <a name="vs-shell-deployment"></a>VS Shell-Bereitstellung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eine isolierte Shell können Sie bestimmen, welche Visual Studio Funktionalität müssen Sie interagieren mit Ihrem Domain-Specific Languge und wie diese Lösung angezeigt werden soll. Weitere Informationen zu Visual Studio isolierte Shell, finden Sie unter [Anpassen der Isolated Shell](../extensibility/customizing-the-isolated-shell.md). Sie finden weitere Informationen zur Verwendung die isolated Shell in anpassen [Anpassen der Isolated Shell](http://msdn.microsoft.com/d75463cd-1155-42e4-8b7a-046ed6becbbf).  
  
### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Eine Visual Studio-Shell als Bereitstellungsziel festlegen  
  
1. In der **DslPackage** geöffneten Projekt **source.extension.tt**.  
  
2. Klicken Sie unter `<SupportedProducts>` einfügen:  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     Ersetzen Sie dies *MyIsolatedShell* mit dem Namen Ihres isolierten Shell-Pakets.
