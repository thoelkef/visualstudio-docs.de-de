---
title: "Parallele Installation mehrerer Visual Studio-Versionen | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Parallele Installationen [Visual Studio]"
  - "Installieren von Visual Studio, Installieren"
  - "Express Edition [Visual Studio]"
ms.assetid: 4d00f240-4910-4699-aaf3-cda6461f0c29
caps.latest.revision: 48
caps.handback.revision: 47
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# Parallele Installation mehrerer Visual Studio-Versionen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können diese Visual Studio\-Version auf einem Computer installieren, auf dem bereits eine frühere Version von Visual Studio installiert ist. Im Falle eines Installationsfehlers können Sie das [Protokollerfassungstool](http://go.microsoft.com/fwlink/?LinkId=262077) nutzen, um Informationen über die Fehler zu erfassen, sodass Sie Probleme selber beheben können.  
  
> [!NOTE]
>  Es wird empfohlen, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Versionen in der Reihenfolge installieren, in der sie veröffentlicht wurden. Installieren Sie beispielsweise Visual Studio 2013, bevor Sie Visual Studio 2015 installieren.  
  
 Bevor Sie Versionen parallel installieren, sollten Sie die folgenden Bedingungen kennen:  
  
-   Wenn Sie Visual Studio 2015 verwenden, um eine Projektmappe zu öffnen, die in [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] erstellt wurde, können Sie die Projektmappe später erneut in der früheren Version öffnen und ändern, sofern Sie keine Funktionen implementiert haben, die für Visual Studio 2015 spezifisch sind.  
  
-   Wenn Sie versuchen, eine Projektmappe mit Visual Studio 2015 zu öffnen, die mit [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] oder einer früheren Version erstellt wurde, müssen Sie gegebenenfalls ihre Projekte und Dateien ändern, damit diese mit Visual Studio 2015 kompatibel sind. Weitere Informationen finden Sie unter [Portieren, Migrieren und Aktualisieren von Visual Studio\-Projekten](../porting/porting-migrating-and-upgrading-visual-studio-projects.md).  
  
-   Wenn Sie eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Version auf einem Computer deinstallieren, auf dem mehrere Versionen installiert sind, werden die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Dateizuordnungen für alle Versionen entfernt. Sie können diesen Dateizuordnungen mit der Schaltfläche **Dateizuordnungen wiederherstellen** auf der Seite **Umgebung**, **Allgemein** des Dialogfelds [Optionen](../ide/reference/general-environment-options-dialog-box.md) neu vornehmen.  
  
-   Visual Studio aktualisiert die Erweiterungen nicht automatisch, da nicht alle Erweiterungen kompatibel sind. Installieren Sie erneut die Erweiterungen aus der [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkId=178891) oder vom Herausgeber der Software.  
  
## .NET Framework\-Versionen und parallele Installationen  
  
-   Visual Basic, Visual C\# und Visual F\#\-Projekte nutzen die Option **Zielframework** im **Projekt\-Designer**, um festzulegen, welche Version von .NET Framework ein Projekt verwendet. Für ein C\+\+\-Projekt können Sie das Zielframework durch Bearbeiten der Projektdatei \(.vcxproj\) ändern. Weitere Informationen finden Sie unter [Versionskompatibilität](../Topic/Version%20Compatibility%20in%20the%20.NET%20Framework.md).  
  
     Wenn Sie ein Projekt erstellen, können Sie angeben, auf welche Version von .NET Framework das Projekt in der Liste **.NET Framework** im Dialogfeld **Neues Projekt** abzielt.  
  
     Sprachspezifische Informationen finden Sie im entsprechenden Thema in der folgenden Tabelle.  
  
    |Sprache|Thema|  
    |-------------|-----------|  
    |[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]|[Seite "Anwendung", Projekt\-Designer \(Visual Basic\)](../ide/reference/application-page-project-designer-visual-basic.md)|  
    |Visual C\#|[Seite "Anwendung", Projekt\-Designer \(C\#\)](../ide/reference/application-page-project-designer-csharp.md)|  
    |Visual F\#|[Configuring Projects](../Topic/Configuring%20Projects%20\(F%23\).md)|  
    |C\+\+|[Gewusst wie: Ändern des Zielframeworks und des Plattformtoolsets](../Topic/How%20to:%20Modify%20the%20Target%20Framework%20and%20Platform%20Toolset.md)|  
    |[!INCLUDE[jsprjscript](../debugger/debug-interface-access/includes/jsprjscript_md.md)]|[Ausführen einer JScript\-Anwendung auf einer früheren Version der Common Language Runtime](http://msdn.microsoft.com/de-de/bbea51b5-ac03-4e6c-b9a6-f487ef63eda5)|  
  
## Siehe auch  
 [Installieren von Visual Studio](../Topic/Installing%20Visual%20Studio%202015.md)   
 [Portieren, Migrieren und Aktualisieren von Visual Studio\-Projekten](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)   
 [Versionskompatibilität](../Topic/Version%20Compatibility%20in%20the%20.NET%20Framework.md)   
 [Installieren mehrerer Sprachversionen von Visual Studio](../Topic/Installing%20Multiple%20Language%20Versions%20of%20Visual%20Studio.md)   
 [Erstellen von isolierten Anwendungen und parallelen Assemblys \(C\/C\+\+\)](/visual-cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies)   
 [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3)