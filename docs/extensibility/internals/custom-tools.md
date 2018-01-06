---
title: Benutzerdefinierte Tools | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7589c9a2aedf987af79689e8babccb554fbb4ccc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="custom-tools"></a>Benutzerdefinierte Tools
*Benutzerdefinierte Tools* können Sie ein Element in einem Projekt ein Tool zuordnen, und führen Sie dieses Tool aus, bei jedem Speichern die Datei. Bestimmte benutzerdefinierte Tools, auch bezeichnet als *Einzeldatei Generatoren*, häufig zum Konvertierer implementieren, das Generieren von Code aus Daten und umgekehrt verwendet werden. Z. B. Einzeldatei Generatoren erstellen [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] und [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Quellcode aus der "Settings" und RESX-Dateien. Die generierten Quellcode stellt stark typisierten Zugriffs auf die Daten in den "Settings" und RESX-Dateien bereit. Die [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] und [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Projekttypen unterstützen benutzerdefinierte Tools; [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Projekttypen nicht der Fall. Eigene Projekttypen können auch benutzerdefinierte Tools unterstützen.  
  
 Benutzerdefinierte Tools sind eingetragene implementierenden Komponenten der `IVsSingleFileGenerator` Schnittstelle.  
  
 Benutzerdefinierte Tools zugeordnet sind ein `ProjectItem` oberflächenobjekts und Designer und Editoren entsprechen. Ein benutzerdefiniertes Tool verwendet die Datei, dargestellt durch eine `ProjectItem` als Eingabe und schreibt eine neue Datei, deren Dateiname, indem bereitgestellt wird, die `DefaultExtension` Methode.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Implementieren von Generatoren einzelner Dateien](../../extensibility/internals/implementing-single-file-generators.md)  
 Beschreibt, wie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> Schnittstelle, um ein benutzerdefiniertes Tool zu implementieren.  
  
 [Registrieren von Generatoren einzelner Dateien](../../extensibility/internals/registering-single-file-generators.md)  
 Stellt Beschreibungen für die Registrierungseinträge für ein benutzerdefiniertes Tool bereit.  
  
 [Verfügbarmachen von Typen für visuelle Designer](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 Erläutert, wie Projektsystemen visuelle Designer zum Zugriff auf generierte Klassen und Typen durch temporäre PE (portable Executable)-Dateien unterstützen.  
  
 [Beibehalten der Eigenschaft eines Projektelements](../../extensibility/persisting-the-property-of-a-project-item.md)  
 Zeigt, wie eine Eigenschaft des Projekt-Element, z. B. der Autor einer Quelldatei, in der Projektdatei beibehalten werden.  
  
## <a name="reference"></a>Verweis  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 Enthält Informationen über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>, die eine einzelne Eingabedatei transformiert, in einer einzigen Ausgabedatei, die kompiliert oder zu einem Projekt hinzugefügt werden kann.  
  
 <xref:EnvDTE.ProjectItem>  
 Erläutert die `ProjectItem` -Schnittstelle, die ein Element in einem Projekt darstellt.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 Enthält Informationen über die `DefaultExtension` -Methode, die die Dateinamenerweiterung abruft, der den Namen der Ausgabedatei zugewiesen ist.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Erweitern von Projekten](../../extensibility/extending-projects.md)  
 Beschreibt, wie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projekte und Projektmappen, Codedateien und Ressourcendateien und wie die quellcodeverwaltung implementiert zu organisieren.