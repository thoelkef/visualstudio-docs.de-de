---
title: Wizard-Support für verschachtelte Projekte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f7f37700d908167ebef8c071021558822bdce173
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703196"
---
# <a name="wizard-support-for-nested-projects"></a>Assistentenunterstützung für geschachtelte Projekte
Die IDE führt zwei Assistenten aus, die das übergeordnete Projekt für verschachtelte Projekte implementieren kann: den Assistenten für **neues Projekt** und den Assistenten zum Hinzufügen von **Element.**

 Wenn ein Benutzer den Assistenten für **neues Projekt** startet, indem er im Menü Datei auf Neues Projekt hinzufügen und auf **Neues Projekt** klicken oder mit der rechten **Maustaste** auf **Neues Projekt** im Projektmappen-Explorer klicken, führt die IDE den Befehl **"Projekt hinzufügen"** aus, und die Implementierung des Befehls **"Projekt"** durch das übergeordnete Projekt gibt entweder eine Vorlagenprojektdatei oder eine Assistentendatei (.vsz) mit einer Reihe von Kontextparametern zurück. **AddProject**

 Ebenso gibt die Implementierung von **AddItem-Assistenten** in einem übergeordneten Projekt eine .vsz-Datei zurück, die einen anderen Satz von Kontextparametern enthält.

 Weitere Informationen zu Assistenten finden Sie unter [Assistent (. Vsz) Datei](../../extensibility/internals/wizard-dot-vsz-file.md), [Kontextparameter](../../extensibility/internals/context-parameters.md) und [Registrieren von Projekt- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Schachteln von Projekten](../../extensibility/internals/nesting-projects.md)
