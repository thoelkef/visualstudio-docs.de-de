---
title: "Projekt Typ Designentscheidungen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Projekttypen, Projekt-Datei-Persistenz"
  - "Engagement-Mechanismen Projekttypen"
  - "Typen, Elemente"
  - "Projekttypen Designentscheidungen"
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Projekt Typ Designentscheidungen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Bevor Sie ein neuer Projekttyp erstellen, müssen Sie einige Entwurfs über den Projekttyp betreffenden Entscheidungen treffen.  Sie müssen festlegen, welche Arten von Elementen die Projekte enthalten, wie Projektdateien beibehalten werden und welche Verpflichtungs Modells verwendet werden sollen.  
  
## Projektelemente  
 Verwendet das Projekt Dateien oder abstrakte Objekten?  Wenn Sie Dateien verwenden, sind sie verweisbasierte oder verzeichnisbasierte Dateien?  Werden die Dateien oder die abstrakten Objekte lokal oder Remot sein?  
  
 Die Elemente in einem Projekt können Dateien sein, oder sie können abstraktere Objekte wie Objekte in einem Repository Datenbank oder Datenverbindungen über das Internet sein.  Wenn die Elemente sind Dateien, kann das Projekt entweder ein verweisbasiertes oder verzeichnisbasiertes Projekt sein.  
  
 In den verweisbasierten Projekten können Elemente in mehreren Projekten verwendet werden.  Allerdings ist die eigentliche Datei, die ein Element darstellt, in nur einem Verzeichnis.  In den verzeichnisbasierten Projekten befinden sich alle Projektelemente in der Verzeichnisstruktur.  Weitere Informationen finden Sie unter [NIB:Item Management in Projects](http://msdn.microsoft.com/de-de/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 Lokalteil wird auf dem gleichen Computer gespeichert, auf dem die Anwendung installiert ist.  Remote Elemente können auf einem separaten Server in einem lokalen Netzwerk oder an einer anderen Stelle im Internet gespeichert werden.  
  
## Projektdatei\-Persistenz  
 Sind Daten in den allgemeinen Flatfile dateisystemen oder strukturiertem Speicher gespeichert werden?  Werden Dateien mit einem Standardwert editors oder einen projektspezifischen Editor geöffnet?  
  
 Um die Daten beizubehalten, speichern die meisten Anwendungen ihre Daten in einer Datei lesen und ihn dann erneut, wenn ein Benutzer die Daten überprüfen oder ändern muss.  
  
 Der strukturierten Speicherung, auch als Verbunddateien, wird normalerweise verwendet, wenn mehrere Objekte \(Component Object Model\) die beibehaltenen Daten in einer einzigen Datei gespeichert werden müssen.  Mit strukturiertem Speicher können verschiedene Softwarekomponenten eine einzelne Datei auf einem Datenträger freigeben.  
  
 Sie haben mehrere Möglichkeiten, Dauerhaftigkeit für die Elemente im Projekt zu berücksichtigen sollten.  Sie können jede der folgenden Optionen aus:  
  
-   Speichern Sie jede Datei einzeln, wenn sie geändert wurde.  
  
-   Zeichnen Sie viele Transaktionen in einem einzigen **Speichern** Vorgang ein.  
  
-   Dateien lokal gespeichert und anschließend auf einem Server veröffentlichen oder einen anderen Ansatz zum Speichern von Projektelementen, wenn das Element eine Datenverbindung zu einem Remoteobjekt darstellt.  
  
 Weitere Informationen zu permanenten Speicher finden Sie unter [Projekt\-Persistenz](../../extensibility/internals/project-persistence.md) und [Öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## Projekt\-Verpflichtungs\-Modell  
 Sind beibehaltene Datenobjekte im Direktbetrieb oder im transaktiven Modus geöffnet?  
  
 Wenn Datenobjekte im Direktbetrieb geöffnet sind, werden Änderungen, die an den Daten vorgenommen wurden, sofort enthalten oder wenn der Benutzer manuell die Datei gespeichert wird.  
  
 Wenn Datenobjekte mithilfe des transaktiven Modus geöffnet werden, werden Änderungen an einem temporären Verzeichnis im Arbeitsspeicher gespeichert und kein Commit ausgeführt, wenn der Benutzer beschließt manuell, um die Datei zu speichern.  Zu diesem Zeitpunkt sind alle Änderungen auftreten oder zusammen keine Änderungen vorgenommen werden.  
  
## Siehe auch  
 [Prüfliste: Erstellen von neuen Typen](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [NIB:Item Management in Projects](http://msdn.microsoft.com/de-de/762e606b-7f44-4b66-97a1-e30a703654a0)   
 [Öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Projekt\-Persistenz](../../extensibility/internals/project-persistence.md)   
 [Elemente eines Projektmodells](../../extensibility/internals/elements-of-a-project-model.md)   
 [Projekt\-Modell\-Kernkomponenten](../../extensibility/internals/project-model-core-components.md)   
 [Erstellen von Projekttypen](../../extensibility/internals/creating-project-types.md)