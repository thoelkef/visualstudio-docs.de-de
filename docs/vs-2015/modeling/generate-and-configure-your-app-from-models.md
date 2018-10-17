---
title: Generieren und Konfigurieren von Apps aus Modellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4dc8f572-a09e-4d19-a92d-f1df383e728b
caps.latest.revision: 9
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: c236a0b0896c135035d4d20eecfe5379b62522a3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49240642"
---
# <a name="generate-and-configure-your-app-from-models"></a>Generieren und Konfigurieren von Apps aus Modellen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Teile Ihrer Anwendung aus einem Modell generieren oder konfigurieren. Es kann sich um ein UML- oder ein DSL-Modell handeln.  
  
 Das Modell stellt die Anforderungen direkter dar als der Code. Durch das Ableiten des Verhaltens der Anwendung direkt aus dem Modell können Sie schneller und zuverlässiger auf geänderte Anforderungen reagieren als durch eine Aktualisierung des Codes. Obwohl anfänglich einiger Arbeitsaufwand zum Einrichten der Ableitung erforderlich ist, rentiert sich diese Investition, wenn Sie Änderungen an den Anforderungen erwarten, oder wenn Sie mehrere Varianten des Produkts fertigen möchten.  
  
## <a name="generating-the-code-of-your-application-from-a-model"></a>Generieren des Codes der Anwendung aus einem Modell  
 Die einfachste Möglichkeit zum Generieren von Code ist die Verwendung von Textvorlagen. Sie können Code generieren, in der gleichen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Lösung, die in dem Sie das Modell speichern. Weitere Informationen finden Sie unter:  
  
-   [Generieren von Code zur Entwurfszeit mithilfe von T4-Textvorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md)  
  
-   [Generieren von Dateien von einem UML-Modell](../modeling/generate-files-from-a-uml-model.md)  
  
-   [Generieren von Code für eine domänenspezifische Sprache](../modeling/generating-code-from-a-domain-specific-language.md)  
  
 Diese Methode lässt sich einfach inkrementell anwenden. Beginnen Sie mit einer Anwendung, die nur für einen bestimmten Fall funktioniert, und wählen Sie einige Teile, die vom Modell abweichen sollen. Benennen Sie die Quelldateien dieser Teile um, sodass sie zu Textvorlagendateien (.tt) werden. An diesem Punkt werden die CS-Quelldateien automatisch aus den Vorlagendateien generiert, sodass die Anwendung wie zuvor funktioniert.  
  
 Anschließend können Sie einen Teil des Codes durch einen Textvorlagenausdruck ersetzen, der das Modell liest und diesen Teil der Quelldatei generiert. Mindestens ein Wert des Modells sollte die ursprüngliche Quelle generieren, sodass Sie die Anwendung erneut ausführen können und sie wie zuvor funktioniert. Nachdem Sie verschiedene Modellwerte getestet haben, können Sie damit fortfahren, Vorlagenausdrücke in einem anderen Teil des Codes einzufügen.  
  
 Dank dieser inkrementellen Methode ist die Codegenerierung in der Regel wenig risikoreich. Die entstehenden Anwendungen funktionieren in der Regel fast genauso gut wie eine handgeschriebene Version.  
  
 Wenn Sie allerdings mit einer vorhandenen Anwendung starten, ist möglicherweise viel Umgestaltung erforderlich, um die verschiedenen Verhaltensweisen, die vom Modell gesteuert werden, zu trennen, damit sie unabhängig voneinander variiert werden können. Wir empfehlen, dass Sie diesen Aspekt der Anwendung bewerten, wenn Sie die Kosten des Projekts schätzen.  
  
## <a name="configuring-your-application-from-a-model"></a>Konfigurieren der Anwendung aus einem Modell  
 Wenn Sie das Verhalten der Anwendung zur Laufzeit ändern möchten, können Sie nicht die Codegenerierung verwenden, die Quellcode generiert, bevor die Anwendung kompiliert wird. Stattdessen können Sie die Anwendung so entwerfen, dass sie das UML- oder DSL-Modell liest und ihr Verhalten entsprechend anpasst. Weitere Informationen finden Sie unter:  
  
-   [Lesen eines UML-Modells im Programmcode](../modeling/read-a-uml-model-in-program-code.md)  
  
-   [Gewusst wie: Öffnen eines Modells aus einer Datei im Programmcode](../modeling/how-to-open-a-model-from-file-in-program-code.md)  
  
 Diese Methode kann auch inkrementell übernommen werden, jedoch fällt am Anfang mehr Arbeit an. Sie müssen den Code schreiben, der das Modell liest, und ein Framework einrichten, dessen Werte für die variablen Teile zugänglich sind. Die variablen Teile generisch zu gestalten ist teurer als eine Codegenerierung.  
  
 Eine generische Anwendung funktioniert in der Regel nicht so gut wie die entsprechenden spezifischen Anwendungen. Wenn es auf die Leistung ankommt, sollte der Projektplan eine Bewertung dieses Risikos enthalten.  
  
## <a name="developing-a-derived-application"></a>Entwickeln einer abgeleiteten Anwendung  
 Die folgenden allgemeinen Richtlinien könnten hilfreich sein.  
  
-   **Beginnen Sie spezifisch und gehen Sie dann.** Schreiben Sie zuerst eine spezifische Version der Anwendung. Diese Version sollte in einem Satz von Bedingungen funktionieren. Wenn Sie zufrieden sind und sie ordnungsgemäß funktioniert, können Sie einen Teil von ihr aus einem Modell ableiten. Erweitern Sie die abgeleiteten Teile nach und nach.  
  
     Entwerfen Sie beispielsweise eine Website, die über einen bestimmten Satz von Webseiten verfügt, bevor Sie eine Webanwendung entwerfen, die Seiten dargestellt, die in einem Modell definiert sind.  
  
-   **Modellieren Sie die abweichenden Aspekte.** Identifizieren Sie die Aspekte, die entweder zwischen zwei Bereitstellungen oder im Laufe der Zeit, wenn sich die Anforderungen ändern, abweichen werden. Diese Aspekte sollten aus einem Modell abgeleitet werden.  
  
     Wenn sich beispielsweise der Satz von Webseiten und die Verknüpfungen zwischen ihnen ändern, Stil und Format der Seiten jedoch immer gleich sind, sollte das Modell die Verknüpfungen beschreiben, aber nicht unbedingt das Format der Seiten.  
  
-   **Separate Aspekte.** Wenn die abweichenden Aspekte in unabhängige Bereiche unterteilt werden können, verwenden Sie separate Modelle für jeden Bereich. Mit ModelBus können Sie Vorgänge definieren, die sowohl Modelle als auch Einschränkungen zwischen diesen betreffen.  
  
     Verwenden Sie beispielsweise ein Modell, um die Navigation zwischen Webseiten zu definieren, und ein anderes Modell, um das Layout der Seiten zu definieren. Weitere Informationen finden Sie unter [Integrieren von UML-Modellen in andere Modelle und Tools](../modeling/integrate-uml-models-with-other-models-and-tools.md).  
  
-   **Modellieren Sie die Anforderung, die nicht in der Projektmappe.** Entwerfen Sie die DSL oder passen Sie die UML an, sodass sie die Benutzeranforderungen beschreiben. Entwerfen Sie aber nicht die Schreibweise entsprechend den abweichenden Aspekten der Implementierung.  
  
     Zum Beispiel sollte das Webnavigationsmodell Webseiten und Hyperlinks zwischen diesen darstellen. Das Webnavigationsmodell sollte keine Fragmente von HTML oder Klassen in der Anwendung darstellen.  
  
-   **Generieren oder interpretieren?** Wenn sich die Anforderungen für eine bestimmte Bereitstellung selten ändern, generieren Sie Programmcode aus dem Modell. Wenn sich die Anforderungen möglicherweise häufig ändern oder gleichzeitig in mehr als einer Variante in der gleichen Bereitstellung existieren können, schreiben Sie die Anwendung so, dass sie ein Modell lesen und interpretieren kann.  
  
     Wenn Sie beispielsweise Ihr Websitemodell verwenden, um eine Reihe von unterschiedlichen und separat installierten Websites zu entwickeln, sollten Sie den Code der Website aus dem Modell generieren. Wenn Sie das Modell hingegen zur Steuerung einer Website verwenden, die sich jeden Tag ändert, ist es besser, einen Webserver zu schreiben, der das Modell liest und die Website entsprechend darstellt.  
  
-   **UML oder DSL?** Erwägen Sie die Erstellung der Modellierungsschreibweise mit Stereotypen, um die UML zu erweitern. Definieren Sie eine DSL, wenn es kein UML-Diagramm gibt, das für den Zweck geeignet ist. Verstoßen Sie aber nicht gegen die UML-Standardsemantik.  
  
     Ein UML-Klassendiagramm beispielsweise ist eine Auflistung von Feldern und Pfeilen. Mit dieser Schreibweise können Sie theoretisch alles definieren. Jedoch empfehlen wir nicht, dass Sie das Klassendiagramm verwenden, es sei denn, Sie beschreiben tatsächlich einen Satz von Typen. Beispielsweise könnten Sie Klassendiagramme so anpassen,dass verschiedene Arten von Webseiten beschrieben werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Generieren von Dateien aus einem UML-Modell](../modeling/generate-files-from-a-uml-model.md)   
 [Lesen eines UML-Modells im Programmcode](../modeling/read-a-uml-model-in-program-code.md)   
 [Generieren von Code aus einer domänenspezifischen Sprache](../modeling/generating-code-from-a-domain-specific-language.md)   
 [Vorgehensweise: Öffnen Sie ein Modell aus einer Datei im Programmcode](../modeling/how-to-open-a-model-from-file-in-program-code.md)   
 [Generieren von Code zur Entwurfszeit mithilfe von T4-Textvorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md)



