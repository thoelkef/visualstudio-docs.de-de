---
title: "Auf &quot;Global&quot; m&#252;ssen &quot;.&quot; und ein Bezeichner folgen. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36000"
  - "vbc36000"
helpviewer_keywords: 
  - "BC36000"
ms.assetid: 0007d7b4-54a2-4f09-904c-d5ad60a55f8e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Auf &quot;Global&quot; m&#252;ssen &quot;.&quot; und ein Bezeichner folgen.
Das Schlüsselwort [Global \- delete](http://msdn.microsoft.com/de-de/18c8ba14-40f6-4978-8096-6a5852324635) ist in einem anderen Kontext als dem für den Zugriff auf einen Namespace enthalten.  
  
 `Global` soll es dem Code ermöglichen, aus einer Namespacestruktur, für die der Namespace auf Stammebene blockiert ist, auf einen Namespace auf Stammebene zuzugreifen.  
  
 **Fehler\-ID:** BC36000  
  
### So beheben Sie diesen Fehler  
  
-   Wenn Sie auf einen Namespace auf Stammebene zugreifen möchten, geben Sie ihn nach dem `Global`\-Schlüsselwort und einem Punkt \(`.`\) an.  
  
    ```  
    Dim keyInfo As Global.System.ConsoleKeyInfo  
    ```  
  
-   Wenn Sie nicht auf einen Namespace auf Stammebene zugreifen möchten, entfernen Sie das `Global`\-Schlüsselwort.  
  
## Siehe auch  
 [Global \- delete](http://msdn.microsoft.com/de-de/18c8ba14-40f6-4978-8096-6a5852324635)