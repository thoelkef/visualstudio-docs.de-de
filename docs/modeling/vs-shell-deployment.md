---
title: "VS Shell-Bereitstellung | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: 2
caps.handback.revision: 2
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# VS Shell-Bereitstellung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Eine lokalisierte Shell können Sie bestimmen, welche Visual Studio\-Funktionalität Sie mit dem domänenspezifischen Sprache interagieren muss, und wie diese Projektmappe angezeigt werden soll.  Weitere Informationen zu der Visual Studio Shell Isolated finden Sie unter [Anpassen der isolierte Shells](../extensibility/customizing-the-isolated-shell.md).  Sie können weitere Informationen dazu, wie Sie finden die lokalisierte Shell in [Customizing the Isolated Shell](http://msdn.microsoft.com/de-de/d75463cd-1155-42e4-8b7a-046ed6becbbf)angepasst wird.  
  
### So erstellen Sie eine Visual Studio\-Shell als das Festlegen Bereitstellungs\-Ziel  
  
1.  Im **DslPackage** Projekt öffnen Sie **source.extension.tt**.  
  
2.  Durch das Einfügen `<SupportedProducts>` :  
  
    ```  
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>  
    ```  
  
     Ersetzen Sie *MyIsolatedShell* durch den Namen des pakets Shell Isolated.