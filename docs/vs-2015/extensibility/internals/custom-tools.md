---
title: Benutzerdefinierte Tools | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 594d564cf4a18eb0b673abd9b45b7d70e20381b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196920"
---
# <a name="custom-tools"></a>Benutzerdefinierte Tools
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Mithilfe von *benutzerdefinierten Tools* können Sie ein Tool einem Element in einem Projekt zuordnen und dieses Tool ausführen, wenn die Datei gespeichert wird. Bestimmte benutzerdefinierte Tools, die manchmal auch als *Einzel Datei-Generatoren*bezeichnet werden, werden häufig verwendet, um Konvertierer zu implementieren, die Code aus Daten generieren und umgekehrt. Beispielsweise erstellen Einzel Datei [!INCLUDE[csprcs](../../includes/csprcs-md.md)] -Generatoren und [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] Quellcode aus den. Settings-und RESX-Dateien. Der generierte Quellcode stellt stark typisierten Zugriff auf die Daten in den. Settings-und RESX-Dateien bereit. Die [!INCLUDE[csprcs](../../includes/csprcs-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] Projekttypen und unterstützen benutzerdefinierte Tools; [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] Projekttypen nicht. Ihre eigenen Projekttypen können auch benutzerdefinierte Tools unterstützen.  
  
 Benutzerdefinierte Tools sind registrierte Komponenten, die die- `IVsSingleFileGenerator` Schnittstelle implementieren.  
  
 Benutzerdefinierte Tools sind einem `ProjectItem` Schnittstellen Objekt zugeordnet und sind wie Designer und Editoren. Ein benutzerdefiniertes Tool nimmt die durch eine dargestellte Datei `ProjectItem` als Eingabe an und schreibt eine neue Datei, deren Dateiname von der-Methode bereitgestellt wird `DefaultExtension` .  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Implementieren von Generatoren einzelner Dateien](../../extensibility/internals/implementing-single-file-generators.md)  
 Beschreibt, wie die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> Schnittstelle zum Implementieren eines benutzerdefinierten Tools verwendet wird.  
  
 [Ermitteln des Standardnamespaces eines Projekts](../../misc/determining-the-default-namespace-of-a-project.md)  
 Beschreibt, wie der richtige Namespace basierend auf der verwendeten Sprache bestimmt wird.  
  
 [Registrieren von Generatoren einzelner Dateien](../../extensibility/internals/registering-single-file-generators.md)  
 Stellt Beschreibungen für alle Registrierungseinträge für ein benutzerdefiniertes Tool bereit.  
  
 [Verfügbarmachen von Typen für visuelle Designer](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 Erläutert, wie Projektsysteme visuelle Designer Unterstützung für den Zugriff auf generierte Klassen und Typen über temporäre portable ausführbare Dateien (PE) bieten.  
  
 [Beibehalten der Eigenschaft eines Projektelements](../../extensibility/persisting-the-property-of-a-project-item.md)  
 Zeigt, wie eine Projekt Element Eigenschaft (z. b. der Autor einer Quelldatei) in der Projektdatei gespeichert wird.  
  
## <a name="reference"></a>Referenz  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 Stellt Details zum bereit <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> , das eine einzelne Eingabedatei in eine einzelne Ausgabedatei transformiert, die kompiliert oder einem Projekt hinzugefügt werden kann.  
  
 <xref:EnvDTE.ProjectItem>  
 Erläutert die- `ProjectItem` Schnittstelle, die ein Element in einem Projekt darstellt.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 Stellt Details zur- `DefaultExtension` Methode bereit, die die Dateinamenerweiterung abruft, die dem Ausgabe Dateinamen zugewiesen wird.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Erweitern von Projekten](../../extensibility/extending-projects.md)  
 Beschreibt, wie Codedateien und Ressourcendateien mithilfe von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]-Projekten und -Projektmappen organisiert werden und wie die Quellcodeverwaltung implementiert wird.
