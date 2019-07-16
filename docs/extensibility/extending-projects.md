---
title: Erweitern von Projekten | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- projects [Visual Studio]
ms.assetid: 096d273d-4fe9-4f24-9b00-470bfbdf4bdf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d0333e09aee207e10657999dda4b5b1d59e181cf
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341107"
---
# <a name="extend-projects"></a>Erweitern von Projekten
Projekte und Projektmappen sind die Methoden, die Visual Studio Code und Ressourcendateien in Einheiten für die Kompilierung und Bereitstellung bereit. Weitere Informationen zu in-Projekten finden Sie [Projekte (Visual Studio SDK)](../extensibility/extending-projects.md).

 Sie können eigene Projekttypen erstellen, mit dem Visual Studio SDK und dem Managed Package Framework für Projekte, die Sie herunterladen können, auf [Managed Package Framework for Projects](https://github.com/tunnelvisionlabs/MPFProj10). Um zu verstehen, wie benutzerdefinierte Projekte implementiert werden, finden Sie unter [Generieren neuer Projekte: In die Hintergründe, Teil 1](../extensibility/internals/new-project-generation-under-the-hood-part-one.md) und [Generieren neuer Projekte: In die Hintergründe, Teil 2](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 In die Themen in diesem Abschnitt wird beschrieben, wie zum Erstellen von benutzerdefinierter Projekten und verschiedene Arten von Visual Studio-Projektmappe zu verwalten.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Erstellen ein grundlegenden Projektsystems, Teil 1](../extensibility/creating-a-basic-project-system-part-1.md) wird beschrieben, wie eine benutzerdefinierte Projektsystem zu erstellen.

- [Erstellen ein grundlegenden Projektsystems, Teil 2](../extensibility/creating-a-basic-project-system-part-2.md) wird beschrieben, wie eine benutzerdefinierte Projektsystem zu erstellen.

- [Speichern von Daten in Projektdateien](../extensibility/saving-data-in-project-files.md) Explains wie Projekt hinzugefügt (<em>.</em> Proj *)-Dateien.

- [Überprüfen von Untertypen eines Projekts zur Laufzeit](../extensibility/verifying-subtypes-of-a-project-at-run-time.md) wird erläutert, wie Sie den Untertyp eines Projekts zur Laufzeit zu überprüfen.

- [Hinzufügen und Entfernen von Eigenschaftenseiten](../extensibility/adding-and-removing-property-pages.md) wird erläutert, wie Sie die Eigenschaftenseiten für das benutzerdefinierte Projekt anpassen.

- [Hinzufügen eines Attributs zu einem Projektelement](../extensibility/adding-an-attribute-to-a-project-item.md) wird erläutert, wie ein Attribut zu einem benutzerdefinierten Projektelement hinzufügen.

- [Speichern Sie die Eigenschaft eines Projektelements](../extensibility/persisting-the-property-of-a-project-item.md) wird erläutert, wie die Eigenschaften eines benutzerdefinierten Projektelements beibehalten.

- [Verwalten von universelle Windows-Projekten](../extensibility/managing-universal-windows-projects.md) wird erläutert, wie universelle Projekte zu verwalten.