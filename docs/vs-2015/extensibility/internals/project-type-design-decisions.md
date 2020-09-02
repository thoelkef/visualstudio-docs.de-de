---
title: Entwurfsentscheidungen für Projekttyp | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cd26e08ab153e96fc601e89788008cb0e9ca38c8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704082"
---
# <a name="project-type-design-decisions"></a>Entwurfsentscheidungen bei Projekttypen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bevor Sie einen neuen Projekttyp erstellen, müssen Sie für den Projekttyp einige Entwurfsentscheidungen treffen. Sie müssen entscheiden, welche Typen von Elementen in Ihren Projekten enthalten sein sollen, wie Projektdateien persistent gespeichert werden und welches Verpflichtungs Modell Sie verwenden werden.  
  
## <a name="project-items"></a>-Projektelemente  
 Werden in Ihrem Projektdateien oder abstrakte Objekte verwendet? Wenn Sie Dateien verwenden, handelt es sich um Verweis basierte oder Verzeichnis basierte Dateien? Werden die Dateien oder abstrakten Objekte lokal oder Remote sein?  
  
 Die Elemente in einem Projekt können Dateien sein, oder es kann sich um abstraktere Objekte handeln, z. b. Objekte in einem Datenbankrepository oder Datenverbindungen über das Internet. Wenn es sich bei den Elementen um Dateien handelt, kann das Projekt entweder ein Verweis basiertes oder ein Verzeichnis basiertes Projekt sein.  
  
 In Verweis basierten Projekten können Elemente in mehr als einem Projekt angezeigt werden. Die tatsächliche Datei, die ein Element darstellt, befindet sich jedoch nur in einem Verzeichnis. In Verzeichnis basierten Projekten sind alle Projekt Elemente in der Verzeichnisstruktur vorhanden. Weitere Informationen finden Sie unter [NIB: Element Verwaltung in Projekten](https://msdn.microsoft.com/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 Lokale Elemente werden auf demselben Computer gespeichert, auf dem die Anwendung installiert ist. Remote Elemente können auf einem separaten Server in einem lokalen Netzwerk oder an einer anderen Stelle im Internet gespeichert werden.  
  
## <a name="project-file-persistence"></a>Persistenz von Projektdateien  
 Werden Daten in gängigen Flatfile-Systemen oder in strukturiertem Speicher gespeichert? Werden Dateien mit einem Standard-Editor oder einem projektspezifischen Editor geöffnet?  
  
 Um Ihre Daten beizubehalten, speichern die meisten Anwendungen Ihre Daten in einer Datei und lesen Sie dann zurück, wenn ein Benutzer die Informationen überprüfen oder ändern muss.  
  
 Strukturierter Speicher, auch als Verbund Dateien bezeichnet, wird normalerweise verwendet, wenn mehrere Component Object Model (com)-Objekte ihre beibehaltenen Daten in einer einzigen Datei speichern müssen. Mit strukturiertem Speicher können mehrere verschiedene Softwarekomponenten eine einzelne Datenträger Datei gemeinsam verwenden.  
  
 Sie haben mehrere Optionen in Bezug auf die Persistenz für die Elemente in Ihrem Projekt. Sie können eine der folgenden Optionen ausführen:  
  
- Speichern Sie jede Datei einzeln, wenn Sie geändert wurde.  
  
- Erfassen Sie viele Transaktionen in einem einzelnen **Speicher** Vorgang.  
  
- Speichern Sie Dateien lokal, und veröffentlichen Sie Sie auf einem Server, oder verwenden Sie einen anderen Ansatz zum Speichern von Projekt Elementen, wenn das Element eine Datenverbindung zu einem Remote Objekt darstellt.  
  
  Weitere Informationen zur Persistenz finden Sie unter [Projekt Persistenz](../../extensibility/internals/project-persistence.md) und [Öffnen und Speichern von Projekt Elementen](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="project-commitment-model"></a>Projekt Verpflichtungs Modell  
 Werden persistente Datenobjekte im direkt Modus oder im Transaktionsmodus geöffnet?  
  
 Wenn Datenobjekte im direkten Modus geöffnet werden, werden Änderungen, die an den Daten vorgenommen wurden, sofort eingefügt, oder wenn der Benutzer die Datei manuell speichert.  
  
 Wenn Datenobjekte mit dem transaktiven Modus geöffnet werden, werden Änderungen an einem temporären Speicherort im Arbeitsspeicher gespeichert, und es wird erst dann ein Commit ausgeführt, wenn der Benutzer die Datei manuell speichert. Zu diesem Zeitpunkt müssen alle Änderungen gleichzeitig erfolgen, oder es werden keine Änderungen vorgenommen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Prüfliste: Erstellen neuer Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [NIB: Element Verwaltung in Projekten](https://msdn.microsoft.com/762e606b-7f44-4b66-97a1-e30a703654a0)   
 [Öffnen und Speichern von Projekt Elementen](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Projekt Persistenz](../../extensibility/internals/project-persistence.md)   
 [Elemente eines Projekt Modells](../../extensibility/internals/elements-of-a-project-model.md)   
 [Projekt Modell-Kernkomponenten](../../extensibility/internals/project-model-core-components.md)   
 [Erstellen von Projekttypen](../../extensibility/internals/creating-project-types.md)
