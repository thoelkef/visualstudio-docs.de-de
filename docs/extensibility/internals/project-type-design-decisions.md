---
title: Entwurfsentscheidungen Typ projizieren | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c28c6f29454feed94407d6e37c3432247b9a4a26
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="project-type-design-decisions"></a>Projekt Typ Entwurfsentscheidungen
Bevor Sie einen neuen Projekttyp erstellen, müssen Sie mehrere entwurfsentscheidungen hinsichtlich Ihres Projekttyps. Sie müssen entscheiden, welche Arten von Projekten enthaltenen Elemente, wie die Projektdateien beibehalten werden und welche Verpflichtung Modell Sie verwenden möchten.  
  
## <a name="project-items"></a>Projektelemente  
 Werden das Projekt werden Dateien oder abstrakten Objekte verwendet? Wenn Sie Dateien verwenden, werden sie anhand von verweisen oder Directory-basierte Dateien? Gibt die Dateien oder abstrakten Objekte passiert, lokalen oder Remotecomputer sein?  
  
 Die Elemente in einem Projekt kann auf Dateien können, oder es abstrakter Objekte wie z. B. die Objekte in einer Datenbank-Repository oder datenverbindungen über das Internet. Wenn die Elemente Dateien befinden, kann das Projekt einen Verweis basierenden oder ein Verzeichnis-basiertes Projekt sein.  
  
 In verweisbasierten Projekten können die Elemente in mehr als ein Projekt angezeigt werden. Allerdings befindet sich die eigentliche Datei, die ein Element darstellt, in nur einem Verzeichnis. In der Directory-basierte Projekte vorhanden sind alle Projektelemente in der Verzeichnisstruktur ein.  
  
 Lokale Elemente werden auf demselben Computer gespeichert, auf dem die Anwendung installiert ist. Remote-Elemente können auf einem separaten Server in einem lokalen Netzwerk oder an anderer Stelle im Internet gespeichert werden.  
  
## <a name="project-file-persistence"></a>Datei Projektdauerhaftigkeit  
 Werden Daten in gängigen Flatfile-Dateisysteme oder in strukturierten Speicher werden gespeichert? Werden Dateien mit einem standard-Editor oder einem projektspezifischen-Editor werden geöffnet?  
  
 Um ihre Daten beizubehalten, die meisten Anwendungen ihre Daten in einer Datei speichern und dann wieder zur Verfügung, wenn ein Benutzer muss überprüfen oder ändern Sie die Informationen lesen.  
  
 Strukturierter Speicher, so genannte Verbunddateien, wird normalerweise verwendet, wenn mehrere Objekte von Component Object Model (COM) ihre permanenten Daten in einer einzelnen Datei zu speichern müssen. Mit dem strukturierten Speicher können mehrere verschiedenen Softwarekomponenten eine einzelne Datei freigeben.  
  
 Sie haben mehrere Optionen für die hinsichtlich der Persistenz für die Elemente in Ihrem Projekt zu beachten. Sie können eine der folgenden Optionen ausführen:  
  
-   Speichern Sie jede Datei einzeln, wenn es geändert wurde.  
  
-   Erfassen Sie viele Transaktionen in einer einzelnen **speichern** Vorgang.  
  
-   Speichern Sie Dateien lokal, und klicken Sie dann auf einem Server veröffentlichen Sie, oder verwenden Sie ein weiteres Verfahren zum Projektelemente speichern, wenn das Element eine Verbindung mit einem Remoteobjekt darstellt.  
  
 Weitere Informationen zu Persistenz, finden Sie unter [Projektdauerhaftigkeit](../../extensibility/internals/project-persistence.md) und [öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="project-commitment-model"></a>Verpflichtung Projektmodell  
 Persistente Datenobjekte geöffnet werden im direkten oder transaktiven Modus?  
  
 Wenn Datenobjekte im direkten Modus geöffnet sind, werden an den Daten vorgenommenen Änderungen integriert, sofort aus, oder wenn der Benutzer manuell die Datei speichert.  
  
 Wenn Data-Objekte mithilfe von transaktiven Modus geöffnet sind, Änderungen an einem temporären Speicherort im Arbeitsspeicher gespeichert werden und kein Commit ausgeführt, bis der Benutzer manuell zum Speichern der Datei wählt. Zu diesem Zeitpunkt alle Änderungen müssen zusammen auftreten, oder keine Änderungen vorgenommen.  
  
## <a name="see-also"></a>Siehe auch  
 [Prüfliste: Erstellen neuen Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Projektdauerhaftigkeit](../../extensibility/internals/project-persistence.md)   
 [Elemente eines Projekt-Modells](../../extensibility/internals/elements-of-a-project-model.md)   
 [Projekt-Modell-Kernkomponenten](../../extensibility/internals/project-model-core-components.md)   
 [Erstellen von Projekttypen](../../extensibility/internals/creating-project-types.md)