---
title: "Gewusst wie: Upgrade von Visual C++-Projekten auf Visual Studio 2015 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Projekte [C++], Aktualisieren"
ms.assetid: 9a283ebb-f6d8-49c0-a73e-323979ff56a2
caps.latest.revision: 22
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Gewusst wie: Upgrade von Visual C++-Projekten auf Visual Studio 2015
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Beim ersten Öffnen eines Visual C\+\+\-Projekts, das in einer früheren Version von Visual Studio erstellt wurde, werden Sie evtl. aufgefordert, das Projekt zu aktualisieren. Sie werden mit einer Meldung gefragt, ob Sie auf die neueste Version des Visual C\+\+\-Compilers und der Bibliotheken aktualisieren möchten. Welche Optionen zum Aktualisieren verfügbar sind, hängt davon ab, welche Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zum Erstellen des Projekts verwendet wurde.  
  
 Sie können [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] verwenden, um [!INCLUDE[win8](../debugger/includes/win8_md.md)]\-Projekte, die in [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] erstellt wurden, zu öffnen, zu bearbeiten und zu erstellen. Um ein neues [!INCLUDE[win8](../debugger/includes/win8_md.md)]\-Projekt zu erstellen, müssen Sie jedoch [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] verwenden. \(Um ein [!INCLUDE[win81](../debugger/includes/win81_md.md)]\-Projekt zu erstellen, müssen Sie [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] verwenden.\)  
  
 Um ein Windows 10\-Projekt zu erstellen, müssen Sie [!INCLUDE[vs_dev14](../msbuild/includes/vs_dev14_md.md)] verwenden.  
  
 Wenn Sie nicht zum Aktualisieren des Projekts aufgefordert werden, müssen Sie möglicherweise gar nichts unternehmen, um das Projekt zu aktualisieren. Weitere Informationen finden Sie unter [Portieren, Migrieren und Aktualisieren von Visual Studio\-Projekten](../porting/porting-migrating-and-upgrading-visual-studio-projects.md).  
  
-   Wurde das Projekt \(.vcproj\) in einer Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erstellt, die älter als [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] ist, müssen Sie das Projekt aktualisieren.  
  
-   Wurde das Projekt \(.vcxproj\) in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)], [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] oder [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] erstellt, haben Sie zwei Möglichkeiten:  
  
    -   Sie können das Update überspringen.[!INCLUDE[vs_dev14](../msbuild/includes/vs_dev14_md.md)] lädt das Projekt, ohne Änderungen vorzunehmen, wenn mit SP1, [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] oder [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] auf die Visual C\+\+\-Tools in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] zugegriffen werden kann. Sie können diesen Zugriff aktivieren, indem Sie die Version von Visual Studio, mit der das Projekt erstellt wurde, auf demselben Computer installieren, auf dem [!INCLUDE[vs_dev14](../msbuild/includes/vs_dev14_md.md)] bereitsteht. Weitere Informationen finden Sie unter [Parallele Installation mehrerer Visual Studio\-Versionen](../Topic/Installing%20Visual%20Studio%20Versions%20Side-by-Side.md).  
  
    -   Sie können das Projekt aktualisieren, indem Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] die Berechtigung erteilen, die weiter hinten in diesem Thema beschriebenen Änderungen vorzunehmen. Wenn Ihre Projektmappe mehrere Visual C\+\+\-Projekte enthält, müssen Sie alle aktualisieren.  
  
        > [!NOTE]
        >  Wenn Sie die Aktualisierung bei der ersten Aufforderung ablehnen, können Sie das Projekt später aktualisieren. Wählen Sie dazu die Option **VC\+\+Projekt aktualisieren** im Menü **Projekt** aus. Wenn der Befehl nicht angezeigt wird, ist kein Update erforderlich.  
  
## Aktualisieren eines Visual C\+\+\-Projekts  
 Wenn Sie zulassen, dass [!INCLUDE[vs_dev14](../msbuild/includes/vs_dev14_md.md)] das Projekt automatisch aktualisiert, werden möglicherweise die folgenden Änderungen vorgenommen:  
  
-   Das Projekt wird dahingehend geändert, dass es den [!INCLUDE[vs_dev14](../msbuild/includes/vs_dev14_md.md)]\-Compiler und die Bibliotheken \(PlatformToolset \= VisualStudio v140\) verwendet.  
  
-   Für [!INCLUDE[cppcli](../misc/includes/cppcli_md.md)]\-Projekte wird "TargetFrameworkVersion" in ".NET Framework 4.5.2" geändert.  
  
## Verwenden eines benutzerdefinierten PlatformToolset  
 Wenn Sie weiterhin ein benutzerdefiniertes PlatformToolset in [!INCLUDE[vs_dev14](../msbuild/includes/vs_dev14_md.md)] verwenden möchten, muss das Toolset unter %ProgramFiles%\\MSBuild\\Microsoft.Cpp\\v4.0\\Platforms\\Win32\\PlatformToolsets\\ auf einem x86\-Computer oder unter %ProgramFiles \(x86\)%\\MSBuild\\Microsoft.Cpp\\v4.0\\Platforms\\Win32\\PlatformToolsets\\ auf einem x64\-Computer gespeichert sein. Informationen zum Erstellen eines benutzerdefinierten PlatformToolset finden Sie im Visual C\+\+\-Teamblog im Beitrag zur [systemeigenen Festlegung von Zielversionen in C\+\+](http://go.microsoft.com/fwlink/?LinkId=248587).  
  
## Siehe auch  
 [Portieren, Migrieren und Aktualisieren von Visual Studio\-Projekten](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)