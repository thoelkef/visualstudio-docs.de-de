---
title: Assistenten Unterstützung für in der Liste eingefügte Projekte | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e498f21499f4b07bf77bb79829fc6d92227f1f2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721433"
---
# <a name="wizard-support-for-nested-projects"></a>Assistentenunterstützung für geschachtelte Projekte
Die IDE führt zwei Assistenten aus, die das übergeordnete Projekt für die untergeordneten Projekte implementieren kann: den Assistenten für **neue** Projekte und den Assistenten zum **Hinzufügen** von Elementen.

 Wenn ein Benutzer den Assistenten für **neue Projekte** startet, klicken Sie im Menü Datei auf **Projekt hinzufügen** und im Menü Datei auf **Neues Projekt** , oder wählen **Sie hinzufügen** aus, und klicken Sie mit der rechten Maustaste auf **Neues Projekt** in Projektmappen-Explorer.der Befehl und die Implementierung des Befehls " **AddProject** " des übergeordneten Projekts gibt entweder eine Vorlagen Projektdatei oder eine Assistenten Datei (. vsz) zurück, die über einen Satz von Kontext Parametern verfügt.

 Entsprechend gibt die Implementierung der **AddItem** -Assistenten eines übergeordneten Projekts eine VSZ-Datei zurück, die über einen anderen Satz von Kontext Parametern verfügt.

 Weitere Informationen zu Assistenten finden Sie unter [Assistent (. VSZ-Datei](../../extensibility/internals/wizard-dot-vsz-file.md), [Kontext Parameter](../../extensibility/internals/context-parameters.md) und das [Registrieren von Projekt-und Element Vorlagen](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Schachteln von Projekten](../../extensibility/internals/nesting-projects.md)