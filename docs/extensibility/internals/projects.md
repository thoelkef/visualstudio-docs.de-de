---
title: Projekte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b7a9299321d2aa80eebb564bf9b926f07ab0108
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706217"
---
# <a name="projects"></a>Projekte
In Visual Studio sind Projekte die Container, die Entwickler zum Organisieren von Quellcodedateien und anderen Ressourcen verwenden, die im **Projektmappen-Explorer**angezeigt werden. In der Regel handelt es sich bei Projekten um Dateien (z. B. eine .csproj-Datei für ein C-Projekt), die Verweise auf Quellcodedateien und Ressourcen wie Bitmapdateien speichern. Mit Projekten können Sie Quellcode, Verweise auf Webdienste und Datenbanken und andere Ressourcen organisieren, erstellen, debuggen und bereitstellen. VSPackages kann das Visual Studio-Projektsystem auf drei Arten erweitern: *Projekttypen*, *Projektuntertypen*und *benutzerdefinierte Tools*.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Projekttypen](../../extensibility/internals/project-types.md)

 *Projekttypen* unterstützen neue Arten von Projekten, z. B. Programmiersprachen. Beispielsweise verfügt jede von Visual Studio unterstützte Sprache über einen eigenen Projekttyp, und das IronPython-Integrationsbeispiel enthält einen Projekttyp für die IronPython-Sprache. Sie müssen einen Projekttyp für andere Sprachen als C- oder Visual Basic erstellen, um anzupassen, wie Elemente erstellt, gedebuggiert, bereitgestellt und im **Projektmappen-Explorer**angezeigt werden. Weitere Informationen finden Sie unter [Projekttypen](../../extensibility/internals/project-types.md).

- [Projektuntertypen](../../extensibility/internals/project-subtypes.md)

 *Projektuntertypen* basieren auf Projekttypen und können verwendet werden, um die Art und Weise anzupassen, wie Projekte erstellt, gedebuggiert und bereitgestellt werden. Visual Studio verwendet Projektuntertypen mit Smart Device-Projekten. Sie passen die Bereitstellung an, indem sie ein neu erstelltes Programm von einem Entwicklungscomputer auf das Zielgerät kopieren. Als Grundlage für Projektuntertypen können die Projekttypen "C" und "Visual Basic" verwendet werden. C++-Projekttypen können dies nicht. Eigene Projekttypen können auch als Grundlage für Projektuntertypen verwendet werden. Weitere Informationen finden Sie unter [Projektuntertypen](../../extensibility/internals/project-subtypes.md).

- [Webprojekte](../../extensibility/internals/web-projects.md)

 Erläutert das Webprojekt, das wiederum Webanwendungen erstellt.

- [Neue Projektgeneration: Unter der Haube, Teil Eins](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) und [neue Projektgeneration: Unter der Haube, Teil 2](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)

 Erläutert, was tatsächlich geschieht, wenn Sie ein neues Projekt erstellen.

- [VSSDK-Beispiele](https://github.com/Microsoft/VSSDK-Extensibility-Samples) Enthält die Beispiele im VSSDK, die sich mit Projekten und Lösungen befassen.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Im Visual Studio SDK](../../extensibility/internals/inside-the-visual-studio-sdk.md)

 Erläutern Sie verschiedene Aspekte der Visual Studio-Erweiterbarkeit.
