---
title: Assistentenunterstützung für geschachtelte Projekte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4621627faae761bfe63b7fd056427a3771d21582
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523110"
---
# <a name="wizard-support-for-nested-projects"></a>Assistentenunterstützung für geschachtelte Projekte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Assistentenunterstützung für geschachtelte Projekte](https://docs.microsoft.com/visualstudio/extensibility/internals/wizard-support-for-nested-projects).  
  
Die IDE ausgeführt wird, zwei Assistenten, die das übergeordnete Projekt für geschachtelte Projekte implementieren können: die **neues Projekt** Assistenten und die **Element hinzufügen** Assistenten.  
  
 Wenn ein Benutzer startet die **neues Projekt** Assistenten dazu **Projekt hinzufügen** und auf **neues Projekt** auf das Menü "Datei" oder durch auswählen **hinzufügen** und mit der rechten Maustaste **neues Projekt** im Projektmappen-Explorer führt die IDE die **AddProject** Befehl und die Implementierung des übergeordneten Projekts der **AddProject**Befehl gibt entweder eine Vorlagendatei für das Projekt oder eine Assistentendateien (VSZ)-Datei, die einen Satz von Kontextparametern verfügt.  
  
 Auf ähnliche Weise des übergeordneten Projekts Implementierung von **AddItem** Assistenten gibt eine VSZ-Datei, die über einen anderen Satz von Kontextparametern verfügt.  
  
 Weitere Informationen zu Assistenten finden Sie unter [Assistenten (. VSZ) Datei](../../extensibility/internals/wizard-dot-vsz-file.md), [Kontextparameter](../../extensibility/internals/context-parameters.md) und [Registrieren von Projekt- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [Schachteln von Projekten](../../extensibility/internals/nesting-projects.md)

