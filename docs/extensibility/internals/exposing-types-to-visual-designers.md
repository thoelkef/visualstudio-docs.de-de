---
title: "-Typen f&#252;r visuelle Designer verf&#252;gbar gemacht | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Typen [Visual Studio SDK] für visuelle Designer verfügbar zu machen"
  - "Designer [Visual Studio SDK]-Typen verfügbar gemacht"
  - "Benutzerdefinierte Tools,-Typen für visuelle Designer verfügbar gemacht"
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# -Typen f&#252;r visuelle Designer verf&#252;gbar gemacht
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] muss der Zugriff auf die Klasse und Typdefinitionen zur Entwurfszeit haben, dass ein visueller Designer anzuzeigen.  Klassen werden von einem vordefinierten Satz von Assemblys geladen, die die komplexe Abhängigkeiten enthalten, die aus dem aktuellen Projekt festgelegt ist \(Verweise sowie die zugehörigen Abhängigkeiten\).  Es ist möglicherweise auch erforderlich für visuelle Designer, Klassen und Typen zuzugreifen, die in benutzerdefinierten Tools generierten Dateien definiert sind.  
  
 Die [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] und [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] Projektsysteme bieten Unterstützung für den Zugriff auf generierten Klassen und Typen durch temporäre portierbare ausführbare Dateien \(temporäre PE\-Datei\).  Jede Datei, die durch ein benutzerdefiniertes Tool generiert wird, kann in eine temporäre Assembly kompiliert werden, sodass Typen von diesen Assemblys geladen werden und Designern verfügbar gemacht werden können.  Die Ausgabe eines benutzerdefinierten Tools ist in einem separaten temporäre PE\-Datei kompiliert, und der Erfolg oder Fehler der temporären Kompilierung nur hängt davon ab, ob die generierte Datei kompiliert werden kann.  Obwohl ein Projekt möglicherweise nicht als Ganzes erstellt, ist möglicherweise einzelnes temporäre PE\-Datei es Designern verfügbar.  
  
 Das Projektsystem bietet vollständige Unterstützung für das Verfolgen von Änderungen in der Ausgabedatei eines benutzerdefinierten Tools, vorausgesetzt, dass diese Änderungen das Ergebnis der Ausführung des benutzerdefinierten Tools sind.  Jedes Mal, wenn das benutzerdefinierte Tool ausgeführt wird, wird eine neue temporäre PE\-Datei generiert, und die entsprechenden Benachrichtigungen werden in Designern gesendet.  
  
> [!NOTE]
>  Da Generierungs ausführbare Datei des temporären Programms im Hintergrund stattfindet, werden keine Fehler an den Benutzer ausgegeben, wenn die Kompilierung schlägt fehl.  
  
 Benutzerdefinierte Tools, die temporäre PE\-Unterstützung nutzen, müssen die folgenden Regeln einhalten:  
  
-   `GeneratesDesignTimeSource` muss bis 1 in der Registrierung festgelegt werden.  
  
     Keine ausführbaren Programms der Kompilierung ohne diese Einstellung findet statt.  
  
-   Der generierte Code muss in derselben Sprache wie die globale Projekteinstellung sein.  
  
     Das temporäre PE\-Datei kompiliert wird, unabhängig davon, welche benutzerdefinierten Tool meldet als die angeforderte Erweiterung in <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> , vorausgesetzt, dass `GeneratesDesignTimeSource` bis 1 in der Registrierung festgelegt ist.  Die Erweiterung muss keine .cs, .vb oder .jsl sein. Es kann eine beliebige Erweiterung sein.  
  
-   Der Code, der vom benutzerdefinierten Tool generiert wird, muss gültig sein, und er muss eigenständig nur mit dem Satz von Verweisen kompilieren, die im Projekt enthalten sind <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> zum Zeitpunkt der Beendigung ausgeführt.  
  
     Wenn eine temporäre PE\-Datei kompiliert wird, ist die einzige Quelldatei, die den Compiler bereitgestellte die benutzerdefinierte Tools.  Daher muss ein benutzerdefiniertes Tool, das eine temporäre PE\-Datei verwendet, Ausgabedateien generiert werden, die unabhängig von anderen Dateien des Projekts kompiliert werden kann.  
  
## Siehe auch  
 [Introduction to the BuildManager Object](http://msdn.microsoft.com/de-de/50080ec2-c1c9-412c-98ef-18d7f895e7fa)   
 [Implementieren von Einzeldatei\-Generatoren](../../extensibility/internals/implementing-single-file-generators.md)   
 [Ermitteln des Standardnamespaces eines Projekts](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Registrieren von Einzeldatei\-Generatoren](../../extensibility/internals/registering-single-file-generators.md)