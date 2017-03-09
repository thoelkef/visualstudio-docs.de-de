---
title: "Dialogfeld &quot;Das Projektzielframework ist nicht installiert&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.TargetFrameworkNotFound"
ms.assetid: 64ce8743-d5bd-447e-ba10-54b2aafe109e
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Dialogfeld &quot;Das Projektzielframework ist nicht installiert&quot;
Sie haben ein Projekt geöffnet, das auf ein Framework abzielt, das nicht auf dem Computer installiert ist. Um fortzufahren, müssen Sie eine der Optionen in diesem Dialogfeld auswählen.  
  
> [!NOTE]
>  Jedes Mal, wenn Sie ein neues Framework herunterladen und installieren, müssen Sie Visual Studio neu starten.  
  
## Visual Basic und Visual C\#  
 Wenn Sie ein Visual Basic\- oder ein Visual C\#\-Projekt geöffnet haben, wählen Sie eine der folgenden Optionen aus.  
  
 **Ziel ändern in .NET Framework 4.5. Sie können später wieder zu .NET Framework** *Version*  **zurückwechseln.**  
 Weist das Projekt auf .NET Framework 4.5 neu zu. Sie können die vorherige Version später neu installieren und das Projekt dann neu zuweisen.  
  
 **Das Zielpaket für .NET Framework \<Version\> herunterladen. Das Projekt wird nicht geändert.**  
 Öffnet die Microsoft Download Center\-Website, von der Sie die gewünschte .NET Framework\-Version herunterladen können. Ihr Projekt wird in der Projektmappe entladen. Nachdem Sie das gewünschte Framework heruntergeladen und installiert haben, müssen Sie Visual Studio neu starten und dann das Projekt erneut öffnen.  
  
 **Das Projekt nicht laden.**  
 Lässt das Projekt in der Projektmappe ungeladen. Sie können das gewünschte Framework oder das Profil später installieren und dann das Projekt erneut laden.  
  
## Visual C\+\+  
 Wenn Sie ein Visual C\+\+\-Projekt geöffnet haben, wählen Sie eine der folgenden Optionen aus.  
  
 **Das Zielpaket für .NET Framework** *Version*  **herunterladen. Das Projekt wird nicht geändert.**  
 Öffnet die Microsoft Download Center\-Website, von der Sie die gewünschte .NET Framework\-Version herunterladen können. Nachdem der Download beendet ist, wird das Projekt dieser Version neu zugewiesen. Ihr Projekt wird in der Projektmappe entladen. Nachdem Sie das gewünschte Framework heruntergeladen und installiert haben, müssen Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] neu starten und dann das Projekt erneut öffnen.  
  
 **Das Projekt nicht laden.**  
 Lässt das Projekt in der Projektmappe ungeladen. Sie können das gewünschte Framework oder das Profil später installieren und dann das Projekt erneut laden.  
  
## Siehe auch  
 [Gewusst wie: .NET Framework\-Version als Ziel](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [Troubleshooting .NET Framework Targeting Errors](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)   
 [Hinzufügen von Verweisen](/visual-cpp/ide/adding-references-in-visual-cpp-projects)