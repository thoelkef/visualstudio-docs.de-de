---
title: "&#220;bersicht &#252;ber Projektmappen | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Projektmappen, Informationen zu Projektmappen"
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# &#220;bersicht &#252;ber Projektmappen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Eine Lösung ist eine Gruppierung von einem oder mehreren Projekten, die zum Erstellen einer Anwendung zusammenarbeiten. Die Projekt\- und Status Informationen zu der Projektmappe in zwei verschiedenen Projektmappendateien gespeichert werden. Die Projektmappendatei \(.sln\) ist ein textbasiertes und Quellcodeverwaltungssystem platziert und von mehreren Benutzern gemeinsam genutzt werden. Die Lösung Benutzeroptionsdatei \(.suo\) ist binär. Daher wird die SUO\-Datei kann nicht unter Quellcode platziert werden und benutzerspezifische Informationen enthält.  
  
 Jedem VSPackage kann auf beide Arten von Projektmappen\-Datei schreiben. Wegen der Art der Dateien es gibt zwei unterschiedliche Schnittstellen implementiert, um in diese schreiben. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> Schnittstelle schreibt Informationen in der SLN\-Datei und die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> Schnittstelle binäre Datenströmen in der SUO\-Datei geschrieben.  
  
> [!NOTE]
>  Ein Projekt muss nicht explizit einen Eintrag für sich selbst in die Projektmappendatei schreiben; die Umgebung, die für das Projekt behandelt werden. Daher, wenn Sie speziell für die Projektmappendatei Weitere Inhalte hinzufügen möchten, müssen nicht Sie Ihr VSPackage auf diese Weise zu registrieren.  
  
 Jede Lösung Persistenz unterstützen VSPackage verwendet drei Schnittstellen, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> \-Schnittstelle, die von der Umgebung implementiert und durch das VSPackage aufgerufen, und `IVsPersistSolutionProps` und `IVsPersistSolutionOpts`, von VSPackages sind beide implementiert. Die `IVsPersistSolutionOpts` Schnittstelle nur implementiert werden, wenn privater Informationen wird durch das VSPackage in der SUO\-Datei geschrieben werden muss.  
  
 Wenn eine Projektmappe geöffnet ist, findet der folgende Prozess.  
  
1.  Die Umgebung liest die Lösung.  
  
2.  Findet die Umgebung eine `CLSID`, lädt er die entsprechenden VSPackage.  
  
3.  Wenn Sie ein VSPackage geladen ist, wird die Umgebung ruft `QueryInterface` für <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> Schnittstelle, für die Schnittstelle, die das VSPackage ist erforderlich.  
  
    1.  Beim Lesen aus einer sln\-Datei, die Umgebung ruft `QueryInterface` für `IVsPersistSolutionProps`.  
  
    2.  Beim Lesen aus einer SUO\-Datei, die Umgebung ruft `QueryInterface` für `IVsPersistSolutionOpts`.  
  
 Spezifische Informationen zur Verwendung dieser Dateien finden Sie im [Lösung \(. Sln\)\-Datei](../../extensibility/internals/solution-dot-sln-file.md) und [Benutzeroptionen bei Projektmappen \(. Datei Suo\)](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
> [!NOTE]
>  Wenn Sie eine neue Projektmappenkonfiguration bestehend aus zwei Projekten Konfigurationen und eine dritte aus dem Build ausschließen erstellen möchten, müssen Sie die Eigenschaft Seiten Benutzeroberfläche oder die Automatisierung verwenden. Sie nicht die Manager Projektmappenbuild\-Konfigurationen und deren Eigenschaften direkt ändern, aber Sie können den Projektmappen\-Build\-Manager, die mit Bearbeiten der `SolutionBuild` Klasse von DTE im Automatisierungsmodell. Weitere Informationen zum Konfigurieren von Lösungen finden Sie unter [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md).  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>