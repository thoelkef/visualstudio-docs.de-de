---
title: Benutzerdefinierte Tools | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 98dce865af4dd1f8498dcd697b53abdb8608abed
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793424"
---
# <a name="custom-tools"></a>Benutzerdefinierte Tools
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

*Benutzerdefinierte Tools* können Sie ein Tool mit einem Element in einem Projekt verknüpfen und das Tool ausführen, wenn die Datei gespeichert wird. Bestimmte benutzerdefinierte Tools, auch bezeichnet als *Einzeldatei-Generatoren*, werden häufig zum Konvertierer implementieren, das Generieren von Code aus und umgekehrt verwendet. Beispielsweise Erstellen von Einzeldatei-Generatoren [!INCLUDE[csprcs](../../includes/csprcs-md.md)] und [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] Quellcode aus dem Settings und RESX-Dateien. Der generierte Quellcode enthält die stark typisierten Zugriff auf die Daten in den Settings und RESX-Dateien. Die [!INCLUDE[csprcs](../../includes/csprcs-md.md)] und [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] Projekttypen unterstützen benutzerdefinierte Tools; [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] Projekttypen nicht der Fall. Eigene Projekttypen können auch benutzerdefinierte Tools unterstützen.  
  
 Benutzerdefinierte Tools sind registrierte Komponenten, implementieren die `IVsSingleFileGenerator` Schnittstelle.  
  
 Benutzerdefinierte Tools zugeordnet sind eine `ProjectItem` oberflächenobjekts und Designer und Editoren entsprechen. Ein benutzerdefiniertes Tool erfordert, die durch dargestellte Datei eine `ProjectItem` als Eingabe und schreibt eine neue Datei, deren Name über erfolgt, die `DefaultExtension` Methode.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Implementieren von Generatoren einzelner Dateien](../../extensibility/internals/implementing-single-file-generators.md)  
 Beschreibt, wie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> Schnittstelle, um ein benutzerdefiniertes Tool zu implementieren.  
  
 [Ermitteln des Standardnamespaces eines Projekts](../../misc/determining-the-default-namespace-of-a-project.md)  
 Beschreibt, wie Sie den richtigen Namespace auf Grundlage der verwendeten Sprache zu bestimmen.  
  
 [Registrieren von Generatoren einzelner Dateien](../../extensibility/internals/registering-single-file-generators.md)  
 Stellt Beschreibungen für die Registrierungseinträge für ein benutzerdefiniertes Tool bereit.  
  
 [Verfügbarmachen von Typen für visuelle Designer](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 Erläutert, wie Projektsystemen visuelle Designer, Zugriff, die generierten Klassen und Typen durch temporäre PE (portable Executable)-Dateien unterstützen.  
  
 [Beibehalten der Eigenschaft eines Projektelements](../../extensibility/persisting-the-property-of-a-project-item.md)  
 Zeigt, wie eine Projektelementeigenschaft, z. B. der Autor einer Quelldatei, in der Projektdatei beibehalten werden.  
  
## <a name="reference"></a>Referenz  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 Enthält Informationen über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>, der transformiert einer einzelnen Eingabedatei in eine einzelne Ausgabedatei, die kompiliert oder zu einem Projekt hinzugefügt werden kann.  
  
 <xref:EnvDTE.ProjectItem>  
 Erläutert die `ProjectItem` -Schnittstelle, die ein Element in einem Projekt darstellt.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 Enthält Informationen über die `DefaultExtension` Methode, die die Dateinamenerweiterung abruft, der den Namen der Ausgabedatei zugewiesen ist.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Erweitern von Projekten](../../extensibility/extending-projects.md)  
 Beschreibt, wie Codedateien und Ressourcendateien mithilfe von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]-Projekten und -Projektmappen organisiert werden und wie die Quellcodeverwaltung implementiert wird.

