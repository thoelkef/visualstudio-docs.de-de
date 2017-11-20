---
title: Im Vergleich zu nicht typisierten Datasets typisierte | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: c83ba0bb-5425-4d47-8891-6b4dbf937701
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 8fda7a1663a8aa9ccbf1f89f2a3b05d74b0a2316
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2017
---
# <a name="typed-vs-untyped-datasets"></a>Typisierte im Vergleich zu nicht typisierten datasets
Ein typisiertes Dataset ist ein Dataset, das zuerst von der Basisklasse abgeleitet wird <xref:System.Data.DataSet> Klasse, und klicken Sie dann mithilfe von Informationen aus der **Dataset-Designer**, die in einer XSD-Datei zum Generieren einer neuen gespeichert wird stark typisierten Dataset-Klasse. Informationen aus dem Schema (Tabellen, Spalten usw.) generiert und in diese neue Datasetklasse als einen Satz von Eigenschaften und Objekte erster Klasse kompiliert. Da ein typisiertes Dataset von der Basisklasse erbt <xref:System.Data.DataSet> -Klasse, übernimmt die typisierte Klasse die Funktionalität der <xref:System.Data.DataSet> Klasse und kann mit Methoden, die eine Instanz von verwendet werden eine <xref:System.Data.DataSet> Klasse als Parameter.  
  
 Ein nicht typisiertes Dataset hat dagegen kein entsprechendes integriertes Schema. Wie in ein typisiertes Dataset, ein nicht typisiertes Dataset enthält Tabellen, Spalten usw. –, aber diese werden nur als Sammlungen verfügbar gemacht. (Allerdings nachdem Sie manuell die Tabellen und andere Datenelemente in ein nicht typisiertes Dataset erstellen, können Sie die Dataset-Struktur als Exportieren eines Schemas mithilfe des Datasets <xref:System.Data.DataSet.WriteXmlSchema%2A> Methode.)  
  
## <a name="contrasting-data-access-in-typed-and-untyped-datasets"></a>Unterschiede beim Datenzugriff in typisierten und nicht typisierten datasets  
 Die Klasse für ein typisiertes Dataset hat ein Objektmodell, in dem die Eigenschaften auf den tatsächlichen Namen der Tabellen und Spalten dauern. Wenn Sie mit einem typisierten Dataset arbeiten, können Sie z. B. eine Spalte verweisen, mit dem folgenden Code:  
  
 [!code-csharp[VbRaddataDatasets#4](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_1.cs)]
 [!code-vb[VbRaddataDatasets#4](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_1.vb)]  
  
 Wenn Sie ein nicht typisiertes Dataset arbeiten, ist im Gegensatz dazu der entsprechende Code auf:  
  
 [!code-csharp[VbRaddataDatasets#5](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_2.cs)]
 [!code-vb[VbRaddataDatasets#5](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_2.vb)]  
  
 Typisierten Zugriff ist nicht nur, einfacher zu lesen, aber auch vollständig von IntelliSense in unterstützten die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **Code-Editor**. Einfacher zu verwenden, sondern enthält die Syntax für das typisierte Dataset für die typüberprüfung zur Kompilierzeit reduziert die Wahrscheinlichkeit von Fehlern beim Zuweisen von Werten zu Dataset-Elemente. Wenn Sie den Namen einer Spalte in der <xref:System.Data.DataSet> -Klasse und kompilieren Sie die Anwendung, erhalten Sie einen Buildfehler. Durch Doppelklicken auf den Buildfehler in der **Aufgabenliste**, können Sie direkt zu der Zeile oder Codezeilen, die Namen der alten Spalte verweisen wechseln. Zugriff auf Tabellen und Spalten in einem typisierten Dataset ist auch zur Laufzeit etwas schneller, da Zugriff zum Zeitpunkt der Kompilierung nicht über Sammlungen zur Laufzeit bestimmt wird.  
  
 Obwohl typisierten "Datasets" viele Vorteile haben, ist ein nicht typisiertes Dataset in einer Vielzahl von Umständen nützlich. Der offensichtlichste Fall sind kein Schema für das Dataset verfügbar ist. Dies kann z. B. auftreten, wenn Ihre Anwendung mit einer Komponente interagiert, die ein Dataset zurückgibt, aber Sie wissen nicht im Voraus dessen Struktur. Ebenso sind Mal, wenn Sie mit Daten arbeiten, die nicht über eine statische, vorhersagbare Struktur verfügt. In diesem Fall ist es unpraktisch, ein typisiertes Dataset zu verwenden, da Sie müssten die typisierte Dataset-Klasse, bei jeder Änderung in der Datenstruktur neu generieren.  
  
 Allgemeiner gesagt ist bestehen häufig, wenn Sie ein Dataset dynamisch erstellt können, ohne ein Schema verfügbar. In diesem Fall wird das Dataset einfach eine praktische Struktur, in der Sie Informationen stets, so lange die Daten in einer relationalen Weise dargestellt werden können. Zur gleichen Zeit können Sie das Dataset-Funktionen, z. B. die Möglichkeit, die Informationen für die Übergabe an einen anderen Prozess oder eine XML-Datei schreiben serialisieren nutzen.

## <a name="see-also"></a>Siehe auch
[DataSet-tools](../data-tools/dataset-tools-in-visual-studio.md)