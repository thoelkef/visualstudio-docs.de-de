---
title: Assistentenunterstützung für geschachtelte Projekte | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2635488c970e0f2b134bf4d54fa6a364a5b30198
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55004759"
---
# <a name="wizard-support-for-nested-projects"></a>Assistentenunterstützung für geschachtelte Projekte
Die IDE ausgeführt wird, zwei Assistenten, die das übergeordnete Projekt für geschachtelte Projekte implementieren können: die **neues Projekt** Assistenten und die **Element hinzufügen** Assistenten.  
  
 Wenn ein Benutzer startet die **neues Projekt** Assistenten dazu **Projekt hinzufügen** und auf **neues Projekt** auf das Menü "Datei" oder durch auswählen **hinzufügen** und mit der rechten Maustaste **neues Projekt** im Projektmappen-Explorer führt die IDE die **AddProject** Befehl und die Implementierung des übergeordneten Projekts der **AddProject**Befehl gibt entweder eine Vorlagendatei für das Projekt oder eine Assistentendateien (VSZ)-Datei, die einen Satz von Kontextparametern verfügt.  
  
 Auf ähnliche Weise des übergeordneten Projekts Implementierung von **AddItem** Assistenten gibt eine VSZ-Datei, die über einen anderen Satz von Kontextparametern verfügt.  
  
 Weitere Informationen zu Assistenten finden Sie unter [Assistenten (. VSZ) Datei](../../extensibility/internals/wizard-dot-vsz-file.md), [Kontextparameter](../../extensibility/internals/context-parameters.md) und [Registrieren von Projekt- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Schachteln von Projekten](../../extensibility/internals/nesting-projects.md)