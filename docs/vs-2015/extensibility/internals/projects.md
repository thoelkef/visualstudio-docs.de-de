---
title: Projekte | Microsoft-Dokumentation
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
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
caps.latest.revision: 44
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ade0234423c907c675bc1dd53e3436dfa38ca26e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47510279"
---
# <a name="projects"></a>Projekte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Projekte](https://docs.microsoft.com/visualstudio/extensibility/internals/projects).  
  
In Visual Studio-Projekte sind Container, mit denen Entwickler zum Organisieren von Quellcodedateien und anderen Ressourcen, die in angezeigt werden **Projektmappen-Explorer**. In der Regel sind Projekte, Dateien (z. B. einer CSPROJ-Datei für ein C#-Projekt), die Verweise auf Quellcodedateien und Ressourcen wie die Bitmap-Dateien zu speichern. Lassen Sie organisieren, erstellen, Debuggen und Bereitstellen von Quellcode-Projekte, Verweise auf Webdienste und Datenbanken und andere Ressourcen. VSPackages können die Visual Studio-Projektsystem erweitern, auf drei Arten: *Projekttypen*, *Projektuntertypen*, und *benutzerdefinierte Tools*.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Projekttypen](../../extensibility/internals/project-types.md)  
 *Projekttypen* Hinzufügen von Unterstützung für neue Arten von Projekten, wie z. B. Programmiersprachen zu vergleichen. Beispielsweise jede Sprache, Visual Studio unterstützt, hat seinen eigenen Projekt, und das IronPython-Integration-Beispiel enthält einen Projekttyp für die Sprache IronPython. Erstellen Sie ein Projekt für andere Sprachen als C#- oder Visual Basic anpassen, wie Elemente werden erstellt, debuggt, bereitgestellt und im angezeigten **Projektmappen-Explorer**. Weitere Informationen finden Sie unter [Projekttypen](../../extensibility/internals/project-types.md).  
  
 [Projektuntertypen](../../extensibility/internals/project-subtypes.md)  
 *Projektuntertypen* basieren auf Projekttypen zur Verfügung und können verwendet werden, um die Methode anpassen, Projekte erstellt, debuggt und bereitgestellt werden. Visual Studio verwendet Projektuntertypen mit Projekte für intelligente Geräte; Sie können Bereitstellung durch Kopieren eines Programms neu erstellt wurden von einem Entwicklungscomputer aus, auf dem Zielgerät anpassen. Die C#- und Visual Basic-Projekttypen können als Grundlage für Projektuntertypen verwendet werden; C++-Projekttypen ist nicht möglich. Eigene Projekttypen können auch als Grundlage für Projektuntertypen verwendet werden. Weitere Informationen finden Sie unter [Projektuntertypen](../../extensibility/internals/project-subtypes.md).  
  
 [Webprojekte](../../extensibility/internals/web-projects.md)  
 Erläutert, Web-Projekt, die wiederum von ASP.NET-Webanwendungen erstellen.  
  
 [Generieren neuer Projekte: Einblick in die Hintergründe, Teil 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) und [Generieren neuer Projekte: Einblick in die Hintergründe, Teil 2](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)  
 Erläutert, was tatsächlich geschieht, wenn Sie ein neues Projekt erstellen.  
  
 [VSSDK-Beispiele](../../misc/vssdk-samples.md)  
 Beschreibt die Beispiele in Visual Studio SDK PASST, die Projekte und Projektmappen behandeln.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Im Visual Studio SDK](../../extensibility/internals/inside-the-visual-studio-sdk.md)  
 Erläutert verschiedene Aspekte der Visual Studio-Erweiterbarkeit.

