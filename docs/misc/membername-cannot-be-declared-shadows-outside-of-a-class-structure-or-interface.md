---
title: "&#39;&lt;Membername&gt;&#39; kann nicht au&#223;erhalb einer Klasse, einer Struktur oder einer Schnittstelle als &#39;Shadows&#39; deklariert werden. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32200"
  - "vbc32200"
helpviewer_keywords: 
  - "BC32200"
ms.assetid: 23e28894-5854-46ef-924d-f1cb6e81bcb1
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;Membername&gt;&#39; kann nicht au&#223;erhalb einer Klasse, einer Struktur oder einer Schnittstelle als &#39;Shadows&#39; deklariert werden.
Das `Shadows`\-Schlüsselwort wird in einer Deklaration auf Namespace\-, Modul\- oder Dateiebene angezeigt. Shadowing ist nur innerhalb von Programmierelementen sinnvoll, die von einem Basiselement erben können.  
  
 **Fehler\-ID:** BC32200  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie das `Shadows`\-Schlüsselwort, oder verschieben Sie die Deklaration innerhalb einer Klasse, Struktur oder Schnittstelle.  
  
## Siehe auch  
 [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)   
 [Shadowing in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/shadowing)