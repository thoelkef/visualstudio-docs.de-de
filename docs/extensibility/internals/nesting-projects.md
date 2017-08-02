---
title: "Die Schachtelung von Projekten | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Projekt Schachtelung"
  - "geschachtelte Projekte"
  - "Projekte [Visual Studio SDK] untergeordnete Projekte"
  - "Projekte [Visual Studio SDK] schachteln"
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Die Schachtelung von Projekten
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Enterprise\-Anwendungsentwickler, die das VS\-Paket zu verwenden, können bequem gruppieren ähnliche Arten von Projekten, die zusammen in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mit *Projekt Schachtelung*. Beispielsweise verwendet das Enterprise\-Vorlagenprojekt geschachtelten Projekte zum Gruppieren von Projekten in Kategorien. Geschäftsprojekte Fassade, Web\-Benutzeroberfläche Projekte usw. werden in einer Kategorie gruppiert.  
  
 In diesem Szenario ist keine Beschränkung für die Anzahl der Projekte, die der Entwickler unter jedem übergeordneten Projekt geschachtelt werden kann, obwohl der Entwickler programmgesteuert Grenzwerte bereitstellen kann. Diese Art der Gruppierung kann auch rekursiv vorgenommen werden in diesem Fall können die Projekte des gleichen Typs als untergeordnetes Projekt geschachtelt werden, unter das untergeordnete Element ein Unterprojekt des untergeordneten Elements, werden die ein Unterprojekt des übergeordneten Elements ist.  
  
 Projekt Schachtelung ist ein integraler Bestandteil von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Sie müssen den Code zum Aktivieren der Schachtelung und Unterprojekt Schachtelung innerhalb von untergeordneten Projekten schreiben. Übergeordnetes Projekt ist eine spezielle VSPackage oder Projekttyp erstellt und registriert eine eigene GUID, die den Code, der erforderlich ist enthält, um die Schachtelung von Projekt zu implementieren.  
  
 Sie finden ein Beispiel für geschachtelte Projekte im Beispiel Example.Nested C\#\-Projekt.  
  
## Beispiel für geschachtelte Projekte  
 ![Geschachtelte Projektmappen](~/docs/extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects")  
Beispiel für geschachtelte Projekte  
  
## Siehe auch  
 [Gewusst wie: Implementieren von geschachtelten Projekte](../../extensibility/internals/how-to-implement-nested-projects.md)   
 [Hinweise für entfernen und erneutes Laden geschachtelten Projekte](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)   
 [Unterstützung für geschachtelte Projekte\-Assistenten](../../extensibility/internals/wizard-support-for-nested-projects.md)   
 [Registrieren von Projekt\- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Implementieren der Befehl für die geschachtelte Projekte](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)   
 [Das Dialogfeld AddItem Filtern für geschachtelte Projekte](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)   
 [Prüfliste: Erstellen von neuen Typen](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Kontextparameter](../../extensibility/internals/context-parameters.md)   
 [Assistenten \(. VSZ\)\-Datei](../../extensibility/internals/wizard-dot-vsz-file.md)