---
title: Verfügbarmachen von Typen für visuelle Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c87f44dd12724c694fc27bae985f5f7fb617e45c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58956830"
---
# <a name="exposing-types-to-visual-designers"></a>Verfügbarmachen von Typen für visuelle Designer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Zugriff auf Klasse und Typdefinitionen erforderlich zur Entwurfszeit um einen visuellen Designer anzuzeigen. Klassen werden aus einem vordefinierten Satz von Assemblys geladen, die die vollständige Abhängigkeit des aktuellen Projekts (Verweise sowie deren Abhängigkeiten) enthalten. Es kann auch erforderlich sein für visuelle Designer zum Zugriff auf Klassen und Typen, die in Dateien, die von benutzerdefinierten Tools erzeugt definiert werden.  
  
 Die [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] und [!INCLUDE[csprcs](../../includes/csprcs-md.md)] Projektsystemen bieten Unterstützung für den Zugriff auf generierte Klassen und Typen über temporäre Portable ausführbare Dateien (temporäre PE-Dateien). Jede Datei, die von einem benutzerdefinierten Tool generierten kann in eine temporäre Assembly kompiliert werden, sodass Typen aus diesen Assemblys geladen und für den Designer verfügbar gemacht werden können. Die Ausgabe der einzelnen benutzerdefinierten Tools in einer separaten temporäre PE-Datei kompiliert, und den Erfolg oder Misserfolg von dieser temporären Kompilierung nur davon abhängig, ob die generierte Datei kompiliert werden kann. Auch wenn ein Projekt nicht als Ganzes erstellen kann, möglicherweise einzelne temporäre PE-Dateien immer noch für Designer zur Verfügung.  
  
 Das Projektsystem bietet vollständige Unterstützung zum Nachverfolgen von Änderungen in die Ausgabedatei eines benutzerdefinierten Tools, vorausgesetzt, dass diese Änderungen auf das Ergebnis der Ausführung des benutzerdefinierten Tools sind. Jedes Mal, wenn das benutzerdefinierte Tool ausgeführt wird, wird eine neue temporäre PE-Datei generiert, und entsprechende Benachrichtigungen für Designer gesendet werden.  
  
> [!NOTE]
>  Da-Datei der temporäre Programmdownloads ausführbare Generation im Hintergrund erfolgt, werden dem Benutzer keine Fehler gemeldet, wenn die Kompilierung schlägt fehl.  
  
 Benutzerdefinierte Tools, die temporäre PE-Support nutzen, müssen die folgenden Regeln entsprechen:  
  
-   `GeneratesDesignTimeSource` muss auf 1 in der Registrierung festgelegt werden.  
  
     Keine ausführbare Datei Programmkompilierung erfolgt ohne diese Einstellung an.  
  
-   Der generierte Code muss in derselben Sprache wie die Einstellung der globalen projektauflistung ab.  
  
     Die temporäre PE-Datei kompiliert wird, unabhängig davon, was das benutzerdefinierte Tool, als die angeforderte Extension in meldet <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> vorausgesetzt, dass `GeneratesDesignTimeSource` in der Registrierung auf 1 festgelegt ist. Die Erweiterung muss nicht vb oder CS jsl sein. Es kann eine beliebige Erweiterung sein.  
  
-   Der vom benutzerdefinierten Tool generierten Code muss gültig sein und muss es kompilieren, zur eigenen Verwendung nur die Gruppe der Verweise im Projekt vorhanden Zeitpunkt <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> Ausführung abgeschlossen ist.  
  
     Wenn eine temporäre PE-Datei kompiliert wird, ist die einzige Quelldatei bereitgestellt, um den Compiler die Ausgabe des benutzerdefinierten Tools. Aus diesem Grund muss ein benutzerdefiniertes Tool, das eine temporäre PE-Datei verwendet Ausgabedateien erstellen, die unabhängig von anderen Dateien in das Projekt kompiliert werden kann.  
  
## <a name="see-also"></a>Siehe auch  
 [Einführung in das BuildManager-Objekt](http://msdn.microsoft.com/50080ec2-c1c9-412c-98ef-18d7f895e7fa)   
 [Implementieren von Einzeldatei-Generatoren](../../extensibility/internals/implementing-single-file-generators.md)   
 [Bestimmen die Standard-Namespace eines Projekts](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Registrieren von Generatoren einzelner Dateien](../../extensibility/internals/registering-single-file-generators.md)
