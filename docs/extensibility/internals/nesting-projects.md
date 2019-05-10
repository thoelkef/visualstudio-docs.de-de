---
title: Schachteln von Projekten | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a2e05b47563c62f34e4a01c945a45d5c7ec069ee
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62909478"
---
# <a name="nesting-projects"></a>Schachteln von Projekten
Entwicklern von Unternehmensanwendungen, die das Visual Studio-Paket zu verwenden, können bequem gruppieren ähnliche Arten von Projekten, die zusammen in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mit *Projekt Schachtelung*. Beispielsweise verwendet das Enterprise-Vorlagenprojekt geschachtelte Projekte zum Gruppieren von Projekten in Kategorien. Business-Fassade-Projekte, Web-UI-Projekte und usw. werden in einer Kategorie gruppiert.

 In diesem Szenario gibt es keine Beschränkung der Anzahl der Projekte, die der Entwickler unter jedes übergeordneten Projekts, geschachtelt werden kann, auch wenn der Entwickler Grenzwerte programmgesteuert bereitstellen kann. Diese Art der Gruppierung kann auch rekursiv erfolgen in diesem Fall können die Projekte des gleichen Typs als ein untergeordnetes Projekt geschachtelt werden, unter das untergeordnete Element ein Unterprojekt des untergeordneten Elements, zu dem ein Unterprojekt des übergeordneten Elements ist.

 Projekt Schachtelung ist nicht fester Bestandteil eines [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Sie müssen den Code zum Aktivieren der Schachtelung und Unterprojekt Schachtelung innerhalb von untergeordneten Projekten schreiben. Das übergeordnete Projekt ist eine spezielle VSPackage oder Projekttyp erstellt und registriert durch eine eigene GUID, die den Code, der erforderlich ist enthält, um die Schachtelung von Projekt zu implementieren.

 Sie finden ein Beispiel für geschachtelte Projekte im Beispiel Example.Nested C#-Projekt.

## <a name="nested-projects-example"></a>Beispiel für geschachtelte Projekte
 ![Geschachtelte Projektmappen](../../extensibility/internals/media/vsnestedprojects.gif "VsNestedProjects") Beispiel für geschachtelte Projekte

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Implementieren von geschachtelten Projekten](../../extensibility/internals/how-to-implement-nested-projects.md)
- [Überlegungen für das Entladen und Neuladen von geschachtelten Projekten](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Assistentenunterstützung für geschachtelte Projekte](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Registrieren von Projekt- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md)
- [Implementieren der Befehlsbehandlung für geschachtelte Projekte](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Filtern des AddItem-Dialogfelds für geschachtelte Projekte](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)
- [Prüfliste: Erstellen neuer Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Kontextparameter](../../extensibility/internals/context-parameters.md)
- [Assistentendatei (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)