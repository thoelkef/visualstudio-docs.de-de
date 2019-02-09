---
title: Generieren und Konfigurieren von Apps aus Modellen
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de62cb46c591b554ea4204e88fedbbfa99381fef
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55907606"
---
# <a name="generate-and-configure-your-app-from-models"></a>Generieren und Konfigurieren von Apps aus Modellen
Sie können Teile Ihrer Anwendung aus einem Modell generieren oder konfigurieren.

 Das Modell stellt die Anforderungen direkter dar als der Code. Durch das Ableiten des Verhaltens der Anwendung direkt aus dem Modell können Sie schneller und zuverlässiger auf geänderte Anforderungen reagieren als durch eine Aktualisierung des Codes. Obwohl anfänglich einiger Arbeitsaufwand zum Einrichten der Ableitung erforderlich ist, rentiert sich diese Investition, wenn Sie Änderungen an den Anforderungen erwarten, oder wenn Sie mehrere Varianten des Produkts fertigen möchten.

## <a name="generating-the-code-of-your-application-from-a-model"></a>Generieren des Codes der Anwendung aus einem Modell
 Die einfachste Möglichkeit zum Generieren von Code ist die Verwendung von Textvorlagen. Sie können Code in der gleichen Visual Studio-Projektmappe generieren, in denen Sie das Modell zu halten. Weitere Informationen finden Sie unter:

- [Generieren von Code zur Entwurfszeit mithilfe von T4-Textvorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

- [Generieren von Code für eine domänenspezifische Sprache](../modeling/generating-code-from-a-domain-specific-language.md)

  Diese Methode lässt sich einfach inkrementell anwenden. Beginnen Sie mit einer Anwendung, die nur für einen bestimmten Fall funktioniert, und wählen Sie einige Teile, die vom Modell abweichen sollen. Benennen Sie die Quelldateien dieser Teile um, sodass sie zu Textvorlagendateien (.tt) werden. An diesem Punkt werden die CS-Quelldateien automatisch aus den Vorlagendateien generiert, sodass die Anwendung wie zuvor funktioniert.

  Anschließend können Sie einen Teil des Codes durch einen Textvorlagenausdruck ersetzen, der das Modell liest und diesen Teil der Quelldatei generiert. Mindestens ein Wert des Modells sollte die ursprüngliche Quelle generieren, sodass Sie die Anwendung erneut ausführen können und sie wie zuvor funktioniert. Nachdem Sie verschiedene Modellwerte getestet haben, können Sie damit fortfahren, Vorlagenausdrücke in einem anderen Teil des Codes einzufügen.

  Dank dieser inkrementellen Methode ist die Codegenerierung in der Regel wenig risikoreich. Die entstehenden Anwendungen funktionieren in der Regel fast genauso gut wie eine handgeschriebene Version.

  Wenn Sie allerdings mit einer vorhandenen Anwendung starten, ist möglicherweise viel Umgestaltung erforderlich, um die verschiedenen Verhaltensweisen, die vom Modell gesteuert werden, zu trennen, damit sie unabhängig voneinander variiert werden können. Wir empfehlen, dass Sie diesen Aspekt der Anwendung bewerten, wenn Sie die Kosten des Projekts schätzen.

## <a name="configuring-your-application-from-a-model"></a>Konfigurieren der Anwendung aus einem Modell
 Wenn Sie das Verhalten der Anwendung zur Laufzeit ändern möchten, können Sie nicht die Codegenerierung verwenden, die Quellcode generiert, bevor die Anwendung kompiliert wird. Stattdessen können Sie Ihre Anwendung aus, um das Modell lesen und sein Verhalten entsprechend angepasst entwerfen. Weitere Informationen finden Sie unter:

- [Vorgehensweise: Öffnen Sie ein Modell aus einer Datei im Programmcode](../modeling/how-to-open-a-model-from-file-in-program-code.md)

  Diese Methode kann auch inkrementell übernommen werden, jedoch fällt am Anfang mehr Arbeit an. Sie müssen den Code schreiben, der das Modell liest, und ein Framework einrichten, dessen Werte für die variablen Teile zugänglich sind. Die variablen Teile generisch zu gestalten ist teurer als eine Codegenerierung.

  Eine generische Anwendung funktioniert in der Regel nicht so gut wie die entsprechenden spezifischen Anwendungen. Wenn es auf die Leistung ankommt, sollte der Projektplan eine Bewertung dieses Risikos enthalten.

## <a name="developing-a-derived-application"></a>Entwickeln einer abgeleiteten Anwendung
 Die folgenden allgemeinen Richtlinien könnten hilfreich sein.

-   **Beginnen Sie spezifisch und gehen Sie dann.** Schreiben Sie zuerst eine spezifische Version der Anwendung. Diese Version sollte in einem Satz von Bedingungen funktionieren. Wenn Sie zufrieden sind und sie ordnungsgemäß funktioniert, können Sie einen Teil von ihr aus einem Modell ableiten. Erweitern Sie die abgeleiteten Teile nach und nach.

     Entwerfen Sie beispielsweise eine Website, die über einen bestimmten Satz von Webseiten verfügt, bevor Sie eine Webanwendung entwerfen, die Seiten dargestellt, die in einem Modell definiert sind.

-   **Modellieren Sie die abweichenden Aspekte.** Identifizieren Sie die Aspekte, die entweder zwischen zwei Bereitstellungen oder im Laufe der Zeit, wenn sich die Anforderungen ändern, abweichen werden. Diese Aspekte sollten aus einem Modell abgeleitet werden.

     Z. B. wenn der Satz von Seiten und die Verknüpfungen zwischen ihnen ändern, aber Stil und Format der Seiten ist immer gleich, und klicken Sie dann das Modell sollten die Verknüpfungen beschreiben, aber es muss nicht das Format der Seiten zu beschreiben.

-   **Separate Aspekte.** Wenn die abweichenden Aspekte in unabhängige Bereiche unterteilt werden können, verwenden Sie separate Modelle für jeden Bereich. Mit ModelBus können Sie Vorgänge definieren, die sowohl Modelle als auch Einschränkungen zwischen diesen betreffen.

     Verwenden Sie z. B. ein Modell, um die Navigation zwischen Webseiten und ein anderes Modell zum Definieren des Layouts der Seiten zu definieren.

-   **Modellieren Sie die Anforderung, die nicht in der Projektmappe.** Entwerfen Sie das Modell, sodass sie die benutzeranforderungen beschreiben. Entwerfen Sie aber nicht die Schreibweise entsprechend den abweichenden Aspekten der Implementierung.

     Beispielsweise sollte das Webnavigationsmodell Webseiten und Hyperlinks zwischen diesen darstellen. Das Webnavigationsmodell sollte keine Fragmente von HTML oder Klassen in der Anwendung dar.

-   **Generieren oder interpretieren?** Wenn sich die Anforderungen für eine bestimmte Bereitstellung selten ändern, generieren Sie Programmcode aus dem Modell. Wenn sich die Anforderungen möglicherweise häufig ändern oder gleichzeitig in mehr als einer Variante in der gleichen Bereitstellung existieren können, schreiben Sie die Anwendung so, dass sie ein Modell lesen und interpretieren kann.

     Z. B. Wenn Sie Ihre Website-Modell verwenden, um eine Reihe von unterschiedlichen und separat installierten Websites zu entwickeln, sollten Sie dann Sie den Code des Standorts aus dem Modell generieren. Aber Sie verwenden das Modell zur Steuerung einer Website, die jeden Tag ändert, ist es besser, einen Webserver zu schreiben, der das Modell liest und die Website entsprechend darstellt.

-   **UML oder DSL?** Erwägen Sie die Erstellung der Modellierungsschreibweise mit Stereotypen, um die UML zu erweitern. Definieren Sie eine DSL, wenn es kein UML-Diagramm gibt, das für den Zweck geeignet ist. Verstoßen Sie aber nicht gegen die UML-Standardsemantik.

     Ein UML-Klassendiagramm beispielsweise ist eine Auflistung von Feldern und Pfeilen. Mit dieser Schreibweise können Sie theoretisch alles definieren. Jedoch empfehlen wir nicht, dass Sie das Klassendiagramm verwenden, es sei denn, Sie beschreiben tatsächlich einen Satz von Typen. Beispielsweise könnten Sie Klassendiagramme, um verschiedene Arten von Webseiten beschrieben anpassen.

## <a name="see-also"></a>Siehe auch

- [Generieren von Code für eine domänenspezifische Sprache](../modeling/generating-code-from-a-domain-specific-language.md)
- [Vorgehensweise: Öffnen Sie ein Modell aus einer Datei im Programmcode](../modeling/how-to-open-a-model-from-file-in-program-code.md)
- [Generieren von Code zur Entwurfszeit mithilfe von T4-Textvorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md)