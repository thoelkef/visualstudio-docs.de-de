---
title: VS Shell-Bereitstellung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: e1a1bd92d1a0b91aa01d940695cd780f7e63c098
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523882"
---
# <a name="vs-shell-deployment"></a>VS Shell-Bereitstellung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [VS Shell-Bereitstellung](https://docs.microsoft.com/visualstudio/modeling/vs-shell-deployment).  
  
Eine isolierte Shell können Sie bestimmen, welche Visual Studio Funktionalität müssen Sie interagieren mit Ihrem Domain-Specific Languge und wie diese Lösung angezeigt werden soll. Weitere Informationen zu Visual Studio isolierte Shell, finden Sie unter [Anpassen der Isolated Shell](../extensibility/customizing-the-isolated-shell.md). Sie finden weitere Informationen zur Verwendung die isolated Shell in anpassen [Anpassen der Isolated Shell](http://msdn.microsoft.com/en-us/d75463cd-1155-42e4-8b7a-046ed6becbbf).  
  
### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Eine Visual Studio-Shell als Bereitstellungsziel festlegen  
  
1.  In der **DslPackage** geöffneten Projekt **source.extension.tt**.  
  
2.  Klicken Sie unter `<SupportedProducts>` einfügen:  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     Ersetzen Sie dies *MyIsolatedShell* mit dem Namen Ihres isolierten Shell-Pakets.



