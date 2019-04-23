---
title: Übersicht über domänenspezifische Sprachtools
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e31d9c01ded7754fd10419f3fd0e18d9616a51eb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60078238"
---
# <a name="overview-of-domain-specific-language-tools"></a>Übersicht über domänenspezifische Sprachtools
Domain-Specific-Sprachtools (DSL-Tools), die in Visual Studio gehostet werden, können Sie eine domänenspezifische Sprache zu entwerfen, und generieren Sie dann alle Elemente, die Benutzer benötigen, um Modelle zu erstellen, die von der Sprache basieren.

 Die folgenden Tools gehören zu den DSL-Tools:

- Ein Projekt-Assistent, der verschiedene Projektmappenvorlagen verwendet, um Ihnen die Entwicklung von domänenspezifischen Sprachen zu erleichtern.

- Ein grafischer Designer zum Erstellen und Bearbeiten der domänenspezifischen Sprachdefinition.

- Eine Validierungs-Engine, die sicherstellt, dass die domänenspezifische Sprachdefinition richtig formatiert ist, und bei Problemen Fehler- und Warnmeldungen anzeigt.

- Ein Codegenerator, der eine domänenspezifische Sprachdefinition als Eingabe behandelt und anschließend Quellcode ausgibt.

## <a name="the-dsl-tools-solution"></a>Die Projektmappe für DSL-Tools
 Der DSL-Designer-Assistent stellt die folgenden Projektmappenvorlagen zur Verfügung:

- Aufgabenfluss

- Klassendiagramme

- Minimal Language (Einfache Version der Sprache)

- Komponentenmodelle

- Minimal WPF (Einfache Version von WPF)

- Minimal Windows.Forms (Einfache Version von Windows.Forms)

- DSL-Bibliothek

  Weitere Informationen finden Sie unter [Choosing a Domain-Specific Language Solution Template (Auswählen einer Projektmappenvorlage für eine domänenspezifische Sprache)](../modeling/choosing-a-domain-specific-language-solution-template.md).

  Der Assistent erstellt Visual Studio-Projektmappe, die die folgenden Projekte enthält:

- DSL

   Das DSL-Projekt definiert die domänenspezifische Sprache sowie Tools zum Bearbeiten und für die Verarbeitung.

- **DslPackage**

   DslPackage-Projekt wird bestimmt, wie die Language-Tools in Visual Studio integriert werden.

## <a name="the-dsl-tools-graphical-interface"></a>Die grafische Benutzeroberfläche der DSL-Tools
 Sie können die grafische Benutzeroberfläche der DSL-Tools verwenden, um Elemente und Beziehungen zu Ihrer domänenspezifischen Sprache hinzuzufügen. Wenn Sie die Elemente hinzugefügt haben, können Sie deren Darstellung definieren, indem Sie ihnen Formen zuordnen, Farben anpassen und Decorator-Elemente hinzufügen. Sie können die Elemente auch der Toolbox hinzufügen.

## <a name="validation-in-dsl-tools"></a>Validierung in DSL-Tools
 Die DSL-Tools umfassen eine Validierungsebene, die sicherstellt, dass das Domänenmodell die allgemeinen Anforderungen für die Codegenerierung erfüllt. Wenn Sie Ihre eigene domänenspezifische Sprache erstellen, sollten Sie Ihre eigene Validierung hinzufügen, um die Regeln Ihrer Geschäftslogik auszudrücken. Weitere Informationen zur benutzerdefinierten Validierung finden Sie unter [Validation in a Domain-Specific Language (Validierung in einer domänenspezifischen Sprache)](../modeling/validation-in-a-domain-specific-language.md).

 Es wird empfohlen, eigene domänenspezifische Sprachen während des Entwurfvorgangs häufig zu überprüfen. Wenn Ihre domänenspezifische Sprache Validierungsfehler aufweist, können Sie keinen Quellcode erstellen. Sie können anhand der Vorlagen Quellcode erstellen, indem Sie in der Symbolleiste des Projektmappen-Explorers auf **Alle Vorlagen transformieren** klicken. Auch wenn Sie die Sprachdefinition ändern, sollten Sie anschließend immer **alle Vorlagen transformieren**. Weitere Informationen finden Sie unter [Vorgehensweise: Create a Domain-Specific Language Solution (Vorgehensweise: Erstellen einer Projektmappe für die domänenspezifische Sprache)](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="customization-of-dsl-tools"></a>Anpassen von DSL-Tools
 Sie können zusätzlichen Code zur Verfügung stellen, um das Verhalten des Modells zu verfeinern und Einschränkungen für Ihre Sprache zu definieren. Wenn nötig können Sie auch wichtige Änderungen vornehmen, indem Sie die Textvorlagen ändern.

## <a name="distributing-your-dsl-solution"></a>Verteilen Ihrer DSL-Projektmappe
 DSL-Tools generiert ein Paket, das gehostet wird, in Visual Studio. Das Paket zeigt eine Toolbox, einen DSL-Explorer und andere Benutzeroberflächenelemente an, über die Benutzer mithilfe Ihrer domänenspezifischen Sprache Modelle erstellen können.

 Wenn Sie erstellen und die Lösung für die DSL-Tools in Visual Studio ausführen, ist eine zweite Instanz von Visual Studio Sie für den Benutzer der Sprache Ihrer Domain-Specific Languge dargestellt. Wenn Sie überprüft haben, dass alles einwandfrei funktioniert, können Sie die `.vsix`-Datei verteilen, die um Buildordner des DslPackage-Projekts enthalten ist. Diese Datei kann verwendet werden, um die DSL als Visual Studio-Erweiterung auf anderen Computern zu installieren.  Weitere Informationen finden Sie unter [Deploying Domain-Specific Language Solutions (Bereitstellen von Projektmappen für eine domänenspezifische Sprache)](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Siehe auch

- [Die experimentelle Instanz](../extensibility/the-experimental-instance.md)
- [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)