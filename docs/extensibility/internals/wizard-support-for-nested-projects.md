---
title: Assistenten Unterstützung für in der Liste eingefügte Projekte | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703196"
---
# <a name="wizard-support-for-nested-projects"></a>Assistentenunterstützung für geschachtelte Projekte
Die IDE führt zwei Assistenten aus, die das übergeordnete Projekt für die untergeordneten Projekte implementieren kann: den Assistenten für **neue** Projekte und den Assistenten zum **Hinzufügen** von Elementen.

 Wenn ein Benutzer den Assistenten für **neue Projekte** startet, klicken **Sie auf Projekt hinzufügen** , und klicken Sie im Menü Datei auf **Neues Projekt** , oder klicken **Sie auf Hinzufügen** , und klicken Sie mit der rechten Maustaste auf **Neues Projekt** in Projektmappen-Explorer. die IDE **AddProject** führt den **AddProject** -Befehl aus, und die Implementierung des übergeordneten Projekts gibt entweder eine Vorlagen Projektdatei oder eine Assistenten Datei (. vsz)

 Entsprechend gibt die Implementierung der **AddItem** -Assistenten eines übergeordneten Projekts eine VSZ-Datei zurück, die über einen anderen Satz von Kontext Parametern verfügt.

 Weitere Informationen zu Assistenten finden Sie unter [Assistent (. VSZ-Datei](../../extensibility/internals/wizard-dot-vsz-file.md), [Kontext Parameter](../../extensibility/internals/context-parameters.md) und das [Registrieren von Projekt-und Element Vorlagen](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Schachteln von Projekten](../../extensibility/internals/nesting-projects.md)
