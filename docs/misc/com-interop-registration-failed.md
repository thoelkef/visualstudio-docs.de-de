---
title: "COM Interop registration failed | Microsoft Docs"
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
  - "vs.tasklisterror.cannot_register_com2"
ms.assetid: d1b81f8e-66d7-4cfc-96ff-f1436a8f854a
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# COM Interop registration failed
Bei der Registrierung einer Assembly, die Funktionen für COM\-Clients offenlegt, ist ein Fehler aufgetreten.  Der Buildprozess schlägt fehl, wenn dieser Fehler auftritt.  
  
 Assemblys können COM\-Clients Objekte zur Verfügung stellen.  Das Projektsystem enthält eine Eigenschaft, um bereitgestellte Klassen für COM\-Interop zu registrieren sowie eine Typbibliothek zu generieren und zu registrieren, sodass diese Klassen sowohl von Skriptsprachen als auch von Visual Basic 6 verwendet werden können.  
  
 Informationen für das Zugreifen auf die Eigenschaft **Für COM\-Interop registrieren** finden Sie auf der Eigenschaftenseite **Erstellen** im Ordner **Konfigurationseigenschaften**.  
  
 Mögliche Ursachen für diesen Fehler:  
  
-   Generieren einer Typbibliothek für die Assembly nicht möglich.  Es kann sich um ein Festplattenspeicherproblem oder eine gesperrte Datei handeln, wenn die Typbibliothek entweder von Visual Studio oder einem anderen Prozess gesperrt wird.  Typbibliotheken für Assemblys, auf die verwiesen wird, sind eventuell nicht ordnungsgemäß auf dem System registriert.  
  
-   Registrieren der generierten Typbibliothek nicht möglich.  Hierbei kann es sich um ein Zugriffsproblem in der Registrierung handeln.  
  
-   Registrieren der Klassen in der Assembly nicht möglich.  Hierbei kann es sich um ein Zugriffsproblem in der Registrierung handeln.  
  
 **So beheben Sie diesen Fehler**  
  
-   Geben Sie auf dem Computer Speicherplatz frei.  
  
-   Starten Sie bei Problemen mit gesperrten Dateien [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] neu.  
  
-   Vergewissern Sie sich, dass Sie als Administrator oder als Mitglied einer Gruppe angemeldet sind, die eine Zugriffsberechtigung für die Registrierung hat.  
  
## Siehe auch  
 [COM Interoperability in .NET Framework Applications](/dotnet/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications)