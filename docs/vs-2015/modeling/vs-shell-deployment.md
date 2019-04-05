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
ms.openlocfilehash: 6c79a8a0558594e8981959750ebd348b6f9f4d60
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58957842"
---
# <a name="vs-shell-deployment"></a>VS Shell-Bereitstellung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eine isolierte Shell können Sie bestimmen, welche Visual Studio Funktionalität müssen Sie interagieren mit Ihrem Domain-Specific Languge und wie diese Lösung angezeigt werden soll. Weitere Informationen zu Visual Studio isolierte Shell, finden Sie unter [Anpassen der Isolated Shell](../extensibility/customizing-the-isolated-shell.md). Sie finden weitere Informationen zur Verwendung die isolated Shell in anpassen [Anpassen der Isolated Shell](http://msdn.microsoft.com/d75463cd-1155-42e4-8b7a-046ed6becbbf).  
  
### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Eine Visual Studio-Shell als Bereitstellungsziel festlegen  
  
1.  In der **DslPackage** geöffneten Projekt **source.extension.tt**.  
  
2.  Klicken Sie unter `<SupportedProducts>` einfügen:  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     Ersetzen Sie dies *MyIsolatedShell* mit dem Namen Ihres isolierten Shell-Pakets.
