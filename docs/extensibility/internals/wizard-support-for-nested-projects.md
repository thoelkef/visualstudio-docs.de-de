---
title: "Assistentenunterstützung für geschachtelte Projekte | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7191d31d4ec53fb26f4ab20114201836f1b58fc5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="wizard-support-for-nested-projects"></a>Assistentenunterstützung für geschachtelte-Projekte
Die IDE führt zwei Assistenten, die das übergeordnete-Projekt für geschachtelte Projekte implementieren können: die **neues Projekt** Assistenten und die **Element hinzufügen** Assistenten.  
  
 Wenn ein Benutzer startet die **neues Projekt** Assistenten dazu **Projekt hinzufügen** und auf **neues Projekt** indem Sie im Menü Datei oder **hinzufügen** und mit der rechten Maustaste **neues Projekt** im Projektmappen-Explorer führt die IDE die **AddProject** Befehl und die Implementierung des übergeordneten Projekts die **AddProject**Befehl gibt entweder eine Projektdatei für die Vorlage oder einem (.vsz)-Assistentendatei, die einen Satz von Kontextparametern aufweist.  
  
 Auf ähnliche Weise des übergeordneten Projekts Implementierung der **AddItem** Assistenten gibt eine VSZ-Datei, die einen anderen Satz von Kontextparametern verfügt.  
  
 Weitere Informationen zu Assistenten finden Sie unter [Assistenten (. VSZ) Datei](../../extensibility/internals/wizard-dot-vsz-file.md), [Kontextparameter](../../extensibility/internals/context-parameters.md) und [Registrieren von Projekt- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Schachteln von Projekten](../../extensibility/internals/nesting-projects.md)