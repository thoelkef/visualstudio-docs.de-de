---
title: Übersicht über domänenspezifische Sprachtools
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 6942511e325b77aaa3d646b6e84cd833b8b55ab2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49871744"
---
# <a name="overview-of-domain-specific-language-tools"></a>Übersicht über domänenspezifische Sprachtools
Domain-Specific-Sprachtools (DSL-Tools), die in Visual Studio gehostet werden, können Sie eine domänenspezifische Sprache zu entwerfen, und generieren Sie dann alle Elemente, die Benutzer benötigen, um Modelle zu erstellen, die von der Sprache basieren.

 Die folgenden Tools sind in DSL-Tools enthalten:

-   Ein Projektassistent, die unterschiedliche Vorlagen verwendet werden, können Sie mit der Entwicklung Ihrer domänenspezifischen Sprache beginnen.

-   Einem grafischen Designer zum Erstellen und Bearbeiten der Definition einer domänenspezifischen Sprache.

-   Eine Überprüfung-Engine, die sicherstellt, dass die Definition einer domänenspezifischen Sprache wohlgeformt ist, und Fehler und Warnungen angezeigt, wenn Probleme auftreten.

-   Ein Code-Generator, der eine domänenspezifischen Sprachdefinition als Eingabe akzeptiert und Quellcode als Ausgabe erzeugt.

## <a name="the-dsl-tools-solution"></a>Der DSL-Tools-Projektmappe
 Der Domain-Specific-Designer-Assistent bietet die folgenden Vorlagen:

- Aufgabenverlauf

- Klassendiagramme

- Minimale Sprache

- Komponentenmodelle

- Minimaler WPF

- Minimale Windows.Forms

- DSL-Bibliothek

  Weitere Informationen finden Sie unter [Auswählen einer Lösungsvorlage für Domain-Specific Language](../modeling/choosing-a-domain-specific-language-solution-template.md).

  Der Assistent erstellt Visual Studio-Projektmappe, die die folgenden Projekte enthält:

- DSL

   Dsl-Projekt definiert, die einer domänenspezifischen Sprache und der zugehörigen Tools bearbeiten und verarbeiten.

- **DslPackage**

   DslPackage-Projekt wird bestimmt, wie die Language-Tools in Visual Studio integriert werden.

## <a name="the-dsl-tools-graphical-interface"></a>Der Grafischen Benutzeroberfläche des DSL-Tools
 Sie können die grafische Benutzeroberfläche des DSL-Tools verwenden, so Ihre DSL-Elementen und Beziehungen hinzu. Nachdem Sie die Elemente hinzugefügt haben, können Sie ihre Darstellung definieren, indem Sie an, die Formen, Anpassen von Farben und Decorator-Elemente hinzufügen. Sie können auch die Elemente zur Toolbox hinzufügen.

## <a name="validation-in-dsl-tools"></a>Validierung in DSL-Tools
 DSL bietet es sich um eine Ebene der Überprüfung, um sicherzustellen, dass das Domänenmodell die Mindestanforderungen für die codegenerierung erfüllt. Wenn Sie Ihre eigenen domänenspezifischen Sprache erstellen, würden Sie in der Regel eigene Überprüfung, um Ihre Geschäftsregeln für die Logik auszudrücken hinzufügen. Weitere Informationen zu benutzerdefinierten Validierung, finden Sie unter [Validierung in einer domänenspezifischen Sprache](../modeling/validation-in-a-domain-specific-language.md).

 Es wird empfohlen, dass Ihre Domain-Specific Languge häufig, beim Entwerfen überprüfen. Wenn Ihre Domain-Specific Languge Validierungsfehler aufweist, nicht Quellcode generiert werden. Der Prozess zum Generieren von Quellcode aus den Vorlagen wird durchgeführt, indem Sie auf **alle Vorlagen transformieren** auf der Symbolleiste des Projektmappen-Explorer. Wenn Sie die Definition der Sprache ändern, stellen Sie außerdem sicher, **alle Vorlagen transformieren**. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen einer domänenspezifischen Sprachlösung](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="customization-of-dsl-tools"></a>Anpassung der DSL-Tools
 Sie können zusätzlichen Code, um das Verhalten des Modells zu verfeinern und zum Definieren der Einschränkungen für die Sprache angeben. Falls erforderlich, können Sie erhebliche Änderungen vornehmen, indem Sie die Textvorlagen ändern.

## <a name="distributing-your-dsl-solution"></a>Verteilen Ihrer DSL-Projektmappe
 DSL-Tools generiert ein Paket, das gehostet wird, in Visual Studio. Das Paket zeigt eine Toolbox, einem DSL-Explorer und anderen UI-Elementen, die Benutzern das Erstellen von Modellen mit einer domänenspezifischen Sprache zu ermöglichen.

 Wenn Sie erstellen und die Lösung für die DSL-Tools in Visual Studio ausführen, ist eine zweite Instanz von Visual Studio Sie für den Benutzer der Sprache Ihrer Domain-Specific Languge dargestellt. Nachdem Sie überprüft haben, dass alles ordnungsgemäß funktioniert, können Sie verteilen die `.vsix` Datei, die Sie im Ordner "Build" der DslPackage-Projekt finden werden. Diese Datei kann verwendet werden, um die DSL als Visual Studio-Erweiterung auf anderen Computern zu installieren.  Weitere Informationen finden Sie unter [Bereitstellen von domänenspezifischen Sprachlösungen](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Siehe auch

- [Die experimentelle Instanz](../extensibility/the-experimental-instance.md)
- [DSL-Tools – Glossar](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)