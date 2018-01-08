---
title: VS Shell-Bereitstellung | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: "2"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: aeb4ca2153d4c060862d31e53202312f061bf1ef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="vs-shell-deployment"></a>VS Shell-Bereitstellung
Eine isolierte Shell können Sie bestimmen, welche Visual Studio Funktionalität müssen Sie für die Interaktion mit einer domänenspezifischen Sprache und wie diese Lösung angezeigt werden soll. Weitere Informationen zu den Visual Studio isolated Shell, finden Sie unter [anpassen Isolated Shell](../extensibility/customizing-the-isolated-shell.md). Weitere Informationen zum Anpassen der isolierten Shells in finden Sie [anpassen Isolated Shell](http://msdn.microsoft.com/en-us/d75463cd-1155-42e4-8b7a-046ed6becbbf).  
  
### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Eine Visual Studio-Shell als das Bereitstellungsziel entweder festlegen  
  
1.  In der **DslPackage** geöffneten Projekts **source.extension.tt**.  
  
2.  Unter `<SupportedProducts>` einfügen:  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     Ersetzen Sie *MyIsolatedShell* mit dem Namen des Pakets isolierte Shell.