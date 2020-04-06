---
title: Verschachtelungsprojekte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 814780fa8e7e57a022a75b2e09115cfa55a1b8be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707032"
---
# <a name="nesting-projects"></a>Schachteln von Projekten
Enterprise-Anwendungsentwickler, die Ihr VS-Paket verwenden, können [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ähnliche Projekttypen bequem mithilfe von *Project Nesting gruppieren.* Beispielsweise verwendet das Enterprise Template-Projekt verschachtelte Projekte, um Projekte in Kategorien zu gruppieren. Business-Fassadenprojekte, Web-UI-Projekte usw. werden in einer Kategorie zusammengefasst.

 In diesem Szenario gibt es keine Begrenzung für die Anzahl der Projekte, die der Entwickler unter jedem übergeordneten Projekt verschachteln kann, obwohl der Entwickler programmgesteuert Grenzwerte bereitstellen kann. Diese Art der Gruppierung kann auch rekursiv gemacht werden, in diesem Fall können die Projekte desselben Typs wie ein untergeordnetes Projekt unter dem untergeordneten Projekt verschachtelt werden, um ein Teilprojekt des untergeordneten Elements zu werden, das ein Teilprojekt des übergeordneten Projekts ist.

 Die Projektverschachtelung ist [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]kein fester Bestandteil von . Sie müssen den Code schreiben, um die Verschachtelung und Dasnierung von Unterprojekten in untergeordneten Projekten zu aktivieren. Das übergeordnete Projekt ist ein spezielles VSPackage oder Projekttyp, das mit einer eigenen GUID erstellt und registriert wurde, die den Code enthält, der zum Implementieren der Projektverschachtelung erforderlich ist.

 Ein Beispiel zum Verschachteln von Projekten finden Sie in den [Abschnitt Gewusst wie: Implementieren verschachtelter Projekte](../../extensibility/internals/how-to-implement-nested-projects.md).

## <a name="nested-projects-example"></a>Beispiel für verschachtelte Projekte
 ![Nested Projects-Projektmappe](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects") Beispiel für verschachtelte Projekte

## <a name="see-also"></a>Weitere Informationen
- [Überlegungen für das Entladen und Neuladen von geschachtelten Projekten](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Assistentenunterstützung für geschachtelte Projekte](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Registrieren von Projekt- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md)
- [Implementieren der Befehlsbehandlung für geschachtelte Projekte](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Filtern des AddItem-Dialogfelds für geschachtelte Projekte](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)
- [Prüfliste: Erstellen neuer Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Kontextparameter](../../extensibility/internals/context-parameters.md)
- [Assistentendatei (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)
