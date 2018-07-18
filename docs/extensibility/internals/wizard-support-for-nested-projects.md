---
title: Assistentenunterstützung für geschachtelte Projekte | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 14e8a32db2542ae1729a7fdc87cc2ab32845f8ca
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31137494"
---
# <a name="wizard-support-for-nested-projects"></a>Assistentenunterstützung für geschachtelte-Projekte
Die IDE führt zwei Assistenten, die das übergeordnete-Projekt für geschachtelte Projekte implementieren können: die **neues Projekt** Assistenten und die **Element hinzufügen** Assistenten.  
  
 Wenn ein Benutzer startet die **neues Projekt** Assistenten dazu **Projekt hinzufügen** und auf **neues Projekt** indem Sie im Menü Datei oder **hinzufügen** und mit der rechten Maustaste **neues Projekt** im Projektmappen-Explorer führt die IDE die **AddProject** Befehl und die Implementierung des übergeordneten Projekts die **AddProject**Befehl gibt entweder eine Projektdatei für die Vorlage oder einem (.vsz)-Assistentendatei, die einen Satz von Kontextparametern aufweist.  
  
 Auf ähnliche Weise des übergeordneten Projekts Implementierung der **AddItem** Assistenten gibt eine VSZ-Datei, die einen anderen Satz von Kontextparametern verfügt.  
  
 Weitere Informationen zu Assistenten finden Sie unter [Assistenten (. VSZ) Datei](../../extensibility/internals/wizard-dot-vsz-file.md), [Kontextparameter](../../extensibility/internals/context-parameters.md) und [Registrieren von Projekt- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Schachteln von Projekten](../../extensibility/internals/nesting-projects.md)