---
title: "Gewusst wie: Ersetzen von Parametern in einer Vorlage | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Vorlagenparameter, Ersetzen"
  - "Visual Studio-Vorlagen, Verwenden von Parametern"
ms.assetid: a62924a7-4ba0-413d-b606-fdbe1fcf2807
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Gewusst wie: Ersetzen von Parametern in einer Vorlage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können Vorlagenparameter, etwa Klassennamen und Namespaces, ersetzen, wenn Sie eine Datei auf Basis einer Vorlage erstellen.  Eine vollständige Liste der Vorlagenparameter finden Sie unter [Vorlagenparameter](../ide/template-parameters.md).  
  
## Prozedur  
 Sie können Parameter in den Dateien einer Vorlage immer dann ersetzen, wenn Sie ein Projekt erstellen, das auf dieser Vorlage basiert.  In dieser Prozedur wird erläutert, wie Sie eine Vorlage erstellen, durch die der Name eines Namespaces durch den sicheren Projektnamen ersetzt wird, wenn ein neues Projekt mit der Vorlage erstellt wird.  
  
#### So verwenden Sie einen Parameter, um einen Namespacenamen durch den Projektnamen zu ersetzen  
  
1.  Fügen Sie den Parameter in eine oder mehrere Codedateien in der Vorlage ein.  Zum Beispiel:  
  
    ```  
    namespace $safeprojectname$  
    ```  
  
    > [!NOTE]
    >  Vorlagenparameter werden im Format $*Parameter*$ geschrieben.  
  
2.  Suchen Sie in der VSTEMPLATE\-Datei der Vorlage nach dem `ProjectItem`\-Element, in dem diese Datei enthalten ist.  
  
3.  Legen Sie das `ReplaceParameters`\-Attribut für das `ProjectItem`\-Element auf `true` fest.  Zum Beispiel:  
  
    ```  
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>  
    ```  
  
## Siehe auch  
 [Erstellen von benutzerdefinierten Projekt\- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [Vorlagenparameter](../ide/template-parameters.md)   
 [Schemareferenz zu Visual Studio\-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [ProjectItem\-Element \(Visual Studio\-Elementvorlagen\)](../extensibility/projectitem-element-visual-studio-item-templates.md)