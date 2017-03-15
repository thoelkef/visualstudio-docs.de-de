---
title: "„BaseLogName“ darf nicht „Nothing“ oder eine leere Zeichenfolge sein. | Microsoft Docs"
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
  - "vbrApplicationLogBaseNameNull"
ms.assetid: 8e7665e3-5343-45fa-bc79-64e235a0477f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# „BaseLogName“ darf nicht „Nothing“ oder eine leere Zeichenfolge sein.
Der Wert der <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.BaseFileName%2A>\-Eigenschaft darf nicht `Nothing` oder eine leere Zeichenfolge sein.  
  
 Die <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.BaseFileName%2A>\-Eigenschaft gibt den Basisnamen für die Protokolldateien an.  
  
### So beheben Sie diesen Fehler  
  
-   Legen Sie die <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.BaseFileName%2A>\-Eigenschaft auf eine Zeichenfolge fest, die mindestens ein Zeichen enthält.  
  
## Siehe auch  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.BaseFileName%2A>   
 [My.Application.Log\-Objekt](/dotnet/visual-basic/language-reference/objects/my-application-log-object)   
 [My.Log Object](/dotnet/visual-basic/language-reference/objects/my-log-object)