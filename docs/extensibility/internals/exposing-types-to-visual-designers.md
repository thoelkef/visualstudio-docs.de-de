---
title: "Verfügbarmachen von Typen in visuellen Designern | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a85648a95a6651ff62f50b2361b07feba9a58b47
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="exposing-types-to-visual-designers"></a>Verfügbarmachen von Typen in visuellen Designern
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]muss den Zugriff auf die Klasse und Typdefinition zur Entwurfszeit besitzen, einen visuellen Designer angezeigt. Klassen sind aus einem vordefinierten Satz von Assemblys geladen, die vollständige Abhängigkeit des aktuellen Projekts (Verweise sowie ihre Abhängigkeiten) enthalten. Es kann auch erforderlich sein für visuelle Designer zum Zugriff auf Klassen und Typen, die in von benutzerdefinierte Tools generierten definiert sind.  
  
 Die [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] und [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] Projektsystemen bieten Unterstützung für den Zugriff auf generierte Klassen und Typen durch temporäre Portable ausführbare Dateien (temporäre PEs). Jede Datei, die durch ein benutzerdefiniertes Tool generiert kann in eine temporäre Assembly kompiliert werden, sodass Typen aus diesen Assemblys geladen und in Designern verfügbar gemacht werden können. Die Ausgabe der einzelnen benutzerdefinierte Tools in einen separaten temporären PE kompiliert wird, und den Erfolg oder Misserfolg von dieser temporären Kompilierung hängt nur fest, ob die generierte Datei kompiliert werden kann. Auch, wenn ein Projekt nicht als Ganzes erstellen kann, möglicherweise einzelne temporäre PEs trotzdem für Designer zur Verfügung.  
  
 Das Projektsystem bietet vollständige Unterstützung für das Nachverfolgen von Änderungen an die Ausgabedatei ein benutzerdefiniertes Tool, vorausgesetzt, dass diese Änderungen auf das Ergebnis der Ausführung des benutzerdefinierten Tools sind. Jedes Mal, wenn das benutzerdefinierte Tool ausgeführt wird, wird eine neue temporäre PE generiert und in Designern entsprechende Benachrichtigungen gesendet werden.  
  
> [!NOTE]
>  Da temporäre Programmdownloads Generation ausführbare Datei im Hintergrund stattfindet, werden keine Fehler an den Benutzer ausgegeben, wenn die Kompilierung schlägt fehl.  
  
 Benutzerdefinierte Tools, die temporäre PE-Unterstützung nutzen, müssen den folgenden Regeln entsprechen:  
  
-   `GeneratesDesignTimeSource`muss 1 in der Registrierung festgelegt werden.  
  
     Keine Programm ausführbare Datei Kompilierung findet ohne diese Einstellung an.  
  
-   Der generierte Code muss in derselben Sprache wie die globalen projekteinstellung sein.  
  
     Die temporäre PE-Datei kompiliert wird, unabhängig davon, was als erforderliche Erweiterung in das benutzerdefinierte Tool meldet <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> vorausgesetzt, dass `GeneratesDesignTimeSource` in der Registrierung auf 1 festgelegt ist. Die Erweiterung muss nicht vb, cs- oder jsl werden; Es kann eine beliebige Erweiterung sein.  
  
-   Die von benutzerdefinierten Tools generierte Code muss gültig sein und es muss Kompilieren auf eigene verwendet nur die Verweise im Projekt vorhanden zum Zeitpunkt <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> Ausführung abgeschlossen ist.  
  
     Wenn eine temporäre PE-Datei kompiliert wird, ist die einzige Quelldatei bereitgestellt, um den Compiler die Ausgabe des benutzerdefinierten Tools. Aus diesem Grund muss ein benutzerdefiniertes Tool, das eine temporäre PE verwendet Ausgabedateien generiert, die unabhängig von anderen Dateien in das Projekt kompiliert werden kann.  
  
## <a name="see-also"></a>Siehe auch  
 [Einführung in das BuildManager-Objekt](http://msdn.microsoft.com/en-us/50080ec2-c1c9-412c-98ef-18d7f895e7fa)   
 [Implementieren von Einzeldatei Generatoren](../../extensibility/internals/implementing-single-file-generators.md)   
 [Registrieren von Generatoren einzelner Dateien](../../extensibility/internals/registering-single-file-generators.md)