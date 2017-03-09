---
title: "At least one startup service is missing the &#39;attribute&#39; attribute | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.projfile_missing_ss_attrib"
ms.assetid: 987c42dc-4394-4b07-b7fa-a8e7afc6fdfb
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# At least one startup service is missing the &#39;attribute&#39; attribute
Ein Startdienst benötigt das **ID**\-Attribut, das auf einem `<Service>`\-Element nicht gefunden wurde.  Beispiele:  
  
```  
<Service ID="{0000-0000-0000-00000000-000000000000}"/>  
```  
  
 Dies gibt an, dass die Projektdatei beschädigt ist.  
  
 Dieser Fehler wird meistens durch das manuelle Bearbeiten der Projektdatei verursacht.  
  
 **So beheben Sie diesen Fehler**  
  
-   Speichern Sie die Projektdatei.  
  
     Der fehlerhafte Abschnitt wird nicht ausgeschrieben, sodass der Fehler beim nächsten Öffnen des Projekts nicht mehr auftritt.  
  
## Siehe auch  
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/de-de/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)