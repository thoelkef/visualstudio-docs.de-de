---
title: Verfügbar machen von Typen für visuelle Designer | Microsoft-Dokumentation
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
ms.openlocfilehash: f4d6c0e163b751f1873fdb941e85c273dcc4fde5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691202"
---
# <a name="exposing-types-to-visual-designers"></a>Verfügbarmachen von Typen für visuelle Designer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] muss zur Entwurfszeit über Zugriff auf Klassen-und Typdefinitionen verfügen, um einen visuellen Designer anzuzeigen. Klassen werden aus einem vordefinierten Satz von Assemblys geladen, die den gesamten Abhängigkeits Satz des aktuellen Projekts (Verweise zuzüglich ihrer Abhängigkeiten) enthalten. Es kann auch erforderlich sein, dass visuelle Designer auf Klassen und Typen zugreifen können, die in Dateien definiert sind, die von benutzerdefinierten Tools generiert werden.  
  
 Die [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] Projektsysteme und bieten Unterstützung für den Zugriff auf generierte Klassen und Typen über temporäre portable ausführbare Dateien (temporäre PES). Alle Dateien, die von einem benutzerdefinierten Tool generiert werden, können in eine temporäre Assembly kompiliert werden, sodass Typen aus diesen Assemblys geladen und für Designer verfügbar gemacht werden können. Die Ausgabe der einzelnen benutzerdefinierten Tools wird in eine separate temporäre PE-Datei kompiliert, und der Erfolg oder Misserfolg dieser temporären Kompilierung hängt nur davon ab, ob die generierte Datei kompiliert werden kann. Obwohl ein Projekt nicht als Ganzes erstellt werden kann, sind einzelne temporäre PES möglicherweise weiterhin für Designer verfügbar.  
  
 Das Projekt System bietet vollständige Unterstützung für das Nachverfolgen von Änderungen an der Ausgabedatei eines benutzerdefinierten Tools, vorausgesetzt, dass diese Änderungen das Ergebnis der Ausführung des benutzerdefinierten Tools sind. Jedes Mal, wenn das benutzerdefinierte Tool ausgeführt wird, wird ein neues temporäres PE generiert, und die entsprechenden Benachrichtigungen werden an die Designer gesendet.  
  
> [!NOTE]
> Da die ausführbare Datei der ausführbaren Programmdatei im Hintergrund ausgeführt wird, werden dem Benutzer keine Fehler gemeldet, wenn die Kompilierung fehlschlägt.  
  
 Benutzerdefinierte Tools, die temporäre PE-Unterstützung nutzen, müssen die folgenden Regeln einhalten:  
  
- `GeneratesDesignTimeSource` muss in der Registrierung auf 1 festgelegt werden.  
  
     Ohne diese Einstellung erfolgt keine Kompilierung der Programm ausführbaren Datei.  
  
- Der generierte Code muss sich in derselben Sprache wie die globale Projekteinstellung befinden.  
  
     Das temporäre PE wird unabhängig davon kompiliert, was das benutzerdefinierte Tool als die angeforderte Erweiterung meldet <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> , sofern in `GeneratesDesignTimeSource` der Registrierung auf 1 festgelegt ist. Die Erweiterung muss nicht ". vb", ". cs" oder ". jsl" lauten. Dabei kann es sich um eine beliebige Erweiterung handeln.  
  
- Der vom benutzerdefinierten Tool generierte Code muss gültig sein, und er muss nur mit dem Satz von verweisen kompiliert werden, der zum Zeitpunkt der Ausführung des Projekts im Projekt vorhanden ist <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> .  
  
     Wenn ein temporäres PE kompiliert wird, ist die einzige für den Compiler bereitgestellte Quelldatei die Ausgabe des benutzerdefinierten Tools. Daher muss ein benutzerdefiniertes Tool, das ein temporäres PE verwendet, Ausgabedateien generieren, die unabhängig von anderen Dateien im Projekt kompiliert werden können.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Einführung in das BuildManager-Objekt](https://msdn.microsoft.com/50080ec2-c1c9-412c-98ef-18d7f895e7fa)   
 [Implementieren von Einzel Datei-Generatoren](../../extensibility/internals/implementing-single-file-generators.md)   
 [Bestimmen des Standard Namespace eines Projekts](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Registrieren von Generatoren einzelner Dateien](../../extensibility/internals/registering-single-file-generators.md)
