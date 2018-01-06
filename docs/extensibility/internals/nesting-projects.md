---
title: Schachtelung Projekte | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5b91f9dc00b9130f2c239bd3254f78376bc0fdf3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="nesting-projects"></a>Schachtelung-Projekte
Enterprise-Anwendungsentwickler, die Ihre VS-Paket verwenden, können ähnliche Arten von Projekten, die zusammen in bequem gruppieren [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mit *Projekt Schachtelung*. Beispielsweise verwendet die Enterprise-Vorlagenprojekt geschachtelte Projekte zum Gruppieren von Projekten in Kategorien. Business Fassade Projekte, Webbenutzeroberfläche Projekte usw. werden in einer Kategorie gruppiert.  
  
 In diesem Szenario ist keine Beschränkung der Anzahl von Projekten, die der Entwickler unter jedes Projekt übergeordneten schachteln, obwohl der Entwickler Grenzwerte programmgesteuert bereitstellen kann. Diese Art der Gruppierung kann auch rekursiven, erfolgen in diesem Fall können die Projekte des gleichen Typs als ein untergeordnetes Projekt geschachtelt werden, unter das untergeordnete Element ein Unterprojekt des untergeordneten Elements, zu dem ein Unterprojekt des übergeordneten Elements ist.  
  
 Projekt Schachtelung ist ein integraler Bestandteil von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Sie haben zum Schreiben des Codes zum Aktivieren der Schachtelung und Unterprojekt Schachtelung innerhalb von untergeordneten Projekten. Übergeordneten Projekts ist eine spezielle VSPackage oder der Projekttyp, erstellt und registriert eine eigene GUID, die den Code, der erforderlich ist enthält, um die Schachtelung von Projekt zu implementieren.  
  
 Ein Beispiel für geschachtelte Projekte finden Sie im C#-Example.Nested projektbeispiel.  
  
## <a name="nested-projects-example"></a>Beispiel für geschachtelte Projekte  
 ![Geschachtelte Projektmappen](../../extensibility/internals/media/vsnestedprojects.gif "VsNestedProjects")  
Beispiel für geschachtelte Projekte  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Implementieren von geschachtelten Projekte](../../extensibility/internals/how-to-implement-nested-projects.md)   
 [Überlegungen zum Entladen und erneutes Laden geschachtelten Projekte](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)   
 [Assistentenunterstützung für geschachtelte-Projekte](../../extensibility/internals/wizard-support-for-nested-projects.md)   
 [Registrieren von Projekt- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Implementieren von Befehlsbehandelung für geschachtelte-Projekte](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)   
 [Das Dialogfeld AddItem Filtern für geschachtelte Projekte](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)   
 [Prüfliste: Erstellen neuen Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Kontextparameter](../../extensibility/internals/context-parameters.md)   
 [Assistentendatei (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)