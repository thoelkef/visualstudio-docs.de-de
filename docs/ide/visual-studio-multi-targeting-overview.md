---
title: "&#220;bersicht &#252;ber die Ausrichtung auf mehrere Zielversionen in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Ausrichtung auf mehrere Zielversionen [Visual Studio]"
  - "Ausrichtung auf mehrere Zielversionen [Visual Studio]"
  - "Ansteuern von .NET Framework-Version [Visual Studio]"
  - "Versionen [Visual Studio], Ansteuern von .NET Framework-Version"
ms.assetid: b1702c33-0672-4ebc-b779-2b324d6ea880
caps.latest.revision: 36
caps.handback.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &#220;bersicht &#252;ber die Ausrichtung auf mehrere Zielversionen in Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In dieser Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] können Sie die Version von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] angeben, die für die Anwendung erforderlich ist.  Wenn Sie diese Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verwenden möchten, um die Entwicklung eines Projekts fortzusetzen, das Sie in einer früheren Version begonnen haben, müssen Sie das Frameworkziel nicht ändern.  Sie können auch eine Projektmappe mit Projekten erstellen, die andere Versionen des Frameworks als Ziel verwenden.  Durch Frameworkziele wird gewährleistet, dass die Anwendung nur Funktionen verwendet, die in der angegebenen Version des Frameworks verfügbar sind.  
  
> [!TIP]
>  Sie können auch Anwendungen für unterschiedliche Plattformen als Ziel verwenden.  Weitere Informationen finden Sie unter [Multitargeting](../msbuild/msbuild-multitargeting-overview.md)  
  
## Frameworkzielfunktionen  
 Frameworkziele umfassen folgende Funktionen:  
  
-   Wenn Sie ein Projekt öffnen, das eine frühere Version von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] als Ziel verwendet, kann [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] das Projekt automatisch aktualisieren oder das Ziel unverändert lassen.  
  
-   Wenn Sie ein Projekt erstellen, können Sie die gewünschte [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Zielversion angeben.  
  
-   Sie können die Version von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] ändern, auf die ein vorhandenes Projekt abzielt.  
  
-   Sie können eine andere [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Version als Zielversion für unterschiedliche Projekte in der gleichen Projektmappe festlegen.  
  
-   Wenn Sie die Version von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] ändern, auf die ein Projekt ausgerichtet ist, werden in [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] alle erforderlichen Änderungen an Verweisen und Konfigurationsdateien vorgenommen.  
  
 Visual Studio kann dynamisch Änderungen in der Entwicklungsumgebung vornehmen, wenn Sie mit einem Projekt arbeiten, das eine frühere [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Version als Ziel hat. Dazu zählen u. a. folgende Aktionen:  
  
-   Filtern von Elementen in den Dialogfeldern **Neues Projekt**, **Neues Element hinzufügen**, **Neuen Verweis hinzufügen** und **Dienstverweis hinzufügen**, um die Optionen auszulassen, die in der Zielversion nicht verfügbar sind.  
  
-   Filtern von benutzerdefinierten Steuerelementen im **Werkzeugkasten**, um die Steuerelemente zu entfernen, die in der Zielversion nicht verfügbar sind, und um nur die neuesten Steuerelemente anzuzeigen, wenn mehrere Steuerelemente für die Zielversion verfügbar sind.  
  
-   Filtern von IntelliSense, um Sprachfunktionen auszulassen, die in der Zielversion nicht verfügbar sind.  
  
-   Filtern von Eigenschaften im Fenster **Eigenschaften**, um die Eigenschaften auszulassen, die in der Zielversion nicht verfügbar sind.  
  
-   Filtern von Menüoptionen, um Optionen auszulassen, die in der Zielversion nicht verfügbar sind.  
  
-   Für Builds werden die Version des Compilers und die Compileroptionen verwendet, die für die Zielversion geeignet sind.  
  
> [!NOTE]
>  Durch Frameworkziele wird nicht garantiert, dass die Anwendung ordnungsgemäß ausgeführt wird.  Sie müssen die Anwendung dennoch testen, um sicherzustellen, dass Sie mit der Zielversion ausgeführt wird.  Sie können keine Frameworkversionen als Ziel verwenden, die älter als .NET Framework 2.0 sind.  
  
## Auswählen einer Zielframeworkversion  
 Wenn Sie ein Projekt erstellen, wählen Sie die [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Zielversion im Dialogfeld **Neues Projekt** aus.  Die Liste der verfügbaren Projektvorlagen wird basierend auf der Auswahl gefiltert.  Für ein vorhandenes Projekt können Sie die Zielversion von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] über das Dialogfeld "Projekteigenschaften" ändern.  Weitere Informationen finden Sie unter [Gewusst wie: .NET Framework\-Version als Ziel](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
> [!NOTE]
>  In den Express\-Editionen von Visual Studio können Sie das Zielframework im Dialogfeld **Neues Projekt** nicht festlegen.  
  
## Auflösen von System\- und Benutzerassemblyverweisen  
 Um eine .NET Framework\-Version als Ziel zu verwenden, müssen Sie zunächst die entsprechenden Assemblyverweise installieren.  Assemblyverweise für die .NET Framework\-Versionen 2.0, 3.0 und 3.5 sind in der Version .NET Framework 3.5 SP1 enthalten, die Sie von der Website [Microsoft Download Center, Microsoft Visual Studio](http://go.microsoft.com/fwlink/?LinkId=227602) herunterladen können.  Assemblyverweise für .NET Framework 3.5 Client Profile, .NET Framework 4, .NET Framework 4 Client Profile und Silverlight sind auch auf der Website [Visual Studio\-Downloads](http://go.microsoft.com/fwlink/?LinkId=179687) verfügbar.  
  
> [!NOTE]
>  Ein .NET Framework Client Profile ist eine Teilmenge von .NET Framework, das einen eingeschränkten Satz von Bibliotheken und Funktionen bereitstellt.  Weitere Informationen zu Client Profile finden Sie unter [.NET Framework Client Profile](../Topic/.NET%20Framework%20Client%20Profile.md).  
  
 Über das Dialogfeld **Verweis hinzufügen** werden Systemassemblys deaktiviert, die nicht zur [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Zielversion gehören, sodass sie nicht versehentlich zu einem Projekt hinzugefügt werden können. \(Systemassemblys sind DLL\-Dateien, die in einer [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Version enthalten sind.\) Verweise, die zu einer .NET Framework\-Version gehören, die älter ist als die Zielversion, werden nicht aufgelöst und Steuerelemente, die von einem solchen Verweis abhängen, können nicht hinzugefügt werden.  Wenn Sie einen solchen Verweis aktivieren möchten, setzen Sie das [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Ziel des Projekts auf eine Version zurück, die den Verweis enthält. Weitere Informationen finden Sie unter [Introduction to the Project Designer](http://msdn.microsoft.com/de-de/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
 Weitere Informationen über Assemblyverweise finden Sie unter [Resolving Assemblies at Design Time](../msbuild/resolving-assemblies-at-design-time.md).  
  
## Aktivieren von LINQ  
 Wenn Sie .NET Framework 3.5 oder eine höhere Version als Ziel verwenden, werden automatisch ein Verweis auf "System.Core" und ein Import auf Projektebene für "System.Linq" \(nur in Visual Basic\) hinzugefügt.  Wenn Sie LINQ\-Features verwenden möchten, müssen Sie zusätzlich Option Infer aktivieren \(nur in Visual Basic\).  Der Verweis und der Import werden automatisch entfernt, wenn Sie die Zielversion auf eine frühere .NET Framework\-Version ändern.  Weitere Informationen finden Sie unter [How to: Create a LINQ Project](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md).  
  
## Siehe auch  
 [Multitargeting](../msbuild/msbuild-multitargeting-overview.md)   
 [.NET Framework Multi\-Targeting for ASP.NET Web Projects](../Topic/.NET%20Framework%20Multi-Targeting%20for%20ASP.NET%20Web%20Projects.md)   
 [Plattformkompatibilität und Systemanforderungen](http://www.microsoft.com/visualstudio/eng/products/compatibility)