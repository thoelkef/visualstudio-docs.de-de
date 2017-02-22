---
title: "Benutzerdefinierte Tools | Microsoft Docs"
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
  - "VSPackages benutzerdefinierte tools"
  - "benutzerdefinierte Tools [Visual Studio]"
  - "Benutzerdefinierte tools"
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# Benutzerdefinierte Tools
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

*Benutzerdefinierte Tools* lassen Sie ein Tool mit einem Element in einem Projekt zugeordnet werden und das Tool ausführen, wenn die Datei gespeichert wird.  Bestimmte benutzerdefinierte Tools, manchmal als *Einzeldateie Generatoren*, werden häufig verwendet, um Übersetzung zu implementieren, die von den Daten Code generieren und umgekehrt.  Zum Beispiel erstellen Einzeldateie Generatoren [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] und [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Quellcode aus den .settings\- und RESX\-Dateien.  Der generierte Quellcode ermöglicht stark typisierten Zugriff auf Daten in den .settings\- und RESX\-Dateien.  Die [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] und [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Projekttypen unterstützen benutzerdefinierte Tools. [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Projekttypen dagegen nicht.  besitzen kann, Projekttypen auch benutzerdefinierte Tools unterstützen.  
  
 Benutzerdefinierte Tools sind registrierte Komponenten, die die `IVsSingleFileGenerator`\-Schnittstelle implementieren.  
  
 Benutzerdefinierte Tools werden mit einem `ProjectItem`\-Schnittstellenobjekt zugeordnet sind und die Designer und Editoren.  Ein benutzerdefiniertes Tool übernimmt die Datei, die von `ProjectItem` als Eingabe dargestellt wird, und schreibt eine neue Datei, deren Dateiname für die `DefaultExtension` Art angegeben ist.  
  
## In diesem Abschnitt  
 [Implementieren von Einzeldatei\-Generatoren](../../extensibility/internals/implementing-single-file-generators.md)  
 Beschreibt, wie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>\-Schnittstelle verwendet, um ein benutzerdefiniertes Tool zu implementieren.  
  
 [Ermitteln des Standardnamespaces eines Projekts](../../misc/determining-the-default-namespace-of-a-project.md)  
 Beschreibt, wie Sie den richtigen Namespace auf Grundlage der Sprache bestimmt.  
  
 [Registrieren von Einzeldatei\-Generatoren](../../extensibility/internals/registering-single-file-generators.md)  
 Enthält Beschreibungen für alle Registrierungseinträge für ein benutzerdefiniertes Tool bereit.  
  
 [\-Typen für visuelle Designer verfügbar gemacht](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 Erläutert das Projektsysteme Unterstützung für visuelle Designer Zugriff generierten Klassen und Typen durch temporäre Dateien der PE\-Datei \(Portable Executable\) \- Datei bereitstellen.  
  
 [Die Eigenschaft eines Projektelements beibehalten](../../extensibility/persisting-the-property-of-a-project-item.md)  
 Zeigt, wie ein Projektelement Eigenschaft, wie der Autor einer Quelldatei, in der Projektdatei beibehalten wird.  
  
## Referenz  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 Enthält Details über <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>bereit, das eine Ein\-Input Datei in eine Datei mit Ein\-Output Transformationen, die einem Projekt kompiliert werden oder hinzugefügt werden kann.  
  
 <xref:EnvDTE.ProjectItem>  
 Erläutert die `ProjectItem`\-Schnittstelle, die ein Element in einem Projekt darstellt.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 Stellt Details über die `DefaultExtension`\-Methode bereit, die die Dateinamenerweiterung abruft, die dem Ausgabedateinamen angegeben ist.  
  
## Verwandte Abschnitte  
 [Erweitern von Projekten](../../extensibility/extending-projects.md)  
 Beschreibt, wie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projekte und Projektmappen, Codedateien und Ressourcendateien zu organisieren und wie die Quellcodeverwaltung implementiert.