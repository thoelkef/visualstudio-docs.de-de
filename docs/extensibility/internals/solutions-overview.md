---
title: "Übersicht über Projektmappen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a6a1afea2357fb0c0ef1bcf8152f8a3785a55786
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="solutions-overview"></a>Übersicht über Projektmappen
Eine Lösung ist eine Gruppierung von einem oder mehreren Projekten, die zum Erstellen einer Anwendung zusammenarbeiten. Projekt- und Status Informationen zu der Projektmappe werden in zwei verschiedenen Projektmappendateien gespeichert. Die Projektmappendatei (sln) basiert auf Text und Quellcodeverwaltungssystem platziert und mehreren Benutzern gemeinsam verwendet werden können. Die Benutzer-Option (.suo) Projektmappendatei ist binär. Daher wird die SUO-Datei kann nicht unter quellcodeverwaltung platziert werden und benutzerspezifische Informationen enthält.  
  
 Alle VSPackage kann entweder Typ Lösungsdatei geschrieben werden. Aufgrund der Natur der Dateien es gibt zwei unterschiedliche Schnittstellen implementiert, um auf diese Laufwerke schreiben. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> Schnittstelle schreibt Informationen in der SLN-Datei und die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> Schnittstelle schreibt binäre Datenströme in der SUO-Datei.  
  
> [!NOTE]
>  Ein Projekt muss nicht explizit einen Eintrag für sich selbst in der Projektmappendatei schreiben; die Umgebung behandelt, die für das Projekt. Deshalb, wenn Sie zusätzliche Inhalte speziell für die Projektmappendatei hinzufügen möchten, müssen nicht Sie das VSPackage auf diese Weise zu registrieren.  
  
 Jedes VSPackage Lösung Persistenz unterstützen drei Schnittstellen verwendet, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> -Schnittstelle, die von der Umgebung implementiert und von dem VSPackage aufgerufen, und `IVsPersistSolutionProps` und `IVsPersistSolutionOpts`, von dem VSPackage sind beide implementiert. Die `IVsPersistSolutionOpts` Schnittstelle muss nur implementiert werden, wenn private Informationen von dem VSPackage in der SUO-Datei geschrieben werden sollen.  
  
 Wenn eine Projektmappe geöffnet ist, findet der folgende Prozess statt.  
  
1.  Die Umgebung liest die Projektmappe.  
  
2.  Wenn die Umgebung findet eine `CLSID`, lädt er die entsprechenden VSPackage.  
  
3.  Wenn eine VSPackage geladen wurde, ist die Umgebung ruft `QueryInterface` für <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> -Schnittstelle, für die Schnittstelle, die das VSPackage erforderlich sind.  
  
    1.  Beim Lesen aus einer sln-Datei, die Umgebung ruft `QueryInterface` für `IVsPersistSolutionProps`.  
  
    2.  Beim Lesen aus einer SUO-Datei, die Umgebung ruft `QueryInterface` für `IVsPersistSolutionOpts`.  
  
 Spezifische Informationen zur Verwendung dieser Dateien befinden sich im [Lösung (. Sln) Datei](../../extensibility/internals/solution-dot-sln-file.md) und [-projektmappenbenutzeroptionen (. Suo) Datei](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
> [!NOTE]
>  Wenn Sie eine neue Projektmappenkonfiguration bestehend aus zwei Projekten Konfigurationen und Ausschließen von einer dritten aus dem Build erstellen möchten, müssen Sie die Eigenschaft Seiten Benutzeroberfläche oder die Automatisierung zu verwenden. Sie können nicht der Manager Projektmappenbuild-Konfigurationen und deren Eigenschaften direkt ändern, aber Sie können den Projektmappen-Build-Manager, die mit Bearbeiten der `SolutionBuild` Klasse von DTE in das Automatisierungsmodell. Weitere Informationen zum Konfigurieren von Lösungen finden Sie unter [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>