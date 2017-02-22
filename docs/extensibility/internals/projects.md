---
title: "Projekte | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Projektmappen [Visual Studio]"
  - "Benutzerdefinierte Tools [Visual Studio SDK]"
  - "Projekt-Untertypen [Visual Studio SDK]"
  - "Projekte [Visual Studio SDK]"
  - "Typen [Visual Studio SDK]"
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
caps.latest.revision: 43
caps.handback.revision: 40
ms.author: "gregvanl"
manager: "ghogen"
---
# Projekte
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], Projekte sind Container, mit denen Entwickler zum Organisieren von Quellcodedateien und anderen Ressourcen, die in **Projektmappen\-Explorer**. Projekte sind in der Regel Dateien, z. B. eine CSPROJ\-Datei für ein [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] Projekt, in denen Verweise auf Quellcodedateien und Ressourcen, wie die Bitmap\-Dateien gespeichert. Projekte können Sie organisieren, erstellen, Debuggen und Bereitstellen von Quellcode, Verweise auf Webdienste und Datenbanken und anderen Ressourcen. VSPackages erweitern die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projektsystem auf drei verschiedene Arten: *Projekttypen*, *Projekt Untertypen*, und *benutzerdefinierte Tools*.  
  
 Ein End\-to\-End\-Beispiel für ein Projektsystem Sprache, finden Sie in der Visual Studio IronPython Beispiel tiefer in die [VSSDK\-Beispiele](../../misc/vssdk-samples.md).  
  
## In diesem Abschnitt  
 [Projekttypen](../../extensibility/internals/project-types.md)  
 *Projekttypen* Hinzufügen von Unterstützung für neue Arten von Projekten, z. B. Programmiersprachen. Z. B. jede Sprache, die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] unterstützt hat seinen eigenen Projekttyp und die IronPython\-Integration\-Beispiel enthält ein Projekt für die Sprache IronPython. Erstellen Sie ein Projekt für Sprachen außer [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] und [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], um anzupassen, wie Elemente werden erstellt, Debuggen, bereitgestellt und im angezeigten **Projektmappen\-Explorer**. Weitere Informationen finden Sie unter [Projekttypen](../../extensibility/internals/project-types.md) und [VSSDK\-Beispiele](../../misc/vssdk-samples.md).  
  
 [Projekt\-Untertypen](../../extensibility/internals/project-subtypes.md)  
 *Projekt Untertypen* basieren auf Projekttypen und kann verwendet werden, die Art und Weise anpassen, Projekte erstellt, gedebuggt und bereitgestellt werden.[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verwendet Projekt Untertypen mit Projekten für intelligente Geräte. Anpassen sie der Bereitstellung durch Kopieren einer neu erstellten Anwendung von einem Entwicklungscomputer auf das Zielgerät. Die [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] und [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Projekttypen dienen als Grundlage für Projekt Untertypen; [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Projekttypen nicht möglich. Eigene Projekttypen können auch als Grundlage für Projekt Untertypen verwendet werden. Weitere Informationen finden Sie unter [Projekt\-Untertypen](../../extensibility/internals/project-subtypes.md).  
  
 [Webprojekte](../../extensibility/internals/web-projects.md)  
 Erläutert die Webprojekt, die wiederum von ASP.NET\-Webanwendungen erstellen.  
  
 [Neue Project\-Generierung: Hinter den Kulissen, Teil 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) und [Neue Project\-Generierung: Hinter den Kulissen, Teil 2](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)  
 Erläutert, was tatsächlich geschieht, wenn Sie ein neues Projekt erstellen.  
  
 [VSSDK\-Beispiele](../../misc/vssdk-samples.md)  
 Beschreibt die Beispiele in der [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] das Arbeiten mit Projekten und Projektmappen.  
  
## Verwandte Abschnitte  
 [NIB: Projekte als Container](http://msdn.microsoft.com/de-de/87d40f63-f487-4767-8963-64beec27ba1b)  
 Beschreibt die Beziehung zwischen Projekten und Projektelementen.