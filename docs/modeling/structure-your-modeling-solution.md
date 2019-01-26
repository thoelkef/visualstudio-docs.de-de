---
title: Strukturieren der Modellierungslösung
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: eeb63a384498e04f4c720dcfa5485f064d65d44c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54955725"
---
# <a name="structure-your-modeling-solution"></a>Strukturieren der Modellierungslösung

Um Modelle in einem Entwicklungsprojekt effizient zu verwenden, müssen die Teammitglieder gleichzeitig an Modellen aus verschiedenen Teilen des Projekts arbeiten können. In diesem Thema wird ein Schema zum Aufteilen der Anwendung in verschiedene Teile vorgeschlagen, die den Ebenen in einem allgemeinen Ebenendiagramm entsprechen.

Um schnell mit einem Projekt oder Unterprojekt beginnen zu können, ist es hilfreich, über eine Projektvorlage zu verfügen,die der gewählten Projektstruktur folgt. In diesem Thema wird beschrieben, wie eine solche Vorlage erstellt und verwendet wird.

In diesem Thema wird davon ausgegangen, dass Sie an einem Projekt arbeiten, das so groß ist, dass mehrere Teammitglieder erforderlich sind, und an dem möglicherweise mehrere Teams beteiligt sind. Der Code und die Modelle des Projekts sind in einem Quellcodeverwaltungssystem wie z. B. [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] gespeichert. Zumindest einige Teammitglieder verwenden Visual Studio zum Entwickeln von Modellen, und andere Teammitglieder können die Modelle mit anderen Versionen von Visual Studio anzeigen.

Welche Versionen von Visual Studio die einzelnen Tools und Modellierungsfunktionen-Funktionen unterstützen, finden Sie unter [versionsunterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="solution-structure"></a>Projektmappenstruktur

In einem mittleren oder großen Projekt basiert die Struktur des Teams auf der Struktur der Anwendung. Jedes Team verwendet eine Visual Studio-Projektmappe.

### <a name="to-divide-an-application-into-layers"></a>So unterteilen Sie eine Anwendung in Ebenen

1. Lassen Sie die Struktur Ihrer Projektmappen auf der Struktur der Anwendung basieren, etwa einer Webanwendung, Dienstanwendung oder Desktopanwendung. Eine verschiedene allgemeine Architekturen erläutert [Anwendungsarchetypen in der Microsoft-Anwendungsarchitekturanleitung](http://go.microsoft.com/fwlink/?LinkId=196681).

2. Visual Studio-Projektmappe, die wir den Namen die Architektur-Projektmappe zu erstellen. Diese Projektmappe wird zur Erstellung des allgemeinen Entwurfs des Systems verwendet. Es enthält Modelle, jedoch keinen Code.

   Fügen Sie ein Abhängigkeitsdiagramm mit dieser Lösung hinzu. Zeichnen Sie auf das Abhängigkeitsdiagramm die Architektur, die Sie für Ihre Anwendung ausgewählt haben. Das Diagramm kann beispielsweise diese Ebenen und die Abhängigkeiten zwischen ihnen anzeigen: Präsentation; Geschäftslogik; und die Daten.

4. Erstellen Sie ein separates Visual Studio-Projektmappe für jede Ebene im Architekturdiagramm Abhängigkeit an.

   Diese Projektmappen werden verwendet, um den Code für die Ebenen zu entwickeln.

5. Erstellen Sie Modelle, die darstellen, die die Entwürfe der Ebenen und Konzepte, die für alle Ebenen gelten. Ordnen Sie die Modelle so an, dass alle Modelle in der Architektur-Projektmappe und die relevanten Modelle in den einzelnen Ebenen angezeigt werden können.

   Sie können dies mit einem der folgenden Verfahren erreichen. Bei der ersten Alternative wird für jede Ebene ein separates Modellierungsprojekt erstellt, und bei der zweiten wird ein einzelnes Modellierungsprojekt erstellt, das von den Ebenen gemeinsam genutzt wird.

#### <a name="use-a-separate-modeling-project-for-each-layer"></a>Verwenden Sie ein separates Modellierungsprojekt für jede Ebene

1. Erstellen Sie in jeder Ebenenprojektmappe ein Modellierungsprojekt.

   Dieses Modell enthält Diagramme, die die Anforderungen und den Entwurf der jeweiligen Ebene beschrieben werden. Sie können auch Abhängigkeitsdiagramme enthalten, die geschachtelte Ebenen zeigen.

   Sie verfügen jetzt über ein Modell für jede Ebene sowie über ein Modell für die Anwendungsarchitektur. Jedes Modell ist in einer eigenen Projektmappe enthalten. Dies ermöglicht es Teammitgliedern, gleichzeitig an den Ebenen zu arbeiten.

2. Fügen Sie der Architektur-Projektmappe das Modellierungsprojekt jeder Ebenenprojektmappe hinzu. Öffnen Sie hierzu die Architektur-Projektmappe. In **Projektmappen-Explorer**, mit der rechten Maustaste des Knotens Projektmappe, zeigen Sie auf Hinzufügen, und klicken Sie dann auf **vorhandenes Projekt**. Navigieren Sie zum Modellierungsprojekt (.modelproj) in einer Ebenenprojektmappe.

   Jedes Modell wird jetzt in zwei Projektmappen angezeigt: der Start-Projektmappe und der Architektur-Projektmappe.

3. Fügen Sie dem Modellierungsprojekt jeder Ebene ein Abhängigkeitsdiagramm aus. Beginnen Sie mit der eine Kopie des Architekturdiagramms Abhängigkeit. Sie können Teile löschen, die keine Abhängigkeiten des Diagramms abhängig sind.

   Sie können auch Abhängigkeitsdiagramme hinzufügen, die die ausführliche Struktur dieser Ebene darstellen.

   Diese Diagramme werden verwendet, um den Code zu überprüfen, der in dieser Ebene entwickelt wird.

4. Bearbeiten Sie in der Architektur-Projektmappe die Anforderungen und die Entwurfsmodelle für alle Ebenen mit Visual Studio.

   Entwickeln Sie in jeder Ebenenprojektmappe den Code für diese Ebene, der auf das Modell verweist. Wenn Sie die Entwicklung durchführen möchten, ohne den gleichen Computer zum Aktualisieren des Modells zu verwenden, können Sie das Modell lesen und Code entwickeln, indem Sie Versionen von Visual Studio verwenden, die keine Modelle erstellen können. Sie können Code auch aus dem Modell in diesen Versionen generieren.

   Diese Methode stellt sicher, dass keine Störungen von Entwicklern verursacht werden, die die Ebenenmodelle zur gleichen Zeit bearbeiten.

   Da die Modelle getrennt sind, ist es jedoch schwierig, auf allgemeine Konzepte zu verweisen. Jedes Modell muss eine eigene Kopie der Elemente aufweisen, von denen es über andere Ebenen und die Architektur abhängig ist. Das Abhängigkeitsdiagramm in jeder Ebene muss mit der Abhängigkeit Architekturdiagramm synchron gehalten werden. Es ist schwierig, die Synchronisierung beizubehalten, wenn sich diese Elemente ändern, obwohl Sie zu diesem Zweck Tools entwickeln könnten.

#### <a name="use-a-separate-package-for-each-layer"></a>Verwenden Sie ein separates Paket für jede Ebene

1. Fügen Sie in der Projektmappe für jede Ebene das Architektur-Modellierungsprojekt hinzu. In **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektmappenknoten, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **vorhandenes Projekt**. Das einzelne Modellierungsprojekt kann nun aus allen Projektmappen aufgerufen werden: das Projekt für die Architektur und das Entwicklungsprojekt für jede Ebene.

2. Erstellen Sie ein Paket für jede Ebene im shared-Modell: In **Projektmappen-Explorer**, wählen Sie das Modellierungsprojekt. In **UML-Modell-Explorer**mit der rechten Maustaste auf den Modellstammknoten, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **Paket**.

   Jedes Paket enthält Diagramme, die die Anforderungen und den Entwurf der jeweiligen Ebene beschrieben werden.

3. Fügen Sie falls erforderlich, lokale Abhängigkeitsdiagramme für die interne Struktur der einzelnen Ebenen hinzu.

   Diese Methode ermöglicht es, dass die Entwurfselemente der einzelnen Ebenen direkt auf die der Ebenen und gemeinsame Architektur verweisen, von denen sie abhängen.

   Obwohl das gleichzeitige Arbeiten an verschiedenen Paketen Konflikte verursachen kann, sind sie relativ einfach zu lösen, da die Pakete in separaten Dateien gespeichert werden.

## <a name="create-architecture-templates"></a>Erstellen von Architekturvorlagen

In der Praxis nicht alle Visual Studio-Projektmappen zur gleichen Zeit zu erstellen, aber während des Projekts hinzufügen. Sie müssen wahrscheinlich auch die dieselbe Projektmappenstruktur für zukünftige Projekte verwenden. Um schnell neue Projektmappen erstellen zu können, können Sie eine Projektmappen- oder Projektvorlage erstellen. Sie können die Vorlage in einer Visual Studio Integration Extension (VSIX) erfassen, damit Sie sie einfach verteilen und auf anderen Computern installieren können.

Wenn Sie beispielsweise häufig Projektmappen mit Präsentations-, Geschäfts- und Datenebenen verwenden, können Sie eine Vorlage konfigurieren, die neue Projektmappen mit dieser Struktur erstellt.

### <a name="to-create-a-solution-template"></a>So erstellen Sie ein Projektmappenvorlage

1. [Herunterladen und installieren Sie den Assistenten zum Exportieren von Vorlagen](http://go.microsoft.com/fwlink/?LinkId=196686).

2. Erstellen Sie die Projektmappenstruktur, die Sie als Ausgangspunkt für zukünftige Projekte verwenden möchten.

3. Klicken Sie im Menü **Datei** auf **Vorlage als VSIX exportieren**.

   Die **Exportieren der Vorlage als VSIX-Assistenten** wird geöffnet.

4. Folgen Sie den Anweisungen im Assistenten und wählen Sie die Projekte aus, die in die Vorlage aufgenommen werden sollen, geben Sie einen Namen und eine Beschreibung für die Vorlage an, und geben Sie einen Ausgabespeicherort an.

## <a name="watch-a-video"></a>Video ansehen

[Organisieren und Verwalten von Modellen](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-9-organizing-and-managing-your-models)

## <a name="see-also"></a>Siehe auch

- [Verwenden von Modellen im Entwicklungsprozess](../modeling/use-models-in-your-development-process.md)
- [Visual Studio Architecture Tooling Guidance](../modeling/visual-studio-architecture-tooling-guidance.md)
