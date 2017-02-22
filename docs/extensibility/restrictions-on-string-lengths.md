---
title: "Einschr&#228;nkungen der Zeichenfolge | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Source Control-Plug-ins Einschränkungen der Zeichenfolge"
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Einschr&#228;nkungen der Zeichenfolge
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Datenquellen\-Steuerelement\-Plug\-in\-API schränkt die Längen der Zeichenfolgen, die in verschiedenen Funktionen verwendet.  
  
## Zeichenfolgenwerte Länge  
  
|Konstante|Wert|  
|---------------|----------|  
|`SCC_NAME_LEN`|31|  
|`SCC_AUXLABEL_LEN`|31|  
|`SCC_USER_LEN`|31|  
|`SCC_PRJPATH_LEN`|300|  
  
> [!NOTE]
>  Länge umfasst keine abschließenden der `null`. Schließen Sie andere Konstanten mit dem Suffix "\_SIZE" anstelle von "\_LEN" Speicherplatz für das abschließende `null`.  
  
|Konstante|Wert|  
|---------------|----------|  
|SCC\_NAME\_SIZE|32|  
|SCC\_AUXLABEL\_SIZE|32|  
|SCC\_USER\_SIZE|32|  
|SCC\_PRJPATH\_SIZE|301|  
  
## Siehe auch  
 [Source Control\-Plug\-ins](../extensibility/source-control-plug-ins.md)