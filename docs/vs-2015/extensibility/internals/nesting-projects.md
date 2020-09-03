---
title: Schachteln von Projekten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0e3a0fae42dc7bf1497e3d0d4a9d23f9cab50675
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180418"
---
# <a name="nesting-projects"></a>Schachteln von Projekten
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Unternehmens Anwendungsentwickler, die ihr vs-Paket verwenden, können ähnliche Projekttypen in mithilfe der Projekt Schachtelung bequem gruppieren [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . *project nesting* Beispielsweise verwendet das Enterprise-Vorlagen Projekt für die Gruppierung von Projekten in Kategorien. Geschäfts Fassaden Projekte, Webbenutzer Oberflächen Projekte usw. werden in einer Kategorie zusammengefasst.  
  
 In diesem Szenario gibt es keine Beschränkung für die Anzahl von Projekten, die der Entwickler unter jedem übergeordneten Projekt Schachteln kann, obwohl der Entwicklerprogramm gesteuert Beschränkungen bereitstellen kann. Diese Art von Gruppierung kann auch rekursiv gemacht werden. in diesem Fall können die Projekte desselben Typs wie ein untergeordnetes Projekt unter dem untergeordneten Projekt untergeordnet werden, um ein untergeordnetes Element des untergeordneten Elements zu werden, bei dem es sich um ein untergeordnetes Element des übergeordneten Projekts handelt.  
  
 Die Projekt Schachtelung ist kein intrinsischer Bestandteil von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Sie müssen den Code schreiben, um Schachtelung und untergeordnete Projekt Schachtelungen in untergeordneten Projekten zu aktivieren. Das übergeordnete Projekt ist ein spezielles VSPackage oder Projekttyp, der mit einer eigenen GUID erstellt und registriert wird, die den Code enthält, der zum Implementieren der Projekt Schachtelung erforderlich ist.  
  
 Ein Beispiel für ein Beispiel für ein-Projekt finden Sie im c#-Beispiel für ein.  
  
## <a name="nested-projects-example"></a>Beispiel für ein Beispiel für ein Beispiel  
 ![Geschachtelte Projektmappen](../../extensibility/internals/media/vsnestedprojects.gif "vsnestedprojects")  
Beispiel für ein Beispiel für ein Beispiel  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gewusst wie: Implementieren von in einem Projekt unter fallenen Projekten](../../extensibility/internals/how-to-implement-nested-projects.md)   
 [Überlegungen zum Entladen und erneuten Laden von in einem Projekt Vorgängen](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)   
 [Unterstützung des Assistenten für die Unterstützung von Projekten](../../extensibility/internals/wizard-support-for-nested-projects.md)   
 [Registrieren von Projekt-und Element Vorlagen](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Implementieren der Befehls Behandlung für in der Liste eingefügte Projekte](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)   
 [Filtern des AddItem-Dialog Felds für in der Liste von Projekten](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)   
 [Prüfliste: Erstellen neuer Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Kontext Parameter](../../extensibility/internals/context-parameters.md)   
 [Assistentendatei (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)
