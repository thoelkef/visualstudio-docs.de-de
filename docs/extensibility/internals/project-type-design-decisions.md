---
title: Projekttypentwurfsentscheidungen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e33ac1c4168593b881f799dfdfb94005fb55fc1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706374"
---
# <a name="project-type-design-decisions"></a>Entwurfsentscheidungen bei Projekttypen
Bevor Sie einen neuen Projekttyp erstellen, müssen Sie mehrere Entwurfsentscheidungen für Ihren Projekttyp treffen. Sie müssen entscheiden, welche Elementtypen Ihre Projekte enthalten, wie Projektdateien beibehalten werden und welches Verpflichtungsmodell Sie verwenden.

## <a name="project-items"></a>-Projektelemente
 Wird Ihr Projekt Dateien oder abstrakte Objekte verwenden? Wenn Sie Dateien verwenden, handelt es sich dann um referenzbasierte oder verzeichnisbasierte Dateien? Werden die Dateien oder abstrakten Objekte lokal oder remote sein?

 Bei den Elementen in einem Projekt kann es sich um Dateien oder um abstraktere Objekte wie Objekte in einem Datenbank-Repository oder Datenverbindungen über das Internet handelt. Wenn es sich bei den Elementen um Dateien handelt, kann es sich bei dem Projekt entweder um ein referenzbasiertes oder um ein verzeichnisbasiertes Projekt handelt.

 In referenzbasierten Projekten können Elemente in mehr als einem Projekt angezeigt werden. Die tatsächliche Datei, die ein Element darstellt, befindet sich jedoch nur in einem Verzeichnis. In verzeichnisbasierten Projekten sind alle Projektelemente in der Verzeichnisstruktur vorhanden.

 Lokale Elemente werden auf demselben Computer gespeichert, auf dem die Anwendung installiert ist. Remoteelemente können auf einem separaten Server in einem lokalen Netzwerk oder an anderer Stelle im Internet gespeichert werden.

## <a name="project-file-persistence"></a>Projektdateipersistenz
 Werden Daten in gängigen Flatfile-Systemen oder im strukturierten Speicher gespeichert? Werden Dateien mit einem Standardeditor oder einem projektspezifischen Editor geöffnet?

 Um ihre Daten beizubehalten, speichern die meisten Anwendungen ihre Daten in einer Datei und lesen sie dann zurück, wenn ein Benutzer die Informationen überprüfen oder ändern muss.

 Strukturierter Speicher, auch zusammengesetzte Dateien genannt, wird normalerweise verwendet, wenn mehrere COM-Objekte (Component Object Model) ihre persistenten Daten in einer einzigen Datei speichern müssen. Mit strukturiertem Speicher können mehrere verschiedene Softwarekomponenten eine einzelne Festplattendatei gemeinsam nutzen.

 Sie haben mehrere Optionen, die Sie hinsichtlich der Persistenz für die Elemente in Ihrem Projekt berücksichtigen können. Sie können eine der folgenden Optionen ausführen:

- Speichern Sie jede Datei einzeln, wenn sie geändert wurde.

- Erfassen Sie viele Transaktionen in einem einzigen **Speichervorgang.**

- Speichern Sie Dateien lokal, und veröffentlichen Sie sie dann auf einem Server, oder verwenden Sie einen anderen Ansatz zum Speichern von Projektelementen, wenn das Element eine Datenverbindung zu einem Remoteobjekt darstellt.

  Weitere Informationen zur Persistenz finden Sie unter [Projektpersistenz](../../extensibility/internals/project-persistence.md) und [Öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md).

## <a name="project-commitment-model"></a>Projektverpflichtungsmodell
 Werden persistente Datenobjekte im Direktmodus oder im Transacted-Modus geöffnet?

 Wenn Datenobjekte im direkten Modus geöffnet werden, werden Änderungen, die an den Daten vorgenommen wurden, sofort übernommen oder wenn der Benutzer die Datei manuell speichert.

 Wenn Datenobjekte mithilfe des Transacted-Modus geöffnet werden, werden Änderungen an einem temporären Speicherort im Arbeitsspeicher gespeichert und erst dann festgeschrieben, wenn der Benutzer die Datei manuell speichert. Zu diesem Zeitpunkt müssen alle Änderungen zusammen erfolgen, oder es werden keine Änderungen vorgenommen.

## <a name="see-also"></a>Weitere Informationen
- [Prüfliste: Erstellen neuer Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md)
- [Projektpersistenz](../../extensibility/internals/project-persistence.md)
- [Elemente eines Projektmodells](../../extensibility/internals/elements-of-a-project-model.md)
- [Hauptkomponenten eines Projektmodells](../../extensibility/internals/project-model-core-components.md)
- [Erstellen von Projekttypen](../../extensibility/internals/creating-project-types.md)
