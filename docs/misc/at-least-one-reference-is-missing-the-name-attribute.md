---
title: "At least one reference is missing the &#39;Name&#39; attribute | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.refmissingname"
ms.assetid: 0703dc20-9cdd-4632-93a0-57a4ccea2fce
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# At least one reference is missing the &#39;Name&#39; attribute
Jeder Verweis muss wie folgt über eine verknüpfte **Name**\-Eigenschaft verfügen:  
  
```  
<Reference  
   Name = "System.XML"  
   AssemblyName = "System.Xml"  
/>  
```  
  
 Dieser Fehler gibt an, dass die **Name**\-Eigenschaft für mindestens einen Verweis nicht gefunden wurde.  
  
 Dieser Fehler wird meistens durch das manuelle Bearbeiten der Projektdatei verursacht.  
  
 **So beheben Sie diesen Fehler**  
  
-   Fügen Sie den Verweis erneut hinzu.  
  
     Betroffene Verweise werden dem Projekt nicht hinzugefügt.  
  
## Siehe auch  
 [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/de-de/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md)