---
title: Übersicht über domänenspezifische Sprachtools
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- Domain-Specific Language
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef80ac1c7e64eb3591e2e6b09de97c77a26e46f8
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85532366"
---
# <a name="overview-of-domain-specific-language-tools"></a>Übersicht über domänenspezifische Sprachtools
Mit DSL-Tools (DSL-Tools), die in Visual Studio gehostet werden, können Sie eine domänenspezifische Sprache entwerfen und dann alle Elemente generieren, die Benutzer benötigen, um auf der Sprache basierende Modelle zu erstellen.

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

  Der Assistent erstellt eine Visual Studio-Projekt Mappe mit den folgenden Projekten:

- DSL

   Das DSL-Projekt definiert die domänenspezifische Sprache sowie Tools zum Bearbeiten und für die Verarbeitung.

- **DslPackage**

   Das dslpackage-Projekt bestimmt, wie die Sprach Tools in Visual Studio integriert werden.

## <a name="the-dsl-tools-graphical-interface"></a>Die grafische Benutzeroberfläche der DSL-Tools
 Sie können die grafische Benutzeroberfläche der DSL-Tools verwenden, um Elemente und Beziehungen zu Ihrer domänenspezifischen Sprache hinzuzufügen. Wenn Sie die Elemente hinzugefügt haben, können Sie deren Darstellung definieren, indem Sie ihnen Formen zuordnen, Farben anpassen und Decorator-Elemente hinzufügen. Sie können die Elemente auch der Toolbox hinzufügen.

## <a name="validation-in-dsl-tools"></a>Validierung in DSL-Tools
 Die DSL-Tools umfassen eine Validierungsebene, die sicherstellt, dass das Domänenmodell die allgemeinen Anforderungen für die Codegenerierung erfüllt. Wenn Sie Ihre eigene domänenspezifische Sprache erstellen, sollten Sie Ihre eigene Validierung hinzufügen, um die Regeln Ihrer Geschäftslogik auszudrücken. Weitere Informationen zur benutzerdefinierten Validierung finden Sie unter [Validation in a Domain-Specific Language (Validierung in einer domänenspezifischen Sprache)](../modeling/validation-in-a-domain-specific-language.md).

 Es wird empfohlen, eigene domänenspezifische Sprachen während des Entwurfvorgangs häufig zu überprüfen. Wenn Ihre domänenspezifische Sprache Validierungsfehler aufweist, können Sie keinen Quellcode erstellen. Sie können anhand der Vorlagen Quellcode erstellen, indem Sie in der Symbolleiste des Projektmappen-Explorers auf **Alle Vorlagen transformieren** klicken. Auch wenn Sie die Sprachdefinition ändern, sollten Sie anschließend immer **alle Vorlagen transformieren**. Weitere Informationen finden Sie unter [Vorgehensweise: Create a Domain-Specific Language Solution (Vorgehensweise: Erstellen einer Projektmappe für die domänenspezifische Sprache)](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="customization-of-dsl-tools"></a>Anpassen von DSL-Tools
 Sie können zusätzlichen Code zur Verfügung stellen, um das Verhalten des Modells zu verfeinern und Einschränkungen für Ihre Sprache zu definieren. Wenn nötig können Sie auch wichtige Änderungen vornehmen, indem Sie die Textvorlagen ändern.

## <a name="distributing-your-dsl-solution"></a>Verteilen Ihrer DSL-Projektmappe
 DSL-Tools generieren ein Paket, das in Visual Studio gehostet wird. Das Paket zeigt eine Toolbox, einen DSL-Explorer und andere Benutzeroberflächenelemente an, über die Benutzer mithilfe Ihrer domänenspezifischen Sprache Modelle erstellen können.

 Wenn Sie die DSL-Tools-Projekt Mappe in Visual Studio erstellen und ausführen, wird in einer zweiten Instanz von Visual Studio gezeigt, wie die domänenspezifische Sprache dem Benutzer der Sprache entspricht. Wenn Sie überprüft haben, dass alles einwandfrei funktioniert, können Sie die `.vsix`-Datei verteilen, die um Buildordner des DslPackage-Projekts enthalten ist. Diese Datei kann verwendet werden, um die DSL als Visual Studio-Erweiterung auf anderen Computern zu installieren.  Weitere Informationen finden Sie unter [Deploying Domain-Specific Language Solutions (Bereitstellen von Projektmappen für eine domänenspezifische Sprache)](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="see-also"></a>Weitere Informationen

- [Die experimentelle Instanz](../extensibility/the-experimental-instance.md)
- [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
