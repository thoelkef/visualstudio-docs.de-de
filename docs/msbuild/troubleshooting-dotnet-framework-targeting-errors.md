---
title: "Troubleshooting .NET Framework Targeting Errors | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.FrameworkTargetingErrors"
  - "MSBuild.ResolveAssemblyReference.FailedToResolveReferenceBecausePrimaryAssemblyInExclusionList"
helpviewer_keywords: 
  - "targeting .NET Framework version [Visual Studio]"
  - "versions [Visual Studio], .NET Framework Client Profile"
  - "multi-targeting"
  - "multitargeting"
  - ".NET Framework Client Profile"
ms.assetid: 830e3e45-9a93-4279-a249-75b84599aefb
caps.latest.revision: 29
caps.handback.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Troubleshooting .NET Framework Targeting Errors
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Thema werden MSBuild\-Fehler, die aufgrund der Bezugsprobleme auftreten können und wie Sie diese Fehler beheben können.  
  
## Sie haben auf ein Projekt oder eine Assembly verwiesen, die auf eine andere Version von .NET Framework abzielt.  
 Sie können Anwendungen erstellen, die auf Projekte oder Assemblys verweisen, die auf andere Versionen von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] abzielen.  Beispielsweise können Sie eine Anwendung erstellen, die das Clientprofil als [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] jedoch Verweisen eine Assembly, die auf .NET Framework 2.0 abzielt.  Wenn Sie ein Projekt erstellen, das auf eine frühere Version [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], Sie keinen Verweis in diesem Projekt auf ein Projekt oder eine Assembly festlegen können, die das Clientprofile für [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] oder [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] selbst abzielt.  Um den Fehler zu beheben, stellen Sie sicher Profilerstellung der Anwendung oder Profile für die dem Profil kompatibel sind das von Projekten oder Assemblys ist die die Anwendung verweist.  
  
## Sie haben für ein Projekt nun eine andere Version von .NET Framework als Zielversion festgelegt.  
 Wenn Sie die Zielversion [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] der Anwendung ändern, ändert Visual Studio einige der Verweise, aber Sie müssen möglicherweise einige Verweise manuell aktualisieren.  Beispielsweise könnte eine der zuvor erwähnten Fehler auf, wenn Sie eine Anwendung ändern, [!INCLUDE[net_v35SP1_long](../msbuild/includes/net_v35sp1_long_md.md)] zuschneiden diese Anwendung Ressourcen oder Einstellungen enthält, die auf dem Clientprofil für [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] basieren.  
  
 Um Anwendungseinstellungen zu arbeiten, öffnen Sie **Projektmappen\-Explorer**, wählen Sie **Alle Dateien anzeigen** aus und bearbeiten dann die Datei app.config im XML\-Editor von Visual Studio.  Ändern Sie die Version in den Einstellungen, um die entsprechende Version von .NET Framework an.  Sie können z. B. die Versionseinstellung von 4.0.0.0 auf 2.0.0.0 ändern.  Entsprechend für eine Anwendung, die Ressourcen hinzugefügt hat, öffnen Sie **Projektmappen\-Explorer** auswählen, die Schaltfläche **Alle Dateien anzeigen**, erweitern **Mein Projekt** \(Visual Basic\) oder **Eigenschaften** \(C\#\) und dann die Resources.resx im XML\-Editor von Visual Studio.  Ändern Sie die Versionseinstellung von 4.0.0.0 auf 2.0.0.0.  
  
 Wenn die Anwendung Ressourcen wie Symbole oder Bitmaps oder Einstellungen wie Datenverbindungszeichenfolgen aufweist, können Sie auch den Fehler beheben, indem Sie alle Elemente auf der Seite **EinstellungenProjekt\-Designer** entfernen und dann die erforderlichen Einstellungen B.  
  
## Sie haben einem Projekt eine andere .NET Framework\-Version als Ziel neu zugewiesen, und Verweise werden nicht aufgelöst.  
 Wenn Sie einem Projekt eine andere Version [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] umleiten, können die Verweise nicht ordnungsgemäß in einigen Fällen auf. Explizite vollqualifizierte Verweise auf Assemblys führen häufig dieses Problem, jedoch beheben, indem Sie die Verweise entfernen, die sich nicht auflösen und sie wieder dem Projekt dann, hinzufügen.  Alternativ können Sie die Projektdatei bearbeiten, um die Verweise zu ersetzen.  Zunächst entfernen Sie Verweise der folgenden Form:  
  
```  
<Reference Include="System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, processorArchitecture=MSIL" />  
```  
  
 Anschließend durch die einfache Form zu ersetzen:  
  
```  
<Reference Include="System.ServiceModel" />  
```  
  
> [!NOTE]
>  Nachdem Sie das Projekt schließen und erneut öffnen, sollte es auch neu erstellen, um sicherzustellen, dass alle Verweise auf korrekt auflösen.  
  
## Siehe auch  
 [Gewusst wie: .NET Framework\-Version als Ziel](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [.NET Framework Client Profile](../Topic/.NET%20Framework%20Client%20Profile.md)   
 [Festlegen einer bestimmten .NET\-Framework\-Zielversion](../ide/targeting-a-specific-dotnet-framework-version.md)   
 [Multitargeting](../msbuild/msbuild-multitargeting-overview.md)