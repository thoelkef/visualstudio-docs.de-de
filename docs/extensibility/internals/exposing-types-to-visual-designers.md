---
title: Aussetzen von Typen für visuelle Designer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9067f88b4bf1334e23a548bc6a2cbeb3eac6ad33
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708435"
---
# <a name="expose-types-to-visual-designers"></a>Verfügbar machen von Typen für visuelle Designer
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]müssen zur Entwurfszeit Zugriff auf Klassen- und Typdefinitionen haben, um einen visuellen Designer anzuzeigen. Klassen werden aus einem vordefinierten Satz von Assemblys geladen, die den vollständigen Abhängigkeitssatz des aktuellen Projekts enthalten (Referenzen plus ihre Abhängigkeiten). Visuelle Designer müssen möglicherweise auch auf Klassen und Typen zugreifen, die in Dateien definiert sind, die von benutzerdefinierten Tools generiert werden.

 Die [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] und Projektsysteme bieten Unterstützung für den Zugriff auf generierte Klassen und Typen über temporäre portable ausführbare Dateien (temporäre PEs). Jede Datei, die von einem benutzerdefinierten Tool generiert wird, kann in eine temporäre Assembly kompiliert werden, sodass Typen aus diesen Assemblys geladen und für Designer verfügbar gemacht werden können. Die Ausgabe jedes benutzerdefinierten Tools wird in eine separate temporäre PE kompiliert, und der Erfolg oder Misserfolg dieser temporären Kompilierung hängt nur davon ab, ob die generierte Datei kompiliert werden kann oder nicht. Auch wenn ein Projekt möglicherweise nicht als Ganzes gebaut wird, können die einzelnen temporären PEs für Designer weiterhin verfügbar sein.

 Das Projektsystem bietet vollständige Unterstützung für das Nachverfolgen von Änderungen an der Ausgabedatei eines benutzerdefinierten Tools, vorausgesetzt, dass diese Änderungen das Ergebnis der Ausführung des benutzerdefinierten Tools sind. Jedes Mal, wenn das benutzerdefinierte Tool ausgeführt wird, wird eine neue temporäre PE generiert, und entsprechende Benachrichtigungen werden an Designer gesendet.

> [!NOTE]
> Da die datei zur Generierung der ausführbaren Temporären Programmdatei im Hintergrund vorliegt, werden dem Benutzer keine Fehler gemeldet, wenn die Kompilierung fehlschlägt.

 Benutzerdefinierte Tools, die die temporäre PE-Unterstützung nutzen, müssen die folgenden Regeln befolgen:

- **GeneratesDesignTimeSource** muss in der Registrierung auf 1 gesetzt werden.

     Ohne diese Einstellung findet keine programmierbare Dateikompilierung statt.

- Der generierte Code muss in derselben Sprache wie die globale Projekteinstellung sein.

     Die temporäre PE wird unabhängig davon kompiliert, was <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> das benutzerdefinierte Tool als angeforderte Erweiterung meldet, vorausgesetzt, dass **GeneratesDesignTimeSource** in der Registrierung auf 1 festgelegt ist. Die Erweiterung muss nicht *.vb*, *.cs*oder *.jsl*sein. es kann eine beliebige Erweiterung sein.

- Der vom benutzerdefinierten Tool generierte Code muss gültig sein, und er muss selbst kompilieren, indem er nur den Satz von Verweisen verwendet, die im Projekt zum Zeitpunkt der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> Ausführung vorhanden sind.

     Wenn ein temporäres PE kompiliert wird, ist die einzige Quelldatei, die dem Compiler zur Verfügung gestellt wird, die benutzerdefinierte Werkzeugausgabe. Daher muss ein benutzerdefiniertes Tool, das ein temporäres PE verwendet, Ausgabedateien generieren, die unabhängig von anderen Dateien im Projekt kompiliert werden können.

## <a name="see-also"></a>Weitere Informationen
- [Einführung in das BuildManager-Objekt](https://msdn.microsoft.com/library/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
- [Implementieren von Single-File-Generatoren](../../extensibility/internals/implementing-single-file-generators.md)
- [Registrieren von Ein-Datei-Generatoren](../../extensibility/internals/registering-single-file-generators.md)
