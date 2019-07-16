---
title: Im Vergleich zu nicht typisierten Datasets typisierte | Microsoft-Dokumentation
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: c83ba0bb-5425-4d47-8891-6b4dbf937701
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0d02f72a686d0f271e387e550122451db34c019a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68192778"
---
# <a name="typed-vs-untyped-datasets"></a>Typisierte Datasets im Vergleich zu nicht typisierten Datasets
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ein typisiertes Dataset ist ein Dataset, das zuerst von der Basisklasse abgeleitet ist <xref:System.Data.DataSet> Klasse, und klicken Sie dann mithilfe von Informationen aus der **Dataset-Designer**, die in einer XSD-Datei zum Generieren einer neuen gespeichert wird stark typisierte Dataset-Klasse. Informationen aus dem Schema (Tabellen, Spalten usw.) generiert und in diese neue Datasetklasse als einen Satz von Eigenschaften und Objekte erster Klasse kompiliert. Da ein typisiertes Dataset von der Basisklasse erbt <xref:System.Data.DataSet> -Klasse übernimmt die typisierte Klasse die Funktionalität der <xref:System.Data.DataSet> Klasse mit Methoden, die eine Instanz von verwendet werden kann, und wählen Sie eine <xref:System.Data.DataSet> Klasse als Parameter.  
  
 Ein nicht typisiertes Dataset, weist im Gegensatz dazu keine entsprechenden integrierten Schema auf. Wie Sie in ein typisiertes Dataset enthält ein nicht typisiertes Dataset Tabellen, Spalten und So weiter, aber diese werden nur als Sammlungen verfügbar gemacht. (Aber nachdem Sie manuell in den Tabellen und andere Datenelemente in einer nicht typisierten Dataset erstellt haben, können Sie die Struktur des als Exportieren eines Schemas mithilfe des Datasets <xref:System.Data.DataSet.WriteXmlSchema%2A> Methode.)  
  
## <a name="contrasting-data-access-in-typed-and-untyped-datasets"></a>Im Gegensatz hierzu-Datenzugriff in typisierte und nicht typisierte datasets  
 Die Klasse für ein typisiertes Dataset verfügt über ein Objektmodell, das in der die Eigenschaften auf die tatsächlichen Namen der Tabellen und Spalten übernehmen. Wenn Sie mit einem typisierten Dataset arbeiten, können Sie z. B. eine Spalte verweisen, mit Code wie den folgenden:  
  
 [!code-csharp[VbRaddataDatasets#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#4)]
 [!code-vb[VbRaddataDatasets#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#4)]  
  
 Im Gegensatz dazu, wenn Sie mit einem nicht typisierten Dataset arbeiten, ist der entsprechende Code:  
  
 [!code-csharp[VbRaddataDatasets#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#5)]
 [!code-vb[VbRaddataDatasets#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#5)]  
  
 Zugriff auf typisierte Datasets ist nicht nur, leichter zu lesen, aber auch Unterstützung von IntelliSense in der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **Code-Editor**. Einfacher zu verwenden, sondern stellt die Syntax für das typisierte Dataset für die typüberprüfung zur Kompilierzeit stark verringert die Wahrscheinlichkeit von Fehlern beim Zuweisen von Werten zu Dataset-Elemente bereit. Wenn Sie den Namen einer Spalte in Ihrer <xref:System.Data.DataSet> Klasse und die Anwendung anschließend kompilieren, erhalten Sie einen Buildfehler. Durch Doppelklicken auf den Buildfehler in der **Aufgabenliste**, wechseln Sie direkt zu der Zeile oder die Codezeilen, die Namen der alten Spalte verweisen. Zugriff auf Tabellen und Spalten in einem typisierten Dataset ist darüber hinaus zur Laufzeit etwas schneller, da Zugriff zum Zeitpunkt der Kompilierung nicht über Auflistungen zur Laufzeit bestimmt wird.  
  
 Obwohl typisierten "Datasets" viele Vorteile haben, ist ein nicht typisiertes Dataset in einer Vielzahl von Situationen nützlich. Das offensichtlichste Szenario ist, wenn kein Schema für das Dataset verfügbar ist. Dies kann beispielsweise auftreten, wenn Ihre Anwendung interagiert mit einer Komponente, die einen Dataset zurückgibt, aber Sie wissen nicht, im Voraus dessen Struktur. Auf ähnliche Weise, es gibt Zeiten, wenn Sie mit Daten arbeiten, die nicht über eine statische, vorhersagbare Struktur verfügt. In diesem Fall ist es unpraktisch, dass ein typisiertes Dataset verwenden, da Sie müssten die typisierte Dataset-Klasse bei jeder Änderung der Datenstruktur generieren.  
  
 Allgemeiner ausgedrückt, fallen oft können Sie ein Dataset dynamisch erstellt, ohne ein Schema zur Verfügung. In diesem Fall ist das Dataset einfach einer praktischen Struktur, in der Sie Informationen beibehalten können, solange die Daten in einer relationalen Weise dargestellt werden können. Zur gleichen Zeit können Sie nutzen das Dataset-Funktionen, z. B. die Möglichkeit zum Serialisieren von des Daten für die Übergabe an einen anderen Prozess oder eine XML-Datei geschrieben.
