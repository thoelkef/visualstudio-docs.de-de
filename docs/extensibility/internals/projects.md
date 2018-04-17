---
title: Projekte | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b2ca4edabcee9f561dea51ea4b579ce194d13fa8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="projects"></a>Projekte
In Visual Studio-Projekte sind Container, mit denen Entwickler zum Organisieren von Quellcodedateien und anderen Ressourcen, die in angezeigt werden **Projektmappen-Explorer**. Projekte werden in der Regel Dateien (z. B. eine CSPROJ-Datei für ein C#-Projekt), in denen Verweise auf Quellcodedateien und Ressourcen, wie mithilfe einer Bitmapdateien gespeichert. Projekte können Sie zu organisieren, erstellen, Debuggen und Bereitstellen von Quellcode, Verweise auf Webdienste und Datenbanken und anderen Ressourcen. VSPackages können die Visual Studio-Projektsystem erweitern, in drei verschiedene Arten: *-Projekttypen*, *Projektuntertypen*, und *benutzerdefinierte Tools*.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Projekttypen](../../extensibility/internals/project-types.md)  
 *Projekttypen* Hinzufügen der Unterstützung für neue Arten von Projekten, z. B. Programmiersprachen zu vergleichen. Beispielsweise jede Sprache, Visual Studio unterstützt, verfügt über einen eigenen Projekttyp und IronPython-Integration-Beispiel enthält ein Projekt für die IronPython-Sprache. Sie müssen einen Projekttyp für andere Sprachen als C#- oder Visual Basic anpassen, wie Elemente werden erstellt, debuggt, bereitgestellt und im angezeigten erstellen **Projektmappen-Explorer**. Weitere Informationen finden Sie unter [Projekttypen](../../extensibility/internals/project-types.md).  
  
 [Projektuntertypen](../../extensibility/internals/project-subtypes.md)  
 *Projektuntertypen* basieren auf Projekttypen und genutzt werden, wie Projekte erstellt, gedebuggt und bereitgestellt werden. Visual Studio verwendet Projekt Untertypen mit Projekte für intelligente Geräte. Sie passen Sie die Bereitstellung durch Kopieren einer neu erstellten Anwendung auf einem Entwicklungscomputer auf dem Zielgerät. Die C#- und Visual Basic-Projekttypen können als Grundlage für das Projekt Untertypen verwendet werden; C++-Projekttypen ist nicht möglich. Eigene Projekttypen können auch als Grundlage für das Projekt Untertypen verwendet werden. Weitere Informationen finden Sie unter [Projekt Untertypen](../../extensibility/internals/project-subtypes.md).  
  
 [Webprojekte](../../extensibility/internals/web-projects.md)  
 Erläutert die Webprojekt, die wiederum Webanwendungen erstellen.  
  
 [Neue Projektgenerierung: Hinter den Kulissen Teil einer](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) und [neue Projekterstellung: hinter den Kulissen Teil 2](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)  
 Erläutert, was tatsächlich geschieht, wenn Sie ein neues Projekt erstellen.  
  
 [VSSDK-Beispiele](http://aka.ms/vs2015sdksamples)  
 Enthält die Beispiele in VSSDK, die mit Projekten und Projektmappen.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Im Visual Studio SDK](../../extensibility/internals/inside-the-visual-studio-sdk.md)  
 Erläutert verschiedene Aspekte der Visual Studio-Erweiterbarkeit.