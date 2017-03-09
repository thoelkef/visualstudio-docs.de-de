---
title: "Could not instantiate the licenses processor | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.no_licx_generator"
ms.assetid: 9e95d590-f41f-4cfa-bc73-fadeacfdb879
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Could not instantiate the licenses processor
Das Tool, das zur Umwandlung von LICX\-Dateien in binäre Ressourcen verwendet wird, konnte nicht instanziiert werden.  
  
 Bei der Kompilierung wandelt das Projektsystem eine LICX\-Textdatei in eine binäre Ressource um, die die Lizenzierung des .NET\-Steuerelements unterstützt.  Die binäre Ressource wird anschließend in die Projektausgabe eingebettet.  
  
 Der Buildprozess schlägt fehl, wenn dieser Fehler auftritt.  
  
 Die LICX\-Datei wird vom Windows Forms\-Designer automatisch generiert oder aktualisiert, sobald dem Formular ein lizenziertes Steuerelement hinzugefügt wird.  Es gibt eine LICX\-Datei pro Projekt. Sie befindet sich immer im Stammverzeichnis und erhält immer den Namen **licenses.licx**.  
  
 **So beheben Sie diesen Fehler**  
  
-   Installieren Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] neu.  
  
## Siehe auch  
 [How to: License Components and Controls](../Topic/How%20to:%20License%20Components%20and%20Controls.md)